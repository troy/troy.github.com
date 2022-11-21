---
layout: post
title: "Clearer permission message for Chrome new tab extensions"
date: 2014-08-16 10:38:02 -0700
---

In creating Taco's [Chrome extension](https://tacoapp.com/chrome), I
became familiar with Chrome's permission system. An extension defines
the information it accesses, like request history, and Chrome shows
permission-specific descriptions to end users when they try to install
it.

I recently added the
[topSites](https://developer.chrome.com/extensions/topSites) permission
to Taco's extension, which grants very limited access: the URLs and page
titles of the 20 most frequently visited sites. It's the information
shown on Chrome's new tab page.

When I added this permission, here's what Chrome presented to users (as
reported by a justifiably surprised user):

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/tacoapp">@tacoapp</a> The reason I ask is that it states on your website that the extension &#39;can&#39;t access your browsing data&#39;… <a href="http://t.co/9EUFn4TrW5">pic.twitter.com/9EUFn4TrW5</a></p>&mdash; Adam Sait (@adamsait) <a href="https://twitter.com/adamsait/statuses/500257116566085632">August 15, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

"Read your browsing history" isn't an accurate description of the access
Taco has, especially when a different permission level ("history")
exists which does grant exactly that. I'm sure that led some users to
uninstall the extension instead of upgrading and granting this
permission, so I wanted to solve the problem for other users like this
person and for other extension authors.

I found [this](https://code.google.com/p/chromium/issues/detail?id=362794)
Chromium issue about improving permission descriptions and posted 
[a request](https://code.google.com/p/chromium/issues/detail?id=362794#c15)
and a followup [justification](https://code.google.com/p/chromium/issues/detail?id=362794#c17),
both duplicated below. The justification led to Chromium 
[issue 404334](https://code.google.com/p/chromium/issues/detail?id=404334)
to change the description to something clearer, like "Read a list of the
20 sites you most frequently visit."

---

### Comment #1 ([original](https://code.google.com/p/chromium/issues/detail?id=362794#c15))

Our users encountered this problem. Namely, as
[permission warnings](https://developer.chrome.com/extensions/permission_warnings#warnings)
says, the `topSites` permission causes users to see the same user-facing
description as the `history` permission, even though it has far, far
less access.

Both permissions say it's possible to "Read and modify your browsing
history." While that's accurate for the history permission, for
topSites, it should say something like "Read the 20 most frequently
visited URLs" or "Read most frequently visited URLs."

(If one wanted to be really user-friendly, I could see checking for
`newtab` in `chrome_url_overrides` and adjusting the message for that,
like "Read most frequently visited URLs (such as for new tab pages)" or
linking to a page which says same.)

Anyway, end result is that right now, end users can't tell the
difference between two permissions which should involve very different
amounts of trust.

---

### Comment #2 ([original](https://code.google.com/p/chromium/issues/detail?id=362794#c17))

Thanks for the fast reply and thoughtful comments, Mustafa. I totally
agree that none of these is universally perfect. I do think there's 3
challenges with the current (new) topSites description:

1. When interpreted by almost any user, it's inaccurate. No user thinks
of "browsing history" as "the most frequently accessed sites," let alone
"the sites on my new tab page." It uses a phrase ("browsing history")
which, while obviously not intentionally wrong, doesn't mean what it's
intended to.

    Here's an example I encountered today: 
[tweet](https://twitter.com/adamsait/status/500242045701988353). Nobody
thinks "browsing history" means "URLs of top 20 sites." This manifests
in lower user satisfaction because users decline to use extensions
they'd actually be comfortable with.

2. Users can't differentiate between 2 very different permission levels.
By conflating two very different amounts of access (`topSites` and
`history`) into the same single message, a user isn't told the difference.
Many, maybe a majority of, users who would be uncomfortable granting
history would be completely comfortable granting topSites.

    In as much as the goal of the permissions system is to let users make
informed decisions, two very different amounts of access should be
described differently. (The corollary of this argument: if they aren't
different enough to justify different descriptions, we might as well
obsolete topSites and exclusively use history. I don't think that at
all, though!).

3. It deters extensions from using topSites, or would if extension authors 
knew about this problem ahead of time. I just released an update to a new 
tab page which started using `topSites`
([tweet](https://twitter.com/tacoapp/status/500268474560946177)). If I'd
known 24 hours ago what I know now about the permission wording, I would
not have added topSites support to our extension. Because it's so
generic, the user message is scarier than the feature justifies.
