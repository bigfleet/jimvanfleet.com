---
layout: post
title: Getting Started with Getting Things Slung
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Insipired by a chance to win <a href="http://developers.joyent.com/wiki">one year of a large accelerator</a>, I started <a href="http://developers.joyent.com/wiki/GettingThingsSlung">Getting Things Slung</a>.  I am working on a Java application that is designed to sync contacts from MS Outlook, so I&#8217;m somewhat interested in the off-line/on-line client space.  Also, the prize is pretty enticing, and the screenshot sure was pretty!  So that&#8217;s all it took for me to decide to spend the plane ride over working on getting an entry ready.</p>


	<p>I&#8217;m doing a Mac <span class="caps">OS X</span> version, and I really have no interest in the Windows side of things.</p>


	<h2>Briefing</h2>


	<p>The pair of Joyent web pages have generally good information.  I&#8217;m intending this blog post to supplement that material.  Also, even though at one point I was using it all the time, there&#8217;s now nothing I hate worse than Trac markup syntax, so I&#8217;m not going to use it.</p>


	<p>I also recommend reading this through once before you go through it and try to follow it.</p>


	<h2>Basecamp (not that one)</h2>


	<p>We&#8217;re trying to simulate a server-side and client-side sync process.  There&#8217;s no reason that we can&#8217;t set that up on the same computer.  Ultimately, in addition, we&#8217;ll want the trunk directory in the Slingshot.app file to be the <strong>same</strong> as the server-side code.</p>


	<h3>Set up Subversion</h3>


	<p>I set up a Subversion repository on my own machine just for these purposes.  I checked in the most recent release of <a href="http://www.rousette.org.uk/projects/">Tracks</a> into my repository, then checked it out to a working directory in my typical Rails workspace, and also checked it in from within the .app file.  (You can cd into them using the terminal&#8212;go ahead!)</p>


	<h3>Getting TextMate open</h3>


	<p>You&#8217;ll end up with <span class="caps">TWO</span> TextMate windows open.  One is for the client-side, and that will have extra directories in it.  The other is for the server-side.</p>


	<h3>Getting Terminals in position</h3>


	<p>You&#8217;ll need terminal windows open to have a window to start mongrel_rails (for the server side) and for running <code>svn up</code> inside the Slingshot VM.</p>


	<h2>Head Above Water</h2>


	<p>The first place to go after getting yourself in position is to work on getting the client side in position to do the first downward sync.  The <a href="http://developers.joyent.com/wiki/BasicApp">wiki docs</a> can walk you through that.  For me, the process involved editing the <code>start.sh</code>, <code>sync_up.sh</code>, and <code>sync_down.sh</code>, while making sure that Tracks itself was running and passing tests.  Let&#8217;s just say that some parts of the code are a little brittle.</p>


	<p>As an example, the operative line from the <code>sync_up.sh</code> file looked like this for me:</p>


<pre>
<code>
ruby ../bin/rake joyent_slingshot:sync_up SYNC_CONTROLLER=http://localhost:4000/sync/up
</code>
</pre>

	<h2> Monday Night <span class="caps">RAW</span> on your adopted application.</h2>


	<p>I had to write migrations and fix not-exactly-bugs in Tracks to get it ready to run in the Slingshot environment.  This will happen to you if you didn&#8217;t write the code, so get ready to &#8220;stand on the shoulders of giants&#8221; as Adam Keys might say.</p>


	<p>You&#8217;ll also have to follow the instructions for the <a href="http://developers.joyent.com/wiki/SlingshotPlugin">Slingshot plugin</a> which, by virtue of being installed on the server-side, is <span class="caps">ALSO</span> installed on the client side, because you set them to be to same with Subversion.  <strong><span class="caps">RIGHT</span>?</strong></p>


	<p>The existing examples include&#8230; let&#8217;s call it a non-granular approach to preparing the set of information to be synchronized.  This is OK for now, go ahead and do that.  We&#8217;ll make things a little better before it&#8217;s all over.</p>


	<h2>Check <span class="caps">XML</span> from the server</h2>


	<p>I had a problem with having the <strong>first</strong> request to my server-side sync action completing successfully.  After catching (by accident) the Joyent Scotts out on the balcony, Scott Burton told me that he had <strong>the same problem</strong> and it had to do with a different version of Rails running in <code>vendor/rails</code> than I had mentioned in <code>config/environment.rb</code> so watch for that.  That brought my first work session to a halt.</p>


	<p>Don&#8217;t stop until you&#8217;re pulling <span class="caps">XML</span> down.  You&#8217;re more than half way done at this point.</p>


	<p>You know, this is enough for one post.</p>
