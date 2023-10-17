---
layout: post
title: Where are the Rails infrastructure support firms?
tags:
- Tech
status: publish
type: post
published: true
meta:
  _edit_last: '3'
  image: ''
  quote-author: Unknown
  quote-url: http://
  quote-copy: Unknown
  audio: http://
  link-url: http://
  seo_follow: 'false'
  _clicky_goal: a:2:{s:2:"id";s:0:"";s:5:"value";s:0:"";}
---
<p><a href="http://blog.scoutapp.com/articles/2010/11/09/where-are-the-rails-infrastructure-support-firms#comment-95480732">Where are the Rails infrastructure support firms?</a>: "Five years ago, the typical Rails stack was just a couple of pieces: Apache/Mongrel, Rails, and MySQL. While Rails is remarkably similar to its original form even today, the stack around it is dramatically more diverse. We’re deploying to automated infrastructures, using NoSQL databases, messaging systems, queuing systems, and more. With the increased complexity of web applications, I’m surprised we’re not seeing companies dedicated to 24/7 infrastructure support: it doesn’t matter where your app is hosted, they manage it."</p>

<p>This is an area of great interest to me;  I am fascinated by the marketplace.  I share my skepticism about the form of the business described herein, but have heard of a company or two in the space.  The primary issue I see is drawn from my own experience.</p>

<p>I was the lead developer for an application that grew large on my watch.  My recollection of the message  coming from presentations in the Rails community at the time was "Learn to be fast when you need to, because you probably won't need to."  While this may be accurate since most projects are failures, it serves you poorly if you later learn that performance is important to you.  It deals with capacity (another critical concept, especially in Rails) not at all.  I wouldn't be surprised to see the two equated by the community at large.</p>

<p>So what are the results of this message?  Developers are writing applications that can get them into trouble-- "design by laptop" has claimed many a deliverable, just that I'm aware of personally.  They're not familiar with operations.  Their systems do not count on failure as an outcome.  The architecture is poor.  Many don't know that there is a solution.  Those that do scratch and claw to find one find that, unlike their development experience so far, tools and systems to increase capacity and performance require a great deal of knowledge to plan for their use.  It is a complicated field requiring great study, and some mind-bending.  This is the path I'm <strong>still</strong> walking down, months after leaving that lead developer job to <a href="http://itsbspoke.com">start my own consulting business</a>, and it's humbling and awe-inspiring all at once.</p>

<p>Part of the issue there is that it can be difficult to find help-- as the commenters to that post point out, engineers with this skillset are in-demand among the already in-demand Rails space.  Talks on the issue are still rare.  I wrote about <a href="http://jimvanfleet.com/chef.html">my love of Chef</a> recently, which includes some exhortations of responsibility on the part of developers, but-- let's get serious-- very few are listening to me right now.  That's OK, I'm working on it.</p>

<p>At the end of the day, these issues matter.  Knowing what to expect from your operating system, your VM's, and your architecture is crucial to acceptable response times and uptime when you start getting the traffic that will make your business a success.  Shouldn't our entire community be more interested in ensuring that our applications have an upside?  There is no silver bullet for this problem, not even hosting with <a href="http://engineyard.com/">Engine Yard</a> or <a href="http://heroku.com/">Heroku</a>.  Shouldn't we have it as our mission to ensure whoever owns <a href="http://canrailsscale.com/">this registration</a> lets it expire?</p>
