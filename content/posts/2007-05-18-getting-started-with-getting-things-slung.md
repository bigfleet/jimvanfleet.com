---
layout: post
title: Getting Started with Getting Things Slung
tags:
- Tech
status: publish
type: post
published: true
Date: 2007-05-18
---

Insipired by a chance to win one year of a large Joyent accelerator, I started Getting Things Slung.  I am working on a Java application that is designed to sync contacts from MS Outlook, so I'm somewhat interested in the off-line/on-line client space.  Also, the prize is pretty enticing, and the screenshot sure was pretty!  So that's all it took for me to decide to spend the plane ride over working on getting an entry ready.


I'm doing a Mac <span class="caps">OS X</span> version, and I really have no interest in the Windows side of things.

## Briefing

The pair of Joyent web pages have generally good information.  I'm intending this blog post to supplement that material.  Also, even though at one point I was using it all the time, there's now nothing I hate worse than Trac markup syntax, so I'm not going to use it.

I also recommend reading this through once before you go through it and try to follow it.

## Basecamp (not that one)

We're trying to simulate a server-side and client-side sync process.  There's no reason that we can't set that up on the same computer.  Ultimately, in addition, we'll want the trunk directory in the Slingshot.app file to be the *same* as the server-side code.


### Set up Subversion

I set up a Subversion repository on my own machine just for these purposes.  I checked in the most recent release of [Tracks](https://www.rousette.org.uk/archives/tracks-102/) into my repository, then checked it out to a working directory in my typical Rails workspace, and also checked it in from within the .app file.  (You can cd into them using the terminal-- go ahead!)


### Getting TextMate open


You'll end up with <span class="caps">TWO</span> TextMate windows open.  One is for the client-side, and that will have extra directories in it.  The other is for the server-side.


### Getting Terminals in position


You'll need terminal windows open to have a window to start `mongrel_rails` (for the server side) and for running `svn up` inside the Slingshot VM.


## Head Above Water


The first place to go after getting yourself in position is to work on getting the client side in position to do the first downward sync.  The wiki docs can walk you through that.  For me, the process involved editing the `start.sh`, `sync_up.sh`, and `sync_down.sh`, while making sure that Tracks itself was running and passing tests.  Let's just say that some parts of the code are a little brittle.


As an example, the operative line from the `sync_up.sh` file looked like this for me:



```
ruby ../bin/rake joyent_slingshot:sync_up SYNC_CONTROLLER=http://localhost:4000/sync/up
```

## Monday Night <span class="caps">RAW</span> on your adopted application.


I had to write migrations and fix not-exactly-bugs in Tracks to get it ready to run in the Slingshot environment.  This will happen to you if you didn't write the code, so get ready to 'stand on the shoulders of giants' as Adam Keys might say.


You'll also have to follow the instructions for the Slingshot plugin which, by virtue of being installed on the server-side, is <span class="caps">ALSO</span> installed on the client side, because you set them to be to same with Subversion.  <strong><span class="caps">RIGHT</span>?</strong>


The existing examples include-- let's call it a non-granular approach to preparing the set of information to be synchronized.  This is OK for now, go ahead and do that.  We'll make things a little better before it's all over.

## Check <span class="caps">XML</span> from the server</h2>


I had a problem with having the *first* request to my server-side sync action completing successfully.  After catching (by accident) the Joyent Scotts out on the balcony, Scott Burton told me that he had *the same problem* and it had to do with a different version of Rails running in `vendor/rails` than I had mentioned in `config/environment.rb` so watch for that.  That brought my first work session to a halt.


Don't stop until you're pulling <span class="caps">XML</span> down.  You're more than half way done at this point.


You know, this is enough for one post.
