---
layout: post
title: You're Fired
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I&#8217;ve never really had that much of a problem with keeping the mapping files seperately.  If you&#8217;re making a change to a domain object, I can&#8217;t imagine even a fairly ignorant developer failing to update the mapping file.  Even then, the problem would quickly bubble to the surface for them.</p>

<p>Also, take a look at <a href="http://www.hibernate.org/102.html">this description</a> of the different phases of round-trip development using Hibernate.  I&#8217;m certainly not of the opinion that schema-to-code or mapping-to-code generation are viable in the long term.  While you may have certain objects that are &#8220;value&#8221; objects in your domain, the entire point of OO programming is to encapsulate state <strong>and</strong> behavior in the same place.  Good luck keeping the methods you write intact out in the wild if you&#8217;re automatically generating your domain object code!</p>

<p>And since the mapping-to-schema connection is quite natural, since I&#8217;m not doing anything but <a href="http://www.site.uottawa.ca:4321/oose/index.html#greenfielddevelopment">green field</a> work, there&#8217;s no question which direction I&#8217;ll be going.  So it all comes down to whether or not XDoclet can do everything that I&#8217;d like in terms of generating a mapping.  While it may be able to, <strong>is it worth learning how?</strong>  You can hand-write Hibernate mapping files easily and exactly to specification.  I just don&#8217;t see that XDoclet is worth it for Hibernate.  I&#8217;m sure <span class="caps">EJB</span> will keep it alive, but I&#8217;m headed back to manual generation of mappings for my next project.</p>
