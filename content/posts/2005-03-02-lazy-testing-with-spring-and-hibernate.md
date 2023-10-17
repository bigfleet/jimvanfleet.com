---
layout: post
title: Lazy Testing with Spring and Hibernate
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I am now writing unit tests that use Hibernate&#8217;s lazy-initialized collections within Spring.  While some tests worked fine outside of the application server, some did not.  This post on the Spring forum <a title="Spring Framework :: View topic - Unit tests and LazyInitializationException" href="http://forum.springframework.org/viewtopic.php?t=76">about nit tests and Hibernate&#8217;s LazyInitializationException</a> was all I needed to get back on track.</p>
