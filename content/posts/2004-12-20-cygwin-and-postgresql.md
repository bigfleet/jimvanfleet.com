---
layout: post
title: Cygwin and PostgreSQL
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-12-20
---
Getting postgreSQL up and running under Cygwin was not that difficult for me, although it does require a couple of Google searches.

First, the basic information is supplied [here](http://www.postgresql.org/docs/faqs/text/FAQ_CYGWIN) by the folks at postgreSQL.

When I followed these instructions, however, I kept getting a failure message.  I should have copied it down, but since I didn't expect the next step to work, I didn't.  I'll edit this soon to include the error message.

The second step came from a Rick Hightower blog post.  Simply use:

```
export CYGWIN=server
```


before you issue any of the commands listed in step 1 and you should be golden.
