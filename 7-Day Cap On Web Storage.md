---
title: 7-Day Cap on Web Storage
created: 2020-03-27
---

# Simple Tracking Prevention

[Recently Apple announced][] that in an attempt to enhance Intelligent Tracking Prevention (ITP), it would start deleting all of a website’s script-writable storage after seven days of Safari use without user interaction on the site.

Some of us [saw it as an obituary for (cloud-free) web][reaction by @gozala], others pointed out that [data was not safe in web storage][reaction by @jlongster] and had to be copied to the cloud anyway, yet some suggested that [historically data has never been safer in the cloud][reaction @by @pvh].

I would like to offer my view of the problem that Apple is trying to attack, elaborate why I do not believe it is going to be effective and propose a direction in a hope that builders of next generation systems may consider.

### Problem

Ads business is the lifeblood of the internet. Turns out tracking enables Ads to be more effective, feeding into growth of economic activity. I do not believe any tracking prevention efforts can be successful long term since sites we visit need to finance their operation. That is to suggest that changes announced by Apple may force change in how tracking is done, but it will continue never the less. There are plenty of techniques to [identify users][AmIUnique] without storing data, as it turns out even [cursor movements can reveal your identity][advanced-tor-browser-fingerprinting]. Just imagine what Google's advances in machine learning can do to [AdSense][].

More importantly tracking is not going away because web sites/services are complicit in enabling it and when they are not they loose their business to those that do. Even if browsers do succeed and prevent tracking on the client side, tracking can just migrate to the cloud where browsers can not prevent servers from reporting your web activity to network of trackers (Your email address is unique enough).

I understand Apple's perspective, they do not view web as an application platform that is App Store, so they get to claim better privacy (which has merit, especially if Ad business decides this isn't not worth hassle) and get more apps in their store.

### Solution ?

Ideally people will start paying for the web and that would address the problem, however that is not happening, not at large enough scale anyway. However there is another effective way to prevent tracking, instead of preventing (web) app from storing information make them incapable of sharing it.

Let's unpack that! If (web) app once loaded becomes local (installed service worker) losses ability to access network it is no longer capable to facilitate tracking. Now that is how applications were pre-internet, and that was not fun either. However, I think we can have our cake and eat it too!

Internet enabled use to share information and collaborate with one another online, and we could enable local (web) applications to do that by substituting capability to dial servers with capability to share stored data and empower users to choose with whom. To make it more concrete User Agent would:

1. Allow apps to store data locally (encrypting it without sharing keys with app)
2. Replicate encrypted data through a service of users choosing (we could probably even extend [SMTP][] to do this everyone has email already).
3. Prevent apps from talking to any cloud (otherwise that that would undermine above 2).

This effectively shifts role of the server from being the "Authority" to a dump pipe that it should have been in first place.

### Decentralization isn't enough

Solution might resemble what my peers in decentralized web are building and that is no coincidence! I do however think that there are some very important details that ofter get overlooked, so I would like to call those out:

1. Web was not envisioned the way we are experiencing it today. It is market forces that deformed it by exploiting its weakness. That is to say beautiful picture that pioneers envision will be distorted.
2. Many decentralized systems today decentralizes tracking along the way. Most use [Distributed Hash Tables (DHT)][DHT] [which can be used for tracking][DHT privacy]. (There are [ongoing effort][hashmatter] to address this).

Many new and exciting protocols seem to assume that restricting what applications can do is bad idea and assume that carrot will do the job! I am afraid that is naive, external forces can and will bend them against their will so it is fundamental to design system such that serves people not merely chooses to do so.

### Epilogue

As André Staltz has suggested [The Web began dying in 2014][Web began dying], after this announcement I can not help, but think that web is beyond recovery. It hurts, but death is integral part of lifecycle. Let's make sure that the void left is filled with something that is just as open, but more resilient, because we learned from our mistakes.



[DHT]:https://en.wikipedia.org/wiki/Distributed_hash_table Distributed hash table 

[web-storage-cap-announcement]:https://webkit.org/blog/10218/full-third-party-cookie-blocking-and-more/ "Webkit announcement regarding enhancements to Intelligent Tracking Prevention (ITP)"
[reaction by @pvh]:https://twitter.com/pvh/status/1242863246756872192?s=20
[reaction by @jlongster]:https://twitter.com/jlongster/status/1243206400924192773?s=20
[reaction by @gozala]:https://twitter.com/gozala/status/1242851636537524224?s=20
[local-first]:https://www.inkandswitch.com/local-first.html "A set of principles for software that enables both collaboration and ownership for users"
[Web began dying]:https://staltz.com/the-web-began-dying-in-2014-heres-how.html "The Web began dying in 2014"
[AmIUnique]:https://amiunique.org/ "Am I Unique"
[advanced-tor-browser-fingerprinting]:http://jcarlosnorte.com/security/2016/03/06/advanced-tor-browser-fingerprinting.html
[AdSense]:https://www.google.com/adsense/
[SMTP]:https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol "Simple Mail Transfer Protocol"
[DHT privacy]:https://www.youtube.com/watch?v=lGk6OErtDFY
[hashmatter]:https://hashmatter.com/ "r&d focused on privacy preserving decentralized networks"