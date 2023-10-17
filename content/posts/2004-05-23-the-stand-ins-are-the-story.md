---
layout: post
title: The Stand-Ins Are The Story
tags: []
status: publish
type: post
published: true
meta: {}
---
<h2>What Are Mock Objects?</h2>

<dl>
<dt>Mock Objects are a stand-in for the real world</dt>
<dd>
<p>Mock Objects make a difference in the web applications, because the objects you&#8217;re writing depend on objects like <span class="inlineCode">ServletRequest</span> and <span class="inlineCode">ServletResponse</span>.  And how do you get them to do something you want?</p></dd>
<dt>Controllable without fuss</dt>
<dd><p>Mock objects implement interfaces like the above, giving you a chance to write up different implementations for different, testable behavior.</p></dd>
<dt>Simulate things that would otherwise be impossible</dt>
<dd><p>What if you need to test the performance of your system when the database goes down, or the network is unreachable?  Depending on your code, those things may actually be impossible to test otherwise, but Mock Objects can make it possible.</p></dd>
<dt>Mock Objects are just like film stand-ins</dt>
<dd>
<ul>
<li>Cheaper than the leading man</li>
<li>Less temperamental</li>
<li>Always available</li>
<li>Good enough for setting up the production environment <i>rimshot</i></li>
</ul>
</dd>
</dl>

<h2>How To Use Mock Objects</h2>

<p>
In a lot of cases, using Mock Objects seems easy enough.  There&#8217;s a <a href="http://www.mockobjects.org">Mock Objects</a> framework already written with many useful implementations already.  There are <a href="http://www.mockobjects.com/wiki/DynaMock">other</a> <a href="http://www.easymock.org/index.html">frameworks</a> designed to make it easier.
</p>
<p>But that&#8217;s really not the whole story.</p>

<h4>About Your Mock Objects</h4>

<p>
One very useful thing to remember is that, unlike a movie stand-in, your Mock Object should provide <strong>more</strong> functionality than the object it&#8217;s standing in for.  If your Mock Object is implementing an interface or extending another class, it&#8217;ll likely need to keep extra state and provide extra methods to provide the means by which you can influence precisely what the Mock implementation will be doing.
</p>

<h4>Making It Happen</h4>
<p>
The most difficult part of the entire process is getting your &#8220;real&#8221; code to use the mock objects during testing, while they use the real objects during production&#8212;or even other levels of testing.  This is where you, as a developer, have to earn your pay.
</p>
<h4>An example</h4>
<p>
What I really wanted to involve in unit testing was my <a href="http://devblog.jimvanfleet.com/archives/000031.html"><span class="caps">SOFIA</span></a> controllers.  I can test my persistence layer with <a href="http://www.dbunit.org/">DbUnit</a> and my domain model with <a href="http://www.junit.org">JUnit</a>.  Those web controllers were the last mile of feeling that I could use full automated testing on my projects.
</p>
<p>
So, the controller doesn&#8217;t implement an interface, and it already extends another class.  The solution for me was to create an abstract class with two concrete subclasses.  One subclass is the real one, referenced in the <span class="caps">JSP</span> page.  The other is the &#8220;mock&#8221; one used for testing.  All the important behavior is located in the abstract superclass.  Since the controllers extend a class with a default constructor, all that needs to be done is some field initialization within the constructor for the mock controller.  That got me almost all the way there.
</p>
<p>There was one last snag.  Some elements of the <span class="caps">SOFIA</span> framework, like <span class="inlineCode">HtmlSubmitButton</span> and <span class="inlineCode">HtmlText</span> call methods that need the <span class="caps">SOFIA</span> system.properties file.  This solution was just as simple.  Use another mock!</p>
<p>I created simple mock subclasses of those concrete classes that override the methods that need initialization of the properties subsystem.  During constructor initialization, instead of assigning a new instance of <span class="inlineCode">HtmlText</span> to the field, I assign a new instance of <span class="inlineCode">MockHtmlText</span> instead.  </p>
<p>
I&#8217;m not done with my testing implementations yet;  I have to get my datastores into the action.  But this is an excellent example of how Mock Objects can make something that&#8217;s nearly impossible to test a possibility.
</p>
