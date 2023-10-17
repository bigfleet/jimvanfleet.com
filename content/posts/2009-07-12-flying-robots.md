---
layout: post
title: Flying Robots!
tags:
- Tech
status: publish
type: post
published: true
meta: {}
---
Anyone who didn't like this talk must not have had a pulse.

The "big idea" of the talk was doing open-source software development on an open-source hardware platform that does something cool!  Like flying a freaking blimp to The Flight of the Valkyries!

<!--more--><a href="http://www.arduino.cc/en/Main/Software">Arduino development</a> (and in this case, <a href="http://diydrones.com/profiles/blog/show?id=705844%3ABlogPost%3A44817">BlimpDuino</a> development seems like the truest form of hackery possible to me, and I found it a thing of beauty.  As they don't appear on the official schedule, I may have gotten their names wrong, but I believe it's the Evans brothers put on quite the show.  It's clear they put a lot of time and love into the project.  And the end result is incredibly cool.

When you are doing this kind of hacking, you'll run into problems that you might never expect.  For example, their blimp's engines both rotate in the same direction.  When the blimp is at full-forward, the torque itself actually steers the ship in the opposite direction to the rotation, and they've not been able to correct (or get an engine that rotates the opposite direction yet.)

I loved the feeling of having two brothers in their garage, working on different parts of the problem, crashing things, setting things on fire, having to chase down their own invention (the tether was added in later models, LOL).  Plus, the style of the hardware hacker with his handlebar mustache and muttonchops was a real plus.

It will be great to watch this field closely, as the Arduino boards are still very limited in terms of capacity and throughput.  They mentioned needing to be able to fit their entire blimp control scheme in about 14k, which is not a lot of resources to bring to bear.  The Ruby code that instructs the hardware compiles to C++ code, then to machine bytecode, and finally uploaded wirelessly to the blimp.  It's cool to watch.  But didn't you get that message already?

Blimp development: p3wn@ge
