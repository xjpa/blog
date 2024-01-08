---
layout: default
title: Fun
---

# FUN

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

/* dynamically changing styles for each photo */
/* blue border for every 3rd photo starting from the 1st */
.photo:nth-child(3n+1) {
    border: 3px solid #3498db; 
}
/* red border for every 3rd photo starting from the 2nd */
.photo:nth-child(3n+2) {
    border: 3px solid #e74c3c; 
}
/* green border for every 3rd photo starting from the 3rd */
.photo:nth-child(3n+3) {
    border: 3px solid #2ecc71; 
}
</style>

<div class="gallery">
    <!-- row 1-->
    <div class="photo photo-left">
        <img src="/photos/fun/family.jpg" alt="Photo 1">
        <p>Winter with the family = skiing</p>
    </div>
    <div class="photo photo-middle">
        <img src="/photos/fun/jetski.jpeg" alt="Photo 2">
        <p>Dad got me into jetskis</p>
    </div>
    <div class="photo photo-right">
        <img src="/photos/fun/football.jpg" alt="Photo 3">
        <p>Was in the football team in high school</p>
    </div>
    <!-- row 2-->
    <div class="photo photo-left">
        <img src="/photos/fun/gang.jpg" alt="Photo 1">
        <p>With the boys</p>
    </div>
    <div class="photo photo-middle">
        <img src="/photos/fun/mydoggo.jpg" alt="Photo 2">
        <p>Doggo</p>
    </div>
    <div class="photo photo-right">
        <img src="/photos/fun/lost.jpg" alt="Photo 2">
        <p>Into travelling and getting lost</p>
    </div>
</div>
