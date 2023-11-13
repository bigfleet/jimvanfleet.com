---
layout: post
title: Getting Started
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-11-15
---
Preparation is key in this effort.  The first step is to go to the Windows Device Manager and copy down all the devices that Windows registers on your system.  If you make a mistake, you'll be very glad that you had this in dead-tree format.  Here's my version

```
ATI Radeon X300 SE 128MB HyperMemory
Philips DVD+-RW DVD8701
Intel 8280 1GB Serial ATA Storage Controller - 27C0
Intel 82801GB Ultra ATA Storage Controllers - 27DF
Intel 537EP V9x DF PCI Modem
Intel PRO/100 VE Network Connection
Intel Pentium 4 3Ghz
```

The second step is becoming familiar with the contents of your hard drive.  On my computer, Dell shipped three primary partitions on the machine.  One is about 55k and is involved with the Dell System Recover utility.  I understand from some of the other postings I've read that Dell has replaced the familiar "System Restore CD" with this, _uh_, feature?  The second is the primary Windows partition.  The last is something I haven't really taken care to fully identify.  You'll see some hints here shortly, but let's not get ahead of ourselves.


The most important detail is that your  partition(s) fill the hard drive.  There's no space to install another operating system.  Sure, you can buy something like Partition Magic to do the resizing for you.  I've used it in the past with success.  I'm also cost sensitive though, so I wanted to see if I could do this for free.  Turns out, it was not a problem.  Err, well, it did take awhile, but not for the reasons you might think.


### Resizing your XP Partition with <span class="caps">RIP</span> and ntfsresize

Fortunately for my wallet, there is an open-source tool to resize <span class="caps">NTFS</span> partitions: ntfsresize.  The Ntfsresize <span class="caps">FAQ</span> lists a host of potential distributions with which you can use ntfsresize to do the partition resizing.  My most successful experiments to date have been with FreeBSD.  However, since FreeBSD chooses to ignore the problem of resizing one's partitions, my <span class="caps">OSOS</span> journey begins with Linux.

Kubuntu, Ubuntu, and Knoppix all lead to <a href="../2005-11-15-the-journey-begins/"><span class="caps">TMDER</span></a> in various ways.  (Also interesting to note was that not a single one of the Linux flavors I've tried thus far worked with a <span class="caps">DVI</span> connection to the monitor; I had to break out the analog cable.)

The technique that did work was to use <span class="caps">RIP</span>, which seems like a really useful tool regardless of your circumstances.  I am glad that I found it.  Odds of it ending up on a flash drive with me at all times is high.

The <span class="caps">RIP</span> readme has an excellent walkthrough of the steps necessary to perform the resizing.

The highlights in brief are the following:

#### Seeing what you've got

Use the `fdisk` command to determine the size and nature of your partitions.  For me, the output looked like this.


```
# fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19412 cylinders
Units = cylinders of 16025 * 512 = 822528 bytes

   Device Boot     Start       End       Blocks    Id   System
/dev/sda1              1         7        56196    de   Dell Utility
/dev/sda2 *            8     18845    151316235     7   HPFS/NTFS
/dev/sda3          18847     19452      4867695    db   CP/M / CTOS / ...

```

#### Measure...


ntfsresize has a very nice manual on the <span class="caps">RIP CD</span> which you can actually gunzip and read.  Feel free to either supplement the <span class="caps">README</span>, or to refer solely to the one provided on disc.  Either would tell me to issue the command to test resizing the partition to approximately 120GB.


```
ntfsresize -n -s 120000M /dev/sda2
```

#### ... then cut.

Having ntfsresize do the actual work is not too much different.  After issuing this command, you'll be prompted to pass the point of no return, as it were.


```
ntfsresize -s 120000M /dev/sda2

```

#### fdisk revisited.

We now have to use `fdisk`` to adjust the partition table in earnest.  This involves (_brace yourself_) deleting the primary partition on your machine.  For those going straight to running only the *nix/*<span class="caps">BSD</span> operating system, that's not much of a concern.  For my purposes, though, that's a bit scary.

At any rate, you shouldn't be scared, because the change is only in memory until you write it to the partition table.  The process is essentially:

1. Delete the primary partition
1. Recreate the primary partition with the same attributes, only smaller
1. Create a partition on which the new OS can reside.

#### Rebooting

Reboot into Windows by removing the CD and calling (_wait for it_) `reboot`

Windows will sense your philandering;  "Your disk is dirty" it will report.  That's right, Windows!  I'm going around behind your back!  You tried to lock me down, but I won't be beaten that easily.

Beginning the install process comes next.