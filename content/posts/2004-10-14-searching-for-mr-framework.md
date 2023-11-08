---
layout: post
title: Searching For Mr. Framework
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-10-14
---

## SOFIA

I've used SOFIA in the past, and I've been quite satisfied with it.  I am strongly committed to working with a [POJO](http://www.martinfowler.com/bliki/POJO.html) domain layer, however, and that doesn't fit with the core Salmon team's development methodology.  <span class="caps">SOFIA</span> has very many nice features, but making my domain objects play nicely with framework constructs is getting harder and harder, and there are plenty of other tasks that I need to spend time on.  Also, the controllers are very tightly coupled to <span class="caps">SOFIA</span>, almost by necessity.  There's simply no way that an application could be meaningfully ported away from <span class="caps">SOFIA</span> with any sort of ease.  I'm learning there are other options.

## Tapestry

Tapestry already got dismissed as too clever, basically.

## Struts

Almost nobody who uses Struts likes it, so why would I?

(ed. note: [WebWork 2 became Struts](https://struts.apache.org/birdseye.html) about 8 months after this post.)

## WebWork 2

The current leader of the pack.  WebWork2 is very simple and quite small, yet contains many of the features needed by all web application frameworks.  I've gotten familiar with [Spring](http://www.springframework.com), and some of the usage patterns with WebWork look *very* very similar to Spring's <span class="caps">IOC</span> functionality.  I'm still in the beginning stages of working up a small test application, but I've already gotten farther more quickly with WebWork than with <span class="caps">SOFIA</span>, and that's having never worked with WebWork before.  It's very easy to test and it's trivial to generate precisely the <span class="caps">HTML</span> that you want.  That will likely be an important requirement for our product.

## Spring MVC

I've got {{<amzn asin=https://a.co/d/7cEetM5 title="The Red Spring Book">}} and reading through that didn't give me the best feeling towards Spring <span class="caps">MVC</span>.  As a matter of fact, I read a post on the WebWork2 mailing list, that a useful summary, and I haven't used WebWork for more than a couple of weeks.  Thanks to Matt Raible, I at least have [an example](https://objectcomputing.com/resources/publications/sett/october-2004-spring-mvc) check out.

## Ruby, the dark horse

Thanks to a Ruby Forum thread, I was able to get RubyGems up and running, and Rails came shortly thereafter.  Rails has its own forum and is mind-bogglingly simple to start using.  The real barrier is my familiarity with Ruby syntax, which leads to pointers to the first Pragmatic Programmers'[book](https://pragprog.com/titles/ruby5/programming-ruby-3-2-5th-edition/) and [why's poignant guide to Ruby](https://poignant.guide/book/chapter-1.html), which is the single funniest technical document I've ever read.

That's it!  I'll keep you informed.
