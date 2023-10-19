---
layout: post
title: ! 'RailsConf Writeups: Taking Rails Tests to the Next Level'
tags:
- Tech
- RailsConf
status: publish
type: post
published: true
Date: 2007-06-01
---
I originally found Jay Fields' blog from a reference in the back of Rails For Java Developers from Stu Halloway.  Reading his blog was really interesting and dealt with a lot of unfamiliar topics.  As a result, I was eager to hear him speak.


Jay had one slide for his entire presentation, but a lot of ideas.  Visiting [Jay's blog](http://blog.jayfields.com/) particularly the posts that he has tagged [Testing Refactorings](http://blog.jayfields.com/search/label/Testing%20Refactorings) would be an excellent start.


Jay's session started one of the ongoing themes of the weekend for me, which was rethinking my approach to testing.  Just because tests deal with models does *not* make them unit tests.  Just because tests deal with controllers does *not* make them functional tests.  That determination depends on the context, and what precisely it is that you are testing.  To that end, during the presentation it was revealed that Rails plans at a later date to begin structuring the test hierarchy to include `model/` and `controller/` directories under `test/` instead of `unit/` and `functional/`.


Less than ten minutes into the presentation, Jay mentioned that one of his development goals was test each test case should fail in isolation.  In other words, if you make a change to your code-base and run the tests, there should be no cascading failures.  I found this to be an outlandish idea at first, but when I started to think about it, it made a lot more sense in certain ways.  My first question for him was if that led to an explosion in the number of his test cases, which he answered in the affirmative.  It makes sense to me, though, that a fuller explication of every bit of behavior that you expect will lead to healthier code-bases in the long term.


One reason that Jay is able to have goals like these is that he is comfortable with Ruby metaprogramming and the various mock libraries for Ruby.  As in Martin Fowler's [Mocks Aren't Stubs](http://www.martinfowler.com/articles/mocksArentStubs.html) article, I have been a classicist for a long time.  Like Mr. Fowler, I find the mockist dependence on implementation troubling.  Unlike Mr. Fowler, I have not worked with mocks nearly enough to have formed my own opinion of their benefits.  It's an exciting area of inquiry for me.


My summary is that Jay is a very thought provoking thinker who is very serious about his testing.  I really appreciated the conversational tone of his talk, and I wouldn't hesitate to ask him a question if I come up with one while looking into the area.
