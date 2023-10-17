---
layout: post
title: What in the Hyades?
tags: []
status: publish
type: post
published: true
meta: {}
---
<h3>Step 1:</h3>


	<p>There are some prerequisites for using Hyades, namelu the Eclipse Modeling Framework (EMF) and the <span class="caps">XML</span> Schema Infoset Model (XSD).  Those are both best installed using <strong>Help &gt; Software Updates &gt; Find And Install &gt; Find new features</strong>  As of this writing, (Eclipse 3.01) Eclipse lists one 2.01 plugin that includes both <span class="caps">XSD</span> and <span class="caps">EMF</span>.  Download that and then get started.</p>


	<h3>Step 2:</h3>


	<p>Get the Hyades files from the <a href="http://dev.eclipse.org/viewcvs/indextools.cgi/~checkout~/hyades-home/downloads/download.html">Download</a> page.  As of this writing, Hyades is on release 3.2.0.  It does appear that the project is about to get folded into another Eclipse initiative, but who knows how long these things will take?  Here&#8217;s what we have right now.</p>


<pre>
Hyades Runtime       hyades.runtime_3.2.0_20041221_1637.zip
Hyades Examples     hyades.examples_3.2.0_20041221_1637.zip
Hyades Component Test     hyades.test_3.2.0_20041221_1637.zip
Hyades Data Collection Engine for Windows (NT, 2000, XP) Runtime
</pre>

	<h3>Step 3:</h3>


	<p>Unzip all the Hyades runtime, examples, and component test archives to the base Eclipse install directory.  Remember <strong><span class="caps">NOT</span></strong> to extract them to the <em>plugins</em> directory, as the archives include elements destined for the <em>plugins</em> and <em>features</em> directories of Eclipse.</p>


	<h4>Step 4:</h4>


	<p>Fortunately for us all, the description of installing the Data Collection Agent is easy to follow and needs no amendment.  Go ahead and take care of this prerequisite first by following the <a href="http://dev.eclipse.org/viewcvs/indextools.cgi/~checkout~/org.eclipse.hyades.datacollection/collection/packaging_md/win_ia32/getting_started.html">installation instructions</a>. </p></p>


	<h3>Step 5:</h3>


	<p>My advice is to not go around to the different examples to figure out what&#8217;s going on.  Just start trying to get Tomcat up and running.  I use the <a href="http://www.sysdeo.com/eclipse/tomcatPlugin.html">Sysdeo Tomcat plugin</a>, which gives some very useful pointers on how to start up Tomcat within Eclipse.  If you are not currently running Tomcat within Eclipse, for god&#8217;s sake, quit this tutorial right now and install the Tomcat plugin.  It&#8217;s straightforward, but feel comfortable working with it before you take the next step.</p>


	<h3>Step 5a:</h3>


	<p>Get your web application up and running comfortably within it.  That portion may be somewhat less straightforward, but I believe in you!  One item to note, you should include as &#8220;external JARs&#8221; in your libraries the entries of <strong><span class="caps">TOMCAT</span>_HOME/common/lib</strong>  These <strong>will</strong> will be part of your running classpath.  You may even find this useful in getting your web application running, especially if your application is using libraries itself.</p>


	<h3>Step 6:</h3>


	<p>Start a Tomcat session using the <strong>Start Tomcat</strong> command.  Switch to the <strong>Debug</strong> perspective.  Right click on the running Tomcat application and select the <strong>Properties</strong> option.  Copy and paste this into your <a href="http://www.notetab.com;">favorite text editor</a> we&#8217;ll use it to help us configure the profiler.</p>


	<p><strong><span class="caps">UPDATE</span></strong>:  You can also use the <em>Create A Launch Configuration</em> button inside of the <strong>Windows &gt; Preferences &gt; Tomcat</strong> menu.</p>


	<h3>Step 7:</h3>


	<p>Use the skills you learned from installing the Tomcat plugin to make the <strong>Profiling and Logging</strong> perspective show up, as well as the <strong>Profile</strong> button on the toolbar.  From the <strong>Profile</strong> button, select that option.  You should see a screen much like the picture below.  Click on <strong>Java Application &gt; New</strong> and you&#8217;ll have an opportunity to begin defining the Java project.</p>


	<p><img src="http://devblog.jimvanfleet.com/imgs/hyades/step7.png" alt="" /></p>


	<p>For the <strong>Project</strong> section, choose the project that you set up in Step 5.</p>


	<p>For the Main class, you want <em>org.apache.catalina.startup.Bootstrap</em> for the Tomcat 5 varieties.  If something else is in your clipboard entry from Step 6, use that instead, but <a href="http://en.wikipedia.org/wiki/YMMV"><span class="caps">YMMV</span></a>.</p>


	<h3>Step 8:</h3>


	<p>Refer to the picture below.</p>


	<p><img src="http://devblog.jimvanfleet.com/imgs/hyades/step8.png" alt="" /></p>


	<p>For the program arguments, select everything that comes after the main class you used in Step 7.</p>


	<p>For the VM arguments, use all the elements you passed in using the <strong>-D</strong> technique, this is everything after the Java invocation but before the classpath declaration.  Of course, your values will differ based on where you have installed Tomcat, but it should look somewhat similar to the picture.</p>


	<h3>Step 9:</h3>


	<p>Refer to the picture below.</p>


	<p><img src="http://devblog.jimvanfleet.com/imgs/hyades/step9.png" alt="" /></p>


	<p>Begin with the defaults, which include the Java standard libraries as your boot classpath and your own web application&#8217;s libraries (as defined by your project) as the user classpath.  Note that not all of these steps may be necessary if you followed the updated instructions above.</p>


	<p>Add your <strong><span class="caps">TOMCAT</span>_HOME/bin/bootstrap.jar</strong> as the next entry after the defaults.</p>


	<p>Add the libraries in <strong><span class="caps">TOMCAT</span>_HOME/server/lib/</strong> as the next entries.</p>


	<p>Add the <strong><span class="caps">JAVA</span>_HOME/lib/tools.jar</strong> from your <span class="caps">JDK</span> so that Tomcat can compile your Java files.  (Note that this may not be necessary with Tomcat 5.5)</p>


	<p>If you use Apache&#8217;s log4j project, you&#8217;ll likely end up with that jar in <strong><span class="caps">TOMCAT</span>_HOME/server/lib/</strong>.  As a result, you&#8217;ll have to provide some directory for the classpath that contains a <em>log4j.properties</em> file so that the log4j system can initialize itself appropriately.</p>


	<h3>Step 10:</h3>


	<p>Start it up!  (Make sure that you&#8217;re running the data collection service mentioned in Step 4.)</p>


	<p>If you want to be gathering other data, you&#8217;ll want to visit the <strong>Profiling</strong> tab on the configuration menu that we&#8217;ve been working with.  Create a new profiling set and you&#8217;ll be in shape.</p>


	<h1>Summary:</h1>


	<p>I&#8217;m absolutely thrilled to have a profiler added to my toolkit, much less one that will be easily accessible from within my <span class="caps">IDE</span>.  Also, I strongly suspect that this product will be vastly improving in quality along with the rest of Eclipse as time passes.</p>
