---
layout: post
title: Installing FreeBSD-STABLE
tags: []
status: publish
type: post
published: true
meta: {}
---
<h3>Before We Get Started</h3>


	<p>First, the <a href="http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html">documentation for FreeBSD</a> is absolutely fabulous.  If you are Googling something about FreeBSD, your heart will sing when one of the links is from the handbook, because the answer will soon be in your grasp.</p>


	<p>Second, <a href="http://www.onlamp.com/pub/ct/15">Dru Lavigne&#8217;s FreeBSD series</a> is another fantastic resources.  I highly recommend reading those articles, as they&#8217;ve been very informative during my adoption process.</p>


	<p>Third, I decided to track FreeBSD-STABLE based on the <a href="http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/current-stable.html">criteria for choosing between <span class="caps">STABLE</span> and <span class="caps">CURRENT</span></a>.  You don&#8217;t have to do either&#8212;you can simply install from binaries.  But this is a learning exercize for me, and I think it would be a great learning experience to be able to contribute to FreeBSD somehow.  That&#8217;s much more likely from <span class="caps">STABLE</span> at least.</p>


	<h3>Step 1: Obtaining the Install CDs</h3>


	<p>FreeBSD 6.0 is the latest release of FreeBSD.  Download both <span class="caps">ISO</span> files, as you&#8217;ll need at least one port off the second CD.  FreeBSD offers <a href="http://www.freebsd.org/releases/6.0R/announce.html">several methods</a> for acquiring the CD&#8217;s or <span class="caps">ISO</span> images.  Assuming that you <a href="http://blog.jimvanfleet.com/articles/2005/11/15/getting-started">have space on your hard drive available</a> you can stick the CD in your drive and get going.</p>


	<h3>Step 2:  Beginning the Installation</h3>


	<p>Don&#8217;t blink an eye during the boot process.  Note that the <strong><span class="caps">F12</span></strong> key is the one to go for during the now lightning-fast <span class="caps">BIOS</span>/POST process on Dell machines.  It will give the the option to boot once from the CD, or to go to the <span class="caps">BIOS</span> menu to permanently move the CD option above the HD for booting purposes.</p>


	<p>When the FreeBSD installer loads, don&#8217;t blink here either.  It&#8217;s very likely that you&#8217;ll need to choose <strong>option 7</strong> to boot with <span class="caps">USB</span> keyboard support.  From there, you should get into the installation itself.</p>


	<h3>Step 3:  Preparing a minimal install.</h3>


	<p>Go through the installation procedure.  You won&#8217;t need a walkthrough for every step, but here are some tips.  If you are going to want any Java elements on your system, enable Linux binary compatability when asked.  I recommend not configuring inetd, but enabling ssh.  Don&#8217;t look to me for advice on your bootloader, but FreeBSD&#8217;s is the bare minimum and don&#8217;t count on its flexibility.</p>


	<p>When installing, you only want to choose one port: <strong>cvsup-without-gui</strong>  One of the strengths of FreeBSD is the <a href="http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports.html">ports collection</a> which is the FreeBSD analog to package administration, if you&#8217;re familiar with Linux system administration.  The ports system works in a fundamentally different way than package management, however.  We&#8217;ll cover that here in time, but Dru&#8217;s resources contain quite a bit of information about the ports system to get you started.</p>


	<p>We&#8217;ll be using <span class="caps">CVSUP</span> to track FreeBSD&#8217;s <span class="caps">CVS</span> repository for ports and kernel code, as well.  Since we&#8217;ll be getting these crucial elements shortly, and they are easy to retrieve form the command line (provided you have a very basic grasp of vi&#8212;which I personally loathe), so that&#8217;s why we&#8217;re going with a minimum install.</p>


	<h3>Step 4: <span class="caps">CVSUP</span></h3>


	<p><span class="caps">CVSUP</span> is a special <span class="caps">CVS</span> bound to the FreeBSD source repositories.  I set up the binding for my machine by copying <code>/usr/share/examples/cvsup/stable-supfile</code> to <code>/root/supfile</code>.  I used vi to assign a hostname and to indicate that in addition to <code>src-all</code> (which downloads the kernel source) I would also like <code>ports-all tag=.</code>.  (Ports are tagged differently than kernel source&#8212;you can read more in the comments.)</p>


	<p>After that, <code>cvsup -L 2 /root/supfile</code> kicks off the download process.  When that&#8217;s complete, you&#8217;ll have everything you need to configure a kernel, and/or get started installing any number of programs.  Hooray!</p>


	<h3>What&#8217;s Next:</h3>


	<p>I choose to set up some userland programs so I can start using my machine again after a long downtime period.</p>
