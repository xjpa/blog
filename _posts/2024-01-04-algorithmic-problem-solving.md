---
layout: post
title: 'Algorithmic Problem Solving'
description: 'Grinding algorithmic problems as a quickie before breakfast'
category: articles
tags: [algorithms]
comments: true
---

Everyday for 100 days I'm going to start grinding 30 mins to max of 1 hour per day solving some algorithmic coding problems to practice C++. This post, continuously updated, will contain all the things I've learned from this grind.

<!-- more -->

I dont intend to spend more than an hour a day at this. Maybe 20-30 mins on average. As frankly, I don't see much value in spending that much time about algorithms. I've honestly never met a top engineer working on large scale P99.999+ systems who've grinded through hundreds of problems.

This is mostly a lazy exercise of mine to write some daily leisure code while keeping my mental gears moving, like playing chess in the morning. It's separate from my other algorithmic grinds, as I'm also grinding through some problems with Python at [the gym](https://github.com/xjpa/the-gym) and this series only tracks my C++ problem solving

<style>
.project-table {
    display: table;
    width: 100%;
    border-spacing: 5px;
}

.project-row {
    display: table-row;
}

.project-cell {
    display: table-cell;
    vertical-align: top;
}
</style>

<div class="project-table">
{% assign projects_posts = site.algorithms | sort: "date" | reverse %}
{% for post in projects_posts %}
    <div class="project-row">
        <div class="project-cell">{{ post.date | date: "%B %d, %Y" }}</div>
        <!-- <div class="project-cell">{{ post.date | date: "%Y-%m-%d" }}</div> -->
        <div class="project-cell"><a href="{{ site.baseurl }}{{ post.url | relative_url }}">{{ post.title }}</a></div>
        <div class="project-cell">{{ post.description }}</div>
    </div>
{% endfor %}
</div>
