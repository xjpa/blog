---
layout: post
title: 'Distributed Locking Counter'
description: 'implementing the concept of distributed locking to a toy counter'
category: articles
tags: [hacking, python, project-distributed-systems]
comments: true
---

I woke up early today and felt good. One of my first thoughts was something I read last night, [distributed locking](https://martin.kleppmann.com/2016/02/08/how-to-do-distributed-locking.html), and I thought I want to implement a very toy version of one. So I made coffee and quickly whipped it out with a few minutes of coding.

<!-- more -->

<img src="/photos/2023/distributed-locking-morning.jpeg">

It is a very bare bones simulation: [https://github.com/xjpa/distributed-locking](https://github.com/xjpa/distributed-locking)

I guess I could work more on this later, make it really distributed instead of just simulating it.

## to run

start server

`$ python3 server.py`

open other terminals, start other clients making requests, like the ff makes 100 requests

`$ python3 client.py 100`

## screenshot

client terminals will be updated concurrently, see screenshot:

<img src="https://raw.githubusercontent.com/xjpa/distributed-locking/main/screenshot.jpg">

## delays

their updates are delayed because of the `time.sleep(0.1)` call which i added for rate limiting and reduce resources being hogged.

i'm using `http.server` which is single threaded based on their source code here [https://github.com/python/cpython/blob/3.11/Lib/http/server.py](https://github.com/python/cpython/blob/3.11/Lib/http/server.py) where it builds upon socketserver, looking at their code, there doesnt seem to be a pattern where each incoming request has a new thread getting spawned to handle it. thus have to limit the requests.

as well as to visually demo it better and "mimic" real world scenarios

## distributed locking

it's a simple version of distributed locking, made on a quick friday morning minutes after waking up cause i got bored and curious from something i read last night. it's very simple, one central server that manages the lock, in real life it's a cluster of servers using some consensus algorithm to decide which gets lock

this simple version demos distributed locking in a simple setup of multiple client nodes accessing a shared resource which in this case is the counter that is managed by the server to ensure sequential access
