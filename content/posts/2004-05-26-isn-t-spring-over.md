---
layout: post
title: ! '... Isn''t Spring Over?'
tags: []
status: publish
type: post
published: true
meta: {}
---
<h2>What is Spring all about?</h2>

<p>Spring is commonly described as an Inversion of Control (IOC) or dependency injection container.  While I understand what the terms mean, I have the <del>- what would Dave Thomas call it? -</del> novice reaction of.. &#8220;So?&#8221;</p>

<p>To say Spring does only one thing would be a great injustice.  But I have to start in one place, and that&#8217;s getting <a href="http://www.hibernate.org/">Hibernate</a> and Spring tied together.  To do this, a perusal of the documentation and the sample application makes it clear that I&#8217;m going to need to work with an <span class="inlineCode">ApplicationContext</span>. <span class="inlineCode">ApplicationContext</span> is a subclass of <span class="inlineCode">BeanFactory</span>, and here&#8217;s what the Spring reference manual says that a <span class="inlineCode">BeanFactory</span> does:</p>

<blockquote>
The <span class="inlineCode">BeanFactory</span> provides an advanced configuration mechanism capable of managing beans of any nature, using potentially any kind of storage facility.
</blockquote>

<p>Here&#8217;s a list of questions I had before my evaluation that were based on this claim, and how Spring ended up.</p>

<dl>
<dt><p>Q. Can it give me access to many different Hibernate <span class="inlineCode">SessionFactory</span> objects at runtime?   Because heaven forbid my bosses would sell an entirely separate version of the application to a client&#8230;</p></dt>
<dd><p>A. Absolutely.  This actually couldn&#8217;t be easier.</p></dd>
<dt><p>Q. What about alternate configurations of the same <span class="inlineCode">SessionFactory</span>?  For example, I need my <span class="inlineCode">SessionFactory</span> pointing at a different database in a production environment than where it points during a developmental one.</p></dt>
<dd><p>A. Yes, this is possible.  It&#8217;s equally as involved as the techniques I&#8217;m using with <a href="http://ant.apache.org">Ant</a> do perform this same task right now, you just have to put the output into a new file.  For my own personal implementation, it will actually reduce the number of files I&#8217;m having to manage, but I need to do some subtle things with my Spring configuration files first.</p></dd>
<dt><p>Q. What about my actual beans?  Certianly my <span class="inlineCode">SessionFactory</span> is a bean.  What about my <span class="caps">POJO</span>&#8217;s?  Do I have to re-do my Hibernate mappings in Spring format?  The sample application would seem to indicate that I do not, but is that just because it&#8217;s a lightweight sample?</p></dt>
<dd><p>A. You can use Spring to configure whatever it is that you want.  You probably shouldn&#8217;t redo your Hibernate mapping files inside, but if you want some pre-fab instantiations of some Hibernate objects, Spring would be the way to go.</p></dd>
</dl>

<h2>OK, So What&#8217;s A Bean?</h2>

<h4>From the reference:</h4>

<blockquote>
The <span class="inlineCode">BeanFactory</span> isn&#8217;t limited to just managing beans, it is also able to manage virtually any class you want it to manage. [...] (I)t&#8217;s possible to have more exotic non-bean-style classes in your BeanFactory.
</blockquote>

<p>In other words, clear your mind of what &#8220;bean&#8221; means in whatever context you are familiar with.  &#8220;Bean&#8221; means any Java class, really.  If you&#8217;re clever enough, you can use Spring to set up nearly any object you&#8217;re interested in.  Bean definitions require an implementation class, which is natural enough.  One more reason to <a href="http://devblog.jimvanfleet.com/archives/000008.html">program to interfaces</a> if you plan on using Spring.  Then, you can let it do the dirty work of carrying the right implementation to your classes!</p>

<p>You can describe the methods that need to be called on initialization and destruction of a bean, which is very nice.  I can think of a few contexts where that might be useful.</p>

<p>Spring beans can depend on other Spring beans, a concept that will be illustrated in the next Spring post, where you see how to get your hands dirty.</p>

<h2>Summary</h2>

<p>At this point in my evaluation process, Spring does two things.  First, it configures <span class="inlineCode">SessionFactory</span> objects very nicely.  I don&#8217;t have to write any ThreadLocal classes, or re-write the same code over and over when I want to use the same code with different input in different contexts (e.g. inside the container, outside the container, local database, remote database).  Second, it will manage the <span class="inlineCode">Session</span> objects so I don&#8217;t have to.  I&#8217;ll have to keep an eye out to make sure that this is actually working in a way I understand;  as a developer, try not to rely on technologies you don&#8217;t understand on some level.</p>

<p>Oh, wait, make it four!  I get transaction management and second level caching <strong>for free</strong>.  I&#8217;m not kidding.  Setting up Hibernate&#8217;s transaction manager is an extra three lines of <span class="caps">XML</span>, and setting up the cache means copying a <span class="caps">JAR</span> file.  Spring actually complained when I left out the <span class="caps">JAR</span> that enabled the caching ability.</p>

<p>These two&#8212;er, four&#8212; areas make a big win for me.  Also, now I&#8217;m in a boat with other people who will be working on the finer points for me, so I can focus on <strong>getting my work done</strong>.  Using open source products puts you on a team, for better or worse.  I love teams, so for me, it&#8217;s better.  Spring does many other things, as well, so they&#8217;re ready when I am.</p>

<h4>Notes:</h4>

<p>I&#8217;m still wondering how on Earth Spring is going to handle <span class="inlineCode">Session</span> management without knowing about <a href="http://www.sf.net/projects/salmon"><span class="caps">SOFIA</span></a>!  The <span class="inlineCode">WebApplicationContext</span> seems like where that magic might happen.  Spring is set up and working, however, after about three days of looking at it and working on it off and on.  If I do need to understand more about <span class="inlineCode">ApplicationContext</span>s to get exactly the behavior I&#8217;m looking for, that&#8217;s quite all right with me.  I&#8217;ll share whatever I learn here!</p>

<p>Maybe I was too hard on <span class="caps">DAO</span> <a href="http://devblog.jimvanfleet.com/archives/000011.html">here</a>.  The <span class="inlineCode">HibernateClinic</span> class which extends Spring&#8217;s <span class="inlineCode">HibernateDaoSupport</span> looks exactly like a class I&#8217;ve already written to provide many of the same features.  If I had <a href="http://devblog.jimvanfleet.com/archives/000008.html">written to an interface</a> in the first place, it would be trivial to plug in Spring behind the scenes&#8230; for that class, anyway!</p>

<p>A question for the future, since no one actually reads this yet.</p>

<p>Inside the sample petclinic <span class="inlineCode">HibernateClinic</span> class, this is about as complex as the code gets:</p>

<pre class="code">
public List findOwners(String lastName) throws DataAccessException {
    return getHibernateTemplate().find("from Owner owner where owner.lastName like ?", lastName + "%");
}
</pre>

<p>What about something more complicated?  Do your most complicated queries belong in the <span class="caps">DAO</span> class/usage pattern?  <span class="caps">DAO</span> seems to only slightly modify <span class="caps">CRUD</span>.  Where&#8217;s the beef?  For now, my persistence service is going to extend <span class="inlineCode">HibernateDaoSupport</span>, but will include all the complicated queries.</p>
