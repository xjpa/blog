---
layout: post
title: 'Reworking the Frontend of My Site: Binary Trees Wont Save You Here'
description: ''
category: articles
tags: [webdev, performance, algorithms, mechanical-sympathy]
comments: true
---

I recently reworked the frontend of my boring personal page at [johnamata.com](https://johnamata.com/)

And look, I know what you're thinking. "Oh great, another kid got hold of some shiny new animation technique and decided to crap all over my browser's performance."

Now you aint wrong. But stick with me here, because this isn't your average, run-of-the-mill, "let's make the user's device catch fire" kind of web animation. I actually spent some tiny effort to give a damn about your CPU and memory

<!-- more -->

So let me quickly write a messy blog post to explain it, although chiefly it's because writing one might direct more traffic to my site: I need to boost the site so that `johnamata.com` is #1 when I search for my name on Google! Even some kid's facebook profile ranks over me 😭

Now cause I dont really have much time to write about all the other changes made and the git commits (that I squashed into big commits - these included tiny optimizations like scheduling animations), for the scope of this blog post I will focus on [this small commit](https://github.com/xjpa/personal-landing/commit/ac4a355bdc252aee767c36f9338809c1fd29f338) specifically for `background.js` which basically improved the average perf by >50% (average of Chrome Dev Tools [Performance Monitor](https://developer.chrome.com/docs/devtools/performance-monitor) Memory Graph for 30-60 seconds)

<center>
<img src="/photos/2024/reworked-the-website.png">
<figcaption>Trust me bro, it was 28 MB one time 😭 <br>JK, these tab info arent a good estimate - use dev tools!</figcaption>
</center>

## Caching

```javascript
const tileCache = {};
function generatePenroseTile(size, color) {
  const key = `${size}-${color}`;
  if (tileCache[key]) return tileCache[key];
  // ... tile generation code ...
  tileCache[key] = dataUrl;
  return dataUrl;
}
```

This right here? This is the difference between "my animation runs smoothly" and "my animation makes CPUs beg for mercy." Let's break it down:

- Memory Efficiency: we're not storing every single tile. We're storing unique combinations of size and color. It's like the Marie Kondo method of tile storage - if it doesn't spark joy (or hasn't been used before), we don't keep it
- Computation Savings: generate once, use many times. It's the "reduce, reuse, recycle" of the programming world. Your CPU will thank you for not making it redraw the same damn triangle fifty times
- String Keys: using `${size}-${color}` as the key makes it simple. It's like the perfect hash function, but without all the complexity that makes you want to headbutt your keyboard

This caching mechanism isn't just about saving CPU cycles. It's about understanding the nature of the beast we're dealing with. These tiles (I was planning on making them [penrose tiles](https://preshing.com/20110831/penrose-tiling-explained/) - maybe later), by their very nature, have a limited set of shapes and orientations. By caching, we're not just optimizing - we're leveraging the inherent properties of the system we're simulating

## Creating Layers Without Angering the Render Gods

Now, let's talk about creating these layers without making the DOM have an existential crisis:

```javascript
function createLayer(layerIndex) {
  const layer = document.createElement('div');
  // ... layer styling ...
  const fragment = document.createDocumentFragment();
  for (let i = 0; i < numberOfTiles; i++) {
    // ... tile creation ...
    fragment.appendChild(tile);
  }
  layer.appendChild(fragment);
  return layer;
}
```

Let's break it down:

- Document Fragments: it's like the staging area for your DOM elements. You're telling the browser, "Hey, I'm not done yet, don't go repainting everything"
- Batch DOM updates: by appending everything to the fragment first, then appending the fragment to the layer, you're essentially saying, "Here's all the changes at once." It's like ripping off a band-aid - painful, but quick
- Minimizing Reflows: every time you touch the DOM, the browser has to recalculate styles, layout, and repaint. This code says, "Let's do that once, not 30 times per layer." And just like that our browser's layout engine just breathed a sigh of relief

This approach isn't just about performance - it's about understanding how browsers work at a fundamental level. It's mechanical sympathy in action (more on what that means later). You're not fighting the browser's natural behavior; you're working with it

## CSS

```javascript
const styleSheet = document.createElement('style');
styleSheet.textContent = `
  @keyframes rotateTile {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }
`;
document.head.appendChild(styleSheet);
```

- Single Keyframe definition: instead of defining animations for each tile, we define it once
- Transform magic: using `transform: rotate()` instead of mucking about with top/left properties is like telling the browser, "Hey, you know that GPU you've got? Let's use it." It's kinda like hardware acceleration without explicitly asking for it
- Simplified Animation logic: by defining the animation once and reusing it, we're reducing the amount of unique data the browser needs to keep track of

This approach is more on having an understanding of how modern browsers handle animations. You're not just writing code; you're speaking the browser's language. You're saying, "I understand how you work, and I'm going to work with you, not against you." It's not some algorithmic optimization

## It's Mechanical Sympathy

Look, I get it. You spent four years (or more, no judgment here - college is fun) slaving away over textbooks, learning about Big O notation, red-black trees, and the intricacies of quicksort vs. mergesort. You emerged, blinking, into the sunlight, armed with the knowledge to conquer any algorithmic challenge thrown your way. And then you started working on web apps, and suddenly, few of that seemed to matter anymore

Welcome to the world of frontend development, where your fancy algorithms take a backseat to an entirely different kind of optimization

First, let's get one thing straight: the optimizations we've been discussing in our tile animation? They're not algorithmic optimizations in the classical computer science sense. They're what we call [mechanical sympathy](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.concept.mechanical-sympathy.en.html) optimizations

"But wait," I hear you cry, "what's the difference?" Glad you asked my hypothetical reader! (or maybe I really have a reader for this post)

1. Algorithmic optimizations: these are about improving the time or space complexity of your algorithm. It's about going from O(n^2) to O(n log n), or reducing your space usage from O(n) to O(1). It's the stuff of coding interviews and whiteboard exercises
2. Mechanical Sympathy optimizations: these are about understanding how your code interacts with the underlying system - in our case, the browser and the JavaScript engine. It's about working with the system, not against it 🤝

Our optimizations? They're firmly in the mechanical sympathy camp. We're not changing the fundamental algorithms (which are pretty simple to begin with). We're changing how we interact with the browser's rendering engine, the DOM, and the JavaScript runtime

## The Constant Time Conundrum: Why O(1) is King in Frontend Land

Now, here's where it gets interesting. In frontend development, we're often operating in what we might call "effective constant time" - or at least, that's what we're aiming for.
What do I mean by that? Well, let's break it down:

1. Render Performance: when you're animating something on screen, you have about 16.67ms to do all your work if you want to hit that silky smooth 60fps. Whether you have 10 elements or 1000, you still have the same time budget
2. User Interaction: when a user clicks a button, they expect an immediate response. Whether your app is managing 100 items or 10,000, that click better register real quick
3. Initial Load: users start getting antsy after about 3 seconds of load time. Whether you're loading a simple blog or a complex web app, you're racing against the same clock

See the pattern? In all these cases, we're not trying to optimize for better-than-linear time complexity. We're trying to optimize for consistent, predictable performance regardless of scale

So why doesn't traditional algorithmic optimization help much here? A few reasons:

1. Scale Isn't the Problem: most web apps aren't dealing with millions of elements in the DOM or running complex computations in the browser. The difference between O(n) and O(log n) often doesn't matter when n is small
2. The Bottleneck is elsewhere: the performance bottleneck in web apps is often in things like DOM manipulation, network requests, and rendering - not in your JavaScript computations
3. [Perceived Performance](https://en.wikipedia.org/wiki/Perceived_performance) matters more: users don't care if your algorithm is O(n) or O(1) - they care if the app feels fast and responsive

So what really matters in frontend optimization? IMO, here are the true heroes:

1. Batch DOM updates: like we did with our document fragments in the animation. This is about reducing the number of expensive DOM operations
2. Efficient Rendering: using things like transform for animations, as we did, to leverage GPU acceleration
3. Resource management: techniques like lazy loading, code splitting, and efficient asset loading
4. Memory management: avoiding memory leaks, using object pools, and being smart about garbage collection
5. Event Delegation and Throttling: managing user interactions efficiently

These are all about working with the browser, understanding its quirks and optimizing for its strengths. They're about constant factors, not algorithmic complexity

Now, don't get me wrong. Algorithmic knowledge is still valuable. There will always be cases where you need to optimize a complex computation or manage large datasets efficiently. But in the day-to-day trenches of frontend development, mechanical sympathy often trumps algorithmic wizardry

Understanding how the browser works, how JavaScript engines optimize code, how the event loop functions - these are the things that will often give you more bang for your buck in web performance

It's not about writing clever algorithms. It's about writing code that plays nice with the platform it's running on. It's about respecting the constraints of the web platform and working within them, not fighting against them

## Takeaway

So, what's the lesson here? Mechanical Sympathy. I was basically thinking of writing a post about it, but I kept on procrastinating until I worked on this tiny rework of my website.

My main takeaway is that even in frontend work, it's important to think of the platform. Learn how browsers work. Understand the DOM, the render pipeline, the JavaScript runtime. These are your real algorithms, your real data structures

Your CS degree isn't useless - far from it. The problem-solving skills, the ability to think abstractly about code, these are invaluable. But don't be surprised or disappointed when you find yourself spending more time thinking about browser quirks than balanced trees

In the end, the best optimization is the one that makes your app feel faster to the user. And in the world of web apps, that often means focusing on those constant time factors, on smoothing out the rough edges of browser performance, rather than shaving a few microseconds off your sorting algorithm

So the next time you're optimizing a web app, remember: your Big O might not be as important as your Big OMG-this-feels-faster-to-the-user. And that's okay. That's part of web development. Peace out
