---
layout: default
title: Designing Data Intensive Applications
---

## Designing Data Intensive Applications aka DDIA (2017)

<img src="/photos/books/ddia.jpeg" height ="300">

Going through this book thanks to a class from my school

Here's a pic of my old copy, lol the front got weathered down so bad, will order a new one later

<img src="https://xjpa-assets-2023.netlify.app/pics/ddia/ddia-book.jpeg">

It's an extremely dense book packed with content, and topics that will leave you asking for more. As you could see on my photo below, I like to write down questions to ask after I read a page. I'd then google them later and go on a rabbit hole.

<img src="https://xjpa-assets-2023.netlify.app/pics/ddia/ddia-preview.jpeg">

The first time I came across the book, I thought it was too basic. I thought this book is recommended for system design, but where's the part of the book that tells me how to really design a system? It seemed so shallow. But sometime later I've made some smart friends, staff engineer level and above working on critical services at top tech that are still learning from this book after their n-th reading of it. So it made me curious and decided to start reading this book again in the end of 2023. And looking at the book now with eyes that have more experience, it is mindblowing.

That said, the book is kind of outdated now. It was published in 2017. Writing this now in December 24, 2023, many changes have gone on since then that are incompatible with what was written in the book. Such as off the top of my head, B-trees have now closed the gap with LSMs in write perf in modern storage systems leading to new DBs shaping the field like duckDB and clickhouse, Kafka no longer needs zookeeper as it now has KRaft. There are also many topics that were barely covered then but are now more relevant today like mixed workload of OLTP and OLAP and today's rise of OLAP.

Perhaps when Martin Kleppmann publishes a new version of DDIA, as [he says on x that he's writing a new version](https://x.com/martinkl/status/1551632043984961543), I'll be writing separate notes for it. But for now, I'll continue reading this version of DDIA. Most of it is still highly relevant, and the fundamentals dont change.

## Notes

## Essentials

Notes: (<a href="/bookshelf/ddia/chapter-1">link</a>)

Basically a concise cheatsheet on what I think are the most important to review

## Chapter 1 - Reliable, Scalable, and Maintainable Applications

Notes: (<a href="/bookshelf/ddia/chapter-1">link</a>)

## Chapter 2 - Data Models and Query Languages

Notes: (<a href="/bookshelf/ddia/chapter-2">link</a>)

<a href="/bookshelf">⬅️ back to bookshelf</a>
