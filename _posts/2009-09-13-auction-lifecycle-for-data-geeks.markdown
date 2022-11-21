---
layout: post
title: Auction lifecycle for data geeks
date: Sep 13, 2009
---

I collected stats from my first sell-side eBay transaction: number of watchers, number of bids, and current item price. Here's what I found: 

![Auction Watchers, Bids, and Price Over Time](http://images.yort.com/blog/auction-lifecycle-1.png)

Specifics: eBay, 7 day duration, start $0.01, no reserve, $167.50 sale, digital camera, July 2009

### 30-second Summary

* 30-50% of prospects are trolling for a bargain that probably doesn't exist

* May be an untapped strategy in bidding at 70% of sale price to "stake a claim"

* Last-minute emotions didn't affect the price much

* 7 days may not be long enough for all prospects to discover


### What's noteworthy?

#### Ratio of watchers:bids (casual interest:purchase intent)

For most buyers, this auction was a 2-stage process: find & watch, wait a couple days, then monitor & bid. Visible interest accumulates for 2.5 days, peaking at 11 watchers per 1 bid, then steadily drops to 1.5:1 at sale.

As the end approaches, there are far fewer lookie-loos relative to participants - most have either bid or left (un-watched) - and the ratio sinks. Nobody bids upfront, probably from past experience: each person knows nobody else will bid, so they just watch too.

![Ratio of Auction Watchers, Bids, and Price](http://images.yort.com/blog/auction-lifecycle-2.png)

#### Ratio of price:bids (strength & frequency of purchase intent)

Because bidding is idle in days 2 and 3, this ratio starts and stays high ($17 of item price per 1 bid). Then bids trend smaller for 2 days, dropping to an average of $7 per bid. Just like a regular auction, the price increase per new bid is smaller later in the auction, though the absolute price increase is large thanks to lots of bids.

Only in the last hour does the dollars per bid spike again, and only in relative terms - small change that happens very quickly. That's the sniper, who must overshoot because there's only one chance to snipe. A larger spike here would indicate a desperate sniper.

#### Ratio of price:watchers (strength & frequency of casual interest)

This stays pretty constant throughout the auction until it rises in the last 2 days  I interpret that as bargain hunters bailing (un-watching) while bidding heats up.


### Analysis

Watchers is linear for the first part of the auction, then bargain hunters start to realize they're not going to get a steal. They adapt: they un-watch the item before it ends.  Watchers started dropping about 12 hours before the auction ended, when the price was at about 60% of final sale price.  This shows that some buyers still think it's a good use of time to hunt for undervalued items. That's a challenge with sub-$200 commodity gadgets.

Assuming our sample size of 1 was representative, one could fit a line to the price ramp and estimate the ending price of a halfway complete auction. This actually might not be far off, at least for auctions matching the same specifics (duration, reserve, category, etc.)

3 bids arrived in the last 40 seconds, yet those were the only bids in the last few hours. I checked the history of automatic bids (where eBay rebids up to your max allowed amount) vs. user-entered ones: only 2 people (winner and 1 other bidder) were online at 11 AM when the auction ended. Only one of them bid until the last 10 seconds. Unlike live auctions, last-minute emotions didn't affect the price much.

This reinforces that online auctions aren't impulse-driven, at least for smaller items that can't draw enough live users to start a bidding war. Someone may get caught up in their own re-bidding midway through the auction, and there's an adrenaline rush for those few who actively bid when it ends, but in this auction there wasn't any going-once gavel pounding.


### Conclusions

Although the winner asked me a question 2-3 days in, their first and only bid was 7 seconds before the end. This was destined to be sniped from the very start.

No one jumps in and makes a semi-serious bid (say, over 60% of final price) before they need to. The serious prospects believe that by placing a real bid, they'll increase the baseline and consequently the sale price. In a sense, we're telling ourselves that we might get a steal by not bidding, and that other people's bid increases are based on the current price more than their willingness to pay.

That may be true when many buyers are already watching an item. However, I could see making a bid on day 1 that's 70% of final value, and thereby decreasing the number of people who bother to watch it. Basically, you'd claim the item for yourself, like bluffing in poker. Assuming the higher first bid translated into fewer watchers, I could see that keeping the final price lower.

Prospective bidders may have still been discovering the item 7 days in. The number of watchers never really flatlined. While the total number of watchers dropped at the very end, we can't tell whether those folks un-watching were partially offset by new watchers. Based on how quickly the watchers dropped in the final 12 hours, I'm guessing the short flat-lining was driven by the auction ending.

Would more people watch an 8 or 9 day auction?  Probably.  Whether one of those watchers would be willing to pay more is a much harder question.


### Ideas

Because eBay doesn't provide an in-depth event history, we don't know when the 2 ending bidders watched the item, nor how they found it (search? what keywords? browse? which category?). A deep "event log" with timestamps, referral reason, and username could let sellers write custom auction strategy management tools - innovate on selling strategy rather than logistics or sourcing.

I could see charging for that post-transaction visibility, since pro sellers are the only ones likely to refine listing strategy, and presumably they're receiving higher sale prices. Bigger challenge: Prospective buyers would need to acknowledge a warning that their watch interest would be made available to the seller, whether or not they actually bid.

About 1 in 3 watchers explicitly un-watched this item in the few days after it ended, rather than letting eBay roll it off their watch list. This may mean that eBay can to do a better job of post-auction cleanup or item segmentation, or that 1 in 3 people are really pedantic.

There's still room for an auction format which ends 10 minutes after the final bid. Such a hybrid of "buy it now" and traditional auctions that might actually speed the auction up - nobody will be motivated by end time, and that could front-load the bidding. Wouldn't take much to be more front-loaded than this auction was.

***Note***: Bid amount is public-facing current bid, and includes automatic bid. By default, eBay post-auction bid history does not include automatic bids.