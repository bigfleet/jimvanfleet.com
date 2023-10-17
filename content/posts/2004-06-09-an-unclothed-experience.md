---
layout: post
title: An Unclothed Experience
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I plan on using Naked Objects for rapid prototyping.  Now that I know how to produce a &#8220;working&#8221; domain model using the framework, I feel that it will be an excellent tool that I actually will use on my next project.  I am <strong>not</strong> going to use Naked Objects in the delivered product.  These notes are geared towards developers who have similar plans.</p>

<h2>The Interface Is The Output</h2>

<p>First, do <strong>not</strong> write your business object interfaces first.  It may seem natural to do so, then grow the interface and the Naked Object implementation together.  That&#8217;s what I actually did.  What a pain!</p>

<p>The rub is that the Naked Objects framework actually uses wrappers around Strings, floats, ints, and the Collections interface.  While implementing the interface is trivial for the primitive wrappers, it&#8217;s not immediately apparent how to implement the methods that would return a <span class="inlineCode">List</span>, for example.  Since the point is rapid prototyping, just start with the basics.  We&#8217;re going to throw this code away, essentially, so why spend time poking in innards?</p>

<p>We&#8217;re also in a period where we expect frequent, massive change to the domain model.  Without implementing the interface, you can aspire to real-time edits and allowing the business customer to see the effects their changes have on the model.  If you treat the interface to the business objects as the output, you get all the benefits of Naked Objects without sacrificing anything truly worthwhile.</p>

<h2>Notes</h2>

<ul>
<li>The documentation is in an interesting state.  First, the tutorial serves as an excellent walkthrough.  There was no information I needed that wasn&#8217;t in the original package, <strong>except</strong> for the fact that you no longer need the two separate icons.</li>
<li>While the wrapping of values and collections seems a little odd, I consider it an extremely small price to pay to get that UI up and running.</li>
<li>It&#8217;d be interesting to see a more involved system than the one I produced.  Mostly, I&#8217;m just fascinated by the concept that this framework could be used directly in a deliverable.  Can users really do it?  Can it possibly be for everyone?</li>
</ul>
