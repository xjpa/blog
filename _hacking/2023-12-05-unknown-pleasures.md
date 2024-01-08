---
layout: post
title: 'Unknown Pleasures'
description: "learning matplotlib by building a visualization of the album art of Joy Division's Unknown Pleasures"
category: articles
tags: [hacking, project-viz]
comments: true
---

I was learning matplotlib for a couple hours when i decided to try making something inspired by the iconic album art of Joy Division's [Unknown Pleasures](https://en.wikipedia.org/wiki/Unknown_Pleasures), which was based on a reversed image of radio waves from [CP 1919](https://en.wikipedia.org/wiki/PSR_B1919%2B21), a pulsar from a rapidly rotating neutron star.

Code: [github.com/xjpa/unknownpleasures](https://github.com/xjpa/unknownpleasures)

<!-- more -->

Here's a fun gif with `def update(frame)` making the animation gradually build up each line, starting from the bottom, adding one line at a time to kinda create an effect similar to lines being drawn sequentially, utilising matplotlib's [FuncAnimation()](https://matplotlib.org/stable/api/_as_gen/matplotlib.animation.FuncAnimation.html) to create and save it as gif (might have to wait for it to load a bit as it's quite big even though i already compressed it):

<center>
<img src="https://github.com/xjpa/unknownpleasures/raw/main/animated-visualization-compressed.gif">
</center>
As you can see, there's still some white border/white space above for the gif, courtesy of matplotlib. I'm too lazy to look into eliminating it... I think it can be done by messing around with some padding settings like you do with CSS

But anyway, now here's 5 pictures generated with matplotlib, inspired by the unknown pleasures album cover. Sorry, I didnt compress them...

First try LOL. Lines arent being offset vertically in a way that would create the layered appearance

<img src="https://raw.githubusercontent.com/xjpa/unknownpleasures/main/1.png">

This time, random central peaks were added to create a jagged mountain effect, with smaller peaks on each side and a smoothing function applied to give a ridge-like appearance

<img src="https://raw.githubusercontent.com/xjpa/unknownpleasures/main/2.png">

Now each line is having its own set of random peaks and valleys

<img src="https://raw.githubusercontent.com/xjpa/unknownpleasures/main/3.png">

Centralized the taller peaks by defining a center region and adjusting peak generation such that those near the center region would be 1.5x taller

<img src="https://raw.githubusercontent.com/xjpa/unknownpleasures/main/4.png">

Better centralization. Also reduced vertical spacing to better fit the peaks (particularly the top) from going over the plot's border. Normalization of each line's height was also adjusted. Now, after creating the peaks, each line's height is scaled down to a uniform maximum height defined by `vertical_spacing`. This scaling ensures that even the tallest peaks in each line stay within the plot's vertical limits.

<img src="https://raw.githubusercontent.com/xjpa/unknownpleasures/main/5.png">

Yeah I didnt get close to unknown pleasures, but it was a fun hour of hacking.
