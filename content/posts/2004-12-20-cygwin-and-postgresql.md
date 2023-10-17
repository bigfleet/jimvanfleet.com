---
layout: post
title: Cygwin and PostgreSQL
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Getting postgreSQL up and running under Cygwin was not that difficult for me, although it does require a couple of Google searches.</p>

<p>First, the basic information is supplied <a href="http://www.postgresql.org/docs/faqs/text/FAQ_CYGWIN">here</a> by the folks at postgreSQL.</p>

<p>When I followed these instructions, however, I kept getting a failure message.  I should have copied it down, but since I didn&#8217;t expect the next step to work, I didn&#8217;t.  I&#8217;ll edit this soon to include the error message.</p>

<p>The second step came from a Rick Hightower blog post.  Simply use</p>
<pre>
&gt; export CYGWIN=server
</pre>
<p> before you issue any of the commands listed in step 1 and you should be golden.</p>
