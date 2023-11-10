---
layout: post
title: Disabling Commons Logging
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-02-07
---
I've developed a suite of test cases for my latest application.  In my architecture, I want to make sure that each of the implementations for each of my interfaces passes the test cases as part of the build process.  I accomplish this goal using Spring configuration and a little property file maintainance.

As a result, however, following the unit test execution was absolutely impossible.  Thanks to a post on the Spring forum, I discovered the key to disabling commons-logging is to set a system property.  It was a slam-dunk after that to change a system property using Ant.  Fortunately, the JUnit Ant task accepts this property!
