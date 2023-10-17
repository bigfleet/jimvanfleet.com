---
layout: post
title: Subversion Apache Installation on Windows
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>A W32Notes.txt file is buried in the distribution, and you can find it online <a href="http://www.endrun.org/xr/svn/source/packages/win32-innosetup/W32notes.txt">here</a>.  It contains very useful tips about the specifics of getting the Subversion modules integrated with Apache.  My advice is to stop Apache, then make frequent use of the &#8220;Test Configuration&#8221; program that the current (2.0.52) version of Apache includes.</p>

<p>Also make sure to uncomment the line in httpd.conf that includes mod_dav.so.  Include the <span class="caps">SVN</span> modules after that.</p>

<p>For me, my configuration passed the &#8220;Test Configuration&#8221; program, but my service doesn&#8217;t start and you can&#8217;t bring up localhost&#8212;reboot your computer.  That&#8217;s right, rebooting still fixes problems!</p>

<p>Now that Apache starts, you may still need to perform one trick to allow Apache to access the file system.  From Cygwin, I issued the commands below.  My repository is in <span class="inlinedCode">C:\dev\repo</span></p>

<pre>
Jim Van Fleet@jimvfxp /cygdrive/c/dev
$ chown -R Administrators repo

Jim Van Fleet@jimvfxp /cygdrive/c/dev
$ chgrp -R SYSTEM repo
</pre>

<p>After that, I was up and running!  I&#8217;ll be adding security at a later time, I&#8217;ll make notes here if that proves to be difficult.</p>
