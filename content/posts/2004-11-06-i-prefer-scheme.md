---
layout: post
title: I Prefer Scheme
tags: []
status: publish
type: post
published: true
meta: {}
---
<p><a title="You are... Lisp" href="http://www.geeksexy.org/<sub>krc//pltest/lisp.html&#8221;&gt;You are&#8230; Lisp</a></p>


They also told me to paste this here.  <font size="+2">You are&#8230; Lisp!</font><br /><font size="-2">
<pre>           (define bottles
                         (lambda (n)
                           (cond ((= n 0) (display "No more bottles"))
                                 ((= n 1) (display "One bottle"))
                                 (else (display n) (display " bottles")))
                           (display " of beer")))

                       (define beer
                         (lambda (n)
                           (if (&gt; n 0)
                               (begin
                                 (bottles n) (display " on the wall") (newline)
                                 (bottles n) (newline)
                                 (display "Take one down, pass it around") (newline)
                                 (bottles (- n 1)) (display " on the wall") (newline)
                                 (newline)
                                 (beer (- n 1))))))

                       (beer 99)
</pre></font><br /><a href="http://www.cs.berkeley.edu/</sub>krc/pltest/pl.html&#8221; target=&#8221;_new&#8221;&gt;What programming language are you?</a>
