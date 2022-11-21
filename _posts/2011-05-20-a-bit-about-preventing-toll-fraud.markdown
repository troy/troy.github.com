---
layout: post
title: A bit about preventing toll fraud
date: May 20, 2011
---


Recently posted this reply to the voiceops mailing list. Pasted below or [read the original](https://puck.nether.net/pipermail/voiceops/2011-May/002499.html).

* * *

On Tue, May 17, 2011 at 3:53 PM, Darren Schreiber wrote:

> Hi folks,
> We have been hit twice in the past two days with calls to 011-252-XXXXXXXX
> (calls to Somalia I believe, and the originating IP is from Pakistan)

Others have suggested NCC-specific firewall policies. I'll put in a plug for using per-country-code dialplan routes and omitting really expensive countries.

Obviously that won't work for worldwide wholesale transport carriers. For everyone else, the most expensive CCs to call aren't worth the trouble. There are very few folks with legitimate needs to call, say, Sierra Leone, that aren't served by Skype. They don't represent enough revenue to justify the risk.

Those few legit higher-volume folks are willing to prepay using reliable methods. They're usually apologetic that their countries receive enough fraudulent calls to need such a policy.

Basically scroll through [http://www.voicetrading.com/en/calling-rates.html](http://www.voicetrading.com/en/calling-rates.html) and omit routes for any country that's had a civil war in the past 20 years. Fringe benefit: when a country code splits, you won't get caught with a rate deck hole (see Timor-Leste, St Maarten).

If you want to get slick, have a call attempt to those country codes page your admins as a honeynet (honeyroute?). Somebody's probably up to something.

Doesn't prevent calls to expensive mobile routes in countries you do reach, they're just a lot less interesting to fraudsters (woo, I can call Proximus!?) and the per-minute costs are mostly way lower.

Troy