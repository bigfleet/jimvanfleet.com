---
layout: post
title: The Stand-Ins Are The Story
tags:
- Development
status: publish
type: post
published: true
Date: 2004-05-23
---
## What Are Mock Objects?

#### Mock Objects are a stand-in for the real world

Mock Objects make a difference in the web applications, because the objects you're writing depend on objects like `ServletRequest` and `ServletResponse`.  And how do you get them to do something you want?

#### Controllable without fuss

Mock objects implement interfaces like the above, giving you a chance to write up different implementations for different, testable behavior.

#### Simulate things that would otherwise be impossible

What if you need to test the performance of your system when the database goes down, or the network is unreachable?  Depending on your code, those things may actually be impossible to test otherwise, but Mock Objects can make it possible.

#### Mock Objects are just like film stand-ins

* Cheaper than the leading man
* Less temperamental
* Always available
* Good enough for setting up the production environment _rimshot_

## How To Use Mock Objects

In a lot of cases, using Mock Objects seems easy enough.  There's a Mock Objects framework already written with many useful implementations already.  There are <a href="http://jmock.org/index.html">JMock</a> and <a href="http://www.easymock.org/index.html">EasyMock</a> designed to make it easier.

But that's really not the whole story.

### About Your Mock Objects

One very useful thing to remember is that, unlike a movie stand-in, your Mock Object should provide <strong>more</strong> functionality than the object it's standing in for.  If your Mock Object is implementing an interface or extending another class, it'll likely need to keep extra state and provide extra methods to provide the means by which you can influence precisely what the Mock implementation will be doing.

### Making It Happen

The most difficult part of the entire process is getting your "real" code to use the mock objects during testing, while they use the real objects during production&#8212;or even other levels of testing.  This is where you, as a developer, have to earn your pay.

### An example

What I really wanted to involve in unit testing was my [SOFIA](../2004-05-10-my-love-letter-to-sofia) controllers.  I can test my persistence layer with [DbUnit](http://www.dbunit.org/) and my domain model with [JUnit](http://www.junit.org").  Those web controllers were the last mile of feeling that I could use full automated testing on my projects.

So, the controller doesn't implement an interface, and it already extends another class.  The solution for me was to create an abstract class with two concrete subclasses.  One subclass is the real one, referenced in the <span class="caps">JSP</span> page.  The other is the "mock" one used for testing.  All the important behavior is located in the abstract superclass.  Since the controllers extend a class with a default constructor, all that needs to be done is some field initialization within the constructor for the mock controller.  That got me almost all the way there.

There was one last snag.  Some elements of the <span class="caps">SOFIA</span> framework, like `HtmlSubmitButton` and `HtmlText` call methods that need the <span class="caps">SOFIA</span> `system.properties` file.  This solution was just as simple.  Use another mock!

I created simple mock subclasses of those concrete classes that override the methods that need initialization of the properties subsystem.  During constructor initialization, instead of assigning a new instance of `HtmlText` to the field, I assign a new instance of `MockHtmlText` instead.

I'm not done with my testing implementations yet;  I have to get my datastores into the action.  But this is an excellent example of how Mock Objects can make something that's nearly impossible to test a possibility.