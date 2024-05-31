---
layout: default
title: Archives
---

<div class="listing">

<center>
<h1>Archives</h1>
</center>

<p>The list below is for my polished blog posts — better written, yet curated opinions.</p>

<p>RAW THOUGHTS, visit <a href="{{ "/tags" | prepend: site.url }}">blog.johnamata.com/tags</a> to see ALL other writings on this blog, or <a href="/rand">/rand</a> to see my personal posts from my travels to fleeting  thoughts I may not agree with today.</p>

<input type="text" id="searchInput" placeholder="Search">

<p></p>

<div id="resultCount"></div>
<p></p>
<script>
//DOMContentLoaded event --> fires when html doc is loaded, doesnt wait for styles, images, frames to load
//more: https://developer.mozilla.org/en-US/docs/Web/API/Document/DOMContentLoaded_event
//moved updateSearch to this event listener to guarantee it gets access to all DOM elements

//did it as i added posts/result counting and my old script was executing before the entire DOM was fully constructed,
//so DOMContentLoaded basically delays the execution of your script until the moment the DOM is

document.addEventListener('DOMContentLoaded', function() {
var searchInput = document.getElementById('searchInput');
searchInput.addEventListener('keyup', updateSearch);
updateSearch();
function updateSearch() {
var searchQuery = searchInput.value.toLowerCase().split(' ');
var results = document.querySelectorAll('.posts-row');
var count = 0;
results.forEach(function(posts) {
var dateCell = posts.querySelectorAll('.posts-cell')[0];
var titleCell = posts.querySelectorAll('.posts-cell')[1];
var descriptionCell = posts.querySelectorAll('.posts-cell')[2];
var date = dateCell ? dateCell.textContent.toLowerCase() : '';
var title = titleCell ? titleCell.textContent.toLowerCase() : '';
var description = descriptionCell ? descriptionCell.textContent.toLowerCase() : '';

            var match = searchQuery.every(function(keyword) {
                return date.includes(keyword) || title.includes(keyword) || description.includes(keyword);
            });
            if (match) {
                posts.style.display = '';
                count++;
            } else {
                posts.style.display = 'none';
            }
        });
        var resultText = searchQuery.join('').length === 0 ? 'Total of ' : 'Showing ';
        document.getElementById('resultCount').textContent = resultText + count + ' results';
    }

});
</script>

<div class="posts-table">

{% assign results_posts = site.posts | sort: "date" | reverse %}
{% for post in results_posts %}

<div class="posts-row">
<div class="posts-cell">{{ post.date | date: "%B %d, %Y" }}</div>
<!-- <div class="posts-cell">{{ post.date | date: "%Y-%m-%d" }}</div> -->
<div class="posts-cell"><a href="{{ site.baseurl }}{{ post.url | relative_url }}">{{ post.title }}</a></div>
</div>
{% endfor %}

</div>

<style>
.table-table {
    display: table;
    width: 100%;
    border-spacing: 5px;
}

.table-row {
    display: table-row;
}

.table-cell {
    display: table-cell;
    vertical-align: top;
}
</style>

<style>
.posts-table {
    display: table;
    width: 100%;
    border-spacing: 5px;
}

.posts-row {
    display: table-row;
}

.posts-cell {
    display: table-cell;
    vertical-align: top;
}

#searchInput {
    width: 100%;
    padding: 10px; 
    font-size: 16px; 
    border: 1px solid #ccc; 
    background-color: #E7DCD2;
}
</style>

<hr/>
<div style="display: flex; justify-content: center;">
  <img src="/assets/transparent-sign.png"> 
</div>
