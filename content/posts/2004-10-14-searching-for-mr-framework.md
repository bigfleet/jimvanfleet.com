---
layout: post
title: Searching For Mr. Framework
tags: []
status: publish
type: post
published: true
meta: {}
---
<dl>
<dt><span class="caps">SOFIA</span></dt>
<dd><p>I&#8217;ve used <a href="http://www.sf.net/projects/salmon"><span class="caps">SOFIA</span></a> in the past, and I&#8217;ve been <a href="http://devblog.jimvanfleet.com/archives/000031.html">quite satisfied</a> with it.  I am strongly committed to working with a <a href="http://www.martinfowler.com/bliki/POJO.html"><span class="caps">POJO</span></a> domain layer, however, and that doesn&#8217;t fit with the core Salmon team&#8217;s development methodology.  <span class="caps">SOFIA</span> has very many nice features, but making my domain objects play nicely with framework constructs is getting harder and harder, and there are plenty of other tasks that I need to spend time on.  Also, the controllers are very tightly coupled to <span class="caps">SOFIA</span>, almost by necessity.  There&#8217;s simply no way that an application could be meaningfully ported away from <span class="caps">SOFIA</span> with any sort of ease.  I&#8217;m learning there are other options.</p></dd>
<dt>Tapestry</dt>
<dd><p>Tapestry already got dismissed <a href="http://devblog.jimvanfleet.com/archives/000061.html>here</a>.</p></dd>
<dt>Struts</dt>
<dd><p>Almost nobody who uses Struts likes it, so why would I?</p></dd>
<dt>WebWork 2</dt>
<dd><p>The current leader of the pack.  <a href="http://www.opensymphony.com/webwork/">WebWork2</a> is very simple and quite small, yet contains many of the features needed by all web application frameworks.  I&#8217;ve gotten familiar with <a href="http://www.springframework.com">Spring</a>, and some of the usage patterns with WebWork look <strong>very</strong> very similar to Spring&#8217;s <span class="caps">IOC</span> functionality.  I&#8217;m still in the beginning stages of working up a small test application, but I&#8217;ve already gotten farther more quickly with WebWork than with <span class="caps">SOFIA</span>, and that&#8217;s having never worked with WebWork before.  It&#8217;s very easy to test and it&#8217;s trivial to generate precisely the <span class="caps">HTML</span> that you want.  That will likely be an important requirement for our product.</p></dd>
<dt>Spring <span class="caps">MVC</span></dt>
<dd><p>I&#8217;ve got <a href="http://www.amazon.com/exec/obidos/redirect?tag=jimvanfleetco-20&#38;path=tg/detail/-/0764558315/qid=1097780042/sr=8-1/ref=pd_csp_1?v=glance&#38;s=books&#38;n=507846">Rod Johnson&#8217;s new book</a> and reading through that didn&#8217;t give me the best feeling towards Spring <span class="caps">MVC</span>.  As a matter of fact, I read a <a href="https://webwork.dev.java.net/servlets/ReadMsg?list=dev&#38;msgNo=3677">post</a> on the WebWork2 mailing list, that a useful summary, and I haven&#8217;t used WebWork for more than a couple of weeks.  Thanks to <a href="http://jroller.com/page/raible">Matt Raible</a>, I at least have a <a href="http://www.devx.com/Java/Article/22134">couple</a> <a href="http://www.ociweb.com/jnb/jnbOct2004.html">places</a> to check out for some easier examples.</p></dd>
<dt>Ruby, the dark horse</dt>
<dd><p>Thanks to <a href="http://www.ruby-forum.org/bb/viewtopic.php?t=87">this thread</a> on the Ruby forum, I was able to get RubyGems up and running, and <a href="http://www.rubyonrails.org/show/HomePage">Rails</a> came shortly thereafter.  Rails has its own <a href="http://www.ruby-forum.org/bb/viewtopic.php?t=87">forum</a> and is mind-bogglingly simple to start using, as .  The real barrier is my familiarity with Ruby syntax, which leads to pointers to the first Pragmatic Programmers&#8217; <a href="http://www.rubycentral.com/book/index.html">book</a> and <a href="http://poignantguide.net/ruby/">why&#8217;s poignant guide to Ruby</a>, which is the single funniest technical document I&#8217;ve ever read.</p></dd>
</dl>

<p>That&#8217;s it!  I&#8217;ll keep you informed.</p>
