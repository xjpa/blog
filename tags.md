---
layout: default
---

<style>
  .tags-expo {
    max-width: 800px;
    padding: 20px;
  }
  .tags-expo-list {
    margin-bottom: 20px;
  }
  .post-tag {
    display: inline-block;
    margin: 5px;
    padding: 5px 10px;
    background: #f0f0f0;
    border-radius: 3px;
    text-decoration: none;
    color: #333;
  }
  .post-tag:hover {
    background: #e0e0e0;
  }
  .tags-expo-section h2 {
    margin-top: 20px;
  }
  .tags-expo-posts {
    list-style: none;
    padding: 0;
  }
  .tags-expo-posts li {
    margin-bottom: 10px;
  }
  .post-title {
    text-decoration: none;
    color: #0066cc;
  }
  .post-title:hover {
    text-decoration: underline;
  }
  .filter-input {
    margin-bottom: 20px;
    padding: 10px;
    width: 100%;
    font-size: 16px; 
    box-sizing: border-box;
    border: 1px solid #ccc; 
    background-color: #E7DCD2;
  }
  .tag-link {
    display: inline-block;
    margin: 5px;
    padding: 5px 10px;
    background: #f0f0f0;
    border-radius: 3px;
    text-decoration: none;
    color: #333;
  }
  .tag-link:hover {
    background: #e0e0e0;
  }
</style>

<div class="tags-expo">
  <div class="tags-expo-list">
    <p>Tags</p>
    <div id="tagLinks">
      {% assign unique_tags = "" | split: "" %}

      {% for post in site.posts %}
        {% for tag in post.tags %}
          {% unless unique_tags contains tag %}
            {% assign unique_tags = unique_tags | push: tag %}
          {% endunless %}
        {% endfor %}
      {% endfor %}

      {% assign sorted_tags = unique_tags | sort %}

      {% for tag in sorted_tags %}
        <a href="#{{ tag | slugify }}" class="tag-link">{{ tag }}</a>
      {% endfor %}
    </div>

  </div>
  <p><sub>Note that sometimes I tag a blog post w/ several tags, e.g. <a href="/articles/2024/05/30/why-i-write.html">Why I Write</a> exists in <a href="/tags#meta">meta</a>, <a href="/tags#self">self</a>, and <a href="/tags#grind">grind</a></sub></p>
  <input type="text" id="postFilter" class="filter-input" placeholder="Search by blog title...">

  <div class="tags-expo-section">
    {% for tag in sorted_tags %}
      <h2 id="{{ tag | slugify }}">{{ tag }}</h2>
      <ul class="tags-expo-posts">
        {% for post in site.posts %}
          {% if post.tags contains tag %}
            <li class="post-item">
              <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
              <a class="post-title" href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
            </li>
          {% endif %}
        {% endfor %}
      </ul>
    {% endfor %}
  </div>
</div>

<script>
  document.getElementById('postFilter').addEventListener('input', function() {
    var filter = this.value.toLowerCase();
    var posts = document.querySelectorAll('.post-item');
    posts.forEach(function(post) {
      var title = post.querySelector('.post-title').textContent.toLowerCase();
      if (title.includes(filter)) {
        post.style.display = 'list-item';
      } else {
        post.style.display = 'none';
      }
    });

    var tags = document.querySelectorAll('.tags-expo-section h2');
    tags.forEach(function(tag) {
      var tagPosts = tag.nextElementSibling.querySelectorAll('.post-item');
      var hasVisiblePosts = Array.from(tagPosts).some(function(post) {
        return post.style.display === 'list-item';
      });
      tag.style.display = hasVisiblePosts ? 'block' : 'none';
    });
  });

  document.querySelectorAll('.tag-link').forEach(function(tagLink) {
    tagLink.addEventListener('click', function(event) {
      event.preventDefault();
      var targetId = this.getAttribute('href').substring(1);
      var targetElement = document.getElementById(targetId);
      window.scrollTo({
        top: targetElement.offsetTop,
        behavior: 'smooth'
      });
    });
  });
</script>
