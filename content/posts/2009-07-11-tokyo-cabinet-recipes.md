---
layout: post
title: Tokyo Cabinet Recipes
tags:
- Tech
status: publish
type: post
published: true
meta: {}
---
Trying to blog on an Ilya Grigorik talk is usually an exercise in linking to the resources he makes available.  In this case, <a href="http://www.slideshare.net/igrigorik/lean-mean-tokyo-cabinet-recipes-with-lua">his slides</a> and <a href="http://twitter.com/igrigorik">his Twitter account</a> for question purposes.

In this case, I'll try to post a brief summary of the technology so you can get an idea of whether or not it's for you.<!--more-->Tokyo Cabinet is a set of database tools that seem to offer a high-performance version of memcached and schema-less databases like CouchDB under one roof.  It's written by a Japanese programmer who works on Japanese equivalent of Facebook, and that site has famously crazy technical specs and requirements.

Tokyo Cabinet has engines that provide different feature sets.  By selecting a different engine, you get different sets of restrictions and different exposed functionality.  You can get a Ruby hash with one of the engines, you can get a schema-less database with another.

There is no ActiveRecord-like index, but the schema-less version is still queriable.  There is a method to define indexes to speed up queries over large datasets.

Tokyo Cabinet also offers extensibility via a sandboxed Lua engine.  You can load arbitrary scripts into the database to extend the functionality.  This is the bulk of what Ilya goes into in his talk, because he is a badass.  For me, it's so far over my head, I need a ladder and a catcher's mitt to get it.

One of his examples is that you can complete a port of Redis functionality in less than 100 lines of code.  Its performance profile is not as good as Redis, but it's a good example of how you can extend Tokyo Cabinet to expand your abilities with the software.

It seems like a very interesting datastore with a bright future.
