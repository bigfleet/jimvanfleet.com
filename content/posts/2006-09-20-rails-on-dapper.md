---
layout: post
title: Rails on Dapper
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I have been using <a href="http://www.rubyonrails.org/">Rails</a> longer than I have been using <a href="http://www.ubuntu.org/">Ubuntu</a>, and only one of them has been longer than a year, so this is a de facto Newbie&#8217;s guide, but hopefully you&#8217;ll find it useful.</p>


	<p>After you&#8217;re done (and it should take you no more than about 10 minutes), you&#8217;ll be able to get a Rails app using <a href="http://www.mysql.com/">MySQL</a> created and running on your local machine using <a href="http://mongrel.rubyforge.org/index.html">Mongrel</a>.  <a href="http://www.postgresql.org/">PostgreSQL</a> fans, feel free to use the common parts to form your own guide.</p>


	<h2>The Prerequisites</h2>


	<h3>Repository Selection</h3>


	<p>If you have already enabled the security and universe repositories, you can skip this step.  I am a big copy-and-paste guy, but this step works better with point-and-click.</p>


	<p>Under <strong>System</strong> on your Gnome panel, under the <strong>Administration</strong> menu, select <strong>Synaptic Package Manager</strong>.</p>


	<p>In Synaptic, select the <strong>Repositories</strong> item under the <strong>Settings</strong> menu.  Enable the &#8216;universe&#8217; repositories for both Dapper <span class="caps">LTS</span> and Dapper <span class="caps">LTS</span> Updates.  (I have enabled multiverse as well, I believe that&#8217;s optional.)</p>


	<p>Also, you&#8217;ll need to enable the Security Updates repository, as it&#8217;s not enabled by default.  I enable all the security update repositories, but again, enabling the multiverse should be optional.</p>


	<p>Quit the application, since we can do the rest using the terminal.</p>


	<p>If you use <span class="caps">KDE</span>, you&#8217;re going to have to figure this out on your own.  If you favor the command line for this part as well, you&#8217;ll be editing your /etc/apt/sources.list file as described at <a href="http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories">the Ubuntu guide</a></p>


	<h3>Update Your Package Database</h3>


Ensure that your system is up-to-date by issuing the following commands.  Enabling the security repository should mean that you have quite a lot to upgrade on top of a base installation.
<pre><code>
sudo apt-get update
sudo apt-get upgrade
</code></pre>

	<h2>The Main Course</h2>


	<h3>Preparation for Gem Installation</h3>


	<p>Ruby and C have some close ties, as languages go.  Some Ruby gems that we&#8217;ll be installing need to do some compilation and installation, so we&#8217;ll prepare ourselves with the basics.</p>


Issue the following command in your terminal.
<pre><code>
sudo apt-get install gcc build-essential automake subversion
</code></pre>

	<h3>Installing Apache 2, MySQL 5, and <span class="caps">PHP 4</span></h3>


If you need <span class="caps">PHP5</span>, this isn&#8217;t the guide for you.  The only reason that I&#8217;m installing <span class="caps">PHP</span> at all is so I have access to <a href="http://www.phpmyadmin.net/">phpMyAdmin</a>.
<pre><code>
sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql libmysqlclient15-dev
sudo a2enmod proxy
</code></pre>

	<h4>Why mod_proxy?</h4>


	<p>I have a <a href="http://www.atlassian.com/confluence">Confluence</a> installation on my home machine that I use in conjunction with my <a href="http://www.dyndns.org/">DynDNS</a> account.  Getting that traffic to flow through your router is outside the scope of this guide, but I need to proxy my incoming <span class="caps">HTTP</span> traffic.  Hence, mod_proxy is in the guide!</p>


	<h3>Installing Ruby</h3>


The gems that you&#8217;ll install later require the Ruby development package.
<pre><code>
sudo apt-get install ruby irb ri rdoc ruby1.8-dev
</code></pre>

	<h3>Installing Ruby Gems</h3>


	<p>You&#8217;ll appreciate not having to depend on Ubuntu and upstream supplying you with the latest version of RubyGems, especially when it plays so nicely with the system you&#8217;ve set up so far.</p>


<pre><code>
wget http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz
tar zxvf rubygems-0.9.0.tgz
cd rubygems-0.9.0
sudo ruby setup.rb
</code></pre>

	<h3>Installing the Gems</h3>


<pre><code>
sudo gem install rails mysql mongrel --include-dependencies
</code></pre>

	<p>Rails and Mongrel have dependencies.  mysql and mongrel have different versions you&#8217;ll have to choose from.  If this is a development box, why not choose the newest of each?  If it&#8217;s a production box, I make no claims that any particular version of a any gem is production ready. Make sure to pick the &#8220;ruby&#8221; versions, since you&#8217;re on Dapper.</p>


	<h2>Done!</h2>


Check out something like <a href="http://mephistoblog.com/">Mephisto</a>, <a href="http://typosphere.org/">Typo</a>, or issue your standard rails command along with a
<pre><code>
mongrel_rails start
</code></pre>

	<p>and that should do the trick.</p>


	<h2>Author&#8217;s Note on Lighttpd and Mongrel</h2>


	<p>Many users have used lighttpd as a replacement for Apache because of the latter&#8217;s support of FastCGI, uh&#8230; leaves something to be desired.  I&#8217;ve had to learn how to use it as part of the long-time recommended stack over a <a href="http://www.textdrive.com/">TextDrive</a>, where they know their Rails.  I still use it there, but, to me, Mongrel is far superior, especially for a development environment.  It&#8217;s like Webrick, only it appears to be more than suitable for production use.  Add the ease of installation factor, and it&#8217;s a no-brainer for me to endorse.  As always, <span class="caps">YMMV</span>.</p>
