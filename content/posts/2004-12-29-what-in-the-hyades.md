---
layout: post
title: What in the Hyades?
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-12-29
---
### Step 1:

There are some prerequisites for using Hyades, namelu the Eclipse Modeling Framework (EMF) and the <span class="caps">XML</span> Schema Infoset Model (XSD).  Those are both best installed using <strong>Help &gt; Software Updates &gt; Find And Install &gt; Find new features</strong>  As of this writing, (Eclipse 3.01) Eclipse lists one 2.01 plugin that includes both <span class="caps">XSD</span> and <span class="caps">EMF</span>.  Download that and then get started.

### Step 2:

Get the Hyades files from the <a href="http://dev.eclipse.org/viewcvs/indextools.cgi/~checkout~/hyades-home/downloads/download.html">Download</a> page.  As of this writing, Hyades is on release 3.2.0.  It does appear that the project is about to get folded into another Eclipse initiative, but who knows how long these things will take?  Here's what we have right now.

<pre>
Hyades Runtime       hyades.runtime_3.2.0_20041221_1637.zip
Hyades Examples     hyades.examples_3.2.0_20041221_1637.zip
Hyades Component Test     hyades.test_3.2.0_20041221_1637.zip
Hyades Data Collection Engine for Windows (NT, 2000, XP) Runtime
</pre>

### Step 3:

Unzip all the Hyades runtime, examples, and component test archives to the base Eclipse install directory.  Remember <strong><span class="caps">NOT</span></strong> to extract them to the <em>plugins</em> directory, as the archives include elements destined for the <em>plugins</em> and <em>features</em> directories of Eclipse.

### Step 4:

Fortunately for us all, the description of installing the Data Collection Agent is easy to follow and needs no amendment.  Go ahead and take care of this prerequisite first by following the <a href="http://dev.eclipse.org/viewcvs/indextools.cgi/~checkout~/org.eclipse.hyades.datacollection/collection/packaging_md/win_ia32/getting_started.html">installation instructions</a>. 

### Step 5:

My advice is to not go around to the different examples to figure out what's going on.  Just start trying to get Tomcat up and running.  I use the <a href="http://www.sysdeo.com/eclipse/tomcatPlugin.html">Sysdeo Tomcat plugin</a>, which gives some very useful pointers on how to start up Tomcat within Eclipse.  If you are not currently running Tomcat within Eclipse, for god's sake, quit this tutorial right now and install the Tomcat plugin.  It's straightforward, but feel comfortable working with it before you take the next step.

#### Step 5a:

Get your web application up and running comfortably within it.  That portion may be somewhat less straightforward, but I believe in you!  One item to note, you should include as "external JARs" in your libraries the entries of <strong><span class="caps">TOMCAT</span>_HOME/common/lib</strong>  These <strong>will</strong> will be part of your running classpath.  You may even find this useful in getting your web application running, especially if your application is using libraries itself.

### Step 6:

Start a Tomcat session using the <strong>Start Tomcat</strong> command.  Switch to the <strong>Debug</strong> perspective.  Right click on the running Tomcat application and select the <strong>Properties</strong> option.  Copy and paste this into your <a href="http://www.notetab.com;">favorite text editor</a> we'll use it to help us configure the profiler.

<strong><span class="caps">UPDATE</span></strong>:  You can also use the <em>Create A Launch Configuration</em> button inside of the <strong>Windows &gt; Preferences &gt; Tomcat</strong> menu.

### Step 7:

Use the skills you learned from installing the Tomcat plugin to make the <strong>Profiling and Logging</strong> perspective show up, as well as the <strong>Profile</strong> button on the toolbar.  From the <strong>Profile</strong> button, select that option.  You should see a screen much like the picture below.  Click on <strong>Java Application &gt; New</strong> and you'll have an opportunity to begin defining the Java project.

For the <strong>Project</strong> section, choose the project that you set up in Step 5.

For the Main class, you want <em>org.apache.catalina.startup.Bootstrap</em> for the Tomcat 5 varieties.  If something else is in your clipboard entry from Step 6, use that instead, but <a href="http://en.wikipedia.org/wiki/YMMV"><span class="caps">YMMV</span></a>.

### Step 8:

For the program arguments, select everything that comes after the main class you used in Step 7.

For the VM arguments, use all the elements you passed in using the <strong>-D</strong> technique, this is everything after the Java invocation but before the classpath declaration.  Of course, your values will differ based on where you have installed Tomcat, but it should look somewhat similar to the picture.

### Step 9:

Begin with the defaults, which include the Java standard libraries as your boot classpath and your own web application's libraries (as defined by your project) as the user classpath.  Note that not all of these steps may be necessary if you followed the updated instructions above.

Add your <strong><span class="caps">TOMCAT</span>_HOME/bin/bootstrap.jar</strong> as the next entry after the defaults.

Add the libraries in <strong><span class="caps">TOMCAT</span>_HOME/server/lib/</strong> as the next entries.

Add the <strong><span class="caps">JAVA</span>_HOME/lib/tools.jar</strong> from your <span class="caps">JDK</span> so that Tomcat can compile your Java files.  (Note that this may not be necessary with Tomcat 5.5)

If you use Apache's log4j project, you'll likely end up with that jar in <strong><span class="caps">TOMCAT</span>_HOME/server/lib/</strong>.  As a result, you'll have to provide some directory for the classpath that contains a <em>log4j.properties</em> file so that the log4j system can initialize itself appropriately.

### Step 10:

Start it up!  (Make sure that you're running the data collection service mentioned in Step 4.)

If you want to be gathering other data, you'll want to visit the <strong>Profiling</strong> tab on the configuration menu that we've been working with.  Create a new profiling set and you'll be in shape.

# Summary:

I'm absolutely thrilled to have a profiler added to my toolkit, much less one that will be easily accessible from within my <span class="caps">IDE</span>.  Also, I strongly suspect that this product will be vastly improving in quality along with the rest of Eclipse as time passes.
