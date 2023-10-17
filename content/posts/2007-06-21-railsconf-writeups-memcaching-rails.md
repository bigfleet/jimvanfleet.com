---
layout: post
title: ! 'RailsConf Writeups: Memcaching Rails'
tags: 
- Tech
- RailsConf
status: publish
type: post
published: true
Date: 2007-06-21
---
This talk was a bit of a stretch for me, having never written an application that was even close to needing Memcached.  I had a great seat, though, and really enjoyed meeting Chris at the "Joyent Happy Hour".  I also had just sat through a talk where all the concepts were familiar.  What was the worst that could happen?


I ended up really enjoying the presentation for multiple reasons.  You can access his presentation here and be sure to look around for the download option.  And get the version with notes!!!

{{<slideshare id="mjiRZKMpUse854">}}

I loved the introduction which definitely made me feel like I might have been sitting there in that GameSpot booth with the same challenges.  (Although odds are good that I would have been watching the braniacs do the real work.)  He also didn't set himself up as an expert, which I normally respond well to, especially if the speaker is obviously lying because he is in the middle of presenting at RailsConf.  I also really appreciated that he shared a mistake he made that brought down GameSpot.  Learning from others' mistakes is the best.


The introduction to memcached couldn't have been better, from my perspective.  I knew almost nothing about it, and learning very quickly about the basics was nice.  Everyone knows what a hash is like, and the presentation built appropriately from there.


It takes balls to put a <span class="caps">YAGNI</span> slide 25 slides into your presentation-- *about your presentation itself!*


The cache_fu plugin appears to be one of my favorite sort of plugins, the sort that does a lot of assembly and simplifying of other work.  The code was never that hard to grasp and his presentation is still available as a starting place.


This presentation also sounded another note about using mocks and stubs.  Gotta look into getting more hands-on experience there.  Check out slide 70 for goodness sakes, although that's not a result of mocha or stubba.


The biggest take home for me is *it's OK to make mistakes*.  It happens all the time.  The problem is not being able to react because you don't know what you're doing.  That's why you can listen to the front-runners and make sure that you do it as right as you can the first time out.
