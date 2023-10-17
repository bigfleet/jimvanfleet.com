---
layout: post
title: ! 'NFJS Review: Rick Hightower on Test Driven Development for the Web'
tags: []
status: publish
type: post
published: true
meta: {}
---
<table align="right" border="2" cellpadding="2" cellspacing="2">
<tr><td>Canoo / HttpUnit / JWebUnit </td></tr>
<tr><td>User Interface </td></tr>
<tr><td>JUnit / Cactus / StrutsTestCase </td></tr>
<tr><td>Controllers / Managers </td></tr>
<tr><td>JUnit / MockObjects </td></tr>
<tr><td>Business Logic </td></tr>
<tr><td>DBUnit test case </td></tr>
<tr><td>Persistence Tier </td></tr>
<tr><td>DBUnit preparation</td></tr>
</table>

<p>The central idea of the presentation was called the &#8220;Web Application Test Sandwich&#8221;.  It looks something like what you&#8217;ll see on the right.  The idea was to present the type of testing each product can perform, and which products compete with and compliment each other in which ways.  It was an excellent primer to have the lightning bolt hit during Dave Thomas&#8217; <a href="http://devblog.jimvanfleet.com/archives/000036.html">Mock Objects</a> talk right afterwards.</p>

<h2>JUnit</h2>

<p>First we talked about JUnit, where I didn&#8217;t really learn anything new.  If you don&#8217;t know about JUnit, Rick&#8217;s recommendation is Kent Beck&#8217;s <a href="http://www.amazon.com/exec/obidos/ASIN/0321146530/jimvanfleetco-20?creative=125581&#38;camp=2321&#38;link_code=as1">Test Driven Development By Example</a>.</p>

<h2>DBUnit</h2>

<p>Next up was DBUnit, a product I will definitely be adding to my toolkit.  DBUnit is designed to be a unit testing tool for <strong>using</strong> databases.  As you might imagine, it handles some very interesting cases gracefully.  You can use <span class="caps">XML</span> files to describe a pre-populated universe for your domain.  You can write these yourself or have DBUnit take an <span class="caps">XML</span> snapshot of a currently existing DB.  You can also just use the test database itself, if you&#8217;d rather avoid <span class="caps">XML</span> altogether.  The flexibility is appreciated.</p>

<p>My Spring+Hibernate experience has moved me towards appreciation of the <span class="caps">DAO</span>, which is an extremely easy pattern to test using DBUnit.  In addition, to speed the running of unit tests, DBUnit can supply an ant command to prepare a test dataset for use during your unit tests.  This way, the <span class="inlineCode"><span class="caps">INSERT</span></span> operations only happen once.</p>

<p>In terms of operations, DBUnit acts much as you&#8217;d expect.  It&#8217;s a thin extension of JUnit;  you have to have your test cases extend a new base class, but most everything else behaves the same.</p>

<h2>Cactus</h2>

<p>I went into the presentation not entirely sure of Cactus&#8217;s role in unit testing.  It seemed so complicated to set up, how could it possibly be a unit test?  Semantic quibbling aside, Cactus can be invaluable for certain projects, but I feel that I don&#8217;t need to use it.</p>

<h4>Why use Cactus?</h4>

<p>I would recommend that a project use Cactus if it depends heavily on it&#8217;s <span class="caps">J2EE</span> environs.  <span class="caps">JNDI</span> lookups, interoperations with <span class="inlineCode">ServletContext</span>, <span class="inlineCode">HttpServletRequest</span>, and <span class="inlineCode">HttpSession</span> objects, or whatever other features you might be using from your application server.  These elements are frequently difficult or impossible to mock, much less provide correct behavior for outside of the real, running environment.  You would know better than me if your project fits the bill.</p>

<p>In my case, the Mock Objects approach is superior.  I can mock certain elements in the Sofia framework, and provide a mock controller in addition to a real controller.  Spring can configure the behavioral testing phase of my mock controller at runtime, and all the actual business code is in the abstract superclass that the controllers share.  Sofia is mature enough that I&#8217;m satisfied that it will behave correctly in nearly all circumstances.  As a result, I focus on whether my code is interacting with the Sofia constructs appropriately.  I don&#8217;t need Tomcat running to interact with any persistence layer;  both memory-based and <span class="caps">RDBMS</span>-based persistence layers will run fine without it, thanks to Spring.<p>

<h2>StrutsTestCase</h2>

<p>No comment, though it looks nice for the Struts users.  Obviously, you would have had to work with Struts to know <strong>how</strong> nice.</p>

<h2>HttpUnit</h2>

<p>HttpUnit is the functional testing slice of the sandwich, the top piece of bread.  HttpUnit and its extension JWebUnit act as modified web browsers that you can command via the Java language.  They both contain advanced capabilities in terms of parsing the responses and providing you with access to the data that has fulfilled your request.</p>

<p>I don&#8217;t live in a world where functional testing is going to be fully replaced by a machine.  My clients are going to want to pound the keys themselves.  As a result, I don&#8217;t know exactly how much time I want to spend testing on this level.  Customers are so picky about their <span class="caps">GUI</span>, sometimes in completely braindead ways.  I don&#8217;t want to be even more frustrated because I have to go back and change a nifty test implementation for something I don&#8217;t even like in the first place.  But what does that have to do with HttpUnit?  :-)</p>

<p>In terms of technology, I&#8217;d likely evaluate both HttpUnit and JWebUnit.  The latter is an extension of the former, although apparently it is not a superset.  Rumor has it that there are some advanced features of HttpUnit that are not present in JWebUnit.  So, when it comes time, I&#8217;ll evaluate further.  The technology at this level, however, will play a role.  Its size is yet to be determined.</p>

<h2>The Presenter</h2>

<p>I can&#8217;t remember which blog I saw that gassed Rick, I think maybe it was Ted Neward&#8217;s, but he wasn&#8217;t wrong.  Rick obviously has a large body of knowledge, and he claims that his group&#8217;s specialty is &#8220;saving your project&#8217;s ass,&#8221; so he&#8217;s got to be ready to put his fees where his mouth is on that score.  Rick continued the high level of speaker quality, in my opinion.</p>
