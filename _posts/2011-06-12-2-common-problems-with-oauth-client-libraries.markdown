---
layout: post
title: 2 common problems with OAuth client libraries
date: Jun 12, 2011
---

I posted a long [explanation](http://groups.google.com/group/fusion-tables-users-group/msg/535854503fa21868) to the fusion-tables-users group about using third-party libraries with Fusion Tables over OAuth. It might also help folks debugging OAuth problems or adding OAuth support to existing libraries. Full text below.

* * *

Just an update for the archives and anyone else debugging this. I went through the [Python example](http://code.google.com/p/fusion-tables-client-python/source/browse/trunk/src/samples/oauth_example.py?r=16) and it does work for POST requests in the body. I tested CREATE and INSERT.

Here are the 2 things that were tripping up the Ruby GData library coupled with someone's monkeypatched OAuth auth_handler (`GData::Auth::OAuth`). They basically boil down to not being designed for, or frequently used with, POST requests. From skimming other libraries, these problems are endemic to lesser-used OAuth libraries.

Here goes:

1. The `GData::Auth::OAuth` only pulled out GET params from the URL, not POST params in the request body. POST params need to be sorted alongside the OAuth parameters when creating the signature base, so this immediately made my signatures invalid.

    I saw a couple causes for this in other libraries:

    * designing for GET and then exposing a convenience POST method as&nbsp;an afterthought (without looking at the body params)
    * one person wrote the HTTP client, another wrote the OAuth signer, and a third wrote the Fusion Tables library or GData extension, and a corner case got missed (or callers can sign requests before a body is even defined)

2. Most language built-in URI encoders are designed for [x-www-form-urlencoded](http://www.w3.org/TR/html401/interact/forms.html#h-17.13.4.1), with spaces as plus characters. OAuth wants everything UTF-8, ie `U+0020` or `%20` for space. The confusing part for Fusion Tables is that this works in GET requests: [select+*+from+317391+limit+1]("https://www.google.com/fusiontables/api/query?sql=select+*+from+317391+limit+1")

    .. but that space encoding won't work in OAuth signature hashes (and thus not the request body itself), and will show up as 401 Unauthorized rather than an app error. If you're adapting an existing Fusion Tables library to work with OAuth, this is something to consider.

Finally, if it helps anyone, here's a signature base string for a CREATE statement (private values replaced), for the table schema in the Python example code:

    POST&http%3A%2F%2Fwww.google.com%2Ffusiontables%2Fapi 
    %2Fquery&oauth_consumer_key%3Ddomain.com%26oauth_nonce 
    %3D75556368%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp 
    %3D1305155510%26oauth_token 
    %3D1%252F98y2rqyfdfhuaiheworh327rahyADYSAIYuioydadio%26oauth_version 
    %3D1.0%26sql%3DCREATE%2520TABLE%2520%2527data.csv 
    %2527%2520%2528%2527col2%2527%253A%2520STRING%252C%2527col3%2527%253A 
    %2520STRING%252C%2527col1%2527%253A%2520STRING%2529

that signature string is for the param:

    sql=CREATE+TABLE+%27data.csv%27+%28%27col2%27%3A+STRING%2C%27col3%27%3A+STRING%2C%27col1%27%3A+STRING%29

I've tested OAuth POST requests sent as the HTTP Authorization header as well as in the body of the POST, and both work.