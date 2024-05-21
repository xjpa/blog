---
layout: default
title: Hacks
---

<h1>Hacking[0]</h1>

Just as each strike of the hammer hones the sword, it also forges the swordsmith, enhancing their sharpness and resilience. Thus let us create[1]. For when we create, we are also creating ourselves.

The following is a list of my personal, side projects I built on my journey to learn programming. Curiosity took me to web dev, graphics programming, AI, compilers, distributed systems, and more.

<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/511910196&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"></div>

<p></p>

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

<input type="text" id="searchInput" placeholder="Search (e.g. python, JS, web, graphics, distributed, visualization, django)">
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
        document.getElementById('resultCount').textContent = resultText + count + ' projects';
    }

});
</script>

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
- [1] For why I started this, see my blog post [If You're Depressed, Build Something](/articles/2024/03/18/build)
- [`photo`] [Steve Jobs](https://en.wikipedia.org/wiki/Steve_Jobs) and [Wozniak](https://en.wikipedia.org/wiki/Steve_Wozniak)
- [`code`] most of the code from my projects are at [github.com/xjpa](https://github.com/xjpa/)
