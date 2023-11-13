---
layout: post
title: Installing FreeBSD-STABLE
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-12-12
---
### Before We Get Started

First, the [documentation for FreeBSD](https://docs.freebsd.org/en/books/handbook/index.html) is absolutely fabulous.  If you are Googling something about FreeBSD, your heart will sing when one of the links is from the handbook, because the answer will soon be in your grasp.


Second, Dru Lavigne's FreeBSD series is another fantastic resources.  I highly recommend reading those articles, as they've been very informative during my adoption process.


Third, I decided to track FreeBSD-STABLE based on the [criteria for choosing between STABLE and CURRENT](https://docs.freebsd.org/en/books/handbook/cutting-edge/#current-stable).  You don't have to do either-- you can simply install from binaries.  But this is a learning exercize for me, and I think it would be a great learning experience to be able to contribute to FreeBSD somehow.  That's much more likely from STABLE at least.


### Step 1: Obtaining the Install CDs


FreeBSD 6.0 is the latest release of FreeBSD.  Download both ISO files, as you'll need at least one port off the second CD.  FreeBSD offers [several methods](http://www.freebsd.org/releases/6.0R/announce.html) for acquiring the CD's or ISO images.  Assuming that you [have space on your hard drive available](../2005/11/15/getting-started) you can stick the CD in your drive and get going.

### Step 2:  Beginning the Installation

Don't blink an eye during the boot process.  Note that the *F12* key is the one to go for during the now lightning-fast BIOS/POST process on Dell machines.  It will give the the option to boot once from the CD, or to go to the BIOS menu to permanently move the CD option above the HD for booting purposes.

When the FreeBSD installer loads, don't blink here either.  It's very likely that you'll need to choose *option 7* to boot with USB keyboard support.  From there, you should get into the installation itself.

### Step 3:  Preparing a minimal install.

Go through the installation procedure.  You won't need a walkthrough for every step, but here are some tips.  If you are going to want any Java elements on your system, enable Linux binary compatability when asked.  I recommend not configuring inetd, but enabling ssh.  Don't look to me for advice on your bootloader, but FreeBSD's is the bare minimum and don't count on its flexibility.

When installing, you only want to choose one port: *cvsup-without-gui*  One of the strengths of FreeBSD is the [ports collection](https://docs.freebsd.org/en/books/handbook/ports/) which is the FreeBSD analog to package administration, if you're familiar with Linux system administration.  The ports system works in a fundamentally different way than package management, however.  We'll cover that here in time, but Dru's resources contain quite a bit of information about the ports system to get you started.

We'll be using CVSUP to track FreeBSD's CVS repository for ports and kernel code, as well.  Since we'll be getting these crucial elements shortly, and they are easy to retrieve form the command line (provided you have a very basic grasp of vi-- which I personally loathe), (ed. note: not anymore) so that's why we're going with a minimum install.

### Step 4: CVSUP

CVSUP is a special CVS bound to the FreeBSD source repositories.  I set up the binding for my machine by copying `/usr/share/examples/cvsup/stable-supfile` to `/root/supfile`.  I used `vi` to assign a hostname and to indicate that in addition to `src-all` (which downloads the kernel source) I would also like `ports-all tag=.`.  (Ports are tagged differently than kernel source-- you can read more in the comments.)

After that, `cvsup -L 2 /root/supfile` kicks off the download process.  When that's complete, you'll have everything you need to configure a kernel, and/or get started installing any number of programs.  Hooray!

### What's Next:

I choose to set up some userland programs so I can start using my machine again after a long downtime period.
