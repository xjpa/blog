---
layout: post
title: 'Gladiator Portfolio'
description: 'building an infinite terrain generator for my portfolio site'
category: articles
tags: [hacking, javascript]
comments: true
---

Just finished watching the film Gladiator last midnight. I think I've watched it 100 times in my life so far. It got me the idea to build my personal website inspired by that extremely satisfying Gladiator ending with a sunset into the mountains. One thing led to another and holy shit it's 06:04 AM.

<!-- more -->
<center>

<style type="text/css" rel="stylesheet">
.video-responsive{
    overflow:hidden;
    padding-bottom:56.25%;
    position:relative;
    height:0;
}
.video-responsive iframe{
    left:0;
    top:0;
    height:100%;
    width:100%;
    position:absolute;
}
</style>

<div class="video-responsive">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/NBE-uBgtINg?si=NRPBYwn6YpwF96HT" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
</center>

5 hours of hacking! I didnt have a design in mind when I began. So I spent 5 hours straight coding and switching between designs until I eventually settled into a minimal-wiry looking flight over the mountains.

Spent hours hacking and learning this library called ThreeJS and learning CSS --- I really need to learn it seriously sometime. As well as learning a bunch of random-looking (yet consistent enough) "mountain" generation algorithms. I didnt have a single idea how to approach this, computer graphics isnt something I know things about. But I picked things up as I go.

Then had to work with clouds, and realised I also need to have a "sun" or a source of light for the clouds. Then I had to figure out how to make the clouds look more like clouds, and after experimenting with various styles, I instead opted for a minecraft look as it feels so refreshing to have them "slap" the screen/user like seriously bro these are so fluffy. I then made the clouds more like particles. It was well, but then I had to figure out out how to make it look more like clouds, that is to group these particles a bit more together to form clouds.

Figure out this, figure out that, etc. Such is the nature of hacking.

For example, the cloud code, I made comments so you can grok it:

```javascript
function createClouds() {
  const particlesPerCloud = 500;
  const coresPerCloud = 3;
  const particlesPerCore = particlesPerCloud / coresPerCloud;

  // Basically this one generates 30 clouds where cloudGeometry is created and stores the
  // positional data for every particle in the cloud.
  for (let i = 0; i < 30; i++) {
    const cloudGeometry = new THREE.BufferGeometry();
    // This is to hold the individual position of the cloud particless
    const vertices = [];

    // Core creation loop
    for (let core = 0; core < coresPerCloud; core++) {
      // X, Y, Z represent the central point of the cloud's core
      const coreX = (Math.random() - 0.5) * 10;
      const coreY = (Math.random() - 0.5) * 10;
      const coreZ = (Math.random() - 0.5) * 10;

      // This loop determines the position of each particle around a core
      for (let j = 0; j < particlesPerCore; j++) {
        // Distribute particles around the core using some variance
        const variance = 3; // Adjust for how spread out particles should be around the core
        // Calculation:  x, y, and z values are calculated using the core's position
        // and random variance. This is to ensure that the particles are scattered
        // around the core in a random but limited manner.
        const x = coreX + (Math.random() - 0.5) * variance;
        const y = coreY + (Math.random() - 0.5) * variance;
        const z = coreZ + (Math.random() - 0.5) * variance;

        vertices.push(x, y, z);
      }
    }

    // Calculated vertices above are now set to the cloud's geometry
    cloudGeometry.setAttribute(
      'position',
      new THREE.Float32BufferAttribute(vertices, 3)
    );

    // Cloud Material and mesh creation
    const cloudMaterial = new THREE.PointsMaterial({
      color: 0xffffff, // define with a white colour
      size: 0.5,
      map: cloudTexture,
      transparent: true,
      opacity: 0.8,
      depthWrite: false,
    });

    const cloud = new THREE.Points(cloudGeometry, cloudMaterial);

    // The cloud's position is randomized within a certain bound
    cloud.position.x = Math.random() * 60 - 30;
    cloud.position.y = Math.random() * 10 + 15;
    cloud.position.z = Math.random() * 40 - 50;

    // Finally we add the clouds to the scene
    scene.add(cloud);
    // And store em in the cloud's array for animation updates
    // and optimization like say I was also thinking of recycling
    // the clouds to the back of the scene to give an
    // illusion of an endless flow of clouds
    clouds.push(cloud);
  }
}
```

Speaking of the last point of repositioning clouds, I was actually thinking of such an optimization. Basically creating and destroying objects frequently can be a costly operation, especially in JS where object destruction triggers [garbage collection](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_management).

This process can cause performance hitches or stuttering in animations. By recycling clouds, we'll be reusing existing objects instead of constantly creating and destroying old ones.

This is actually a design pattern:

