---
layout: post
title: Getting Started
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Preparation is key in this effort.  The first step is to go to the Windows Device Manager and copy down all the devices that Windows registers on your system.  If you make a mistake, you&#8217;ll be very glad that you had this in dead-tree format.  Here&#8217;s my version</p>


<pre>
ATI Radeon X300 SE 128MB HyperMemory
Philips DVD+-RW DVD8701
Intel 8280 1GB Serial ATA Storage Controller - 27C0
Intel 82801GB Ultra ATA Storage Controllers - 27DF
Intel 537EP V9x DF PCI Modem
Intel PRO/100 VE Network Connection
Intel Pentium 4 3Ghz
</pre>

	<p>The second step is becoming familiar with the contents of your hard drive.  On my computer, Dell shipped three primary partitions on the machine.  One is about 55k and is involved with the Dell System Recover utility.  I understand from some of the other postings I&#8217;ve read that Dell has replaced the familiar &#8220;System Restore CD&#8221; with this, <em>uh</em>, feature?  The second is the primary Windows partition.  The last is something I haven&#8217;t really taken care to fully identify.  You&#8217;ll see some hints here shortly, but let&#8217;s not get ahead of ourselves.</p>


	<p>The most important detail is that your  partition(s) fill the hard drive.  There&#8217;s no space to install another operating system.  Sure, you can buy something like Partition Magic to do the resizing for you.  I&#8217;ve used it in the past with success.  I&#8217;m also cost sensitive though, so I wanted to see if I could do this for free.  Turns out, it was not a problem.  Err, well, it did take awhile, but not for the reasons you might think.</p>


	<h3> Resizing your XP Partition with <span class="caps">RIP</span> and ntfsresize</h3>


	<p>Fortunately for my wallet, there is an open-source tool to resize <span class="caps">NTFS</span> partitions: ntfsresize.  The <a href="http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html">Ntfsresize <span class="caps">FAQ</span></a> lists a host of potential distributions with which you can use ntfsresize to do the partition resizing.  My most successful experiments to date have been with FreeBSD.  However, since FreeBSD chooses to ignore the problem of resizing one&#8217;s partitions, my <span class="caps">OSOS</span> journey begins with Linux.</p>


	<p>Kubuntu, Ubuntu, and Knoppix all lead to <a href="http://blog.jimvanfleet.com/articles/2005/11/15/the-journey-begins"><span class="caps">TMDER</span></a> in various ways.  (Also interesting to note was that not a single one of the Linux flavors I&#8217;ve tried thus far worked with a <span class="caps">DVI</span> connection to the monitor; I had to break out the analog cable.)</p>


	<p>The technique that did work was to use <a href="http://www.tux.org/pub/people/kent-robotti/looplinux/rip/"><span class="caps">RIP</span></a>, which seems like a really useful tool regardless of your circumstances.  I am glad that I found it.  Odds of it ending up on a flash drive with me at all times is high.</p>


	<p>The <a href="http://www.tux.org/pub/people/kent-robotti/looplinux/rip/RIP.readme"><span class="caps">RIP</span> readme</a> has an excellent walkthrough of the steps necessary to perform the resizing.</p>


	<p>The highlights in brief are the following:</p>


	<h4>Seeing what you&#8217;ve got</h4>


	<p>Use the <code>fdisk</code> command to determine the size and nature of your partitions.  For me, the output looked like this.</p>


<pre>
# fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19412 cylinders
Units = cylinders of 16025 * 512 = 822528 bytes

   Device Boot     Start       End       Blocks    Id   System
/dev/sda1              1         7        56196    de   Dell Utility
/dev/sda2 *            8     18845    151316235     7   HPFS/NTFS
/dev/sda3          18847     19452      4867695    db   CP/M / CTOS / ...
</pre>

	<h4>Measure&#8230;</h4>


	<p>ntfsresize has a very nice manual on the <span class="caps">RIP CD</span> which you can actually gunzip and read.  Feel free to either supplement the <span class="caps">README</span>, or to refer solely to the one provided on disc.  Either would tell me to issue the command to test resizing the partition to approximately 120GB.</p>


<pre>
ntfsresize -n -s 120000M /dev/sda2
</pre>

	<h4>... then cut.</h4>


	<p>Having ntfsresize do the actual work is not too much different.  After issuing this command, you&#8217;ll be prompted to pass the point of no return, as it were.</p>


<pre>
ntfsresize -s 120000M /dev/sda2
</pre>

	<h4>fdisk revisited.</h4>


	<p>We now have to use <code>fdisk</code> to adjust the partition table in earnest.  This involves (<em>brace yourself</em>) deleting the primary partition on your machine.  For those going straight to running only the <strong>nix/</strong><span class="caps">BSD</span> operating system, that&#8217;s not much of a concern.  For my purposes, though, that&#8217;s a bit scary.</p>


	<p>At any rate, you shouldn&#8217;t be scared, because the change is only in memory until you write it to the partition table.  The process is essentially:</p>


	<ol>
	<li>Delete the primary partition</li>
		<li>Recreate the primary partition with the same attributes, only smaller</li>
		<li>Create a partition on which the new OS can reside.</li>
	</ol>


	<h4>Rebooting</h4>


	<p>Reboot into Windows by removing the CD and calling (<em>wait for it</em>) <code>reboot</code></p>


	<p>Windows will sense your philandering;  &#8220;Your disk is dirty&#8221; it will report.  That&#8217;s right, Windows!  I&#8217;m going around behind your back!  You tried to lock me down, but I won&#8217;t be beaten that easily.</p>


	<p>Beginning the install process comes next.</p>
