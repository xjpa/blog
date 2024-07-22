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

<style>
.custom-audio-player {
  display: flex;
  align-items: center;
  background-color: #E7DCD2;
  padding: 10px;
  border-radius: 25px;
  width: 280px;
  font-family: Arial, sans-serif;
}

.play-btn {
  background-color: #333;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  margin-right: 10px;
  position: relative;
  overflow: hidden;
}

.play-btn::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: conic-gradient(from 0deg, black, white);
  opacity: 0.3;
}

.play-btn.rolling::before {
  animation: roll 2s linear infinite;
}

@keyframes roll {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.play-icon, .pause-icon {
  position: relative;
  z-index: 1;
}

.play-icon {
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 10px 0 10px 17px;
  border-color: transparent transparent transparent #E7DCD2;
}

.pause-icon {
  width: 17px;
  height: 17px;
  display: flex;
  justify-content: space-between;
}

.pause-icon::before,
.pause-icon::after {
  content: "";
  width: 6px;
  height: 17px;
  background-color: #E7DCD2;
}

.progress-container {
  flex-grow: 1;
  background-color: white;
  height: 5px;
  border-radius: 5px;
  cursor: pointer;
  overflow: hidden;
}

.progress {
  background-color: #555;
  height: 100%;
  width: 0%;
}

.time {
  font-size: 12px;
  margin-left: 10px;
  min-width: 70px;
  text-align: right;
}
</style>

<div class="custom-audio-player">
  <button class="play-btn" id="playBtn">
    <div class="play-icon"></div>
  </button>
  <div class="progress-container" id="progressContainer">
    <div class="progress" id="progress"></div>
  </div>
  <span class="time" id="time">0:00 / 0:00</span>
</div>

<audio id="audio" src="https://xjpa-assets-2023.netlify.app/music/iron_lung.mp3"></audio>

<script>
document.addEventListener('DOMContentLoaded', () => {
  const audio = document.getElementById('audio');
  const playBtn = document.getElementById('playBtn');
  const progressContainer = document.getElementById('progressContainer');
  const progress = document.getElementById('progress');
  const time = document.getElementById('time');

  function togglePlay() {
    if (audio.paused) {
      audio.play();
      playBtn.innerHTML = '<div class="pause-icon"></div>';
      playBtn.classList.add('rolling');
    } else {
      audio.pause();
      playBtn.innerHTML = '<div class="play-icon"></div>';
      playBtn.classList.remove('rolling');
    }
  }

  function updateProgress() {
    const { currentTime, duration } = audio;
    const progressPercent = (currentTime / duration) * 100;
    progress.style.width = `${progressPercent}%`;
    
    const currentMinutes = Math.floor(currentTime / 60);
    const currentSeconds = Math.floor(currentTime % 60);
    const durationMinutes = Math.floor(duration / 60);
    const durationSeconds = Math.floor(duration % 60);
    
    time.textContent = `${currentMinutes}:${currentSeconds.toString().padStart(2, '0')} / ${durationMinutes}:${durationSeconds.toString().padStart(2, '0')}`;
  }

  function setProgress(e) {
    const width = this.clientWidth;
    const clickX = e.offsetX;
    const duration = audio.duration;
    audio.currentTime = (clickX / width) * duration;
  }

  playBtn.addEventListener('click', togglePlay);
  audio.addEventListener('timeupdate', updateProgress);
  progressContainer.addEventListener('click', setProgress);

  audio.addEventListener('loadedmetadata', () => {
    const { duration } = audio;
    const minutes = Math.floor(duration / 60);
    const seconds = Math.floor(duration % 60);
    time.textContent = `0:00 / ${minutes}:${seconds.toString().padStart(2, '0')}`;
  });

  audio.addEventListener('ended', () => {
    playBtn.innerHTML = '<div class="play-icon"></div>';
    playBtn.classList.remove('rolling');
  });
});
</script>

<p></p>

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
<p>tech: <a href="/tags#systems" target="_blank">systems</a>, <a href="/tags#computer-graphics" target="_blank">graphics</a>, <a href="/tags#data-stores" target="_blank">data stores</a>, <a href="/tags#webdev" target="_blank">web</a>, <a href="/tags#language-design" target="_blank">language design</a>, <a href="/tags#ai" target="_blank">AI</a></p>
<p>i started this blog because <a href="/articles/2024/05/30/why-i-write" target="_blank">writing makes you more curious</a></p>
<p>feel free to send emails at &lt;<code id="myEmail" onclick="changeEmail()">click to view email</code>&gt;</p>

<script>
  //shift of 4
function changeEmail() {
  document.getElementById('myEmail').innerHTML = decryptCaesarCipher(
    'n@nslreqexe.gsq',
    4
  );
}
function decryptCaesarCipher(str, shift) {
  shift = ((shift % 26) + 26) % 26;
  let result = '';
  for (let i = 0; i < str.length; i++) {
    let charCode = str.charCodeAt(i);
    if (charCode >= 65 && charCode <= 90) {
      let letterValue = charCode - 65;
      letterValue = (letterValue - shift + 26) % 26;
      charCode = letterValue + 65;
    } else if (charCode >= 97 && charCode <= 122) {
      let letterValue = charCode - 97;
      letterValue = (letterValue - shift + 26) % 26;
      charCode = letterValue + 97;
    }
    result += String.fromCharCode(charCode);
  }
  return result;
}

  </script>
