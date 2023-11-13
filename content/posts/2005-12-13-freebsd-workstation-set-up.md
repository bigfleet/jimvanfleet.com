---
layout: post
title: FreeBSD Workstation set up
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-12-13
---

## Before We Begin


The point of this lesson is to get you on your feet in an X environment; the basis of any workstation.  You'll get an introduction to the ports system and see what it's like to use it.  I include a couple of tips for ordering your port installation and a few examples of ports that I've installed at the end.

## Ports, Explained

In the [last lesson](../2005-12-12-installing-freebsd-stable), we covered installing the ports system using CVSUP.  Ports is the package management system for FreeBSD.  It's highly dependent on source code compilation, so it's not for the impatient.  However, the ports system has high standard for a "non-broken" port, and the maintainers of any given port are given continuous feedback for circumstances that "break" the port.  As a result, you can use ports without being that comfortable with many of the major compilation issues and strategies;  odds are that it will _just work_.


## Using the ports system.

The first step I took with my newly installed system was to log in as root and--


```
# cd /usr/ports/x11-servers/xorg-server/
# make install clean
```

That's it.  Let that run, and eventually you will have an X server running.  The ports system itself will walk the necessary dependency chains, installing other ports as needed.

## Interlude: configuration and `rehash`

After the above command has completed, issue the `rehash` command.  Essentially, this tells FreeBSD to go back and re-evaluate your PATH, giving you access to any newly installed programs.  In this case, you've picked up `xorgconfig`, which you should now run.

## Getting a bit tricky


Ports evaluate dependency chains as best it can, but it's not a perfect system.  For example, if we were to&#8230;

```
# cd /usr/ports/x11-wm/gnome2
```

we could `make install clean` immediately, but let's say we were going to sleep after issuing that command.  During the middle of the night, this command would end up blocking on configuration choices for the `ghostscript` port.

So you don't wake up to yummy Gnome!  The answer, in this case, is to install the `print/ghostscript-gpl` port first (which doesn't take very long) then start gnome.


(KDE, by the way, blocks on at least a half-dozen dependencies. `artswrapper`, `postgres-client` (?!?), `openslp`, `kdegraphics`, `kdemultimedia`, `kdepim`, and `boost-python`)


There are ways to have these preferences taken into account without having them come up directly in the `make` process, but I'm still experimenting with the alternatives and trying to figure out how some of the tricky stuff works.  I'll be happy to leave an update when I crack the case.

## Recommended Ports

* Firefox (www/firefox)</li>
* OpenOffice.Org v.2 (editors/openoffice-2.0)
* Gnome (x11-wm/gnome2) (although gnome2-lite looks interesting&#8230;)
* lighttpd (www/lighttpd)
* Ruby (devel/ruby18)
* Subversion (devel/subversion)
* tsclient (net/tsclient) This program handles RDP connections to Windows machines and VNC connections to others.  Beats both gdesktop and kdesktop.
* Trac (www/trac)
* Gimp (graphics/gimp)
* Gaim (net-im/gaim)

## What's Next?

The Java ports.  FreeBSD's support for Java might seem intimidating, but it's not so bad, as long as you can live with 1.4.  You can still run Eclipse, and a lot of Java programs on the 1.4 JDK.
