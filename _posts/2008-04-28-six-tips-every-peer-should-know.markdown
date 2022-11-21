---
layout: post
title: Six tips every peer should know
date: Apr 28, 2008
---

A gaggle of Seattle network operators converged in one room last week, for the annual Seattle Internet Exchange (SIX) members meeting. As a janitor and board director, I was already preparing a handout, so I used the back side for six SIX tips.

#### How TCP sliding windows and the bandwidth*delay product works

Given the desired throughput of a TCP connection and its round-trip time, the [bandwidth*delay product](http://en.wikipedia.org/wiki/Bandwidth-delay_product) is the minimum [TCP window size](http://www.rhyshaden.com/tcp.htm) that each endpoint (host) must support in order to transfer at that throughput. Trying to saturate a 100 Mbps cross-country MPLS VPN with a single HTTP transfer?

    BDP = bandwidth * RTT

    100 Mb/sec * 70 ms = 12,500,000 bytes/sec * 0.070 sec = 875,000 bytes

Each endpoint's OS TCP window size must be at least 875 KB, or it will be the bottleneck.

#### Enlightenment through iperf

iperf beautifully solves two problems. First, how to generate a fixed amount of traffic and measure packet loss at that rate. "Send 30 Mbps of UDP to this IP, regardless of TCP congestion control, packet loss, or anything else."  Second, how to simulate a TCP flow given different parameters (bitate, window size).

#### See whole packet payload, not just headers, with tcpdump

Most folks have used tcpdump to show packet headers. Even handier for diagnosing protocol-related problems is to print the full payload. To disable reverse DNS lookups, sniff eth0, print the payload, and sample whole packet: `tcpdump -n -i eth0 -X -s 0`

#### Find a LAN IP's port without tracing cables

Get the MAC address. Using another system or router on the same segment, generate traffic to the IP in question. First, get its MAC: `arp -a` or `show arp`. Then find the MAC. In IOS: `show mac-address-table address 00ff.dead.beef`

#### 5 minute samples are almost meaningless for many traffic profiles

While measuring usage counters every 5 minutes works wonderfully for calculating total traffic passed, in many cases it leads to wildly inaccurate throughput estimates. 5 minute averages round off most useful granularity; when a circuit's 5 minute average usage is over 50%, it may already be the bottleneck for on microsecond granularity, depending on number of endpoints, traffic profile, serialization time, and other characteristics.

Try polling 1 device on a 1 minute or 30 second sample and prepare to be amazed.

#### Filtering ICMP is not a security requirement, and in fact doesn't improve security.

It's just really annoying. If you must filter, allow the types  required for basic operation, like TTL Exceeded and Host/Port Unreachable.