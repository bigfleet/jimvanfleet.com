---
layout: post
title: Subversion Apache Installation on Windows
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-12-15
---
A W32Notes.txt file is buried in the distribution, and you can find it online [here](https://opensource.apple.com/source/subversion/subversion-16/subversion/packages/windows-innosetup/W32notes.txt.auto.html).  It contains very useful tips about the specifics of getting the Subversion modules integrated with Apache.  My advice is to stop Apache, then make frequent use of the "Test Configuration" program that the current (2.0.52) version of Apache includes.

Also make sure to uncomment the line in httpd.conf that includes mod_dav.so.  Include the <span class="caps">SVN</span> modules after that.

For me, my configuration passed the "Test Configuration" program, but my service doesn't start and you can't bring up localhost-- reboot your computer.  That's right, rebooting still fixes problems!

Now that Apache starts, you may still need to perform one trick to allow Apache to access the file system.  From Cygwin, I issued the commands below.  My repository is in `C:\dev\repo`

```
Jim Van Fleet@jimvfxp /cygdrive/c/dev
$ chown -R Administrators repo

Jim Van Fleet@jimvfxp /cygdrive/c/dev
$ chgrp -R SYSTEM repo
```

After that, I was up and running!  I'll be adding security at a later time, I'll make notes here if that proves to be difficult.
