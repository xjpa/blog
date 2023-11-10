---
layout: post
title: 'TreeCache'
description: 'simple in-memory NoSQL-like database'
category: articles
tags: [hacking]
comments: true
---

Today was one stormy afternoon, it had just began raining when I was reading a book called <a href="/bookshelf/ddia/">Designing Data Intensive Applications</a>. It got me into thinking about exploring some data structures and algorithms used in building databases. In particular I learned about B-Trees.

<!-- more -->

<img src="/photos/2023/b-tree.jpeg">

I wanted to know how it really works. As I had just gotten from doing some good cardio outside and I wanted to chill in my room for a bit, I thought why not use my downtime at my room to study? I'm gonna be in my room anyway for recovery. Might as well hit 2 birds with one stone, recover my body while improving my mind by building something. I thus opened VS Code and started writing some JavaScript code.

Thus we got, TreeCache, a toy in-memory NoSQL-like DB:

[https://github.com/xjpa/treecache](https://github.com/xjpa/treecache)

# Other things learned

- we can use hashtable to build an in-memory DB and mySQL does allow it for some indexing: [https://dev.mysql.com/doc/refman/8.0/en/memory-use.html](https://dev.mysql.com/doc/refman/8.0/en/memory-use.html)

- but it's poor for things like range queries such as the following:

```sql
SELECT *
FROM orders
WHERE order_date < '2023-01-01';

SELECT *
FROM sales
WHERE transaction_date BETWEEN '2023-01-01' AND '2023-08-31'
  AND amount BETWEEN 1000.00 AND 5000.00;
```

- range queries benefit more from data structures that maintain order like b-trees. Actually, range queires typically require ordered data as well. Meanwhile hashtables do not inherently maintain order of any keys

- b-trees are highly efficient and have o(logn) time complexity

- b-trees get complex when we're inserting something when the leaf node is full as we have to keep the tree balanced. when this happens we do splitting. Basically we take the middle item of a node to promote it to the parent node, then we create a new child node based on the remaining. If it's already at the parent/root node, and nothing to promote the middle to, then we just create a new node at the top.

> source: [https://condor.depaul.edu/ichu/csc383/notes/notes7/btree.html](https://condor.depaul.edu/ichu/csc383/notes/notes7/btree.html)
>
> If is node becomes "too full," it is necessary to perform a split operation. The split operation moves the median key of node x into its parent y where x is the ith child of y. A new node, z, is allocated, and all keys in x right of the median key are moved to z. The keys left of the median key remain in the original node x. The new node, z, becomes the child immediately to the right of the median key that was moved to the parent y, and the original node, x, becomes the child immediately to the left of the median key that was moved into the parent y.

That's a good project for today...
