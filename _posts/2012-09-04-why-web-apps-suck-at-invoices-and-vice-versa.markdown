---
layout: post
title: Why Web apps suck at invoices (and vice versa)
date: Sep 04, 2012
---

On the [Scout](https://scoutapp.com/) support [mailing list](https://groups.google.com/group/scoutapp), a prospective customer asked to receive an invoice instead of the typical credit card payment. I have some unique experience with that, so I posted the comment below as food for thought (see [thread](https://groups.google.com/group/scoutapp/browse_thread/thread/660f3ade8bcd5928/e3dce7fb91a7d1b2?#e3dce7fb91a7d1b2)).</p>

This is "Why Web apps suck at invoices" and "Why invoices suck for Web apps," all rolled into one. Next time someone requests an invoice, send them here.

* * *

Subject: invoice billing (was: Re: Fees for Rails Apps..)

I'm not affiliated with Scout except as a customer, but I run an unrelated subscription Web service that sells to businesses and I'm occasionally asked the same question. It sounds like a really simple request, so I can understand the frustration at not being able to accommodate it.

I wanted to add some color about how challenging it is to provide invoices. I'm speaking only about my experience, not Scout's. Here's why this is often a much bigger pain than it looks like, and is often actually a disadvantage to both parties:

* Everything is a one-off. Almost everyone who wants an invoice also needs some other customization: the delivery process, the followup, the formatting ("We're in Germany and our government requires you to tell us who we are"), whatever. Aside from tracking those one-offs, they makes it harder to solve or automate the other issues below. Which leads me to..

* Everything requires a human. If you don't pay, a human has to email you, and it will almost never be worth the time to automate that process (especially in light of customer-specific processes above). Even something as simple as a credit becomes a time sink. A human needs to figure out how much is due (best case, transferring the amount from a summary email that a developer had to implement; worst case, calculating it manually); figure out how to get you the money (edit a future invoice, reissue an existing invoice, or cut you a check); deliver that credit, probably to someone in accounting who doesn't know anything about what's being purchased; process the payment; and come back a few weeks later to verify it was paid.

* Someone has to go to the PO Box and then to the bank, and it needs to happen often enough that you don't look like an idiot for depositing a 2 month old check.

* Reconciliation is harder. Accounting typically needs an entry for every individual customer payment, rather than one per day per credit card or however other transactions are handled.

* Having an elastic payment method is really awesome, and our service and many others bake that assumption into our UX decisions and business processes. By "elastic" I mean that the amount isn't set in stone a month before the service is provided. What should happen if you add a new host that you didn't plan for? Does the vendor extend credit, or do they issue an invoice with a pro-rated line item and make you wait until it's paid? How about 100 new hosts? Before long, the customer is predicting and committing to a certain amount of usage, quite possibly just to make billing simpler, and we've undone 15 years of software-as-a-service progress.

* All of this distracts from making the product better. Whether a company has 2 people or 100, the resources are finite, and at some level any other work is in place of product improvements. No Web service will ever be great at invoicing, most will never be good at it, and not one will ever enjoy it. That "morale debt" accumulates.

* The overhead will eventually be reflected in prices, and it's way higher than the ~3% for credit cards. This thread started as a question about fees. One reason that Scout is such a good value is that their decisions mostly optimize for practical value. Building off its usage-based fees, would you be willing to pay a $25/invoice fee, and/or have a $500/invoice minimum? From my own experience, that's the absolute minimum it takes to make this practical, and I'm probably still way too low.

None of this is rocket science, it just takes time, and that's why invoices suck for typical business subscription services. I consider it a positive that Scout is savvy enough to focus on what they're good at.

Finally, a potential solution: get a company card that's only used for recurring purchases like this. You're freed from monthly employee expense reports and accounting gains authoritative information about the transaction, since it's essentially their card.