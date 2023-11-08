---
layout: post
title: Getting Started With Rails
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-11-07
---
### Rails Tips

* After installing Ruby, Gems, and Rails, make sure that the `script/new_*` elements point to the correct Ruby interpreter

* Make sure that you use `script/new_model` with a capital letter model name.  I got errors on Windows when I issued the command using a lower case entity name.

* Just because you're using Ruby doesn't mean that you automatically import everything under the sun.  You still have to "import" the classes that you want to use, but the compiler isn't around to warn you that you haven't included the correct "require" line.

* Don't name any database field `index` unless you want to be messing with Ruby defaults.  When a framework is built around guessing defaults intelligently, why get in the way?  My column name decisions are arbitrary.

* Make sure to get your RDoc found and loaded in your browser.  Rails is going to come in as a Ruby gem, and under Cygwin, that'll mean it's in something similar to `C:/cygwin/lib/ruby/gems/1.8/doc/`  You wouldn't think about working in Java without your JavaDoc handy, would you?

That got me to get some very simple models and views up.  Here's where the lack of source-code actually hurts Ruby, though.  Am I going to be poring through source code I only partly understand to figure out how to name my database columns to get the has_many and belongs_to relationships working?  With Hibernate, you can count on having to make your mapping file define exactly what's going on.  It's great that Ruby doesn't need that help, but <strong>you, as the developer</strong> need to understand what's going on to begin with.

So, I need to learn by example.  Be prepared to hack the provided Rails demos extensively.  I was unable to get any of the examples to do anything useful, with one exception: RubyBB.

### RubyBB tips

* If you were unable to get a vhost installation, or didn't use rubybb as the vhost name, you'll need to edit the standard.rhtml file to change the basic link.  You'll also need to change the stylesheet, javascript, and image links to perhaps go ../ a directory.

* Three database edits are necessary to run the program as written, these aren't too tough to figure out from the error messages though.

* Install `RedCloth` and `builder` gems.  You'll need RedCloth for the topic page and builder for the <span class="caps">RSS</span> functionality.

But then I was up and running.  Sure, it took me about a day to get there, but that's why I'm leaving my breadcrumbs</p>

### RubyBB lessons

* `before_save` is an example of an ActiveRecord object hook to step in and do something during the object lifecycle.  There's no need to use <span class="caps">XML</span> and implement special interceptors, etc.  Just implement the method, and you've got it.

* `validate` defines validation for the Ruby object.  Author has a few examples.   Include `<%= error_message_on "author", "name" %>` in the appropriate .html view, and you've got your error reporting in place.  Check your `ActiveRecord::Errors` RDoc for more information.

### Ruby/RubyBB questions

* `def self.find_by_name(name)`  What does the `self.` prefix do?

