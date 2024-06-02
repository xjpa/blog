---
layout: default
title: About John
---

<head>
<style>

body {
display: inline;
}
div#image-container {
height: 530px;
width: 50%;
}
div.image {
background-size: cover;
background-position: center;
background-repeat: no-repeat;
height: 100%;
width: 100%;
display: none;
}
.encircle {
border-radius: 50%;
border: 1px solid black;
padding: 6px;
display: inline;
}

</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
<script>
$(document).ready(function () {
  let i = 1;
  let total = 4;
  setInterval(function () {
    changeImage(i++ % 4);
  }, 3000);
});

function changeImage(i) {
$('.image').hide();
$('#image-' + i).show();
}
</script>

</head>
<audio controls>
  <source src="https://xjpa-assets-2023.netlify.app/music/iron_lung.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>
<div id="image-container">
  <div id="image-0" class="image" style="background-image:url('./photos/skiface.jpg'); display: block;"></div>
  <div id="image-1" class="image" style="background-image:url('./photos/me-101.jpg');"></div>
  <div id="image-2" class="image" style="background-image:url('./photos/field.jpeg');"></div>
  <div id="image-3" class="image" style="background-image:url('./photos/gundam.jpg');"></div>
	</div>

<p align="justify">
	  <big><strong>Hello!</strong></big> I'm <big><span style="font-family: 'Averia Serif Libre', serif;">John</span></big> but my friends call me Ice 🧊 
</p>
<p><a href="https://www.theregister.com/2022/11/16/musk_twitter_ultimatum/" target="_blank">hardcore</a>, <a href="https://web.archive.org/web/20231020192708/https://www.paulgraham.com/gba.html" target="_blank">hacker</a> learning to be <a href="https://steve-yegge.blogspot.com/2008/06/done-and-gets-things-smart.html" target="_blank">done and get things smart</a></p>
<p>tech: <a href="/tags#systems" target="_blank">systems</a>, <a href="/tags#computer-graphics" target="_blank">graphics</a>, <a href="/tags#data-stores" target="_blank">data stores</a>, <a href="/tags#language-design" target="_blank">language design</a>, and <a href="/tags#ai" target="_blank">AI</a></p>
<p>i started this blog because <a href="/articles/2024/05/30/why-i-write" target="_blank">writing makes you more curious</a></p>
<p>feel free to send emails at &lt;<code>j+p@johnamata.com</code>&gt;</p>
