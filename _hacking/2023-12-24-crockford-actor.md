---
layout: post
title: 'Crockford Actor'
description: 'basic implementation of the actor model in python'
category: articles
tags: [hacking, project-computation]
comments: true
---

Code: [github.com/xjpa/crockford-actor](https://github.com/xjpa/crockford-actor)

<!-- more -->

I'm implementing it based on the model described on this RacketCon talk by [Douglas Crockford](https://en.wikipedia.org/wiki/Douglas_Crockford):

[https://www.youtube.com/watch?v=vMDHpPN_p08](https://www.youtube.com/watch?v=vMDHpPN_p08)

<center>

<style type="text/css" rel="stylesheet">
.video-responsive{
    overflow:hidden;
    padding-bottom:56.25%;
    position:relative;
    height:0;
}
.video-responsive iframe{
    left:0;
    top:0;
    height:100%;
    width:100%;
    position:absolute;
}
</style>

<div class="video-responsive">
<iframe width="560" height="315" src="https://www.youtube.com/embed/vMDHpPN_p08?si=lSm18HZ4DIMClHJ6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
</center>

Based on the part at around 19:00 on the video, here's what an actor model system is:

- an actor is a program running in a single process in a machine

- an actor communicates with other actors only be message passing

- there is no sharing, even between actors in the same machine

- an actor can create new actors in its own machine

- every actor has a private address

- if you have an actor's private address, you can send messages to that actor

- messages can contain private addressses

- actors can have state, which can change based on received messages
