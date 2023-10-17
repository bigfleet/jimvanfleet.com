---
layout: post
title: ! 'Write-Up:  Introduction to Tapestry'
tags: []
status: publish
type: post
published: true
meta: {}
---
<dl>
<dt><font size="+2">Pure <span class="caps">HTML</span> capabilities</font></dt>
<dd>
<p>You can mark up a page in pure, unadorned <span class="caps">HTML</span>.  The files that your application will server are <span class="caps">HTML</span> files.  This allows a level of separation between the developers and the web design team.  I&#8217;m wishing I could pull that off!  My pages just don&#8217;t look good.</p>
<p>It also allows for rapid prototyping.  You can make everything look the way it&#8217;s supposed to look in <span class="caps">HTML</span>, then have the developers come in behind.  Tapestry will automatically replace certain <span class="caps">HTML</span> tags once the developers touch them up a bit.</p></dd>
<dt><font size="+2">Architecture</font></dt>
<dd><p>Tapestry ends up being a single-servlet <a href="http://www.martinfowler.com/eaaCatalog/frontController.html">front controller</a> onto the rest of your application.  It uses extensive <span class="caps">URL</span> rewriting, and external file resources to tie everything together.</p></dd>
<dt><font size="+2">Teamwork</font></dt>
<dd><p>My first impression is that Tapestry would integrate extremely well with <a href="http://www.hibernate.org/">Hibernate</a>.  The &#8220;distance&#8221; between a web request and your domain model is considerably shorter than with Servlets, Struts, or possibly even <span class="caps">SOFIA</span>.  Also, the lifecycle of Hibernate Sessions has a natural management within a certain Tapestry construct.</p>
<p>If a small team wanted to put together a quick, easily defined application for themselves, they might be looking at a week for the whole thing.  And if the team had a graphic designer, it would even look good.</p></dd>
<dt><font size="+2">Getting Down To Business</font></dt>
<dd><p>There is a lot of mental overhead when using Tapestry.  A developer would probably need someone either very smart or quite experienced to use it reliably.  Although it does have line-precise error reporting (quite nice), good developer documentation, etc. it will still be very hard for an average developer to use it effectively without some practice.  I do feel that this is an advantage for <a href="http://www.sf.net/projects/salmon"><span class="caps">SOFIA</span></a>.</p></dd>
<dt><font size="+2">Power</font></dt>
<dd><p>In terms of functionality, Tapestry can take the roof right off for you.  There are some extremely advanced features which we only briefly touched on.  For those developers who are already familiar with complementary technologies like <a href="http://jakarta.apache.org/velocity/">Velocity</a>, Tapestry could wrap your problem up and put a bow on it</p></dd>
<dt><font size="+2">Extensibility</font></dt>
<dd><p>One of the reasons I&#8217;m bullish on its future of Tapestry is its component based nature.  I saw an excellent calendar, something they called a &#8220;pallete,&#8221; which is exactly what <a href="http://fantasysports.yahoo.com">Yahoo! Fantasy Sports</a> uses for pre-ranking fantasy drafts.</p>
<p>I do forsee some, but not nearly all, shops currently using <a href="http://jakarta.apache.org/struts/">Struts</a> migrating to Tapestry. Erik certainly seems to have evangelical conviction for it.  As a result, the &#8220;libraries&#8221; for Tapestry will continue to grow and provide developers more useful, user-friendly tools to develop with.  It will be harder and harder to ignore as time passes.  But, who knows what tomorrow brings?</p></dd>
</dl>
