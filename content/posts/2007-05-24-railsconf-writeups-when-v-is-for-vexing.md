---
layout: post
title: ! 'RailsConf Writeups: When V is for Vexing'
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Put on by <a href="http://codefluency.com/">Bruce Williams</a> and an uncredited <a href="http://vernix.org/marcel/">Marcel Molina, Jr.</a>, this session proved to be one of the highlights of the conference for me personally.  My experience up to this point has led to a lot of time spent with <span class="caps">HTML</span> and <span class="caps">CSS</span> education&#8212;thus I spend a lot of time working with those two technologies.  As a result, I&#8217;ve seen a lot of view code, and produce a lot of the code smells that they covered in the talk.</p>


	<p>I want to specifically give voice on my own forum to echo one of their own observations.  So much focus has been given in the Rails community toward getting the right balance of responsibility between the model and the controller.  Between them, the model and the data just make data available to the controller.  That&#8217;s a <strong>lot</strong> of work to do in the view, to create the sort of dynamic interfaces that end users expect us in this day and age.  <span class="caps">HTML</span>, JavaScript, and <span class="caps">CSS</span> are complicated enough that there are many professionals who operate only on that level.  At least to this point, the view has not gotten the same sort of attention that the other levels have gotten from the developer community, even though it&#8217;s very important and difficult to get view code written cleanly and correctly.  The two speakers then gave a dynamic walkthrough of several problems that manifest in view code, along with examples of &#8220;smelly&#8221; and &#8220;fixed&#8221; code.  In the session, they went into greater depth for some of the examples.</p>


	<p>If you deal with Rails views at all, I recommend as strongly as possible that you <a href="http://www.web2expo.com/presentations/rails2007/VisForVexing.pdf">download the slides</a> and read through their presentation.  You won&#8217;t have a chance to ask them questions directly, but I&#8217;m quite sure that the two of them would be happy to engage with a reader.</p>


	<p>One particular technique that received quite a bit of attention, and which I plan on following up on as soon as I can is the block helper.  It was used twice for the smells that I put out quite frequently, as well as getting some discussion as an alternative for partials.  Seeing how I use partials in my own code, this is a very big deal.  Anticipate more posts from me on this topic in the future.</p>
