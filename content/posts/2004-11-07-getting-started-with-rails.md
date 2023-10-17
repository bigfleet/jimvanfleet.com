---
layout: post
title: Getting Started With Rails
tags: []
status: publish
type: post
published: true
meta: {}
---
<h3>Rails Tips</h3>

<ul>
<li>After installing Ruby, Gems, and Rails, make sure that the script/new_* elements point to the correct Ruby interpreter</li>

<li>Make sure that you use script/new_model with a capital letter model name.  I got errors on Windows when I issued the command using a lower case entity name.</li>

<li>Just because you&#8217;re using Ruby doesn&#8217;t mean that you automatically import everything under the sun.  You still have to &#8220;import&#8221; the classes that you want to use, but the compiler isn&#8217;t around to warn you that you haven&#8217;t included the correct &#8220;require&#8221; line.</li>

<li>Don&#8217;t name any database field &#8216;index&#8217; unless you want to be messing with Ruby defaults.  When a framework is built around guessing defaults intelligently, why get in the way?  My column name decisions are arbitrary.</li>

<li>Make sure to get your RDoc found and loaded in your browser.  Rails is going to come in as a Ruby gem, and under Cygwin, that&#8217;ll mean it&#8217;s in something similar to C:/cygwin/lib/ruby/gems/1.8/doc/  You wouldn&#8217;t think about working in Java without your JavaDoc handy, would you?</li>

</ul>

<p>That got me to get some very simple models and views up.  Here&#8217;s where the lack of source-code actually hurts Ruby, though.  Am I going to be poring through source code I only partly understand to figure out how to name my database columns to get the has_many and belongs_to relationships working?  With Hibernate, you can count on having to make your mapping file define exactly what&#8217;s going on.  It&#8217;s great that Ruby doesn&#8217;t need that help, but <strong>you, as the developer</strong> need to understand what&#8217;s going on to begin with.</p>

<p>So, I need to learn by example.  Be prepared to hack the provided Rails demos extensively.  I was unable to get any of the examples to do anything useful, with one exception: RubyBB.</p>

<h3>RubyBB tips</h3>

<ul>
<li><p>If you were unable to get a vhost installation, or didn&#8217;t use rubybb as the vhost name, you&#8217;ll need to edit the standard.rhtml file to change the basic link.  You&#8217;ll also need to change the stylesheet, javascript, and image links to perhaps go ../ a directory.</p></li>

<li><p>Three database edits are necessary to run the program as written, these aren&#8217;t too tough to figure out from the error messages though.</p></li>

<li><p>Install RedCloth and builder gems.  You&#8217;ll need RedCloth for the topic page and builder for the <span class="caps">RSS</span> functionality.</p></li>

</ul>

<p>But then I was up and running.  Sure, it took me about a day to get there, but that&#8217;s why I&#8217;m leaving my breadcrumbs</p>

<h3>RubyBB lessons</h3>

<ul>
<li><p>before_save is an example of an ActiveRecord object hook to step in and do something during the object lifecycle.  There&#8217;s no need to use <span class="caps">XML</span> and implement special interceptors, etc.  Just implement the method, and you&#8217;ve got it.</p></li>
<li><p>validate defines validation for the Ruby object.  Author has a few examples.   Include <span class="inlineCode">&lt;%= error_message_on &#8220;author&#8221;, &#8220;name&#8221; %&gt;</span> in the appropriate .html view, and you&#8217;ve got your error reporting in place.  Check your ActiveRecord::Errors RDoc for more information.</p></li>
</ul>

<h3>Ruby/RubyBB questions</h3>

<ul>
<li><p class="inlineCode">def self.find_by_name(name)</p> <p>What does the self. prefix do?</p></li>
</ul>
