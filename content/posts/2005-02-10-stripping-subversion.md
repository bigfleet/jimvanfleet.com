---
layout: post
title: Stripping Subversion
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>or&#8230;  recursively deleting directories of the same name.</p>


	<p>The only tool that I&#8217;m comfortable with that could do something like this is Ant.  But I thought, hey, you know it&#8217;s possible in Unix.  It took me about five minutes in Cygwin with <kbd>man find</kbd> to come up with this one.</p>


<pre>
Jim Van Fleet@jimvfxp /cygdrive/c/dev/eclipse-3.1M4/workspace
$ find . -name .svn -exec rm -rf '{}' \;
</pre>

	<p>That did the trick!</p>
