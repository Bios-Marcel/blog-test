---
layout: post
title: VPNs and the lies you are being fed
---

Today I'd like to talk about VPNs, despite the fact that many people have
probably already told you the same thing that I am about to tell you.

So, I have noticed that recently a lot of YouTubers are advertising VPN
services. Those are usually PIA or NordVPN. The promise usually make in
those advertisements, is something along the lines of `Privacy due to full
encryption of your traffic`. Now that sure sounds great, right? Err ... not
really. While encryption would prevent someone from reading or manipulating
your data, you can't simply End-To-End encrypt any traffic.

Usually when you make a requet over the internet, you (the host) create your
request and target some other machine (the server), that lies somewhere else.
Since you are not directly connected to the server (in the same local area
network), your request has to be routed over the internet, meaning it will
hop from device to device, trying to find the most efficient route to your
requests target.

So yes, theoretically you could now encrypt this request before sending it, but
your target server would not understand your encrypted request, since it has no
clue about how to decrypt it. So what a VPN means when it claims that it
encrypts your traffic, is that the route to the VPN (your man in the middle),
will be fully encrypted. As soon as your VPN has proxied your request to your
actual target, your traffic will look the same as it did before encrypting it.
This doesn't mean that unless you use a VPN your traffic is always unencrypted.
As long as your requests uses some protocol that has encryption built-in, your
data will still be encrypted til it reaches the requests target.

So, what does this mean in the end? It means you don't really achieve privacy
just by using some VPN service.

Some people actually get a VPN in order to hide their malicious activies from
third parties that could potentially track them down. Does that at least make
sense? Yes, kinda. The original location of the request will not be known to
a third party. However, they can still ask your VPN who you are or where you
are. And I doubt you really want to trust some random company that promises
you full privacy for just *2.99€* a month. However, using the VPN to access
some service that has geographical restrictions or get around blockades that
your government has put up, a VPN is still fine. Even though a simple proxy
would probably do the job, unless your government does deep packet inspection.

Let's not get started talking about free VPN services, like the one that
facebook offered (or still does?). They obviously don't do this because they
want to keep everyone from reading your precious traffic.

Anyway ... back to the YouTubers! It's a shame that strong social media
presences advocate for something they don't seem to understand much about. If
they'd really care about their audiences, they should not advertise such
services or at least inform themselves a bit before doing so. In order to
prevent such false advertisements.

**EDIT:**

Someone has pointed out to me that those YouTubers are being paid for making
those advertisements in their videos. I was well aware of that when writing
the post, however, I didn't feel like this would be worth mentioning.
