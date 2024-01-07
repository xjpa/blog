---
layout: default
title: Archives
---

<div class="listing">

<center>
<h1>Main Posts</h1>
</center>

<p>alternatively, to see all posts, here's a list sorted in <a href="{{ "/tags" | prepend: site.url }}">tags/categories</a></p>

<ul class="tags-box">

{% if site.posts != empty %}

{% for post in site.posts %}
{% if post.tags contains 'hacking' %}
{% continue %}
{% endif %}

{% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
{% unless year == this_year %}
{% assign year = this_year %}

<p><strong>{{ year }}</strong></p>
{% endunless %}
<time datetime="{{ post.date | date:"%Y-%m-%d" }}">
{{ post.date | date:"%Y-%m-%d" }}
</time>
<!-- to lowercase everything:
&raquo; <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title | capitalize }}</a><br />
-->
&raquo; <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><br />
{% endfor %}

{% else %}

<span>No posts</span>

{% endif %}

</ul>
</div>
<hr/>
<div style="display: flex; justify-content: center;">
  <img src="/assets/transparent-sign.png"> 
</div>
