---
layout: post
title: ! '... Isn''t Spring Over?'
tags:
- Development
status: publish
type: post
published: true
Date: 2004-05-26
---
## What is Spring all about?

Spring is commonly described as an Inversion of Control (IOC) or dependency injection container.  While I understand what the terms mean, I have the <del>- what would Dave Thomas call it? -</del> novice reaction of.. "So?"

To say Spring does only one thing would be a great injustice.  But I have to start in one place, and that's getting [Hibernate](http://www.hibernate.org/) and Spring tied together.  To do this, a perusal of the documentation and the sample application makes it clear that I'm going to need to work with an `ApplicationContext`. `ApplicationContext` is a subclass of `BeanFactory`, and here's what the Spring reference manual says that a `BeanFactory` does:

> The `BeanFactory` provides an advanced configuration mechanism capable of managing beans of any nature, using potentially any kind of storage facility.

Here's a list of questions I had before my evaluation that were based on this claim, and how Spring ended up.

<dl>
<dt>Q. Can it give me access to many different Hibernate <span class="inlineCode">SessionFactory</span> objects at runtime?   Because heaven forbid my bosses would sell an entirely separate version of the application to a client&#8230;</dt>
<dd>A. Absolutely.  This actually couldn't be easier.</dd>
<dt>Q. What about alternate configurations of the same <span class="inlineCode">SessionFactory</span>?  For example, I need my <span class="inlineCode">SessionFactory</span> pointing at a different database in a production environment than where it points during a developmental one.</dt>
<dd>A. Yes, this is possible.  It's equally as involved as the techniques I'm using with <a href="http://ant.apache.org">Ant</a> do perform this same task right now, you just have to put the output into a new file.  For my own personal implementation, it will actually reduce the number of files I'm having to manage, but I need to do some subtle things with my Spring configuration files first.</dd>
<dt>Q. What about my actual beans?  Certianly my <span class="inlineCode">SessionFactory</span> is a bean.  What about my <span class="caps">POJO</span>'s?  Do I have to re-do my Hibernate mappings in Spring format?  The sample application would seem to indicate that I do not, but is that just because it's a lightweight sample?</dt>
<dd>A. You can use Spring to configure whatever it is that you want.  You probably shouldn't redo your Hibernate mapping files inside, but if you want some pre-fab instantiations of some Hibernate objects, Spring would be the way to go.</dd>
</dl>

<h2>OK, So What's A Bean?</h2>

<h4>From the reference:</h4>

<blockquote>
The <span class="inlineCode">BeanFactory</span> isn't limited to just managing beans, it is also able to manage virtually any class you want it to manage. [...] (I)t's possible to have more exotic non-bean-style classes in your BeanFactory.
</blockquote>

In other words, clear your mind of what "bean" means in whatever context you are familiar with.  "Bean" means any Java class, really.  If you're clever enough, you can use Spring to set up nearly any object you're interested in.  Bean definitions require an implementation class, which is natural enough.  One more reason to <a href="http://devblog.jimvanfleet.com/archives/000008.html">program to interfaces</a> if you plan on using Spring.  Then, you can let it do the dirty work of carrying the right implementation to your classes!

You can describe the methods that need to be called on initialization and destruction of a bean, which is very nice.  I can think of a few contexts where that might be useful.

Spring beans can depend on other Spring beans, a concept that will be illustrated in the next Spring post, where you see how to get your hands dirty.

<h2>Summary</h2>

At this point in my evaluation process, Spring does two things.  First, it configures <span class="inlineCode">SessionFactory</span> objects very nicely.  I don't have to write any ThreadLocal classes, or re-write the same code over and over when I want to use the same code with different input in different contexts (e.g. inside the container, outside the container, local database, remote database).  Second, it will manage the <span class="inlineCode">Session</span> objects so I don't have to.  I'll have to keep an eye out to make sure that this is actually working in a way I understand;  as a developer, try not to rely on technologies you don't understand on some level.

Oh, wait, make it four!  I get transaction management and second level caching <strong>for free</strong>.  I'm not kidding.  Setting up Hibernate's transaction manager is an extra three lines of <span class="caps">XML</span>, and setting up the cache means copying a <span class="caps">JAR</span> file.  Spring actually complained when I left out the <span class="caps">JAR</span> that enabled the caching ability.

These two&#8212;er, four&#8212; areas make a big win for me.  Also, now I'm in a boat with other people who will be working on the finer points for me, so I can focus on <strong>getting my work done</strong>.  Using open source products puts you on a team, for better or worse.  I love teams, so for me, it's better.  Spring does many other things, as well, so they're ready when I am.

<h4>Notes:</h4>

I'm still wondering how on Earth Spring is going to handle <span class="inlineCode">Session</span> management without knowing about <a href="http://www.sf.net/projects/salmon"><span class="caps">SOFIA</span></a>!  The <span class="inlineCode">WebApplicationContext</span> seems like where that magic might happen.  Spring is set up and working, however, after about three days of looking at it and working on it off and on.  If I do need to understand more about <span class="inlineCode">ApplicationContext</span>s to get exactly the behavior I'm looking for, that's quite all right with me.  I'll share whatever I learn here!

Maybe I was too hard on <span class="caps">DAO</span> <a href="http://devblog.jimvanfleet.com/archives/000011.html">here</a>.  The <span class="inlineCode">HibernateClinic</span> class which extends Spring's <span class="inlineCode">HibernateDaoSupport</span> looks exactly like a class I've already written to provide many of the same features.  If I had <a href="http://devblog.jimvanfleet.com/archives/000008.html">written to an interface</a> in the first place, it would be trivial to plug in Spring behind the scenes&#8230; for that class, anyway!

A question for the future, since no one actually reads this yet.

Inside the sample petclinic <span class="inlineCode">HibernateClinic</span> class, this is about as complex as the code gets:

<pre class="code">
public List findOwners(String lastName) throws DataAccessException {
    return getHibernateTemplate().find("from Owner owner where owner.lastName like ?", lastName + "%");
}
</pre>

What about something more complicated?  Do your most complicated queries belong in the <span class="caps">DAO</span> class/usage pattern?  <span class="caps">DAO</span> seems to only slightly modify <span class="caps">CRUD</span>.  Where's the beef?  For now, my persistence service is going to extend <span class="inlineCode">HibernateDaoSupport</span>, but will include all the complicated queries.
