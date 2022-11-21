---
layout: post
title: Towards BPM-based "Exercise Radio" stations
date: Sep 25, 2009
highlight: true
---

**Update** (2015-11-23): Spotify has this! Check out
[Spotify Running](https://www.spotify.com/us/running/) for tempo-based
playlists and automatic tempo calculation.

Someone, somewhere has the metadata and music chops to deliver BPM-based radio streams. DJs and gym rats will follow. A couple ideas.

The closest are [Echo Nest's API](http://developer.echonest.com/) (`get_tempo`) and [Last.fm's](http://www.last.fm/api) API (`Track.getInfo`). Echo Nest's requires uploading the song audio data (which I don't have). Last.fm's can be queried with metadata (artist+song name) yet doesn't provide BPM. This NYTimes [Gadgetwise blog post](http://gadgetwise.blogs.nytimes.com/2009/06/19/marathon-tech-review-music-you-can-run-to/) has local file (MP3) and podcast options.

I posted this to the [Last.fm Web Services](http://www.last.fm/group/Last.fm+Web+Services/forum/21604/_/568730) discussion group, and [asked on Twitter](http://twitter.com/troyd/status/4352076414). I'll update this post if something comes of it.

* * *

I prefer to exercise to music, and it's much nicer when the beats per minute matches what I'm physically doing. I think this could happen 3 ways:

1. Faster/slower tempo adjustment of any station. This could be a really awesome subscriber feature.

2. Adding BPM as a new radio station "station type" (from [http://www.last.fm/api/radio](http://www.last.fm/api/radio) and exposing it in the UI as a Tempo dropdown. For example: lastfm://bpm/140

3. A third party app which creates/queues a playlist based on BPM. This would be almost entirely doable with the existing API (get similar artists, add to playlist) if `track.getInfo` included BPM.

    There's lots of docs for estimating BPM for a bitstream, but short of someone with a huge music collection, Last.fm would need to pregenerate them and expose it in the API. This API is particularly well thought out: [http://developer.echonest.com/docs/method/get_tempo/](http://developer.echonest.com/docs/method/get_tempo/) (but it too needs the bits; it's not an existing database).

    Mass BPM calculations would be a killer use for Map/Reduce.
