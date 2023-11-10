---
layout: post
title: A Ruby Writeup
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-05-29
---
Original poster writes:


> Anyone is using Ruby on Rail application for production? Is it hype? Is it really new way to increase productivity? Humm I am very skeptical to believe that. Let's see the development effort wil be 10x faster by telling the team members to use the new programming language, new framework, etc. Does ruby has multi-thread capabilities? concurrency? what kind of data persistent technology are there for Ruby? Does it work with hibernate? How you would like to built ruby applications with transaction support?

My Java stack of choice includes Spring, Hibernate, and WebWork.  I am not an expert with those technologies, but I have now completed two fairly major projects with them, and I like them quite a lot.  I've been programming in Java since college, and I like it quite a lot as well.

I've put together three smaller applications with Ruby on Rails, am beginning to build one large one.  Here's my take, and I'd be glad to give a bullet presentation at a meeting if there was interest in learning more.

I love Ruby and Rails.  It's a great fit for a lot of the work I do, since I do a lot of green-field work.  I have my doubts if Rails is ready for the enterprise in general, but it could definitely be right for *some* enterprises.  For example, I'm using Rails to write the project that I just started my first business to manage.

I'll run down your questions in turn.

### Is it hype?

No.  There is a lot of developer buy-in.  The community around Rails is unbelievably helpful and knowledgeable.  The framework itself is a joy to work with, and reminds me and many others of why they started programming in the first place.  It is making headway in the "Java thought leader" space, as well.  As Erik mentioned, the leader knows how to get the project exposure.  Rails is here to stay.

### Does it increase productivity?

Yes.  How much depends on your familiarity with Java, how well you have your Java <span class="caps">IDE</span> shortcuts set up, etc.  But if you are hand-typing your Hibernate mapping files or Spring configuration, it's a good bet you that you will be more productive in Rails.  

Maybe if you're as smart as Justin Gehtland (which I am not) you'll be more productive in four days.  For me, it's taken a few months to get comfortable with the language and the framework.  You can't just hop right over and expect to still be an expert in a language you've never used before.  

If your project is large enough for a team, your team will have to buy in.  This is one of the considerations to make.  You might be better off giving a [free electron](https://randsinrepose.com/archives/free-electron/) a gigantic project and watching them go.  Your programmers should evaluate Rails individually and you should value their input.  But it is worth their time to make an evaluation.  If they don't feel comfortable with Ruby, any potential productivity gains could disappear.

### Is Ruby multi-threaded with concurrency?

Yes, but to be fair, this is not as good as it could be.  Rails cannot make use of multiple processors at this time, as I understand.  This is due to limitations in Ruby, not in the framework.

### What kind of data persistence is there for Ruby?

While Erik's answer is correct for Ruby (the language), if you plan to use Rails (the framework) with anything but ActiveRecord (a helper framework for Rails), you will need someone who really knows their stuff to write you some code.  Switching out ActiveRecord is not a trivial activity when writing a Rails application.  I've heard those "in the know" speculate that it would be "a hundred lines of code" but take that with a grain of salt.

### "Does it work with Hibernate?"

Not directly.  You could, however, access a Rails database with Hibernate *very* easily.  Hibernate is simply more flexible than ActiveRecord in what it can map.  ActiveRecord relies on certain naming and structure conventions to make it easier and quicker to get an application working.
For this reason, Rails may not be a good choice for legacy applications, or applications where the schema has been handed down from on high.
ActiveRecord and Hibernate are both <span class="caps">ORM</span> tools, but I don't think they're very similar.  In terms of feel, they're nothing alike.  (Also, I have not used transactions in Rails because I haven't needed them.)

Maybe I should add another question here which is 

### Bonus Question: "Can this get me fired?"

The answer here is maybe.  If you just jump into it and spend all your work time toying with Ruby, then your claims of "This will make me more productive!" might fall on deaf ears.  

But get used to the language, browse the good [Ruby](http://poignantguide.net/ruby/) books on-line, and do a few demos in your off hours.  Or, if you've got a Friday that you can bluff your way through, give it a day.  You might catch the bug.

I ended up throwing together a bug tracker that was more fully-featured than the one it had taken the resident programmer a few months to put together in a couple of days.  That could get you the opposite of fired, if handled appropriately.   The gains are real, but I don't believe it's for everyone in every situation.

Of course, three days later, I ditched what I had written for trac--  Ruby doesn't necessarily improve your decision making skills.


### My conclusion:

Rails is cutting edge, but not bleeding.  I anticipate in the next few months, Rails is going to go 1.0.  There have been parties launching production sites, and they are doing a superb job of getting the bugs out.

If you have a dedicated server for your application, the leading web-server stack (Apache and fastcgi) should have no problem <span class="caps">RIGHT NOW</span>.  If you're willing to experiment with a new web-server as well, lighttpd and fastcgi are reported to do even better.  You may have to babysit lighttpd a little.

### Update:

The original poster contacted me asking to clarify that he did *not* ask if it would get him fired.  I thought that I pointed out that I had added that question in the post, but I'll reiterate here for clarity's sake.
