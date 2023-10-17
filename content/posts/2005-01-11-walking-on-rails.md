---
layout: post
title: Walking On Rails
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>To anyone experimenting with <a href="http://www.rubyonrails.com/">Ruby on Rails</a>, I highly recommend starting with a domain model and a debugging session.  Knowing how to create and associate elements in your model lends a lot of focus to how you&#8217;d like to write your views.</p>

<p>To do this, there&#8217;s only one real deviation from the video <a href="http://www.leetsoft.com/rails/lesson4.html">here.</a>  You now have a script command ready to do the task for you.</p>
<pre>
ruby script/console development
</pre>
<p>or its cousins will let you instantiate objects, assign their properties, and save them.  It will also let you know about syntax errors, missing columns, or misnamed columns in the most direct way possible.  After a walk through your model in irb, you should feel confident about constructing the view in a similar way.</p>
<p>I think <a href="http://curry.elitists.net/~scott/ARAssociations.png">this representation</a> of the association directions can help.  Note, though, that <span class="inlinedCode">belongs_to</span> seems to be simply a bidirectionality tool;  It&#8217;s not required for <span class="inlinedCode">has_one</span> to work.
