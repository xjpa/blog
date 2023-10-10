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
height: 500px;
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
  <div id="image-1" class="image" style="background-image:url('./photos/jetski.jpeg');"></div>
  <div id="image-2" class="image" style="background-image:url('./photos/some_place.jpg');"></div>
  <div id="image-3" class="image" style="background-image:url('./photos/field.jpeg');"></div>
	</div>

<p align="justify">
	<big><strong>Hello!</strong></big> I'm John, but my friends call me Ice
</p>
<p>I'm into complex systems: Software and Economics</p>
<p>Feel free to send emails at &lt;<code>j+p@johnamata.com</code>&gt;</p>
<p>1 Corinthians 13:11-12</p>
