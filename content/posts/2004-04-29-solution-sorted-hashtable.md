---
layout: post
title: ! 'Solution: Sorted Hashtable'
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>For a problem I face in my code, I want a key-value pair with quick lookup and a sorted set of keys.  Sounds like a job for TreeMap, right?</p>


	<p>The wrinkle is that I&#8217;d like an option for ascending and descending order, not just the natural order of my keys.</p>


	<p>Enter <a title="developerWorks : Java : Forums : sort Strings descending" href="http://www-106.ibm.com/developerworks/forums/dw_expandTree.jsp?thread=31491&#38;cat=10&#38;forum=177&#38;message=1935880">a forum post on Comparators in descending order</a>.  I can feed this Comparator to my TreeMap, then I get the sorting I&#8217;d like.</p>


	<p>Just thought I&#8217;d share!</p>
