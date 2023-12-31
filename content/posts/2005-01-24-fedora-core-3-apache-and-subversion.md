---
layout: post
title: Fedora Core 3, Apache, and Subversion
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-01-24
---

After trying out a local repository using Windows, I became sold on using Subversion and TortoiseSVN during the upcoming development effort.  This means that it was time to get the repository up and running on a server flavor much closer to the production environment.</p>

I have a Fedora Core 3 box accessible to me through VMWare, which is one of the neatest inventions I've ever seen.    To get the install completed, I roughly followed these instructions for installing Subversion on <span class="caps">FC2</span>.

The key observation is that you must create the repository as the root user.  I had been creating the repository as a user in the wheel group, which is not enough.  On a default installation, also don't forget to view the Subversion <span class="caps">FAQ</span></a> to find a command that you must issue if you have SELinux enabled on your machine.
