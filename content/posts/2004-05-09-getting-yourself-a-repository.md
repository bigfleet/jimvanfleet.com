---
layout: post
title: Getting yourself a repository.
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>First, you&#8217;ll need to visit the excellent <a href="http://www.cvsnt.org/wiki/">Wiki for <span class="caps">CVSNT</span></a>, an open-source <span class="caps">CVS</span> server with great integration with Windows.  Their <a href="http://www.cvsnt.org/wiki/InstallationTips">Installation instructions</a> are similarly great;  you&#8217;ll be able to walk through them almost exactly.</p>


	<p>Instead of configuring your repository to use a default prefix, however, you&#8217;ll want to configure each repository to point to a separate directory without using a prefix.  Special elements of the Eclipse <span class="caps">CVS</span> capabilities require that setting to work correctly.</p>


	<p>Then, you can go <a href="http://www.3plus4software.de/eclipse/cvs_en.html">here</a> to finish up setting up your repository within Eclipse.</p>


	<p>Note that I did try <a href="http://subversion.tigris.org/">Subversion</a> and <a href="http://subclipse.tigris.org/">Subclipse</a>, but it didn&#8217;t work The First Time.  I really do love the work that <a href="http://www.collab.net/">collabNet</a> and <a href="http://www.tigris.org">Tigris</a> are doing, but documentation is a weakness there.  <a href="http://scarab.tigris.org/">Scarab</a> <strong>did</strong> work for me the first time, and I&#8217;ve been using it very happily since, but if it doesn&#8217;t Just Work with those products, it seems very tough to get them on track.</p>
