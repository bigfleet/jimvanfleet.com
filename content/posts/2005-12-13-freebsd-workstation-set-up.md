---
layout: post
title: FreeBSD Workstation set up
tags: []
status: publish
type: post
published: true
meta: {}
---
<h2>Before We Begin</h2>


	<p>The point of this lesson is to get you on your feet in an X environment; the basis of any workstation.  You&#8217;ll get an introduction to the ports system and see what it&#8217;s like to use it.  I include a couple of tips for ordering your port installation and a few examples of ports that I&#8217;ve installed at the end.</p>


	<h2> Ports, Explained</h2>


	<p>In the <a href="http//blah/">last lesson</a>, we covered installing the ports system using <span class="caps">CVSUP</span>.  Ports is the package management system for FreeBSD.  It&#8217;s highly dependent on source code compilation, so it&#8217;s not for the impatient.  However, the ports system has high standard for a &#8220;non-broken&#8221; port, and the maintainers of any given port are given continuous feedback for circumstances that &#8220;break&#8221; the port.  As a result, you can use ports without being that comfortable with many of the major compilation issues and strategies;  odds are that it will <em>just work</em>.</p>


	<h2> Using the ports system.</h2>


	<p>The first step I took with my newly installed system was to log in as root and&#8230;</p>


<code>
<pre>
# cd /usr/ports/x11-servers/xorg-server/
# make install clean
</pre>
</code>

	<p>That&#8217;s it.  Let that run, and eventually you will have an X server running.  The ports system itself will walk the necessary dependency chains, installing other ports as needed.</p>


	<h2> Interlude: configuration and <code>rehash</code></h2>


	<p>After the above command has completed, issue the <code>rehash</code> command.  Essentially, this tells FreeBSD to go back and re-evaluate your <span class="caps">PATH</span>, giving you access to any newly installed programs.  In this case, you&#8217;ve picked up <code>xorgconfig</code>, which you should now run.</p>


	<h2> Getting a bit tricky</h2>


Ports evaluate dependency chains as best it can, but it&#8217;s not a perfect system.  For example, if we were to&#8230;
<code><pre>
# cd /usr/ports/x11-wm/gnome2
</pre></code>
we could <code>make install clean</code> immediately, but let&#8217;s say we were going to sleep after issuing that command.  During the middle of the night, this command would end up blocking on configuration choices for the <code>ghostscript</code> port.

	<p>So you don&#8217;t wake up to yummy Gnome!  The answer, in this case, is to install the <code>print/ghostscript-gpl</code> port first (which doesn&#8217;t take very long) then start gnome.</p>


	<p>(KDE, by the way, blocks on at least a half-dozen dependencies. <code>artswrapper, postgres-client (?!?), openslp, kdegraphics, kdemultimedia, kdepim, and boost-python</code>)</p>


	<p>There are ways to have these preferences taken into account without having them come up directly in the <code>make</code> process, but I&#8217;m still experimenting with the alternatives and trying to figure out how some of the tricky stuff works.  I&#8217;ll be happy to leave an update when I crack the case.</p>


	<h2>Recommended Ports</h2>


	<ul>
	<li>Firefox (www/firefox)</li>
		<li>OpenOffice.Org v.2 (editors/openoffice-2.0)
 Gnome (x11-wm/gnome2)
(although gnome2-lite looks interesting&#8230;)</li>
		<li>lighttpd (www/lighttpd)</li>
		<li>Ruby (devel/ruby18)</li>
		<li>Subversion (devel/subversion)</li>
		<li>tsclient (net/tsclient) This program handles <span class="caps">RDP</span> connections to Windows machines and <span class="caps">VNC</span> connections to others.  Beats both gdesktop and kdesktop.</li>
		<li>Trac (www/trac)</li>
		<li>Gimp (graphics/gimp)</li>
		<li>Gaim (net-im/gaim)</li>
	</ul>


	<h2>What&#8217;s Next?</h2>


	<p>The Java ports.  FreeBSD&#8217;s support for Java might seem intimidating, but it&#8217;s not so bad, as long as you can live with 1.4.  You can still run Eclipse, and a lot of Java programs on the 1.4 <span class="caps">JDK</span>.</p>
