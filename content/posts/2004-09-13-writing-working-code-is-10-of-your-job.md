---
layout: post
title: Writing Working Code Is 10% Of Your Job
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>My typical pattern of code development to this point has consisted of writing code that &#8220;works,&#8221; by trying your single implementation over and over again with tweaking until it gives you the results you want.  This normally brings the &#8220;Yay!&#8221; feeling and I go grab a beer.</p>


	<p>Now that I&#8217;m a year older, I realize that I&#8217;m at <strong>most</strong> 30% done.  There are two other responsibilities all developers should feel morally bound to provide with their code:  proof of correctness, and a maintainable state.</p>


	<p>Proof of correctness would normally be seen as an accompanying unit test suite.  This is probably the best solution, but I can&#8217;t say that yet.  I know it&#8217;s the one I&#8217;m most comfortable using.  Some sort of formal documentation (not formal, as in, no visible pizza droppings, formal as in discrete math or logic) might be used instead for the right kind of problem.  This ensures that there is at least somewhere to start when your solution ends up working only 95% or even 99% of the time, or when things change into the future, and someone who has never met you has to start working with your code anew.</p>


	<p>Maintainable state has many criterion.  Is your code written to some sort of coding conventions for variable naming and static access?  What&#8217;s your package structure like?  How easy is it to &#8220;translate&#8221; domain concerns and find them in the code?  If there were no &#8220;copy and paste,&#8221; could the project have been completed at all?</p>


	<p>Those who come after you will end up paying the costs that you have deferred to them without an effort to do these things.</p>


	<p>This is why I&#8217;m starting to multiply my estimates by eight to determine how long a task will really take.</p>
