---
layout: post
title: A Ruby Writeup
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Original poster writes:</p>


<blockquote><pre>
&gt; Anyone is using Ruby on Rail application for
&gt; production? Is it hype? Is it really new way to
&gt; increase productivity? Humm I am very skeptical to
&gt; believe that. Let's see the development effort wil be
&gt; 10x faster by telling the team members to use the new
&gt; programming language, new framework, etc. Does ruby
&gt; has multi-thread capabilities? concurrency? what kind
&gt; of data persistent technology are there for Ruby? Does
&gt; it work with hibernate? How you would like to built
&gt; ruby applications with transaction support?
</pre></blockquote>
<p>
My Java stack of choice includes Spring, Hibernate, and WebWork.  I am not an expert with those technologies, but I have now completed two fairly major projects with them, and I like them quite a lot.  I&#8217;ve been programming in Java since college, and I like it quite a lot as well.
</p>
<p>
I&#8217;ve put together three smaller applications with Ruby on Rails, am beginning to build one large one.  Here&#8217;s my take, and I&#8217;d be glad to give a bullet presentation at a meeting if there was interest in learning more.
</p>
<p>
I love Ruby and Rails.  It&#8217;s a great fit for a lot of the work I do, since I do a lot of green-field work.  I have my doubts if Rails is ready for the enterprise in general, but it could definitely be right for <strong>some</strong> enterprises.  For example, I&#8217;m using Rails to write the project that I just started my first business to manage.
</p>
<p>
I&#8217;ll run down your questions in turn.
</p>
<h3>&#8220;Is it hype?&#8221;</h3>
<p>No.  There is a lot of developer buy-in.  The community around Rails is unbelievably helpful and knowledgeable.  The framework itself is a joy to work with, and reminds me and many others of why they started programming in the first place.  It is making headway in the &#8220;Java thought leader&#8221; space, as well.  As Erik mentioned, the leader knows how to get the project exposure.  Rails is here to stay.</p>

<h3>&#8220;Does it increase productivity?&#8221;</h3>
<p>Yes.  How much depends on your familiarity with Java, how well you have your Java <span class="caps">IDE</span> shortcuts set up, etc.  But if you are hand-typing your Hibernate mapping files or Spring configuration, it&#8217;s a good bet you that you will be more productive in Rails.  </p>

<p>Maybe if you&#8217;re as smart as Justin Gehtland (which I am not) you&#8217;ll be more productive in four days.  For me, it&#8217;s taken a few months to get comfortable with the language and the framework.  You can&#8217;t just hop right over and expect to still be an expert in a language you&#8217;ve never used before.  </p>

<p>If your project is large enough for a team, your team will have to buy in.  This is one of the considerations to make.  You might be better off giving a <a href="http://www.randsinrepose.com/archives/2005/03/20/free_electron.html">free electron</a> a gigantic project and watching them go.  Your programmers should evaluate Rails individually and you should value their input.  But it is worth their time to make an evaluation.  If they don&#8217;t feel comfortable with Ruby, any potential productivity gains could disappear.</p>

<h3>&#8220;Is Ruby multi-threaded with concurrency?&#8221;</h3>

<p>Yes, but to be fair, this is not as good as it could be.  Rails cannot make use of multiple processors at this time, as I understand.  This is due to limitations in Ruby, not in the framework.</p>

<h3>&#8220;What kind of data persistence is there for Ruby?&#8221;</h3>

<p>While <a href="http://groups.yahoo.com/group/novajug/message/8456">Erik&#8217;s answer</a> is correct for Ruby (the language), if you plan to use Rails (the framework) with anything but ActiveRecord (a helper framework for Rails), you will need someone who really knows their stuff to write you some code.  Switching out ActiveRecord is not a trivial activity when writing a Rails application.  I&#8217;ve heard those &#8220;in the know&#8221; speculate that it would be &#8220;a hundred lines of code&#8221; but take that with a grain of salt.</p>

<h3>&#8220;Does it work with Hibernate?&#8221;</h3>

<p>Not directly.  You could, however, access a Rails database with Hibernate <strong>very</strong> easily.  Hibernate is simply more flexible than ActiveRecord in what it can map.  ActiveRecord relies on certain naming and structure conventions to make it easier and quicker to get an application working.</p>
<p>For this reason, Rails may not be a good choice for legacy applications, or applications where the schema has been handed down from on high.</p>
<p>ActiveRecord and Hibernate are both <span class="caps">ORM</span> tools, but I don&#8217;t think they&#8217;re very similar.  In terms of feel, they&#8217;re nothing alike.  (Also, I have not used transactions in Rails because I haven&#8217;t needed them.)</p>

<p>Maybe I should add another question here which is </p>

<h3>Bonus Question: &#8220;Can this get me fired?&#8221;</h3>

<p>The answer here is maybe.  If you just jump into it and spend all your work time toying with Ruby, then your claims of &#8220;This will make me more productive!&#8221; might fall on deaf ears.  </p>

<p>But get used to the language, browse the good <a href="http://poignantguide.net/ruby/">Ruby</a> <a href="http://www.whytheluckystiff.net/ruby/pickaxe/">books</a> on-line, and do a few demos in your off hours.  Or, if you&#8217;ve got a Friday that you can bluff your way through, give it a day.  You might catch the bug.

	<p>I ended up throwing together a bug tracker that was more fully-featured than the one it had taken the resident programmer a few months to put together in a couple of days.  That could get you the opposite of fired, if handled appropriately.   The gains are real, but I don&#8217;t believe it&#8217;s for everyone in every situation.</p>


	<p>Of course, three days later, I ditched what I had written for trac&#8230;  Ruby doesn&#8217;t necessarily improve your decision making skills.</p>


<h3>My conclusion:</h3>

<p>Rails is cutting edge, but not bleeding.  I anticipate in the next few months, Rails is going to go 1.0.  There have been parties launching production sites, and they are doing a superb job of getting the bugs out.</p>

<p>If you have a dedicated server for your application, the leading web-server stack (Apache and fastcgi) should have no problem <span class="caps">RIGHT NOW</span>.  If you&#8217;re willing to experiment with a new web-server as well, lighttpd and fastcgi are reported to do even better.  You may have to babysit lighttpd a little.</p>

<h3>Update</h3>

<p>The original poster contacted me asking to clarify that he did <strong>not</strong> ask if it would get him fired.  I thought that I pointed out that I had added that question in the post, but I&#8217;ll reiterate here for clarity&#8217;s sake.</p>
