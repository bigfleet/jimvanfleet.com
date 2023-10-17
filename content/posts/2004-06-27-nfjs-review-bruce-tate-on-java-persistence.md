---
layout: post
title: ! 'NFJS Review:  Bruce Tate on Java Persistence'
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>We started with <span class="caps">EJB</span>.  I listened to this essentially out of curiousity.  I know <span class="caps">EJB</span> is not going to fit with the projects I do in the near future.  When the time comes to fully undertake an <span class="caps">EJB</span> project, I&#8217;ll need to see real code before these background talks are really useful&#8212;I already know <span class="caps">EJB</span> is very complicated.</p>


	<p>He followed with a discussion of <span class="caps">JDO</span>.  This discussion raised a philosophical question for me that I really can&#8217;t evaluate at this time.  I&#8217;ll pose it to you.</p>


	<p><span class="caps">JDO</span> is a spec.  That means when you talk about <span class="caps">JDO</span>, you&#8217;re not talking about a product, you&#8217;re talking about a kind of tool that you&#8217;d like to use.  To this end, <span class="caps">JDO</span> is a generic persistence spec.  The persistent space could be a flat file, <span class="caps">XML</span>, OODBMS, or <span class="caps">RDBMS</span>&#8212;or probably even memory, we didn&#8217;t discuss that.</p>


	<p>As an agile practitioner, this sounds great!  I&#8217;d love to be able to develop client and test code that would not change when it&#8217;s time to change the persistent store configuration from memory to <span class="caps">RDBMS</span>.  Make the change, run the unit tests, and wham, you&#8217;ve taken a gigantic step towards deployment.  As a user, I&#8217;d wonder, &#8220;But what on earth are they going to do about the query language?  Surely you can&#8217;t query an <span class="caps">XML</span> file the same way that you can query a database?&#8221;  Turns out this is only partly true, but the query language differences do lead to complications.  As a project manager, I say &#8220;OK, sounds nice.  But why do we actually <strong>need</strong> this?  And wait, it costs $600 for each developer to code with?  Why not just code your own memory persistence layer (2 minute hashtable) if you need one, put it behind a factory/interface, and save us some money?&#8221;</p>


	<p>Is there sometimes a conflict between &#8220;potential&#8221; agility and need?  If agility is the ability to respond to problems quickly, is it possible to extend a measure of agility into the future?</p>


	<p>At any rate, this particular manifestation of the issue is moot.  As long as <span class="caps">JDO</span> remains at 1.x, no way am I spending money on an implementation when I&#8217;m &#8220;vested&#8221; in Hibernate.  Hibernate came out well in the comparison, although many are concerned about its youth, support, and lack of proven track record.  Note that I&#8217;m just parroting, I have no idea what Hibernate&#8217;s track record is.  It certainly seems to me like if you paid for support, that&#8217;d be all that was necessary.  Paying for support of a free product has always seemed extremely reasonable to me.  Also, in my experience, the free support community for Hibernate is actually quite good.</p>


	<p>In the end, Bruce looked to the future with <span class="caps">EJB 3</span> and <span class="caps">JDO 2</span>.  He&#8217;s doing a good enough job keeping his thoughts on this in public, so I won&#8217;t go into them here.  But remember, those specs aren&#8217;t even out, and they will take time to implement&#8212;time which I certainly don&#8217;t have, I need to be growing.</p>


	<p>My marks for Bruce were excellent.  He is a very effective group speaker, surprisingly so for a code monkey.</p>
