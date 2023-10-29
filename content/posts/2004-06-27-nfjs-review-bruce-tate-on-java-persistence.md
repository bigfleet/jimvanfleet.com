---
layout: post
title: ! 'NFJS Review:  Bruce Tate on Java Persistence'
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-06-27
---
We started with <span class="caps">EJB</span>.  I listened to this essentially out of curiousity.  I know <span class="caps">EJB</span> is not going to fit with the projects I do in the near future.  When the time comes to fully undertake an <span class="caps">EJB</span> project, I'll need to see real code before these background talks are really useful&#8212;I already know <span class="caps">EJB</span> is very complicated.

He followed with a discussion of <span class="caps">JDO</span>.  This discussion raised a philosophical question for me that I really can't evaluate at this time.  I'll pose it to you.

<span class="caps">JDO</span> is a spec.  That means when you talk about <span class="caps">JDO</span>, you're not talking about a product, you're talking about a kind of tool that you'd like to use.  To this end, <span class="caps">JDO</span> is a generic persistence spec.  The persistent space could be a flat file, <span class="caps">XML</span>, OODBMS, or <span class="caps">RDBMS</span>&#8212;or probably even memory, we didn't discuss that.

As an agile practitioner, this sounds great!  I'd love to be able to develop client and test code that would not change when it's time to change the persistent store configuration from memory to <span class="caps">RDBMS</span>.  Make the change, run the unit tests, and wham, you've taken a gigantic step towards deployment.  As a user, I'd wonder, "But what on earth are they going to do about the query language?  Surely you can't query an <span class="caps">XML</span> file the same way that you can query a database?"  Turns out this is only partly true, but the query language differences do lead to complications.  As a project manager, I say "OK, sounds nice.  But why do we actually *need* this?  And wait, it costs $600 for each developer to code with?  Why not just code your own memory persistence layer (2 minute hashtable) if you need one, put it behind a factory/interface, and save us some money?"

Is there sometimes a conflict between "potential" agility and need?  If agility is the ability to respond to problems quickly, is it possible to extend a measure of agility into the future?

At any rate, this particular manifestation of the issue is moot.  As long as <span class="caps">JDO</span> remains at 1.x, no way am I spending money on an implementation when I'm "vested" in Hibernate.  Hibernate came out well in the comparison, although many are concerned about its youth, support, and lack of proven track record.  Note that I'm just parroting, I have no idea what Hibernate's track record is.  It certainly seems to me like if you paid for support, that'd be all that was necessary.  Paying for support of a free product has always seemed extremely reasonable to me.  Also, in my experience, the free support community for Hibernate is actually quite good.

In the end, Bruce looked to the future with <span class="caps">EJB 3</span> and <span class="caps">JDO 2</span>.  He's doing a good enough job keeping his thoughts on this in public, so I won't go into them here.  But remember, those specs aren't even out, and they will take time to implement-- time which I certainly don't have, I need to be growing.


My marks for Bruce were excellent.  He is a very effective group speaker, surprisingly so for a code monkey.
