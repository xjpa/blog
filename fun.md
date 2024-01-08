---
layout: default
title: Fun
---

# `/fun`

<style>
.gallery {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

.photo {
background: #f8f8f8;
padding: 5px;
text-align: center;
overflow: hidden;
position: relative;
cursor: pointer;
transition: box-shadow 0.3s ease;
}

.photo img {
width: 100%;
height: 200px;
object-fit: cover;
transition: transform 0.3s ease;
}

.photo p {
margin: 10px 0 0;
font-size: 0.9em;
color: #333;
}

.photo:hover {
box-shadow: 0 8px 15px rgba(0,0,0,0.3);
}

.photo:hover img {
transform: scale(1.05);
}

.photo:nth-child(3n+1) {
border: 3px;
}
.photo:nth-child(3n+2) {
border: 3px;
}
.photo:nth-child(3n+3) {
border: 3px;
}

@media (max-width: 768px) {
.gallery {
grid-template-columns: repeat(2, 1fr); /_ 2 columns for tablets _/
}
.photo img {
height: 150px; /_ Adjust height for smaller screens _/
}
}

/_ Responsive adjustments for mobile phones _/
@media (max-width: 480px) {
.gallery {
grid-template-columns: 1fr; /_ 1 column for mobile phones _/
}
.photo img {
height: 200px; /_ Adjust height for mobile screens _/
}
}
</style>

<div class="gallery">
    <!-- row 1-->
    <div class="photo photo-left">
        <img src="/photos/fun/family.jpg">
        <p>Winter with the family = skiing break</p>
    </div>
    <div class="photo photo-middle">
        <img src="https://i.imgur.com/R7rVAri.jpg">
        <p>Chess: 10 years to realize it's not for me</p>
    </div>
    <div class="photo photo-middle">
        <img src="/photos/fun/jetski.jpeg">
        <p>Dad got me into jetskis</p>
    </div>
    <div class="photo photo-right">
        <img src="/photos/fun/football.jpg">
        <p>High school is my football era</p>
    </div>
    <!-- row 2-->
    <div class="photo photo-left">
        <img src="/photos/fun/gang.jpg">
        <p>With the boys</p>
    </div>
    <div class="photo photo-middle">
        <img src="/photos/fun/mydoggo.jpg">
        <p>My doggo loves the beach</p>
    </div>
    <div class="photo photo-right">
        <img src="/photos/fun/lost.jpg">
        <p>Travelling & getting lost is always fun</p>
    </div>
</div>

---
