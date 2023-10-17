---
layout: post
title: Screaming Headless Servers
tags: []
status: publish
type: post
published: true
meta: {}
---
<h2>Problem</h2>
<p>
If you&#8217;re working with a server-side application, like I am, that imports a <pre>javax.swing</pre> package, you might get strange errors, such as the one described <a href="https://sourceforge.net/forum/message.php?msg_id=2545939">here</a>.  <pre>javax.swing</pre> packages expect to find an <a href="http://www.xfree86.org/"><span class="caps">X11</span> server</a> running on the machine.  In my case, it wants to access the graphical subsystem because <a href="http://www.jfree.org/">JFreeReport</a> wants to use a <pre>TableModel</pre> as a kind of spreadsheet.

<h2>Solution</h2>

<p>append <pre>java.awt.headless=true</pre> to your <pre>JAVA_OPTS&lt;pre&gt; in catalina.sh.  Mine ended up looking like this.&lt;/p&gt;

&lt;pre&gt;
JAVA_OPTS=-Dsalmon.props.path=/home/opgi/bin/jakarta-tomcat-4.1.30/salmon/properties
JAVA_OPTS = "$JAVA_OPTS -Djava.awt.headless=true"
&lt;/pre&gt;
