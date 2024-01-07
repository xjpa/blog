---
layout: post
title: 'Elements of Web Engineering'
description: 'The quest to become hardcore'
category: articles
tags: [web]
comments: true
---

I'm learning JS stack web development, and this post will be a complete collection of links towards my notes from learning the basics of HTML to backend engineering.

[<img src="/photos/2023/tower-of-babel.jpeg">](<https://en.wikipedia.org/wiki/The_Tower_of_Babel_(Bruegel)>)

<!-- more -->

Like all posts on this blog, this is more to serve as my personal wiki, my second brain. So if you somehow stumbled upon this website, forgive my formatting of the notes - although I am sometimes using this as well as an exercise to get better in writing and technical communication.

# The Journey

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
#searchInput {
    width: 100%;
    padding: 10px; 
    font-size: 16px; 
    border: 1px solid #ccc; 
}
</style>
<input type="text" id="searchInput" placeholder="Search posts...">
<div id="resultCount"></div>
<p></p>
<script>
//DOMContentLoaded event --> fires when html doc is loaded, doesnt wait for styles, images, frames to load
//more: https://developer.mozilla.org/en-US/docs/Web/API/Document/DOMContentLoaded_event
//moved updateSearch to this event listener to guarantee it gets access to all DOM elements

//did it as i added project/result counting and my old script was executing before the entire DOM was fully constructed,
//so DOMContentLoaded basically delays the execution of your script until the moment the DOM is

document.addEventListener('DOMContentLoaded', function() {
var searchInput = document.getElementById('searchInput');
searchInput.addEventListener('keyup', updateSearch);
updateSearch();
function updateSearch() {
var searchQuery = searchInput.value.toLowerCase().split(' ');
var projects = document.querySelectorAll('.project-row');
var count = 0;
projects.forEach(function(project) {
var dateCell = project.querySelectorAll('.project-cell')[0];
var titleCell = project.querySelectorAll('.project-cell')[1];
var descriptionCell = project.querySelectorAll('.project-cell')[2];
var date = dateCell ? dateCell.textContent.toLowerCase() : '';
var title = titleCell ? titleCell.textContent.toLowerCase() : '';
var description = descriptionCell ? descriptionCell.textContent.toLowerCase() : '';

            var match = searchQuery.every(function(keyword) {
                return date.includes(keyword) || title.includes(keyword) || description.includes(keyword);
            });
            if (match) {
                project.style.display = '';
                count++;
            } else {
                project.style.display = 'none';
            }
        });
        var resultText = searchQuery.join('').length === 0 ? 'Total of ' : 'Showing ';
        document.getElementById('resultCount').textContent = resultText + count + ' posts';
    }

});
</script>

<div class="project-table">
{% assign projects_posts = site.web | sort: "date" | reverse %}
{% for post in projects_posts %}
    <div class="project-row">
        <div class="project-cell">{{ post.date | date: "%B %d, %Y" }}</div>
        <!-- <div class="project-cell">{{ post.date | date: "%Y-%m-%d" }}</div> -->
        <div class="project-cell"><a href="{{ site.baseurl }}{{ post.url | relative_url }}">{{ post.title }}</a></div>
        <div class="project-cell">{{ post.description }}</div>
    </div>
{% endfor %}
</div>
