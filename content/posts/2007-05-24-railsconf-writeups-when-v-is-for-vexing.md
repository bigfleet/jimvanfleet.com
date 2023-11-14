---
layout: post
title: ! 'RailsConf Writeups: When V is for Vexing'
tags:
- RailsConf
- Tech
status: publish
type: post
published: true
Date: 2007-05-24
---
Put on by Bruce Williams and an uncredited [Marcel Molina, Jr.](http://marcelmolina.com/), this session proved to be one of the highlights of the conference for me personally.  My experience up to this point has led to a lot of time spent with <span class="caps">HTML</span> and <span class="caps">CSS</span> education-- thus I spend a lot of time working with those two technologies.  As a result, I've seen a lot of view code, and produce a lot of the code smells that they covered in the talk.


I want to specifically give voice on my own forum to echo one of their own observations.  So much focus has been given in the Rails community toward getting the right balance of responsibility between the model and the controller.  Between them, the model and the data just make data available to the controller.  That's a *lot* of work to do in the view, to create the sort of dynamic interfaces that end users expect us in this day and age.  <span class="caps">HTML</span>, JavaScript, and <span class="caps">CSS</span> are complicated enough that there are many professionals who operate only on that level.  At least to this point, the view has not gotten the same sort of attention that the other levels have gotten from the developer community, even though it's very important and difficult to get view code written cleanly and correctly.  The two speakers then gave a dynamic walkthrough of several problems that manifest in view code, along with examples of "smelly" and "fixed" code.  In the session, they went into greater depth for some of the examples.


One particular technique that received quite a bit of attention, and which I plan on following up on as soon as I can is the block helper.  It was used twice for the smells that I put out quite frequently, as well as getting some discussion as an alternative for partials.  Seeing how I use partials in my own code, this is a very big deal.  Anticipate more posts from me on this topic in the future.
