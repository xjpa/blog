---
layout: default
title: How to Design Programs
---

## How to Design Programs, 2nd Edition

<a href="https://htdp.org/"><img src="/photos/books/htdp2.jpg" height ="300"></a>

This book is being recommended over other classics like Robert Martin's [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) as a better way to learn (systematic) "program design" while learning about programming "the right way." That... and because <a href="https://hn.algolia.com/?q=%22how+to+design+programs%22">all the shills at Hacker News</a> are posting and [writing comments about it](https://hn.algolia.com/?dateRange=all&page=0&prefix=false&query=%22how%20to%20design%20programs%22&sort=byDate&type=comment) several times a year about how it's the best book to learn computational thinking, is what got me to go through it.

## Code

[https://github.com/xjpa/htdp](https://github.com/xjpa/htdp)

## Notes

- <p>Fixed Size Data (<a href="/bookshelf/htdp2/fixed-size-data">link</a>)</p>

## Course Notes

- How to Code: Simple Data: (<a href="/bookshelf/htdp2/course/simple-data">link</a>)

- How to Code: Complex Data: (<a href="/bookshelf/htdp2/course/complex-data">link</a>)

## Racket Quirks

- <p>if statements in racket must have an else, just like in other languages like haskell. Java, Python, etc. the else is optional</p>

```racket
; style
(if condition
    then-expr
    else-expr)

;; example
; i had to put the "" as the else expression
(define (string-first string)
  (if (> (string-length string) 0)
      (substring string 0 1) ""))
```

- <p>in racket, cant use <code>=</code> to compare booleans as it's only used for numbers, thus i have to use <code>eq?</code></p>

```racket
;; with eq?
(define (==> sunny friday)
  (if (or (eq? sunny #false) (eq? friday #true))
      #true
      #false))

;; alternatively, with not
(define (==> sunny friday)
  (if (or (not sunny) friday)
      #true
      #false
  ))
```

<a href="/bookshelf">⬅️ back to bookshelf</a>
