---
layout: post
title: Stripping Subversion
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-02-10
---
or--  recursively deleting directories of the same name.

The only tool that I'm comfortable with that could do something like this is Ant.  But I thought, hey, you know it's possible in Unix.  It took me about five minutes in Cygwin with `man find` to come up with this one.</p>

```
Jim Van Fleet@jimvfxp /cygdrive/c/dev/eclipse-3.1M4/workspace
$ find . -name .svn -exec rm -rf '{}' \;
```

That did the trick!
