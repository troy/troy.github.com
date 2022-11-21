---
layout: post
title: Making 2-factor authentication grow faster than linear
date: Jul 16, 2012
redirects:
- /making-2-factor-authentication-viral
---

I'm doing what I can to spread the gospel of 2-factor authentication. My hope is that it will be adopted at a faster-than-linear rate, ideally much faster.

2FA isn't a silver bullet, but it's a gigantic improvement for relatively little effort. The elements that prevented mainstream adoption - key fobs, constantly re-entering keys - are not present in modern implementations like Google's. With most of the usability tradeoffs eliminated, we're left with a fairly typical sales problem (and of course, more operators implementing Google's 2FA or an equally elegant alternative).

For my part, "doing what I can" means:

* requiring 2FA on systems I maintain, at least where SSH keys aren't practical or aren't sufficient

* sharing my success stories, especially how I solved common objections to 2FA (it's annoying to use; I only have a few users; it's a pain to setup)

* helping others find accurate, deep descriptions of current threats (like [Krebs on Security](http://krebsonsecurity.com/)) so they treat malware and botnets (and thus keystroke logging) as an endemic threat

I think with enough satisfied users as advocates, 2FA could grow exponentially for a while (albeit with a [tiny base](http://www.wolframalpha.com/input/?i=1.03%5Ex) today). Google has basically turned 2FA into an impulse decision with a simple pitch: "Have 5 minutes? Use wifi hotspots? Protect your email from hackers (free)." I'd settle for [logistic growth](http://en.wikipedia.org/wiki/Logistic_function) up to something short of 100% adoption, though I'm not sure a hard [carrying capacity](http://20bits.com/article/three-myths-of-viral-growth) exists. Future incremental usability improvements should make it palatable for more people.

Sales starts with awareness: that it exists, that it's already being used by seemingly-sane people to solve similar problems (indeed, [social proof](http://en.wikipedia.org/wiki/Social_proof)), and that it stands up to daily production use. Here's an email that I sent to the Seattle Internet Exchange [chat](http://www.seattleix.net/faq.htm) mailing list.

* * * 

To: chat@

Passing this on in case anyone else could use flexible, painless, free 2-factor auth for servers and network devices.

I've been testing Google's 2-factor authentication via a [PAM](http://code.google.com/p/google-authenticator/wiki/PamModuleInstructions). It's working beautifully. Google has iOS, Android, and Blackberry one-time password [apps](http://support.google.com/accounts/bin/answer.py?hl=en&amp;answer=1066447). Ubuntu and Debian package the module as libpam-google-authenticator. During setup, it spits out the key as an ASCII QR code that the mobile apps read.

I haven't tried having RADIUS use google-authenticator's PAM, but it seems like it would work. Other people talk about using it: [](http://code.google.com/p/google-authenticator/issues/detail?id=145).

By default, SSH with challenge/response prompts for the challenge first (with a prompt of its own), but PAM supports a [concatenated mode](http://code.google.com/p/google-authenticator/issues/detail?id=39) where the OTP is prepended to the static secret. This should play well with network devices that present a single password prompt. Google's module validates the OTP, then passes the secret on to the next module as usual.

Also, SSH authorized keys still work (assuming the SSH config permits them), so you can decide how annoying one-time passwords will be.

Finally, worth noting that this setup is completely separate from having a Google account. An account isn't required. This setup uses Google's mobile app implementation of [time-based one-time passwords](http://tools.ietf.org/html/rfc6238), the app's ability to import your own key(s), and a PAM that they maintain, all of which are [OSS](http://code.google.com/p/google-authenticator/source/browse).