- [https://en.wikipedia.org/wiki/Object_pool_pattern](https://en.wikipedia.org/wiki/Object_pool_pattern).

- [https://learn.unity.com/tutorial/introduction-to-object-pooling](https://learn.unity.com/tutorial/introduction-to-object-pooling)

There were a number of performance optimizations made throughout the code, like say. Object pooling for clouds. Object pooling for terrain as well

```javascript
if (terrain.position.z > camera.position.z + terrainLength) {
  scene.remove(terrain);
  terrains.shift();
  createTerrain(terrains[terrains.length - 1].position.z - terrainLength);
}
```

And several more quick hacks like preloading and efficient lighting with ambient and directional light for better resource management.

It was fun that I didnt even realise it was 6 AM.

I actually added a sun and shadows, but i thought it could be too computationally intensive for lower end devices, so I just stuck with being minimal. This is the "v1"

<img src="https://raw.githubusercontent.com/xjpa/gladiator-mountains-portfolio/main/screenshot.jpeg">

But anyway it's alright, the site's done. The 6:04 AM screenshot:

<img src="https://xjpa.github.io/blog-assets-2023/pics/2023-09-22-gladiator.jpg">

I like it. It's minimal and I guess I could say hacker-ish. Algorithmic-like. I guess I could add a camera control for the user, to make it more interactive but I decided to keep it minimal.

Anyway that is the one deployed to [johnamata.com](https://johnamata.com/), though I made a couple edits here and there. Take a flight from the heavens over the dawning of a new day, [now we are free](https://www.youtube.com/watch?v=-yOZEiHLuVU):

<video controls ="" width="100%" src="https://xjpa.github.io/blog-assets-2023/videos/gladiator-site.mp4" type='video/mp4'>
</video>

Here is a version with more features:

[https://github.com/xjpa/gladiator-mountains-portfolio](https://github.com/xjpa/gladiator-mountains-portfolio)

<img src="https://raw.githubusercontent.com/xjpa/gladiator-mountains-portfolio/main/screenshot2.jpeg">

On that version I added back the sun. I created a shadow system, corona effect, etc.I created a sky. I added colours to depict the beaches, shallow waters, marshes, sand dunes, snow-capped mountains. There's a bunch more that I'm forgetting.

The rendering method for the terrain generation has changed as well. I decided to stitch vertices together, calling it a "segmented terrain" to reduce any gaps:

```javascript
function createSegmentedTerrains(zPosition) {
  const totalLength = terrainLength * 2; // Double the terrain length
  const geometry = new THREE.PlaneGeometry(
    terrainWidth,
    totalLength,
    terrainWidth,
    totalLength
  );
  geometry.rotateX(-Math.PI / 2);

  // Now, cut this terrain into two segments:
  const firstHalfGeom = geometry.clone();
  firstHalfGeom.scale(1, 0.5, 1);
  const secondHalfGeom = geometry.clone();
  secondHalfGeom.scale(1, 0.5, 1);
  secondHalfGeom.translate(0, -terrainLength / 2, 0);

  const material = new THREE.MeshStandardMaterial({
    vertexColors: true,
    side: THREE.DoubleSide,
  });

  const firstTerrain = new THREE.Mesh(firstHalfGeom, material);
  firstTerrain.position.z = zPosition;
  const secondTerrain = new THREE.Mesh(secondHalfGeom, material);
  secondTerrain.position.z = zPosition - terrainLength;

  scene.add(firstTerrain);
  scene.add(secondTerrain);
  terrains.push(firstTerrain, secondTerrain);
}
```

It's very different from the terrain rendering code on my main site (johnamata.com) as well as the other version [I made](https://github.com/xjpa/gladiator-mountains-portfolio/blob/main/render-v1.js) (the v1 screenshot shown earlier). Basically it accomplishes these things

Step 1: Larger Terrain Creation

- We created a terrain that is twice as long.

- Generate noise values for this terrain.

- Segment this terrain into two: The first half and the second half.

- Keep the second half as a buffer. When the first half has moved past the camera view, introduce the second half to the scene, and generate a new terrain (again twice as long) for further segments.

Step 2: Segmentation

- <p>By doing this, we ensure that the edges of our segmented terrains always match because they are derived from a single larger terrain.</p>

But there's a potential issue with iterating through the terrains list while modifying it. I'm looping over every terrain and shifting elements out of it within the loop, which can lead to unexpected behavior.

I think a safe way to handle it would be to separate the movement logic from the removal and creation logic, avoid the pitfalls of modifying a list while iterating over it. This ensures a more consistent and predictable behavior.

```javascript
// move terrains
for (let terrain of terrains) {
  terrain.position.z += terrainMoveSpeed;
}

// check for first pair of terrains to see if they should be replaced
if (terrains[0].position.z > camera.position.z + terrainLength) {
  scene.remove(terrains[0]);
  scene.remove(terrains[1]);
  terrains.shift();
  terrains.shift();

  // replace the removed terrains with a new pair at the end
  createSegmentedTerrains(
    terrains[terrains.length - 1].position.z - terrainLength
  );
}
```

That, as well as some performance issues need to be fixed. Like for example the creation of a full-sized `geometry` which is then cloned twice and scaled down to make two separate halves is obviously inefficient, it's a quick hack to get the desired visual result. But I'm honestly done from coding now, and I think that is good enough, so not gonna push anything. Although later I did come back but not to do that, but to optimize and smoothen the transition, a quick hack by blending values from neighboring coordinates:

```javascript
let height =
  (noiseGenerator.noise((x + xOffset) / 10, (z + zOffset) / 10) +
    noiseGenerator.noise((x + xOffset + 1) / 10, (z + zOffset) / 10) +
    noiseGenerator.noise((x + xOffset - 1) / 10, (z + zOffset) / 10) +
    noiseGenerator.noise((x + xOffset) / 10, (z + zOffset + 1) / 10) +
    noiseGenerator.noise((x + xOffset) / 10, (z + zOffset - 1) / 10)) /
  5;
```

It basically averages the height value of a point with its neighbors, smoothing rapid height transitions. I dont think I'm going back to it though, as it's not something I'm using for my portfolio anyway. I'm staying with the minimal version of wiry mountains

Anyway, that's it. See you on my next hacking
