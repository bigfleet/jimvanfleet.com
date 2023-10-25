---
layout: post
title: Screaming Headless Servers
tags:
- Development
status: publish
type: post
published: true
Date: 2004-05-18
---

## Problem

If you're working with a server-side application, like I am, that imports a `javax.swing` package, you might get strange errors, such as the one described [here](https://sourceforge.net/forum/message.php?msg_id=2545939).  `javax.swing` packages expect to find an [X11](http://www.xfree86.org/) server running on the machine.  In my case, it wants to access the graphical subsystem because [JFreeReport](http://www.jfree.org/) wants to use a `TableModel` as a kind of spreadsheet.

## Solution

append `java.awt.headless=true` to your `JAVA_OPTS` in `catalina.sh`.  Mine ended up looking like this.

```bash
JAVA_OPTS=-Dsalmon.props.path=/home/opgi/bin/jakarta-tomcat-4.1.30/salmon/properties
JAVA_OPTS = "$JAVA_OPTS -Djava.awt.headless=true"
```
