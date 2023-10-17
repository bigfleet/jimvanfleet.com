---
layout: post
title: ! 'What''s Now In Rails: Libraries'
tags:
- Tech
status: publish
type: post
published: true
Date: 2008-11-24
---
> What Gems/Jimmies are you finding indispensable these days?

@peter_braswell

## Dr. Nic's Textmate Footnotes


	Famous Railsist "Dr. Nic" has a great [footnotes plugin](http://github.com/drnic/rails-footnotes/tree/master) which you can get a taste for from the <span class="caps">README</span> on that page.  It's a must install if you choose TextMate as your editor.


## Named scopes

Your Rails developer badge will shortly be revoked if you do not learn and use named scopes liberally.  The way that they can be named, composed, and reused in multiple contexts can result in some extremely powerful and expressive code, that remains readable and even has some excellent performance characteristics.

Learn more at [RailsCasts](http://railscasts.com/episodes/108-named-scope) 


## will_paginate

Out of the box Rails pagination is a thing of the past, I think.  [will_paginate](http://github.com/mislav/will_paginate/tree/master) is as much of a drop in as it gets, and it's flexible in all the right ways.  It's also kept very much up to date and remains in active development.


## rSpec and cucumber


	While I've decided that my overall thoughts on testing are probably going to end up being a talk, I can provide my favorites here. [rSpec](http://rspec.info/) provides a nicer syntax than test/unit for my tastes.  Further, the capabilities that come with the stories functionality provided by [cucumber](https://cucumber.io/) (detailed by Peepcode) have been a revelation on my primary project.


# fixture_replacement


	I personally have come to dislike fixtures strongly.  There are definitely techniques that can be used to reduce their downsides, like [dataset](http://github.com/aiwilliams/dataset/tree/master) (previously known as scenarios), but I favor leaving them behind altogether.  Once you've made *that* decision, you have options still, like [factory-girl](https://thoughtbot.com/blog/factory_bot) (plenty of good alternatives mentioned at that link, as well).  dataset even mentions that it can play along with other alternatives

	These are the only tips and techniques that I'd bring onto each project.  For anything else, I'd be checking out the diverse Rails ecosystem out there!  It's getting more pleasant by the week.
