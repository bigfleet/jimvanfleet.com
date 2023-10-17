---
layout: post
title: ! 'Lesson: Design to Interfaces'
tags: []
status: publish
type: post
published: true
meta: {}
---
<iframe style="float:right" marginwidth="0" marginheight="0"  scrolling="no" frameborder="2" width="120" height="150" src="http://rcm.amazon.com/e/cm?o=1&#38;l=as1&#38;f=ifr&#38;t=jimvanfleetco-20&#38;dev-t=D68HUNXKLHS4J&#38;p=6&#38;asins=0764543857&#38;bg1=ffffff&#38;fc1=000000&#38;lc1=6633ff&#38;lt1=_blank"><map NAME="boxmap-p6"><area SHAPE="RECT" COORDS="1, 140, 83, 150" HREF="http://rcm.amazon.com/e/cm/privacy-policy.html?o=1" ><area COORDS="0,0,10000,10000" HREF="http://www.amazon.com/exec/obidos/redirect-home/jimvanfleetco-20" ></map><img src="http://rcm-images.amazon.com/images/G/01/rcm/120x150.gif" width="120" height="150" border="0" usemap="#boxmap-p6" alt="Shop at Amazon.com"></iframe>

<h2>The Set Up</h2>
<p>In reviewing the <a href="http://www.salmonllc.com/website/Jsp/vanity/bin/UserGuide.pdf">Sofia User&#8217;s Guide</a>, I stumble upon their facility to implement a site map.  Their site map is an <span class="caps">XML</span> file that can be used to edit page locations and preferences at runtime without a re-compile.  Their <span class="caps">GUI</span> tools have great support for it, and it gets rid of all the mis-typed <span class="caps">URL</span>&#8217;s and saves some time.</p>

<h2>What I Should Have Done</h2>
<p>
<ol>
<li>Go to the vending machines and get some <a href="http://www.mountaindew.com/code_red/index.php">Code Red</a></li>
<li>Think about what my real needs are for the linkage.  I don&#8217;t need every last little bit of the Sofia capabilities, I just want a way to get &#8220;Dreamweaver-style&#8221; link assurances within Java code.  In addition, I have my help files laid out in such a way that I can get those <span class="caps">URL</span>&#8217;s for free for any given page name&#8212;it&#8217;d be nice to include that too, with a little Javascript to make it pop up in a new window.</li>
<li>Design an interface with appropriate methods for the above&#8212;like <pre>getUrl(String key)</pre> and <pre>getHelpUrl(String url)</pre></li>
<li>Implement the interface with a default implementation, passing those methods along to the appropriate Sofia site map calls.</li>
<li>Set up a separate, constants class to represent keys for the various pages</li>
</ol>
</p>
<h2>What I Did Do</h2>
<p>
<ol>
<li>Went to the vending machines and got some <a href="http://www.mountaindew.com/code_red/index.php">Code Red</a></li>
<li>While sipping, put the calls to the site map functionality into the controller.  This went on for weeks as I added more keys, and I refactored the code a bit in the middle.  Since I needed the <span class="caps">URL</span> in some places (to append a query string before a redirect), and ordered a full redirect in others, I had several different methods of interacting with the site maps calls.</li>
</ol>
</p>
<h2>The Pinch</h2>
<p>
During development, I had noticed occassional spurts of</p> <pre>/opgi360/Jsp/admin/mail/participant.notification.jsp</pre> <p>becoming</p> <pre>/ant.ntofication.jsp</pre><p> but since I was constantly editing the site map, and never had a major problem with whatever pages I was testing at the time, I chalked it up to <a href="http://www.mdx.ac.uk/www/study/glocom.htm#gremlin">computer gremlins</a> and ignored it.</p>
<p>Obviously, the gremlins infested the deployed system.  Major pages were unreachable.</p>
<p>Looking for a solution, I see that Sofia&#8217;s site map functionality is a pretty skeletal implementation over a <a href="http://java.sun.com/webservices/docs/ea2/tutorial/doc/JAXPIntro4.html"><span class="caps">SAX</span> parser</a>.  I don&#8217;t know a ton about <span class="caps">XML</span>, but I do know, thanks to a workshop at <a href="http://www.sigcse.org"><span class="caps">SIGCSE</span></a> that <span class="caps">SAX</span> parsing is the one I&#8217;m least likely to understand or enjoy working with, and that it&#8217;s a part of the 1.4 library.
</p>
<p>In other words, I have little to no idea where to look for the bugs, and probably wouldn&#8217;t recognize them when or if I saw them.  I could try to move the site map over to using a <a href="http://java.sun.com/webservices/docs/1.0/tutorial/doc/JAXPIntro5.html"><span class="caps">DOM</span></a> parser, which I can understand more easily.  But how on earth could I know how long that would take?  And, the biggest test, what value does it add for the people using the system?</p>
<p>So, the solution is: rip out the site map functionality, replace the Dreamweaver links with something a little more hard-coded, and figure out something to do with the Java linkage.</p>

<h2>What Should Have Happened</h2>

<p>
<ol>
<li>Grab a drink</li>
<li>Reimplement the interface, only this time the &#8220;keys&#8221; are constants that look like page names and represent the actual page <span class="caps">URL</span>&#8217;s.</li>
<li>Rewrite the implementation&#8217;s methods to only operate on the &#8220;keys&#8221; instead of doing anything with the site map.</li>
<li>Check out the Dreamweaver pages, searching for any Sofia links that could be replaced with regular links, and hard-coding the <span class="caps">URL</span>&#8217;s for the ones that could not.</li>
</ol>
</p>
<p>Estimated time:  a half day.</p>

<h2>What Did Happen</h2>
<p>
<ol>
<li>Wake up early to have Easter Sunday</li>
<li>Check out the Dreamweaver pages, searching for any Sofia links that could be replaced with regular links, and hard-coding the <span class="caps">URL</span>&#8217;s for the ones that could not.</li>
<li>Go to the class where I&#8217;ve been storing the keys and comment everything out.</li>
<li>Freak out when I see how many times I link to another page in the hard code.</li>
<li>Do a primitive separation of the interface and implementation.</li>
<li>Go through the code, fixing compilation errors</li>
<li>Stumble back and forth over whether to use an interface or an abstract class.  (Conclusion: the keys are present for both, but have different semantics in each&#8212;I went the abstract class route).  This decision ended up getting made at about 11PM.</li>
<li>Go to sleep feeling very tired, and not that good.</li>
</ol>
</p>
<p>Estimated time: a day and a half, on a holiday</p>

<h2>Conclusion</h2>
<p>Whenever I find an exciting new feature, it&#8217;s natural to want to dig in and start using it immediately.  I need to stop doing it with code I depend on, and start doing that with <a href="http://www.drjava.org">DrJava</a>&#8217;s interaction pane (which I now have set up in <a href="http://www.eclipse.org/">Eclipse</a> as a plugin).</p>

<p>When you design away from the implementations and class instances, you end up with a nifty little <a href="http://www.martinfowler.com/eaaCatalog/serviceLayer.html">Service Layer</a> for whatever service you&#8217;re using.  (It doesn&#8217;t have to be a domain model, like in the picture.)  And, when you find out you need to pull everything apart, you aren&#8217;t ripping your code into pieces.</p>

<p>That&#8217;s today&#8217;s tip, from me to you</p>
