---
layout: default
title: Me
---

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
        /* 2 columns for tablets */
        grid-template-columns: repeat(2, 1fr); 
    }
    .photo img {
        /* adjust height for smaller screens */
        height: 150px; 
    }
}

/*mobile phone responsiveness*/
@media (max-width: 480px) {
    .gallery {
        /* 1 column for mobile phones */
        grid-template-columns: 1fr; 
    }
    .photo img {
        /* height for mobile screens */
        height: 200px; 
    }
}

.terminal {
    /* dark gray style similar to iTerm's default background */
    background-color: #2d2d2d; 
    padding: 20px;
    font-family: "Menlo", "Monaco", "Consolas", "Courier New", monospace;
    /* white  */
    color: #fff; 
    border-radius: 5px;
}

.terminal-text {
    margin: 0;
}

.cursor {
    display: inline-block;
     /* white */
    background-color: #fff;
    width: 8px;
    animation: blink 1s step-start 0s infinite;
}

@keyframes blink {
    50% {
        background-color: transparent;
    }
}
</style>

<div class="terminal">
        <h1 class="terminal-text">$ ls /me<span class="cursor">|</span></h1>
    </div>

<p></p>

<div class="gallery">
    <!-- row 1-->
    <div class="photo photo">
        <img src="/photos/me/family.jpg">
        <p>Winter with the family = skiing break</p>
    </div>
    <div class="photo photo-middle">
        <img src="/photos/me/chess.jpeg">
        <p>Chess: 10 years to realize it's not for me</p>
    </div>
    <div class="photo photo-right">
        <img src="/photos/me/jetski.jpeg">
        <p>Dad got me into jetskis</p>
    </div>
    <!-- row 2-->
    <div class="photo photo-left">
        <img src="/photos/me/guns.jpg">
        <p>Dad also got me into guns when I was 13</p>
    </div>
    <div class="photo photo-middle">
        <img src="/photos/me/football.jpg">
        <p>High school is my football era</p>
    </div>
    <div class="photo photo-left">
        <img src="/photos/me/gang.jpg">
        <p>The Crew: I'm the 4th from the left</p>
    </div>
    <div class="photo photo-middle">
        <img src="/photos/me/mydoggo.jpg">
        <p>My doggo loves the beach</p>
    </div>
    <div class="photo photo-right">
        <img src="/photos/me/lost.jpg">
        <p>Travelling & getting lost is always fun</p>
    </div>
</div>

---
