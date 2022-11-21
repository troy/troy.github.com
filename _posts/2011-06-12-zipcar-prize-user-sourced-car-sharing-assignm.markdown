---
layout: post
title: ! 'Zipcar Prize proposal: user-sourced car sharing planning algorithm'
date: Jun 12, 2011
redirects:
- /zipcar-prize-user-sourced-car-sharing-assignm
---

**Update (December, 2012)**: [Car2Go](http://car2go.com) seems to be trying this and even uses municipal parking spaces, so trips could end essentially anywhere.

[Zipcar](http://www.zipcar.com/) customers must return a car to the same parking spot that it was borrowed from. That means customers must rent (and pay for) one specific car for their entire trip, even when it will be parked in an urban area for many hours during the trip.

In 2009, I emailed Zipcar about cloning [The Netflix Prize](http://www.netflixprize.com/) for a similar purpose: crowd-sourcing (really, expert-sourcing) a set of algorithms, incentives, and restrictions that would let Zipcar offer one-way rentals. Like Netflix, The Zipcar Prize would release an anonymized set of trip data, parking space locations, and an evaluation method (which might emphasize certain aspects, as Netflix [did](http://www.netflixprize.com//faq#prize)).

This would be a mix of:

* **incentives**: "We'll discount $2 for returning it a mere 5 blocks away from your preferred location"
* **fees**: "Returning to this location will cost $4 more"
* **enforced policies**, like: must reserve 1 day in advance; one-way trip can't leave a lot empty; only offered at certain urban lots (initially)

The email after the jump has lots more details (slightly formatted and edited). As far as I know, no one has tackled this. Zipcar hasn't and I didn't receive a reply.

The first car-sharing service to pull it off will have an amazing competitive advantage: paying for only what you actually need and the ability to **get** a car to the right place at the right time.

* * *

Hi \<Zipcar executive\>,

Hope this finds you well. I signed up for Zipcar and found that it didn't have the killer feature for me: the ability to return a car to a different lot, even if that spot had to be selected at reservation time. [This tweet](http://twitter.com/troyd/status/3625900233) has a bit more.

Nothing new there, but here's why I'm emailing. Wishing for this feature (and not finding it in the [FAQ](http://www.zipcar.com/how/)) led me to wonder whether, as a technical and generally creative guy, I could try my hand at a skunkworks location/availability optimization for returning cars to a second location. Specifically, at:

* minimizing additional parking spaces
* maximizing availability of at least 1 car at every lot
* minimizing distance between user's requested destination lot and system's permitted destistination lot

The first hard part is getting a machine-parsable, anonymized rental history and lot locations, which is why I'm emailing. With an anonymized rental history (where users are identified by GUIDs) and "home" car locations, I or anyone could make 5 or 10 fake scenarios where some percent of users request different destination lots at time of reservation.

It could play out like a [Netflix Prize](http://www.netflixprize.com/) for scheduling. Zipcar would get a ton of press, customers would try to solve one of your most intriguing scale problems, it would go a long way to associate Zipcar with open source and open government (which the Flexcar brand had a stronger association to), and it would cement Zipcar's justification for a $50 late fee as necessary rather than onerous.

At least in metro Seattle, I think you have enough cars to pull it off, especially with a few restrictions, like that you can't return a car to a different destination lot when it leaves the origin lot empty (because all other cars there are already reserved). That restriction would reduce - potentially avoid - any decrease in local coverage, preserving customer satisfaction.

Moreover, that restriction would motivate people to make one-way reservations farther in advance, which would let the system guide folks to alternative destination lots ("You're starting in Ballard. We can't let you return it to 4th & Wall, but we'd love for you to return it to 2nd & Vine 5 blocks away.").

I could even see a $X tax on same-day alternative destination lot reservations, although that negates some of the long-term value it would create for Zipcar. Eventually, you'd want everyone using this with reckless abandon, since it turns customers into your car gofers and makes otherwise-impractical trips affordable.

If something like a Netflix Contest is interesting, or you already have these data files), please let me know.