---
layout: default
---

<div class="tags-expo">
  <div class="tags-expo-list">
    <p>Tags</p>
    <ul>
      {% assign all_posts = site.posts | concat: site.hacking | concat: site.python | concat: site.rand %}
      {% assign tag_items = "" %}

      {% for post in all_posts %}
        {% for tag in post.tags %}
          {% unless tag_items contains tag %}
            {% assign tag_items = tag_items | append: tag | append: "," %}
          {% endunless %}
        {% endfor %}
      {% endfor %}

      {% assign tags = tag_items | split: "," | sort %}

      {% for tag in tags %}
        <li><a href="#{{ tag | slugify }}" class="post-tag">{{ tag }}</a></li>
      {% endfor %}
    </ul>

  </div>
  <hr/>
  <div class="tags-expo-section">
    {% for tag in tags %}
      <h2 id="{{ tag | slugify }}">{{ tag }}</h2>
      <ul class="tags-expo-posts">
        {% for post in all_posts %}
          {% if post.tags contains tag %}
            <li>
              {{ post.date | date: "%Y-%m-%d" }}
              <a class="post-title" href="{{ site.baseurl }}{{ post.url }}">
                {{ post.title }}
              </a>
            </li>
          {% endif %}
        {% endfor %}
      </ul>
    {% endfor %}
  </div>
</div>
