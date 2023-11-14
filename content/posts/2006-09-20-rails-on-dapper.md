---
layout: post
title: Rails on Dapper
tags:
- Tech
status: publish
type: post
published: true
Date: 2006-09-20
---
I have been using [Rails](http://www.rubyonrails.org/) longer than I have been using [Ubuntu](http://www.ubuntu.org/), and only one of them has been longer than a year, so this is a de facto Newbie's guide, but hopefully you'll find it useful.

After you're done (and it should take you no more than about 10 minutes), you'll be able to get a Rails app using [MySQL](http://www.mysql.com/) created and running on your local machine using Mongrel.  [PostgreSQL](http://www.postgresql.org/) fans, feel free to use the common parts to form your own guide.

## The Prerequisites

### Repository Selection

If you have already enabled the security and universe repositories, you can skip this step.  I am a big copy-and-paste guy, but this step works better with point-and-click.

Under *System* on your Gnome panel, under the *Administration* menu, select *Synaptic Package Manager*.

In Synaptic, select the *Repositories* item under the *Settings* menu.  Enable the 'universe' repositories for both Dapper LTS and Dapper LTS Updates.  (I have enabled multiverse as well, I believe that's optional.)

Also, you'll need to enable the Security Updates repository, as it's not enabled by default.  I enable all the security update repositories, but again, enabling the multiverse should be optional.

Quit the application, since we can do the rest using the terminal.

If you use KDE, you're going to have to figure this out on your own.  If you favor the command line for this part as well, you'll be editing your /etc/apt/sources.list file as described at [the Ubuntu guide](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

### Update Your Package Database

Ensure that your system is up-to-date by issuing the following commands.  Enabling the security repository should mean that you have quite a lot to upgrade on top of a base installation.

```
sudo apt-get update
sudo apt-get upgrade
```

## The Main Course

### Preparation for Gem Installation

Ruby and C have some close ties, as languages go.  Some Ruby gems that we'll be installing need to do some compilation and installation, so we'll prepare ourselves with the basics.

Issue the following command in your terminal.

```
sudo apt-get install gcc build-essential automake subversion
```

### Installing Apache 2, MySQL 5, and PHP 4

If you need PHP5, this isn't the guide for you.  The only reason that I'm installing PHP at all is so I have access to [phpMyAdmin](http://www.phpmyadmin.net/).

```
sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql libmysqlclient15-dev
sudo a2enmod proxy
```

#### Why mod_proxy?

I have a [Confluence](http://www.atlassian.com/confluence) installation on my home machine that I use in conjunction with my [DynDNS](http://www.dyndns.org/) account.  Getting that traffic to flow through your router is outside the scope of this guide, but I need to proxy my incoming HTTP traffic.  Hence, `mod_proxy` is in the guide!


### Installing Ruby

The gems that you'll install later require the Ruby development package.

```
sudo apt-get install ruby irb ri rdoc ruby1.8-dev
```

### Installing Ruby Gems

You'll appreciate not having to depend on Ubuntu and upstream supplying you with the latest version of RubyGems, especially when it plays so nicely with the system you've set up so far.

```
wget http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz
tar zxvf rubygems-0.9.0.tgz
cd rubygems-0.9.0
sudo ruby setup.rb
```

### Installing the Gems

```
sudo gem install rails mysql mongrel --include-dependencies
```

Rails and Mongrel have dependencies.  mysql and mongrel have different versions you'll have to choose from.  If this is a development box, why not choose the newest of each?  If it's a production box, I make no claims that any particular version of a any gem is production ready. Make sure to pick the "ruby" versions, since you're on Dapper.

## Done!

Check out something like [Mephisto](http://mephistoblog.com/), [Typo](http://typosphere.org/), or issue your standard `rails` command along with a

```
mongrel_rails start
```

and that should do the trick.


## Author's Note on Lighttpd and Mongrel

Many users have used lighttpd as a replacement for Apache because of the latter's support of FastCGI, uh&#8230; leaves something to be desired.  I've had to learn how to use it as part of the long-time recommended stack over at TextDrive, where they know their Rails.  I still use it there, but, to me, Mongrel is far superior, especially for a development environment.  It's like Webrick, only it appears to be more than suitable for production use.  Add the ease of installation factor, and it's a no-brainer for me to endorse.  As always, YMMV.
