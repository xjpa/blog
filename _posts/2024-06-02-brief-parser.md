---
layout: post
title: 'Parsers, briefly.'
description: ''
category: articles
tags: [language-design]
comments: true
---

Five days ago there was a post on parsers at a forum I was in that went:

◉ How to implement a parser?

<!-- more -->

Now I dont know much about parsers... so, let's talk about parsers 💀

After all it gives me a good excuse to learn it too

So after some moments of brief studying...

Basically, a parser takes a stream of data and turns it into a structured format, often an Abstract Syntax Tree (AST). This stream of data is usually a series of tokens—tiny chunks of information tagged with what they represent in the language

Let's say we're working with a tiny script written in a simple language, it's JS-like:

```
let x = 5;
if (x > 3) {
    x = x + 1;
}
```

First, we lex (tokenize) this script

Lexing is basically just breaking the script into tokens like so:

```
let: KEYWORD
x: IDENTIFIER
=: OPERATOR
5: NUMBER
;: DELIMITER
if: KEYWORD
(: DELIMITER
x: IDENTIFIER
>: OPERATOR
3: NUMBER
): DELIMITER
{: DELIMITER
x: IDENTIFIER
=: OPERATOR
x: IDENTIFIER
+: OPERATOR
1: NUMBER
;: DELIMITER
}: DELIMITER
```

Next, the parser comes into play. It takes these tokens and builds a data structure, usually an AST. Parsers do this by looking at tokens, figuring out what they represent, and recursively building the structure

Let's see how this works with our `if` statement

```
if (x > 3) {
    x = x + 1;
}
```

Step 1 - Recognizes `if`

- The parser sees `if` and starts an IfStatement node
- **Recursive Call**: it calls a function to parse the condition

Step 2 - Parsing the condition

- Inside the function for parsing conditions, the parser sees `(` and calls another function to parse the expression inside
- **Recursive Call**: it calls a function to parse `x > 3`

Step 3 - Parsing the expression `x > 3`

- Inside the function for parsing expressions, the parser sees `x` and calls a function to parse an identifier
- **Recursive Call**: it calls a function to parse `x` as an identifier
- Then it sees `>` and continues parsing
- It sees `3` and calls a function to parse a number
- **Recursive Call**: it calls a function to parse `3` as a number
- It combines these into a BinaryExpression node and returns it -- I name it BinaryExpression as its just two operands and one operator, it's not a formal definitive thing, there's probably a more precise name for it

Step 4 - Parsing the body

- After the condition is parsed, the parser expects `{` and calls another function to parse the block of code
- **Recursive Call**: it calls a function to parse the block

Step 5 - Parsing the block `x = x + 1;`

- Inside the block, it sees `x = x + 1;` which it identifies as a statement
- **Recursive Call**: it calls a function to parse `x = x + 1`
- This function further breaks down the assignment into smaller parts and calls functions to handle each part recursively

After all of these, you got an AST that would look similar to this

```
IfStatement {
    condition: BinaryExpression {
        left: Identifier { name: x },
        operator: >,
        right: Number { value: 3 }
    },
    body: Block {
        statements: [
            Assignment {
                identifier: Identifier { name: x },
                value: BinaryExpression {
                    left: Identifier { name: x },
                    operator: +,
                    right: Number { value: 1 }
                }
            }
        ]
    }
}
```

And that's pretty much it I guess

The AST can then be used for whatever you need—interpreting the code, compiling it, or anything else

Parsers can get pretty complex, especially with different parsing techniques out there (like LL(1) or LR parsers), but at their core, they all break down a stream of tokens into a structured format. This blog post, the parser described is recursive descent, implemented LL(1) (see addendum). It's all about recognizing patterns and building a corresponding structure

### Addendum

I have a python implementation of the parser described here on my github at:

[github.com/xjpa/recursive-descent-parser](https://github.com/xjpa/recursive-descent-parser)

It parses the sample script above including the `let x = 5;` and prints a rudimentary visualization of the AST tree
