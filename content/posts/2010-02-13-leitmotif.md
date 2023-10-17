---
layout: post
title: Leitmotif
tags:
- Tech
status: publish
type: post
published: true
Date: 2010-02-13
---
## A variation on a theme in modern software development.

A few weeks ago, I was wondering about how to keep my fledgling start-up from falling prey to unplanned maintenance or downtime.  Because of the nature of the site (managing design mockups), the element that most concerned me was in-Passenger handling of thumbnailing. We use [paperclip](http://github.com/thoughtbot/paperclip).  Paperclip relies on [ImageMagick](http://www.imagemagick.org/script/index.php), a notorious resource hog, [especially when it comes to RAM](http://magick.imagemagick.org/script/architecture.php#cache).  I didn't want to be able to let a single user hamstring our entire site for a thumbnail.

Fortunately, at exactly the same time, [Jesse Storimer](http://www.jstorimer.com/) created [delayed_paperclip](https://thoughtbot.com/blog/nearby-in-open-source#delayed_paperclip) to defer thumbnailing (or any other paperclip processing) using [delayed_job](http://github.com/tobi/delayed_job).  Very cool!  I started watching it.

I knew that I wanted A/B testing and metrics to play a big role in Mocksup and, right now, that means [Redis](https://redis.io/) and [Vanity](https://vanity.labnotes.org/).  After a very successful trial run with them both, I knew that Redis would play a part in the application's future.  Having read [a history of Resque](http://github.com/blog/542-introducing-resque) from my friend [defunkt](http://twitter.com/defunkt), that bit of software was on my list to try out anyway.  Resque was easy to get up and running.  Why not try to port delayed_paperclip to Resque?  After some  hacking, it was working fine in my application.  Even cooler!  So [I blabbed on Twitter about it](http://twitter.com/bigfleet/status/8733966363) to see if anybody else liked the idea.  Some people did, including Chris.  But I couldn't release with broken tests, that's not me!

I got the tests passing, and let Chris know.  [He tweeted about it](https://twitter.com/verbal/status/8819098298) and suddenly my little hack is trending on GitHub.  If Mom could see me now!  Well, I mean, she can see me, but if I could explain it to her without her being bored!  Yeah, that's it!

<p>Seeing my "name in lights" was definitely gratifying, but I started to wonder what the future would be for this little piece of code.  The author is using Delayed::Job; he _works_ at [Shopify](http://www.shopify.com/) for god's sakes.  He may not be interested in this functionality.  And what of the integration with paperclip over time; am I really going to be able to keep this supported?  There's a lot of sophisticated Ruby work happening in that plugin, to balance Rails, Paperclip, and Delayed::Job.  So I sent a pull request and figured "Let's just see".

[Jesse](http://twitter.com/jstorimer) could not have been cooler, and integrated my changes immediately!  He even added on an additional bit of coolness that made the plugin even better for the end user.  After one last little change pointing that additional nicety out to the plugin's potential users, I was done!  I updated my fork and pointers to it with the information that the functionality I added was merged into the project.

Let's recap the winners:

* [Thoughtbot](http://thoughtbot.com/), for getting an even more robust and featureful plugin allowing delayed post-processing
* Jesse Storimer, who gets a plugin with more exposure.
* Chris and resque, for getting a new [plugin for resque](https://github.com/resque/resque/wiki/Plugins)
* The potential users of delayed_paperclip, for being able to choose which work queue system fits them better.
* Me, for scratching an itch and getting involved with all these great people and projects.

To me, much of the beauty of contributing to open source is being a member of this kind of community.  I enjoyed it so much, I had to write a little bit about it.
