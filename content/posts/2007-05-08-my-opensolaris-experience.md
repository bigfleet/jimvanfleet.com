---
layout: post
title: My OpenSolaris Experience
tags:
- Tech
status: publish
type: post
published: true
Date: 2007-05-08
---

Thanks to the work of the Joyent team, through their <a href="http://youngobungo.bingodisk.com/bingo/public/pspipegrep/Site/Podcast/Podcast.html">podcast</a> and working with top-level <a href="https://www.tritondatacenter.com/blog/solaris-dtrace-and-rails">Rails sites on Solaris with DTrace</a>, I am sold on the OpenSolaris operating system.  I am pretty rusty with my Solaris admin skills, since most of the ones that I used the most often at Rice were written by senior IT engineers.  We really didn't do a lot of software installation and maintenance.  I don't even know how much has changed for Solaris in the past 2 or 3 versions.  I started out with the intent to just build a Ruby deployment stack, but the journey ended up further down the road!  I'll walk you through what I did.


## Download the Parallels instance from Sun.

Sun has recently made available their Solaris Express for Parallels instance, and that's where my journey started.  Sun, get an easier to use website.

## Hit up Blastwave

### A word on package management

My experience with Ubuntu and `apt-get` has changed my expectations in terms of package management.  The only time that apt-get has not given me exactly what I have expected has been when I'm trying some experiment that later turns out to be completely boneheaded.  Ubuntu, particularly, has a very large space of packages.  <a href="http://wwww.blastwave.org/">Blastwave</a> is the OpenSolaris equivalent, although <a href="http://www.gnusolaris.org/gswiki">Nexenta</a> attempts to bring the whole of apt-get to OpenSolaris, boasting currently of more than 12,000 packages available.  For your own purposes, you may wish to evaluate Nexenta, but with their most recent release being <a href="http://www.gnusolaris.org/gswiki/Download">Nexenta Alpha 6</a>, I was more interested in something that I could feel comfortable using in production right away.  That's right, calling your software alpha <strong>does</strong> scare me off.


### Now on with our regularly scheduled program

An ugly fact:  I am completely useless with `vi`.  So for me, Blastwave is the next step.  <a href="http://www.blastwave.org/howto.html">Blastwave's <span class="caps">HOWTO</span></a> was no problem to follow.  Don't miss the last line of Step 7, which you will definitely want to do as you install more software.


Next step:


`
pkg-get -i nano
`

## Install MySQL

Sun has a BigAdmin article that's a great <a href="http://www.sun.com/bigadmin/features/articles/samp_setup.html">walkthrough for setting up MySQL on OpenSolaris</a> using <a href="http://www.blastwave.org/">Blastwave</a>.

I completed through step 5I (Yikes!), the one about installing the MySQL <span class="caps">SMF</span> service.  It ends with this:

```
svcs -a | grep mysql
online 15:12:43 svc:/network/cswmysql5:default
```

Perhaps I'll write a post specifically on <span class="caps">SMF</span> on some point, but suffice to say, that I really really liked it.  It beats the Linux equivalent (/etc/init.d/) without breaking a sweat.


Also note that it's probably time to revisit your path, as when I followed the Blastwave instructions followed by these, I ended up with the wrong version of `mysql` coming first.


## Get familiar with your Apache

Be sure that you work with the version of Apache httpd that you intend to.  /etc/apache and /etc/apache2 are both present.  This is a good time to familiarize yourself with [SMF cheatsheet](https://www.oracle.com/docs/tech/smf-admin-cheat-sheet.pdf).


## Install Ruby and Subversion

Prepare yourself.


`
pkg-get -i ruby
`

* ...coffee break&#8230; *

`
pkg-get -i subversion
`

That gets you Ruby 1.8.5 and Subversion 1.4.3.  Not bad!

## Download and install RubyGems and needed gems</h2>


To get started with RubyGems, there's nothing different from the regular installation process.

After that, try this command:


`
gem install rails mysql mongrel_cluster -y
`

It might work right off.


## Enjoy your Ruby stack!

The particulars of how you might want to set up a mongrel_cluster <span class="caps">SMF</span> may vary, but this should be enough to get you in the ballpark.

## Postscript

My experiments with OpenSolaris were so successful that I took an installation on a physical machine at work and prepared it to be our extranet hub.  The best part is that all of our most critical corporate data can get packaged up and sent off to Amazon's S3 service by a Ruby script that I whipped up in conjunction.  That beats the pants off what we had before, and now we've got a solid backup strategy on a solid system.  Very nice!
