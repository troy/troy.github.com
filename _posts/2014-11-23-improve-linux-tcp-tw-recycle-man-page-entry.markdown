---
layout: post
title: "Improve Linux tcp_tw_recycle man page entry"
date: 2014-11-23 09:01:38 -0800
---

We recently identified the cause of a problem affecting one of
[Papertrail's](https://papertrailapp.com) service providers. Their hosts 
occasionally could not establish TCP connections with a seemingly-random 
small set of Internet hosts.

Troubleshooting was difficult because:

* The affected hosts changed. One host would oscillate between being able to establish a connection for a 
few hours (or days) and not, seemingly with no pattern.

* I didn't have direct access to the service provider's hosts or the end 
users' hosts. This made reproducing the problem in a controlled environment 
basically impossible. "Paste the output of.." and "Run this packet capture.."
was what I had to work with.
* I couldn't draw conclusions from the end users who reported the problem.
Fewer than 5 users reported problems and they were biased towards inquisitive 
people (who investigated or reported the first occurrence) or those who 
experienced the problem multiple times. Presumably, some end users couldn't 
connect once and just tried again later.

Among this tiny pool, there was one common theme: the remote hosts traversed 
NAT. My investigation eventually led to `tcp_tw_recycle`, a Linux `sysctl` flag 
with [far more Google results](https://www.google.com/search?q=tcp_tw_recycle) 
than it deserves. Here's why.

### Linux TCP header verification

Modern Linux kernels verify that TCP header values meet certain requirements. 
These include "Protect Against Wrapped Sequence numbers" or PAWS, defined in 
[RFC 1323](https://www.ietf.org/rfc/rfc1323.txt), and 
[RFC 6191](https://tools.ietf.org/html/rfc6191) "Reducing the TIME-WAIT State 
Using TCP Timestamps."

With `tcp_tw_recycle` enabled, a connection's TCP header timestamp value is 
retained in cases where it otherwise would not have been kept. From 
[tcp_ipv4.c](https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/net/ipv4/tcp_ipv4.c?h=linux-2.6.32.y#n200):

```
if (tcp_death_row.sysctl_tw_recycle &&
    !tp->rx_opt.ts_recent_stamp && rt->rt_dst == daddr) {
        struct inet_peer *peer = rt_get_peer(rt);
        /*
         * VJ's idea. We save last timestamp seen from
         * the destination in peer table, when entering state
         * TIME-WAIT * and initialize rx_opt.ts_recent from it,
         * when trying new connection.
         */
        if (peer != NULL &&
            peer->tcp_ts_stamp + TCP_PAWS_MSL >= get_seconds()) {
                tp->rx_opt.ts_recent_stamp = peer->tcp_ts_stamp;
                tp->rx_opt.ts_recent = peer->tcp_ts;
        }
}
```

The problem: the TCP timestamp is only tracked on a per-remote-IP basis, yet
some NAT devices don't rewrite TCP timestamps in the translation process.
As a result, the Internet-facing IP of a NAT device may transmit valid packets 
with unrelated timestamps.

The problem we saw manifests when more than one remote host (for example, two 
employees on an office network) try to connect to this Linux host within a few
minutes of one another. The first connection will succeed, but the
second connection attempt (from the same public NAT IP) will fail. The
kernel considers its timestamp invalid.

In another function, a comment hints at the difference between tracking 
timestamps on a per-host basis and doing so on a per-port-pair basis. From 
[tcp_ipv4.c](https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/net/ipv4/tcp_ipv4.c?h=linux-2.6.32.y#n112):

```
/* With PAWS, it is safe from the viewpoint
   of data integrity. Even without PAWS it is safe provided sequence
   spaces do not overlap i.e. at data rates <= 80Mbit/sec.

   Actually, the idea is close to VJ's one, only timestamp cache is
   held not per host, but per port pair and TW bucket is used as state
   holder.

   If TW bucket has been already destroyed we fall back to VJ's scheme
   and use initial timestamp retrieved from peer table.
```

Note: I haven't read anywhere near all of Linux's TCP header source. If you 
find an error in this post, let me know.

### Root cause

Although that's the problem, the root cause is poor documentation. The two
places that a systems administrator is most likely to consult are 
the kernel [IP sysctl docs](https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/Documentation/networking/ip-sysctl.txt?h=linux-2.6.32.y#n438), which suggests consulting "technical experts":

```
tcp_tw_recycle - BOOLEAN
        Enable fast recycling TIME-WAIT sockets. Default value is 0.
        It should not be changed without advice/request of technical
        experts.
```

.. and the [tcp.7 man page](http://man7.org/linux/man-pages/man7/tcp.7.html), which says:

```
tcp_tw_recycle (Boolean; default: disabled; since Linux 2.4)
        Enable fast recycling of TIME_WAIT sockets.  Enabling this
        option is not recommended since this causes problems when
        working with NAT (Network Address Translation).
```

Neither of these explain what the option changes or how it interacts with
NAT. I've submitted [a patch](http://marc.info/?l=linux-man&m=141676013318902&w=2)
for the man page. The changed copy warns of the possible impact and says 
where to learn more.

> Enable fast recycling of TIME_WAIT sockets. Enabling this option is
> not recommended for devices communicating with the general Internet
> or using NAT (Network Address Translation). Since some NAT gateways
> pass through IP timestamp values, one IP can appear to have
> non-increasing timestamps. See RFC 1323 (PAWS), RFC 6191.

There's also a 2013 [BCP](https://tools.ietf.org/html/draft-penno-behave-rfc4787-5382-5508-bis-04#section-3.1.2)
("Network Address Translation Behavioral Requirements Updates")
which informs future NAT implementors of this consideration.
