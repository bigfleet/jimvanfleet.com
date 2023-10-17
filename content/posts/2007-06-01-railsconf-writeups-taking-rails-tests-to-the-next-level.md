---
layout: post
title: ! 'RailsConf Writeups: Taking Rails Tests to the Next Level'
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I originally found Jay Fields&#8217; blog from a reference in the back of Rails For Java Developers from Stu Halloway.  Reading his blog was really interesting and dealt with a lot of unfamiliar topics.  As a result, I was eager to hear him speak.</p>


	<p>Jay had one slide for his entire presentation, but a lot of ideas.  Visiting <a href="http://blog.jayfields.com/">Jay&#8217;s blog</a> particularly the posts that he has tagged <a href="http://blog.jayfields.com/search/label/Testing%20Refactorings">Testing Refactorings</a> would be an excellent start.</p>


	<p>Jay&#8217;s session started one of the ongoing themes of the weekend for me, which was rethinking my approach to testing.  Just because tests deal with models does <strong>not</strong> make them unit tests.  Just because tests deal with controllers does <strong>not</strong> make them functional tests.  That determination depends on the context, and what precisely it is that you are testing.  To that end, during the presentation it was revealed that Rails plans at a later date to begin structuring the test hierarchy to include <code>model/</code> and <code>controller/</code> directories under <code>test/</code> instead of <code>unit/</code> and <code>functional/</code>.</p>


	<p>Less than ten minutes into the presentation, Jay mentioned that one of his development goals was test each test case should fail in isolation.  In other words, if you make a change to your code-base and run the tests, there should be no cascading failures.  I found this to be an outlandish idea at first, but when I started to think about it, it made a lot more sense in certain ways.  My first question for him was if that led to an explosion in the number of his test cases, which he answered in the affirmative.  It makes sense to me, though, that a fuller explication of every bit of behavior that you expect will lead to healthier code-bases in the long term.</p>


	<p>One reason that Jay is able to have goals like these is that he is comfortable with Ruby metaprogramming and the various mock libraries for Ruby.  As in Martin Fowler&#8217;s <a href="http://www.martinfowler.com/articles/mocksArentStubs.html">Mocks Aren&#8217;t Stubs</a> article, I have been a classicist for a long time.  Like Mr. Fowler, I find the mockist dependence on implementation troubling.  Unlike Mr. Fowler, I have not worked with mocks nearly enough to have formed my own opinion of their benefits.  It&#8217;s an exciting area of inquiry for me.</p>


	<p>My summary is that Jay is a very thought provoking thinker who is very serious about his testing.  I really appreciated the conversational tone of his talk, and I wouldn&#8217;t hesitate to ask him a question if I come up with one while looking into the area.</p>
