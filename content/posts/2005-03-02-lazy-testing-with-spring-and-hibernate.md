---
layout: post
title: Lazy Testing with Spring and Hibernate
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-03-02
---
I am now writing unit tests that use Hibernate's lazy-initialized collections within Spring.  While some tests worked fine outside of the application server, some did not.  This post on the Spring forum about unit tests and Hibernate's `LazyInitializationException` was all I needed to get back on track.
