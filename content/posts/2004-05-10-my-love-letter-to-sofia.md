---
layout: post
title: My Love Letter to SOFIA
tags:
- Development
status: publish
type: post
published: true
Date: 2004-05-10
---
In November, I was evaluating frameworks to help me build web applications in Java.  My <a href="../2004-04-11-my-background">background</a> includes constructing several in <span class="caps">PHP</span> using Dreamweaver.  I had done a couple of "messy" projects using Servlets, <span class="caps">JSP</span> and Taglibs, but I wanted to get real experience with what Java, my "native" language, had to offer.  While I was looking for a job, I took the time to evaluate the web application frameworks that were available.  I already knew about Struts, and excitedly dug into the Manning [Struts in Action](https://www.manning.com/books/struts-in-action) book.</p>

I read the entire thing, and was kind of puzzled.  I didn't see anything in there that dealt with the problems I was familiar with, and the areas of flexibility that it offered didn't add as much value for me as I had expected.  Still, though, I knew Struts was famous, and was confident that I could at least use it.

What I wanted, in addition, was a "last mile" solution for doing my web design.  I knew that Dreamweaver didn't have the greatest level of support for <span class="caps">JSP</span> tags.  It was this search that led me to <span class="caps">SOFIA</span>.  I downloaded the platform, went through the tutorial and looked over the examples.  That was all it took for me to dispatch Struts from my toolkit and use <span class="caps">SOFIA</span> in its place.

Here's a list of the other bonuses that I got from <span class="caps">SOFIA</span> within the first two weeks.

#### "Live Page" view in Dreamweaver, via the translator servlet

This was exactly what I was looking for with my search in the first place.

#### Java-code free <span class="caps">JSP</span> pages

Java code on <span class="caps">JSP</span> pages is ugly, unrenderable by Dreamweaver, difficult to debug, nigh-impossible for web designers to work with, etc.

#### Swing-like coding of pages

I've since seen other frameworks that have similar <span class="caps">MVC</span> coding techniques, but I still like <span class="caps">SOFIA</span>'s the best.  I'd had exposure to Swing in the past, and this capability made coding <span class="caps">SOFIA</span> controllers a snap to get right into.  Suddenly, worrying about which submit button was pressed was a thing of the past.  You can have a submit button for each row in a DataStore and you're one event.getRow() call away from figuring out exactly what to do with what set of data.

#### Trivial in-IDE debugging

Set breakpoints in your controller code and watch your page execute just as a standard Java application would.  This one still makes me very happy.

#### Professional construction and power

The <span class="caps">SOFIA</span> team has been at this for quite some time.  You might find their philosophy regarding <span class="caps">SOFIA</span>'s open source status an interesting read.  I don't have to read a book to reap the benefits of the long, hard road that the <span class="caps">SOFIA</span> developers have travelled; they've left a framework behind instead.  (Not that I mind reading!  I love it.)  They provide solutions to many advanced problems, and some quite interesting features that I'm still learning about.

### Support and flexibility

<span class="caps">SOFIA</span> does not use any bean or <span class="caps">POJO</span> persistence strategy itself, opting for <span class="caps">SQL</span>.  I felt that Hibernate more closely fit my needs in terms of database access and use.  Even though <span class="caps">SOFIA</span> doesn't particularly have a use for it, there was a `BeanDataStore` ready for me to use and adapt.  In addition, the <span class="caps">SOFIA</span> team has been nothing but helpful in helping me through troubles, and the user community is a fairly active one.

I don't anticipate leaving <span class="caps">SOFIA</span> any time soon;  they've enabled me to focus on the problems my application faces, and not on data interface and plumbing.  I'm fortunate that I'm doing green field work, but if you're fortunate enough not to be tied in already, I couldn't recommend <span class="caps">SOFIA</span> more highly.
