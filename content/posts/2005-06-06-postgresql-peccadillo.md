---
layout: post
title: postgreSQL Peccadillo
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Given the task of creating a &#8220;staging area&#8221; where some users can play around with the application without worrying about the data available, I  ran into the following problem when attempting to create the database schema.</p>

<pre>
ERROR: permission denied for relation cpt_code
</pre>

<p>I thought that was pretty odd, since I had just created the database as that user.  Investigating afterwards showed that just by issuing the <keyboard>createdb</keyboard> command that I had copied all the elements in my original database!</p>

<p>Issuing the <keyboard>createdb</keyboard> command with the specific option to use <keyboard>template0</keyboard> was the key to getting me up and running.  You&#8217;d think that creating a new database would default to creating something completely empty, but I guess not!</p>

<p>Now back to dealing with the <strong><strong>(#$(%</strong>#*$</strong> Tomcat classloader and log4j.</p>
