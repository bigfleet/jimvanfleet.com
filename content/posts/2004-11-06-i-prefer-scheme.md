---
layout: post
title: I Prefer Scheme
tags:
- Personal
- Tech
status: publish
type: post
published: true
Date: 2004-11-06
---
An online quiz told me I was LISP.

They also told me to paste this here.

```
(define bottles
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
```
