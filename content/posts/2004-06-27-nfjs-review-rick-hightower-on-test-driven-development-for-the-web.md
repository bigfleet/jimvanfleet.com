---
layout: post
title: ! 'NFJS Review: Rick Hightower on Test Driven Development for the Web'
tags:
- NFJS
- Tech
status: publish
type: post
published: true

---

* Canoo / HttpUnit / JWebUnit
* User Interface
* JUnit / Cactus / StrutsTestCase
* Controllers / Managers
* JUnit / MockObjects
* Business Logic
* DBUnit test case
* Persistence Tier 
* DBUnit preparation


The central idea of the presentation was called the &#8220;Web Application Test Sandwich&#8221;.  It looks something like what you'll see on the right.  The idea was to present the type of testing each product can perform, and which products compete with and compliment each other in which ways.  It was an excellent primer to have the lightning bolt hit during Dave Thomas' <a href="http://devblog.jimvanfleet.com/archives/000036.html">Mock Objects</a> talk right afterwards.

## JUnit
https://a.co/d/

First we talked about JUnit, where I didn't really learn anything new.  If you don't know about JUnit, Rick's recommendation is Kent Beck's {{<amzn asin=aKgg3u8 title="Test Driven Development By Example">}}

## DBUnit

Next up was DBUnit, a product I will definitely be adding to my toolkit.  DBUnit is designed to be a unit testing tool for *using* databases.  As you might imagine, it handles some very interesting cases gracefully.  You can use <span class="caps">XML</span> files to describe a pre-populated universe for your domain.  You can write these yourself or have DBUnit take an <span class="caps">XML</span> snapshot of a currently existing DB.  You can also just use the test database itself, if you'd rather avoid <span class="caps">XML</span> altogether.  The flexibility is appreciated.

My Spring+Hibernate experience has moved me towards appreciation of the <span class="caps">DAO</span>, which is an extremely easy pattern to test using DBUnit.  In addition, to speed the running of unit tests, DBUnit can supply an ant command to prepare a test dataset for use during your unit tests.  This way, the `INSERT` operations only happen once.

In terms of operations, DBUnit acts much as you'd expect.  It's a thin extension of JUnit;  you have to have your test cases extend a new base class, but most everything else behaves the same.

## Cactus

I went into the presentation not entirely sure of Cactus's role in unit testing.  It seemed so complicated to set up, how could it possibly be a unit test?  Semantic quibbling aside, Cactus can be invaluable for certain projects, but I feel that I don't need to use it.

### Why use Cactus?

I would recommend that a project use Cactus if it depends heavily on it's <span class="caps">J2EE</span> environs.  <span class="caps">JNDI</span> lookups, interoperations with `ServletContext`, `HttpServletRequest`, and `HttpSession` objects, or whatever other features you might be using from your application server.  These elements are frequently difficult or impossible to mock, much less provide correct behavior for outside of the real, running environment.  You would know better than me if your project fits the bill.

In my case, the Mock Objects approach is superior.  I can mock certain elements in the Sofia framework, and provide a mock controller in addition to a real controller.  Spring can configure the behavioral testing phase of my mock controller at runtime, and all the actual business code is in the abstract superclass that the controllers share.  Sofia is mature enough that I'm satisfied that it will behave correctly in nearly all circumstances.  As a result, I focus on whether my code is interacting with the Sofia constructs appropriately.  I don't need Tomcat running to interact with any persistence layer;  both memory-based and <span class="caps">RDBMS</span>-based persistence layers will run fine without it, thanks to Spring.

## StrutsTestCase

No comment, though it looks nice for the Struts users.  Obviously, you would have had to work with Struts to know *how* nice.

## HttpUnit

HttpUnit is the functional testing slice of the sandwich, the top piece of bread.  HttpUnit and its extension JWebUnit act as modified web browsers that you can command via the Java language.  They both contain advanced capabilities in terms of parsing the responses and providing you with access to the data that has fulfilled your request.

I don't live in a world where functional testing is going to be fully replaced by a machine.  My clients are going to want to pound the keys themselves.  As a result, I don't know exactly how much time I want to spend testing on this level.  Customers are so picky about their <span class="caps">GUI</span>, sometimes in completely braindead ways.  I don't want to be even more frustrated because I have to go back and change a nifty test implementation for something I don't even like in the first place.  But what does that have to do with HttpUnit?  :-)

In terms of technology, I'd likely evaluate both HttpUnit and JWebUnit.  The latter is an extension of the former, although apparently it is not a superset.  Rumor has it that there are some advanced features of HttpUnit that are not present in JWebUnit.  So, when it comes time, I'll evaluate further.  The technology at this level, however, will play a role.  Its size is yet to be determined.

## The Presenter

I can't remember which blog I saw that gassed Rick, I think maybe it was Ted Neward's, but he wasn't wrong.  Rick obviously has a large body of knowledge, and he claims that his group's specialty is "saving your project's ass," so he's got to be ready to put his fees where his mouth is on that score.  Rick continued the high level of speaker quality, in my opinion.
