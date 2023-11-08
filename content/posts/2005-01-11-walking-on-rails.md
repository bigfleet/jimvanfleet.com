---
layout: post
title: Walking On Rails
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-01-11
---
To anyone experimenting with [Ruby on Rails](http://www.rubyonrails.com/), I highly recommend starting with a domain model and a debugging session.  Knowing how to create and associate elements in your model lends a lot of focus to how you'd like to write your views.

```
ruby script/console development
```

or its cousins will let you instantiate objects, assign their properties, and save them.  It will also let you know about syntax errors, missing columns, or misnamed columns in the most direct way possible.  After a walk through your model in irb, you should feel confident about constructing the view in a similar way.

(ed. note, updated and revised below-- above remains as an artifact of time)

Also Google "Active Record relationships" and search for images.  You'll find some good blogs.
