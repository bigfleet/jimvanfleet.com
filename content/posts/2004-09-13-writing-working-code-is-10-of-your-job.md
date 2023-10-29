---
layout: post
title: Writing Working Code Is 10% Of Your Job
tags:
- Tech
status: publish
type: post
published: true
Date: 2004-09-13
---
My typical pattern of code development to this point has consisted of writing code that "works," by trying your single implementation over and over again with tweaking until it gives you the results you want.  This normally brings the "Yay!" feeling and I go grab a beer.

Now that I'm a year older, I realize that I'm at *most* 30% done.  There are two other responsibilities all developers should feel morally bound to provide with their code:  proof of correctness, and a maintainable state.

Proof of correctness would normally be seen as an accompanying unit test suite.  This is probably the best solution, but I can't say that yet.  I know it's the one I'm most comfortable using.  Some sort of formal documentation (not formal, as in, no visible pizza droppings, formal as in discrete math or logic) might be used instead for the right kind of problem.  This ensures that there is at least somewhere to start when your solution ends up working only 95% or even 99% of the time, or when things change into the future, and someone who has never met you has to start working with your code anew.

Maintainable state has many criterion.  Is your code written to some sort of coding conventions for variable naming and static access?  What's your package structure like?  How easy is it to "translate" domain concerns and find them in the code?  If there were no "copy and paste," could the project have been completed at all?

Those who come after you will end up paying the costs that you have deferred to them without an effort to do these things.

This is why I'm starting to multiply my estimates by eight to determine how long a task will really take.
