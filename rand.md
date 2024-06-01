---
layout: default
title: Recommend
---

<h1 style="font-family: monospace;">rand()</h1>

These are my more candid random posts, the early ones <2024 are selected posts from my older blogs such as those at wordpress and blogger. They mostly contain some glimpses of my life, some of my travels, and random thoughts at the time. And so -- [BEWARE](https://en.wiktionary.org/wiki/abandon_hope_all_ye_who_enter_here).

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

<input type="text" id="searchInput" placeholder="Search">
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
{% assign results_posts = site.rand | sort: "date" | reverse %}
{% for post in results_posts %}
    <div class="posts-row">
        <div class="posts-cell">{{ post.date | date: "%B %d, %Y" }}</div>
        <!-- <div class="posts-cell">{{ post.date | date: "%Y-%m-%d" }}</div> -->
        <div class="posts-cell"><a href="{{ site.baseurl }}{{ post.url | relative_url }}">{{ post.title }}</a></div>
        <div class="posts-cell">{{ post.description }}</div>
    </div>
{% endfor %}
</div>

<img src="/photos/cropped-trip.jpg">
