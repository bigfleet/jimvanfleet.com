---
layout: post
title: ! 'Write-Up:  Introduction to Tapestry'
tags:
- Development
status: publish
type: post
published: true
Date: 2004-04-15
---

## Pure <span class="caps">HTML</span> capabilities

You can mark up a page in pure, unadorned <span class="caps">HTML</span>.  The files that your application will server are <span class="caps">HTML</span> files.  This allows a level of separation between the developers and the web design team.  I'm wishing I could pull that off!  My pages just don't look good.

It also allows for rapid prototyping.  You can make everything look the way it's supposed to look in <span class="caps">HTML</span>, then have the developers come in behind.  Tapestry will automatically replace certain <span class="caps">HTML</span> tags once the developers touch them up a bit.

## Architecture

Tapestry ends up being a single-servlet [front controller](https://www.martinfowler.com/eaaCatalog/frontController.html) onto the rest of your application.  It uses extensive <span class="caps">URL</span> rewriting, and external file resources to tie everything together.

## Teamwork

My first impression is that Tapestry would integrate extremely well with [Hibernate](http://www.hibernate.org/).  The "distance" between a web request and your domain model is considerably shorter than with Servlets, Struts, or possibly even <span class="caps">SOFIA</span>.  Also, the lifecycle of Hibernate Sessions has a natural management within a certain Tapestry construct.

If a small team wanted to put together a quick, easily defined application for themselves, they might be looking at a week for the whole thing.  And if the team had a graphic designer, it would even look good.

## Getting Down To Business

There is a lot of mental overhead when using Tapestry.  A developer would probably need someone either very smart or quite experienced to use it reliably.  Although it does have line-precise error reporting (quite nice), good developer documentation, etc. it will still be very hard for an average developer to use it effectively without some practice.  I do feel that this is an advantage for [SOFIA](http://www.sf.net/projects/salmon).

## Power

In terms of functionality, Tapestry can take the roof right off for you.  There are some extremely advanced features which we only briefly touched on.  For those developers who are already familiar with complementary technologies like <a href="https://velocity.apache.org/">Velocity</a>, Tapestry could wrap your problem up and put a bow on it.

## Extensibility

One of the reasons I'm bullish on its future of Tapestry is its component based nature.  I saw an excellent calendar, something they called a "pallete," which is exactly what Yahoo! Fantasy Sports uses for pre-ranking fantasy drafts.

## Conclusion

I do forsee some, but not nearly all, shops currently using <a href="https://struts.apache.org/">Struts</a> migrating to Tapestry. Erik certainly seems to have evangelical conviction for it.  As a result, the "libraries" for Tapestry will continue to grow and provide developers more useful, user-friendly tools to develop with.  It will be harder and harder to ignore as time passes.  But, who knows what tomorrow brings?