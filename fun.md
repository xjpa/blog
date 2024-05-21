---
layout: default
title: Projects
---

<center><h1>Fun</h1>
<p>As a Man Playeth</p>
</center>

<div class="full-width-background">
  <div class="content-container">
    <h1>Table of Contents</h1>
    <div class="toc">
    <p><a href="#project1"><u>I</u> Operating System</a></p>
    </div>
  </div>
</div>

<h1></h1>

<div id="project1">
    <div class="project-container">
        <div class="project-description">
        <h1>I. starOS</h1>
            <p><i>May 21, 2024</i></p>
            <p>Stack: C, Assembly</p>
            <p>Links: <a href="https://github.com/xjpa/starOS">code</a>, <a href="#">blog</a></p>
            <p>Currently building an operating system from scratch, named after my doggo. Long term project. Likely will be refactored or rebuilt again from scratch multiple times in the future as I learn about better ways to approach operating systems development. The github repo will be more updated than this description, so go check out that one.</p>
        </div>
        <div class="project-screenshot">
            <img src="https://raw.githubusercontent.com/xjpa/starOS/main/hello.png">
        </div>
    </div>
    <div class="additional-details">
        </div>
</div>

<style>
.full-width-background {
  position: relative; 
  width: 100vw; 
  left: 50%;
  transform: translateX(-50%);
  background-color: #1A202C;
  color: white;
  font-family: Georgia, Arial;
  z-index: 1; 
  box-sizing: border-box; 
  text-shadow: none;
}

.content-container {
  width: 60%; 
  margin: 0 auto; 
  position: relative; 
  padding: 20px; 
  box-sizing: border-box; 
}

.toc {
  position: relative;
  color: white;
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: 20px;
  text-shadow: none;
}

.toc a {
  color: white;
  text-decoration: none;
  position: relative;
  z-index: 2;
}

.toc a:hover {
  color: yellow;
  text-decoration: none;
}

.project-container {
  display: flex;
  align-items: center; 
}

.project-description {
  flex: 2;
}

.project-screenshot {
  flex: 1; 
}
</style>

<div>
<hr>
<center>
<p>see <code>/<a href="/hacking">hacking</a></code> for random stuff </p>
</center>
</div>
