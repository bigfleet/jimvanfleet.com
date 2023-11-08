---
layout: post
title: Spring and Hibernate
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-04-13
---

* My picture looks more or less the same, only instead of Spring in the middle, I have bits of <span class="caps">SOFIA</span>, and my domain model
* I really like the way the responsibilities of the layers are broken down.  I don't even know if this is an area that people debate, but it looks all right to me.  It'll probably end up as the genesis of those blog entries here
* Hibernate is medium learning curve?  I have not yet used the advanced features, but I found it pretty easy to get comfortable with. 
* Right now, I haven't figured out the best way to have Hibernate abstract away cleanly.  Also, why would I do this?  If this project is alive two years from now, it will be because it's running bug-free.  Why mess with something that's working?  And would I ever leave Hibernate in the near future?  No.
* Now I need to implement <span class="caps">DAO</span> because I might migrate away from Hibernate?  Sounds like [YAGNI](http://xp.c2.com/YouArentGonnaNeedIt.html) to me.  Also, [DAO](https://www.oracle.com/java/technologies/data-access-object.html) makes my head hurt.
* I wouldn't say that [XDoclet](https://xdoclet.sourceforge.net/xdoclet/index.html) assists with writing the mapping file.  I'd say that it helps you manage your mapping files by allowing you to write them within the source code itself, instead of having to maintain *another* resource.
* I didn't know that's what [inversion of control](https://www.martinfowler.com/articles/injection.html) was.  Now I do.
* I'm going to quit reading.  Struts is just so complicated to me.
