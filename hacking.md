---
layout: default
title: Hacks
---

<h1>Hacking[0]</h1>

Just as each strike of the hammer hones the sword, it also forges the swordsmith, enhancing their sharpness and resilience. Thus let us create[1]. For when we create, we are also creating ourselves.

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
{% assign projects_posts = site.hacking | sort: "date" | reverse %}
{% for post in projects_posts %}
    <div class="project-row">
        <div class="project-cell">{{ post.date | date: "%B %d, %Y" }}</div>
        <!-- <div class="project-cell">{{ post.date | date: "%Y-%m-%d" }}</div> -->
        <div class="project-cell"><a href="{{ site.baseurl }}{{ post.url | relative_url }}">{{ post.title }}</a></div>
        <div class="project-cell">{{ post.description }}</div>
    </div>
{% endfor %}
</div>

<p></p>

<figure>
<img src="/photos/Jobs-and-Woz.webp">
</figure>

- [0] See Paul Graham's [The Word "Hacker"](https://archive.is/9MloV)
- [1] For why I started this, see my blog post [If You're Depressed, Build Something](/articles/2023/08/16/build)
- [`photo`] steve jobs and wozniak
