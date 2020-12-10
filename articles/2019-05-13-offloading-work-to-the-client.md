---
layout: post
title: About offloading work to the client
---

I have been working on an open source Discord client for a while, it uses the
official REST API and tries to reproduce the features of the original electron
client. When I got to the point where I could actually chat, one of the first
things I tried, was sending emojis. Well, didn't quite work out. When I entered
emoji-sequences like `:cry:` or `:sunglasses:`, all I got back was plaintext.
But why is that, if the original client converts all those sequences into
actual Unicode characters? This is simply due to the fact, that in order to
implement this feature, Discord uses client-sided business logic. So before
sending the message to the server, for example:

```
What a great day :sunglasses:
```

It converts the message into this:

```
What a great day 😎
```

This feature works on the desktop-client, the web-client and the mobile-client.
However, my client couldn't do it, since the server doesn't do this thing, even
though the behaviour is supposed to be the same across all devices (clients).

There are other scenarios though, where even the official Discord clients
differ in their behaviour. Take a look at the commands that the client suggests
you when you type a `/`. The desktop-client and the web-client will show you a
list of available commands and allows you to chose one of them. However, the
mobile client does nothing at all, since it doesn't support a single of those
commands. Not even simple ones like `/shrug`, which simply inserts a shrugging
kaomoji into the message. But hey, who needs consistency, am I right
`¯\_(ツ)_/¯`?

So what if the Discord team decides that they want to write an additional
client at some point? Maybe a native desktop client that doesn't use electron.
Well, they'll have to replicate all client-sided behaviour in their new client,
which means additional time consumption and therefore additional cost. On top
of that it increases the margin for error. If you write the same code twice
in different languages, maybe even with different testing and whatnot, you
might end up introducing errors in one version of the code, but not in the
other. On top of that, maintaining the code becomes harder, since changing the
behaviour on the client means having to change it twice.

Most likely they have a reason to not implement such behaviour on the
server-side though. One of the most obvious reasons would be lowering the
workloads on the server and therefore reducing the amount of money needed in
order to run the backend infrastructure. Even though such a simple feature
sounds trivial and like it wouldn't cost much performance, think about how many
active users Discord has that send messages every second. Eventually for a big
service like Discord it might just pay off.

The next time you implement business logic, you might want to ask yourself the
following question:

>Does it technically matter where I implement the behaviour? Iff not, what are
>the benefits for each decision and how much weight do those benefits have to
>me personally?

My own approach is usually to avoid writing business logic more than once,
since it usually just introduces more work in the long-run. As it shouldn't be
a problem as long as you don't have scaling problems, whether due to money
restrictions or hardware restrictions.