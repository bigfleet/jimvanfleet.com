---
layout: post
title: Spring and Hibernate
tags: []
status: publish
type: post
published: true
meta: {}
---
<ul>
<li>My picture looks more or less the same, only instead of Spring in the middle, I have bits of <span class="caps">SOFIA</span>, and my domain model</li>
<li>I really like the way the responsibilities of the layers are broken down.  I don&#8217;t even know if this is an area that people debate, but it looks all right to me.  It&#8217;ll probably end up as the genesis of those blog entries here</li>
<li>Hibernate is medium learning curve?  I have not yet used the advanced features, but I found it pretty easy to get comfortable with. </li>
<li>Right now, I haven&#8217;t figured out the best way to have Hibernate abstract away cleanly.  Also, why would I do this?  If this project is alive two years from now, it will be because it&#8217;s running bug-free.  Why mess with something that&#8217;s working?  And would I ever leave Hibernate in the near future?  No.</li>
<li>Now I need to implement <span class="caps">DAO</span> because I might migrate away from Hibernate?  Sounds like <a href="http://xp.c2.com/YouArentGonnaNeedIt.html"><span class="caps">YAGNI</span></a> to me.  Also, <a href="http://java.sun.com/blueprints/patterns/DAO.html"><span class="caps">DAO</span></a> makes my head hurt.</li>
<li>I wouldn&#8217;t say that <a href="http://xdoclet.sourceforge.net/">XDoclet</a> assists with writing the mapping file.  I&#8217;d say that it helps you manage your mapping files by allowing you to write them within the source code itself, instead of having to maintain <strong>another</strong> resource.</li>
<li>I didn&#8217;t know that&#8217;s what <a href="http://www.martinfowler.com/articles/injection.html">inversion of control</a> was.  Now I do.</li>
<li>I&#8217;m going to quit reading.  Struts is just so complicated to me.</li>
