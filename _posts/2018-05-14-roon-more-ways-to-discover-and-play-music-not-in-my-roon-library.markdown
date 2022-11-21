---
layout: post
title: "Roon: More ways to discover/play music not in my Roon library"
date: 2018-05-14 10:40:08 -0700
---

I recently started using [Roon Labs](https://roonlabs.com/) and [posted this suggestion](https://community.roonlabs.com/t/more-any-ways-to-discover-play-music-not-in-my-roon-library/43136) in their customer Discourse forum.

Here's the suggestion:

---

Hey all, here's a wish and a few possible implementation ideas. Please understand that I'm spending the effort to write this down because I care about seeing Roon succeed, not because I want to slam Roon.

Also, as with any feature request, some of this is almost certainly wrong or doesn't apply to Roon's business :-)

## Summary

Make it easier - heck, make it possible - to play music that I haven't explicitly added to my library. At a minimum, expose Tidal's artist radio and track radio.

One step up from there, make navigating between Roon's version of an artist and Tidal's more seamless, like letting me see my favorited or frequently played albums on Roon's view of an artist (instead of a separate "Go to Tidal artist" dropdown choice and "Tidal artist" in search results).

One step up from there, let me treat Tidal as my Roon library, at least in concept if not in implementation.

Ideally, eliminate the idea of a binary "it's in or it's out" library entirely and split that into 2 concepts: music Roon has access to, and a continuum of opinions about that music (from love to hate). "The longer-term solution" has more on that.

## Background

 It feels like 10 or 15 years ago, the standard for music software was to play the music I had. Roon's current feature set is basically the perfect implementation of what I wanted, and would have been thrilled with, in about 2005.

In the last 10 years, a couple things changed:

* Access to music. Thanks to Tidal (and before it, Rdio, Spotify, etc.) "My library" is actually almost the entire North American music catalog. I don't have an "it's in or out" library (where anything in the library should never be played), I have a continuum of I love, like, am so-so about, dislike, or never want to hear again.
* Quality of that music. Tidal is as good or better than anything I'd ever have locally. In the last 2 years, lossless and MQA eliminated the last reason that music from other sources might not be as play-worthy as "library" music.
* Expectations. Between the size of someone's "library" (ie, all Tidal music) and the rise of machine learning, a computer (think Discover Weekly) can do a great job of finding new music I like -- way better than I'd do with manual curation, and good enough that I'd put my effort into correcting it rather than creating playlists myself.
* Publishing rate. The number of new songs appearing on even Tidal, let alone Spotify or Soundcloud, makes it impossible to listen to and curate new stuff even if I wanted to. I'd literally be listening to only new stuff just to decide whether I liked it.
* User persona. 10 years ago, Roon would have been most valuable to folks with hundreds of albums (in a sense, Roon depended on a substantial investment in media). Not only is that no longer true, it might not even be a predictor of/correlated with interest in music or playback portability anymore. Now that lossless subscriptions exist, I'd guess that an appreciation for audio quality (ie, lossless playback) plus ownership of more than 1 output are better predictors of suitability for Roon than, say, a desire or past experience collecting albums.

To boil this down: The idea of a binary "it's in or out" library was a byproduct of needing to collect albums or at least ripped MP3s. Today, the hard part isn't playing stuff that I know I like; that's table stakes. The hard part is surfacing new stuff that I didn't know I liked, and delivering a great playlist from the entire music catalog that (a) matches my mood or interests, and (b) doesn't require explicit curation. That's also the only viable way to surface new music at the scale it's currently released.

This is also where the market is going. In 3 years, the idea of a manually-curated library will feel even more outdated than it does now. Even if Roon considers music fanatics to be its only target user (and isn't ever trying to serve a more mainstream audience), having a manually-curated library is not correlated with that category anymore. And if Roon does want to serve a mass market at some point, it's a gatekeeper to doing that.

## The problem

Roon is built on the idea of a binary "in or out" library, which makes it difficult - actually, almost impossible - to play anything not in my library that I don't curate manually (say, manually creating a playlist or going to a specific album).

As an extreme example, if one uses Roon's "Focus" feature and the Focus only matches a single song in one's library, Roon will play that one song on a continuous loop.

Imagine if, instead of listening to an entire set from Imogen Heap, you want a multi-artist playlist of stuff similar to or related to her or a song of hers, across all music you have access to (ie, Tidal, not one's library). As I understand it and Roon's staff confirmed, there's no way to do that in Roon today.

The obvious example is dynamic artist or track-inspired radio, what Tidal calls "Track radio" and "Artist radio." These aren't currently exposed anywhere in Roon. So, my first and probably simplest wish would be new choices in the "Play" dropdown for "Track radio" and "Artist radio" that use Tidal's implementations of same.

## The longer-term solution

If one agrees with the factors in "Background," then having access to lossless versions of almost every song ever released should cause Roon to adapt. Today, the library serves 2 purposes:

1. Ability to play. Roon considers the library to be the music that it has access to (other than being specifically told to play an album not in my library)
2. Preferences. Roon considers adding something to my library as a proxy for my preferences. Music in one's library is presumed to be loved (it's the only music that Focus and Roon Radio will play), and music not in one's library is presumed to be hated (never played automatically).

These were never actually the same thing, though. Only item 1 - "Do I have a way to play this song?" - is binary. Item 2 is not binary. Right now, item 2 is treated as binary even though it's not, and item 1 isn't treated as a separate construct.

Using Roon's terminology, I want a way to add the entire Tidal catalog to my library. Obviously that's probably not the best actual implementation, but it's a good explanation. At that point, item 1 is actually correct (my library is all music that can be played, so Focus and Roon Radio can consider way more music), and item 2 would adjust based on ratings at playback.

In practice, it probably means splitting these two purposes. Item 1 becomes "Anything on a remote service that I have access to, plus anything I have locally" and might eliminate the concept of a library.

Hopefully obvious, but just to say it: none of this is mutually exclusive with local music storage. Someone with no Tidal subscription and purely locally-stored music is just a different set of item 1 -- it's no worse for them than today. The core concept is recognizing that for many Roon users, items 1 and 2 are actually separate concepts, so that for users who do have access to a ton of music (Tidal subscription), Roon automatically makes use of it.
