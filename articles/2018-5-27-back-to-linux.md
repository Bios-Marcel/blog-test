---
layout: post
title: A month into using Solus Budgie
---

A while ago I decided to start abandoning proprietary services, one of those was windows.

Well, obviously I had to find a new system first.

## Backstory

The first Linux I had ever seen and actively used was `open SUSE` in 2011 I believe, I was about 13 years old at that time.

I was just a "normal" user and solely used it to play games and surf the web.
At some point I stopped using SUSE ... I forgot why, but probably due to me being too stupid to achieve what I wanted to achieve.
I then switched to `Windows 7` and used it for about 3 to 4 years and then decided to get [Ubuntu](https://www.ubuntu.com/), at that
point and time I had to abandon all the games that I had played on windows.
I missed my games and switched back to windows 7 after about 3 months.
As soon as Windows 10 was available I did the free upgrade and was quite satisfied, since Windows 10 fixed a lot of the quirks that Windows 7 had:

* Flat Design
* Multiple workspaces (desktops)
* windows snapping with proper multi monitor support
* It was faster
* more ... (I am too lazy to list more)

on the other hand it introduced some annoying stuff, like `builtin advertisements` in the startmenu, `preinstalled bloatware`, `annoying popups` and `additional telemetry` that you can't easily disable.
Also they started to replace more and more of old Windows 8.1 and below GUI with their new fluent design GUI ... which to be honest is worse in my opinion. Well ... enough talking about windows.

## Solus

In the beginning I decided to go with [open SUSE](https://www.opensuse.org/) due to the fact that it was the first linux I had ever seen and used. After only 3 days of pain (KDE 5 Plasma constantly crashing) I switched to Solus.

Just like `open SUSE`, Solus wasn't based on another big distro, like `Ubuntu` is based on `Debian`. One downside was, that I can't use any `.rpm` or `.deb` packages (at least not by default). On the other hand we have [Snap](https://snapcraft.io/) and [Flatpak](https://flatpak.org/) nowadays, which provide a way to easily install software across different linux distributions. Most of the software I needed was available in official Solus repositories, those are quite up-to-date, sadly they are lacking some old and common stuff like `xterm`, simply because `there is no need for it`.


I really hate waiting, which is why I am happy that Solus starts up quick, logs you in quick and even shuts down lighting fast.

I actually don't use much operating system features, but neither did I use much operating system features when I was on Windows though.
I just need a minimal OS, which is fast, up-to-date and looks good, Solus satisfies all of those needs in my opinion.

### Budgie

Solus is available with different desktop environments:

* Gnome
* Mate
* Budgie

I decided to go for Budgie, simply because it looked minimal and well designed. I also wanted to try something new. Overall I like Budgie.

It comes with some `Windows 10`-like Notification center, called `Raven` which also integrates media playback 

![Media playback raven](https://raw.githubusercontent.com/bios-marcel/Bios-Marcel.github.io/master/images/solusbudgiepost/mediaplayback.png)

and easy access to your audio input and output devices

![Audio control](https://raw.githubusercontent.com/bios-marcel/Bios-Marcel.github.io/master/images/solusbudgiepost/audiocontrol.png)

It also supports system tray icons by default, unlike Gnome nowadays.

It has an application menu for listing and grouping installed applications, the `Budgie Menu`, sadly [i have experienced heavy problems with said component](https://github.com/solus-project/budgie-desktop/issues/1444), which is why I deactivated it and use the `run command prompt` instead. The `run command prompt` only allows you to type in a name and execute one of the search results. Back on Windows 10 I only ever used the start menu to do exactly that, so I am not missing out on anything here.

Budgie has some Gnome integration and ships with some of the default gnome tools. I am not the biggest friend of the gnome tooling. As I already mentioned I used KDE for a short while, I really loved it, especially the file manager (`Dolphin`), which had terminal integration and multi pane support and the terminal (`Konsole`) which supports horizontal and vertical tiling.

Budige comes with `Nautilus`, which doesn't support the two features I like about `Dolphin`, so I ended up deleting `Nautilus` and am now using `Caja`, which is a fork of the old `Nautilus` (back when it still had features). I first tried using Dolphin, but sadly it didn't work that well without the KDE desktop.

I removed `gnome-terminal` and replaced it with [Tilix](https://github.com/gnunn1/tilix). I went for Tilix due to the fact that it supports tabs, horizontal and vertical tiling and easy customization of keybindings.

### Gaming

Okay, let's talk about the actually important stuff ... playing games!
I bet you all know, that windows is usually the best choice for gaming, sadly I can't deny that fact.

However, Solus allows easy installation of 32-bit and 64-bit NVIDIA drivers, reducing the initial problems a lot. And by using [Lutris](https://lutris.net/), you can easily install a lot of different Windows-only games.

Lutris can manage games for different platforms:

* wine
* native Linux games
* Linux Steam
* Windows Steam
* Browser
* and a couple more

allowing you to easily manage your game library using a single application.

You could also manually install the native Steam client via wine, but I would suggest using Lutris if possible, as you’d have to do all the dependency management for the games yourself otherwise and probably you’d even have to create two wine prefixes, one for 64-Bit Steam and one for 32-Bit Steam.

Solus allows you to install the native Steam client via `eopkg`, its integrated package manger, in addition to that, it also offers [improved integration for steam](https://github.com/solus-project/linux-steam-integration).


Back on windows I played a lot of different games:

* Dark Souls 2
* Dark Souls 3
* Dishonored 2
* Warframe
* Heroes of the Storm
* Hearthstone
* League of Legends
* Brawlhalla
* Battlerite
* CS:GO
* Fortnite
* Osu!
* *Insert bunch of indie games here*

Except for some of the indie games and CS:GO, those are all non-linux titles.

It is no problem to run low graphics games like, Brawlhalla, League of Legends or Hearthstone via Wine, but games like Dark Souls, Dishonored or Fortnite aren't playable unless you have very powerful hardware.

Even though I have a GTX 1050 TI, I am unable to play Warframe, Dishonored, Heroes of the Storm or Dark Souls via wine.

Currently, those are the Windows-only games that I got up and running (putting native Linux titles aside):

* League of Legends
> I am using the OpenGL version with low graphic settings, since directX9 causes heavy client bugs
* Brawlhalla
> Has lags sometimes, but runs fine most of the time.
* Battlerite
> Runs fine with directX9
* Hearthstone
> Might not run perfect at all times, but it is a card game, so it doesn’t really matter
* Osu!
> Runs fluid and my Tablet (Huion H420) also works. In order to easily add new songs to the song directory, I use the `mv` command as my default application for `.osz` files.

And those are the ones that I didn’t get to work:

* Heroes of the Storm
> This really surprised me, the game had pretty stable fps of 120+, but the fps dropped to `0` for a moment, as soon as any character used an ability. Since using abilities is what you do the whole time, the game was simply unplayable.
* Dark Souls 3
> I don’t know why, but the game simply didn’t start, I might investigate this further at some point.
* Fortnite
> Since Fortnite uses BattleEye anti-cheat, which doesn’t work with wine, this game can’t be played.
* Warframe
> Well, it works, but only at unstable 40 fps on minimal settings, which is no fun


### Conclusion

I can recommend Solus for daily usage. Most people might not be as picky about their file manager and terminal as I am, so that shouldn't be something that most users would have to mess with.

Probably Solus shouldn’t have been my first choice though, since I obviously preferred the tooling that KDE 5 Plasma gave me, but sadly I had already lost trust in it after seeing how buggy it is on open SUSE Tumbleweed and open SUSE Leap. I didn’t feel like wasting my time to give it a third try.

---

I have probably just scratched the surface of what might be important to some people, sorry for that.

If you find any mistakes, like wrong information or typos, feel free to submit a pull request.

