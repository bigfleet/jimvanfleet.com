---
layout: post
title: postgreSQL Peccadillo
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-06-06
---
Given the task of creating a "staging area" where some users can play around with the application without worrying about the data available, I ran into the following problem when attempting to create the database schema.

```
ERROR: permission denied for relation cpt_code
```

I thought that was pretty odd, since I had just created the database as that user.  Investigating afterwards showed that just by issuing the `createdb`` command that I had copied all the elements in my original database!

Issuing the `createdb` command with the specific option to use `template0` was the key to getting me up and running.  You'd think that creating a new database would default to creating something completely empty, but I guess not!

Now back to dealing with the (expletives deleted) Tomcat classloader and log4j.
