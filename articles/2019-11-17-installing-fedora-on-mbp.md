---
layout: post
title: Installing Fedora 31 on a Macbook Pro 2014
---

The last time I decided to install something else than Mac OS on my Macbook, I
decided to install an arch-based distribution. My choice was Antergos, since
it was basically an easy installation of arch, but without additional
software and all the good stuff, I guess. For my DE I decided to use i3, which
was a pre-installation option at Antergos. However, the whole thing was
somewhat painful, as there were a couple of unfunctional-by-default things:
* Backlight (Changing / Restoring)
* Brightness (Changing / Restoring)
* Wi-Fi (Even after installing the driver, I still had connection issues)
* Bluetooth (Even after getting the driver, it was horrible)
* No system-wide scaling
* No thermal management

While all of that was kind of annoying, it was somewhat manageable, but stuff
like the brightness changing at some point even broke during an update.

*Now, behold Fedora!*

Fedora 31 comes with Gnome 3.34+ which has recently seen a lot of improvements.
Out of the box, everything except for the Wi-Fi just worked. Getting the
proprietary Broadcom 4360 driver needed to be done via a custom package.
Besdides that, the only other thing I had to change was the fn-mode key, which
I swapped from `1` (always pressed) to `2` (Never pressed). Two of the FN-Keys
are dead, but I don't even know what they were for. Dead meaning that they are
just not bound to any function by default.

Besides those two little itches, there were three other welcome suprises. Those
being that the scrolling direcrion was "correct" by default (the Mac way) and
the screen brightness automatically adjusts according to the light sensor. The
best of those three, was probably the fact that scaling just worked out of the
box. Both the Gnome UI and application all seemed to scale correctly. In the
past, this was, in my opinion, one the major weaknesses on the Linux desktop.

Oh and sadly, the Bluetooth had stutters as well. This was due to interferences
with 2.4Ghz Wi-Fi and could be temporarily fixed by swapping over to 5Ghz.
This issue might be fixable by changing some settings, but I don't care for
now, as I don't really use Bluetooth.

The only other nice to have thing so far, would be the nice touchpad gestures
that you get by default in Mac OS. Especially the basic ones like pinch to zoom
were really pleasant to use.

So far, it seems like Fedora will be the daily driver for my MBP.
