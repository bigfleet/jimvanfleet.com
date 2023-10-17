---
layout: post
title: Leitmotif
tags:
- Tech
status: publish
type: post
published: true
meta:
  _edit_last: '1'
---
<h2>A variation on a theme in modern software development.</h2>
<p>A few weeks ago, I was wondering about how to keep <a href="http://mocksup.com/">my fledgling start-up</a> from falling prey to unplanned maintenance or downtime.  Because of the nature of the site (managing design mockups), the element that most concerned me was in-Passenger handling of thumbnailing. We use <a href="http://github.com/thoughtbot/paperclip">paperclip</a>.  Paper relies on <a href="http://www.imagemagick.org/script/index.php">ImageMagick</a>, a notorious resource hog, <a href="http://magick.imagemagick.org/script/architecture.php#cache">especially when it comes to <span class="caps">RAM</span></a>.  I didn&#8217;t want to be able to let a single user hamstring our entire site for a thumbnail.</p>
<p>Fortunately, at exactly the same time, <a href="http://www.jstorimer.com/">Jesse Storimer</a> created <a href="http://www.jstorimer.com/ruby/2010/01/30/delayed-paperclip.html">delayed_paperclip</a> to defer thumbnailing (or any other paperclip processing) using <a href="http://github.com/tobi/delayed_job">delayed_job</a>.  Very cool!  I started watching it.</p>

<p>I knew that I wanted A/B testing and metrics to play a big role in <a href="http://mocksup.com/">Mocksup</a> and, right now, that means <a href="http://code.google.com/p/redis/">Redis</a> and <a href="http://vanity.labnotes.org/">Vanity</a>.  After a very successful trial run with them both, I knew that Redis would play a part in the application&#8217;s future.  Having read <a href="http://github.com/blog/542-introducing-resque">a history of Resque</a> from my friend <a href="http://twitter.com/defunkt">defunkt</a>, that bit of software was <a href="http://jimvanfleet.com/career/telling-the-future.html">on my list</a> to try out anyway.  Resque was easy to get up and running.  Why not try to port delayed_paperclip to Resque?  After some  hacking, it was working fine in my application.  Even cooler!  So <a href="http://twitter.com/bigfleet/status/8733966363">I blabbed on Twitter about it</a> to see if anybody else liked the idea.  Some people did, including <a href="http://twitter.com/defunkt/status/8739679556">the man himself</a>.  But I couldn&#8217;t release with broken tests, that&#8217;s not me!</p>

<p>I got the tests passing, and let Chris know.  <a href="http://twitter.com/defunkt/statuses/8818912762">He tweeted about it</a> and suddenly my little hack is <a href="http://skitch.com/bigfleet/nwka6/explore-github-github">trending on GitHub</a>.  If Mom could see me now!  Well, I mean, she can see me, but&#8212; if&#8230; I could explain it to her without her being bored!  Yeah, that's it!</p>

<p>Seeing my "name in lights" was definitely gratifying, but I started to wonder what the future would be for this little piece of code.  The author is using Delayed::Job; he <strong>works</strong> at <a href="http://www.shopify.com/">Shopify</a> for god&#8217;s sakes.  He may not be interested in this functionality.  And what of the integration with paperclip over time&#8212; am I really going to be able to keep this supported?  There&#8217;s a lot of sophisticated Ruby work happening in that plugin, to balance Rails, Paperclip, and Delayed::Job.  So I sent a pull request and figured &#8220;Let&#8217;s just see.&#8221;

<a href="http://twitter.com/jstorimer">Jesse</a> could not have been cooler, and integrated my changes immediately!  He even added on an additional bit of coolness that made the plugin even better for the end user.  After one last little change pointing that additional nicety out to the plugin&#8217;s potential users, I was done!  I updated my fork and pointers to it with the information that the functionality I added was merged into the project.</p>

<p>Let&#8217;s recap the winners:</p>

<ul>
	<li><a href="http://thoughtbot.com/">Thoughtbot</a>, for getting an even more robust and featureful plugin allowing delayed post-processing</li>
	<li>Jesse Storimer, who gets a plugin with more exposure.</li>
	<li>Chris and resque, for getting a new <a href="http://wiki.github.com/defunkt/resque/plugins">plugin for resque</a></li>
	<li>The potential users of delayed_paperclip, for being able to choose which work queue system fits them better.</li>
	<li>Me, for scratching an itch and getting involved with all these great people and projects.</li>
</ul>

<p>To me, much of the beauty of contributing to open source is being a member of this kind of community.  I enjoyed it so much, I had to write a little bit about it.</p>
