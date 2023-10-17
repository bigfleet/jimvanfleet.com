---
layout: post
title: My OpenSolaris Experience
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Thanks to the work of the Joyent team, through their <a href="http://youngobungo.bingodisk.com/bingo/public/pspipegrep/Site/Podcast/Podcast.html">podcast</a> and working with top-level <a href="http://joyeur.com/2007/04/24/solaris-dtrace-and-rails">Rails sites on Solaris with DTrace</a>, I am sold on the OpenSolaris operating system.  I am pretty rusty with my Solaris admin skills, since most of the ones that I used the most often at Rice were written by senior IT engineers.  We really didn&#8217;t do a lot of software installation and maintenance.  I don&#8217;t even know how much has changed for Solaris in the past 2 or 3 versions.  I started out with the intent to just build a Ruby deployment stack, but the journey ended up further down the road!  I&#8217;ll walk you through what I did.</p>


	<h2>Download the Parallels instance from Sun.</h2>


	<p>Sun has recently made available their <a href="http://www.sun.com/download/products.xml?id=461d6b7d">Solaris Express for Parallels</a> instance, and that&#8217;s where my journey started.  Sun, get an easier to use website.</p>


	<h2>Hit up Blastwave</h2>


	<h3>A word on package management</h3>


	<p>My experience with Ubuntu and apt-get has changed my expectations in terms of package management.  The only time that apt-get has not given me exactly what I have expected has been when I&#8217;m trying some experiment that later turns out to be completely boneheaded.  Ubuntu, particularly, has a very large space of packages.  <a href="http://wwww.blastwave.org/">Blastwave</a> is the OpenSolaris equivalent, although <a href="http://www.gnusolaris.org/gswiki">Nexenta</a> attempts to bring the whole of apt-get to OpenSolaris, boasting currently of more than 12,000 packages available.  For your own purposes, you may wish to evaluate Nexenta, but with their most recent release being <a href="http://www.gnusolaris.org/gswiki/Download">Nexenta Alpha 6</a>, I was more interested in something that I could feel comfortable using in production right away.  That&#8217;s right, calling your software alpha <strong>does</strong> scare me off.</p>


	<h3>Now on with our regularly scheduled program</h3>


	<p>An ugly fact:  I am completely useless with vi.  So for me, Blastwave is the next step.  <a href="http://www.blastwave.org/howto.html">Blastwave&#8217;s <span class="caps">HOWTO</span></a> was no problem to follow.  Don&#8217;t miss the last line of Step 7, which you will definitely want to do as you install more software.</p>


	<p>Next step:</p>


<code>
# pkg-get -i nano
</code>

	<h2>Install MySQL</h2>


	<p>Sun has a BigAdmin article that&#8217;s a great <a href="http://www.sun.com/bigadmin/features/articles/samp_setup.html">walkthrough for setting up MySQL on OpenSolaris</a> using <a href="http://www.blastwave.org/">Blastwave</a>.</p>


	<p>I completed through step 5I (Yikes!), the one about installing the MySQL <span class="caps">SMF</span> service.  It ends with this:</p>


<code>
# svcs -a | grep mysql
online 15:12:43 svc:/network/cswmysql5:default
</code>

	<p>Perhaps I&#8217;ll write a post specifically on <span class="caps">SMF</span> on some point, but suffice to say, that I really really liked it.  It beats the Linux equivalent (/etc/init.d/) without breaking a sweat.</p>


	<p>Also note that it&#8217;s probably time to revisit your path, as when I followed the Blastwave instructions followed by these, I ended up with the wrong version of <code>mysql</code> coming first.</p>


	<h2>Get familiar with your Apache</h2>


	<p>Be sure that you work with the version of Apache httpd that you intend to.  /etc/apache and /etc/apache2 are both present.  This is a good time to familiarize yourself with <a href="http://www.cuddletech.com/blog/pivot/entry.php?id=182">benr&#8217;s <span class="caps">SMF</span> cheatsheet</a> and the <a href="http://mail.opensolaris.org/pipermail/smf-discuss/2006-June/000672.html"><span class="caps">SMF FAQ</span></a> from Sun.  (That&#8217;s on a mailing list archive?  From last year?  Seriously?)</p>


	<h2>Install Ruby and Subversion</h2>


	<p>Prepare yourself.</p>


<code>
# pkg-get -i ruby
</code>
* ...coffee break&#8230; *
<code>
# pkg-get -i subversion
</code>

	<p>That gets you Ruby 1.8.5 and Subversion 1.4.3.  Not bad!</p>


	<h2>Download and install RubyGems and needed gems</h2>


	<p>To get started with RubyGems, there&#8217;s nothing different from <a href="http://docs.rubygems.org/read/chapter/3#page13">the regular installation process</a>.</p>


	<p>After that, try this command:</p>


<code>
# gem install rails mysql mongrel_cluster -y
</code>

	<p>It might work right off.</p>


	<p>If it fails, try installing some packages like autoconf, automake, and gcc3.  Try again ad see if the errors match those mentioned in  <a href="http://forum.textdrive.com/viewtopic.php?id=12630">this discussion</a>.  If so, <a href="http://svn.joyent.com/public/accelerators/">benr&#8217;s rbconfig.rb file</a> will solve the problem.  I <strong>didn&#8217;t</strong> have this problem when I worked with the OpenSolaris VMWare image, but I did when I installed b62 on a real physical machine.</p>


	<h2>Enjoy your Ruby stack!</h2>


	<p>The particulars of how you might want to set up a mongrel_cluster <span class="caps">SMF</span> may vary, but this should be enough to get you in the ballpark.</p>


	<h2>Postscript</h2>


	<p>My experiments with OpenSolaris were so successful that I took an installation on a physical machine at work and prepared it to be our extranet hub.  The best part is that all of our most critical corporate data can get packaged up and sent off to Amazon&#8217;s S3 service by a Ruby script that I whipped up in conjunction.  That beats the pants off what we had before, and now we&#8217;ve got a solid backup strategy on a solid system.  Very nice!</p>
