---
layout: post
title: My Love Letter to SOFIA
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>In November, I was evaluating frameworks to help me build web applications in Java.  My <a href="http://devblog.jimvanfleet.com/archives/000003.html">background</a> includes constructing several in <span class="caps">PHP</span> using Dreamweaver.  I had done a couple of &#8220;messy&#8221; projects using Servlets, <span class="caps">JSP</span> and Taglibs, but I wanted to get real experience with what Java, my &#8220;native&#8221; language, had to offer.  While I was looking for a job, I took the time to evaluate the web application frameworks that were available.  I already knew about Struts, and excitedly dug into the Manning <a href="http://www.manning.com/husted/">Struts in Action</a> book.</p>

<p>I read the entire thing, and was kind of puzzled.  I didn&#8217;t see anything in there that dealt with the problems I was familiar with, and the areas of flexibility that it offered didn&#8217;t add as much value for me as I had expected.  Still, though, I knew Struts was famous, and was confident that I could at least use it. </p>

<p>What I wanted, in addition, was a &#8220;last mile&#8221; solution for doing my web design.  I knew that Dreamweaver didn&#8217;t have the greatest level of support for <span class="caps">JSP</span> tags.  It was this search that led me to <span class="caps">SOFIA</span>.  I downloaded the platform, went through the tutorial and looked over the examples.  That was all it took for me to dispatch Struts from my toolkit and use <span class="caps">SOFIA</span> in its place.  </p>

<p>Here&#8217;s a list of the other bonuses that I got from <span class="caps">SOFIA</span> within the first two weeks.</p>

<dl>
<dt>&#8220;Live Page&#8221; view in Dreamweaver, via the translator servlet</dt>
<dd><p>This was exactly what I was looking for with my search in the first place.</p></dd>
<dt>Java-code free <span class="caps">JSP</span> pages</dt>
<dd><p>Java code on <span class="caps">JSP</span> pages is ugly, unrenderable by Dreamweaver, difficult to debug, nigh-impossible for web designers to work with, etc.</p></dd>
<dt>Swing-like coding of pages</dt>
<dd><p>I&#8217;ve since seen other frameworks that have similar <span class="caps">MVC</span> coding techniques, but I still like <span class="caps">SOFIA</span>&#8217;s the best.  I&#8217;d had exposure to Swing in the past, and this capability made coding <span class="caps">SOFIA</span> controllers a snap to get right into.  Suddenly, worrying about which submit button was pressed was a thing of the past.  You can have a submit button for each row in a DataStore and you&#8217;re one event.getRow() call away from figuring out exactly what to do with what set of data.</p></dd>
<dt>Trivial in-IDE debugging</dt>
<dd><p>Set breakpoints in your controller code and watch your page execute just as a standard Java application would.  This one still makes me very happy.</p></dd>
<dt>Professional construction and power</dt>
<dd><p>The <span class="caps">SOFIA</span> team has been at this for quite some time.  You might find their <a href="http://www.salmonllc.com/website/Jsp/vanity/SofiaPhilosophy.jsp">philosophy</a> regarding <span class="caps">SOFIA</span>&#8217;s open source status an interesting read.  I don&#8217;t have to read a book to reap the benefits of the long, hard road that the <span class="caps">SOFIA</span> developers have travelled; they&#8217;ve left a framework behind instead.  (Not that I mind reading!  I love it.)  They provide solutions to many advanced problems, and some quite interesting features that I&#8217;m still learning about.</p></dd>
<dt>Support and flexibility</dt>
<dd><p><span class="caps">SOFIA</span> does not use any bean or <span class="caps">POJO</span> persistence strategy itself, opting for <span class="caps">SQL</span>.  I felt that Hibernate more closely fit my needs in terms of database access and use.  Even though <span class="caps">SOFIA</span> doesn&#8217;t particularly have a use for it, there was a BeanDataStore ready for me to use and adapt.  In addition, the <span class="caps">SOFIA</span> team has been nothing but helpful in helping me through troubles, and the user community is a fairly active one.</p></dd>
</dl>

<p>
I don&#8217;t anticipate leaving <span class="caps">SOFIA</span> any time soon;  they&#8217;ve enabled me to focus on the problems my application faces, and not on data interface and plumbing.  I&#8217;m fortunate that I&#8217;m doing green field work, but if you&#8217;re fortunate enough not to be <a href="http://www.theserverside.com/discussions/thread.tss?thread_id=24685">tied in</a> already, I couldn&#8217;t recommend <span class="caps">SOFIA</span> more highly.</p>
