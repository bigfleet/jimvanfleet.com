---
layout: post
title: ! 'What''s Now In Rails: Libraries'
tags:
- Tech
status: publish
type: post
published: true
meta:
  _clicky_goal: a:2:{s:2:"id";s:0:"";s:5:"value";s:0:"";}
---
<blockquote>
		<p>What Gems/Jimmies are you finding indispensable these days?</p>
	</blockquote>


	<p><cite style="float:right;margin-right:10%"><a href="http://www.twitter.com/peter_braswell">@peter_braswell</a></cite></p>


	<h2>Dr. Nic&#8217;s Textmate Footnotes</h2>


	<p>Famous Railsist &#8220;Dr. Nic&#8221; has a great <a href="http://github.com/drnic/rails-footnotes/tree/master">footnotes plugin</a> which you can get a taste for from the <span class="caps">README</span> on that page.  It&#8217;s a must install if you choose TextMate as your editor.</p>


	<h2>Named scopes</h2>


	<p>Your Rails developer badge will shortly be revoked if you do not learn and use named scopes liberally.  The way that they can be named, composed, and reused in multiple contexts can result in some extremely powerful and expressive code, that remains readable and even has some excellent performance characteristics.</p>


	<p>Learn more at <a href="http://railscasts.com/episodes/108-named-scope">RailsCasts</a> and <a href="http://ryandaigle.com/articles/2008/3/24/what-s-new-in-edge-rails-has-finder-functionality">Ryan&#8217;s blog</a></p>


	<h2>will_paginate</h2>


	<p>Out of the box Rails pagination is a thing of the past, I think.  <a href="http://github.com/mislav/will_paginate/tree/master">will_paginate</a> is as much of a drop in as it gets, and it&#8217;s flexible in all the right ways.  It&#8217;s also kept very much up to date and remains in active development.</p>


	<h2>rSpec and cucumber</h2>


	<p>While I&#8217;ve decided that my overall thoughts on testing are probably going to end up being a talk, I can provide my favorites here.  <a href="http://rspec.info/">rSpec</a> provides a nicer syntax than test/unit for my tastes.  Further, the capabilities that come with the stories functionality provided by <a href="http://github.com/aslakhellesoy/cucumber/wikis">cucumber</a> (detailed by <a href="http://peepcode.com/products/rspec-user-stories">Peepcode</a>) have been a revelation on my primary project.</p>


	<h2>fixture_replacement2</h2>


	<p>I personally have come to dislike fixtures strongly.  There are definitely techniques that can be used to reduce their downsides, like <a href="http://github.com/aiwilliams/dataset/tree/master">dataset</a> (previously known as scenarios), but I favor leaving them behind altogether.  Once you&#8217;ve made <strong>that</strong> decision, you have options still, like <a href="http://giantrobots.thoughtbot.com/2008/6/6/waiting-for-a-factory-girl">factory-girl</a> (plenty of good alternatives mentioned at that link, as well).  dataset even mentions that it can play along with other alternatives</p>


	<p>For my part, I&#8217;m satisfied with <a href="http://github.com/smtlaissezfaire/fixture-replacement-git/tree/master">fixture_replacement</a> which is in a second version.  It doesn&#8217;t look like it&#8217;s active, but I enjoy the flexibility that comes with being able to ask easily for objects that have or have not been persisted and they have the exact same set-up.  I hope to provide more detail there later.</p>


	<p>These are the only tips and techniques that I&#8217;d bring onto each project.  For anything else, I&#8217;d be checking out the diverse Rails ecosystem out there!  It&#8217;s getting more pleasant by the week.</p>
