---
layout: post
title: Short, fast micro-whois
date: Mar 21, 2009
---

90% of my whois queries are to check whether a domain name is registered, where I don't need any details. Here's a Bash function to check domain availability; type one character, get one character.

**Problem**: I want a responsive checker that I can start in an instant, with almost no typing. It should be omnipresent: accessible from as many desktop windows as possible, without task switching. Rather than showing details, output should be short so I can see my query history evolve. And since most domains are registered (and I want to get past them), response time matters for registered domains more than available ones.

**Solution**: I have this bash function in my .bashrc (update: two versions by request -- shell script and Ruby). You can [download micro-whois here](http://gist.github.com/82956).

<script src="https://gist.github.com/troy/82956.js"></script>

and voila, zero-effort domain name availability:

    $ d yort.com
    1
    $ d ihopethisonedomainisnotregistered.com
    0

Registered:

    $ time d yort.com
    1 real 0m0.260s

    $ time whois -n yort.com
    .. [ 60 lines ]
    real 0m0.782s

Unregistered:

    $ time d ihopethisonedomainisnotregistered.com
    real 0m0.649s

    $ time whois -n ihopethisonedomainisnotregistered.com
    real 0m0.657s
