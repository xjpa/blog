---
layout: post
title: 'Pyperlinmap'
description: 'toy project with python building an ultra simple 2d map generator with perlin noise'
category: articles
tags: [hacking, project-desktop]
comments: true
---

Simple python project. It generates a map of emojis via a perlin noise algorithm. Of course, implementing perlin noise is too much of a time suck for me, or maybe I'll do that later... But right now, I just decided to [use a library](https://pypi.org/project/noise/) to do that.

It prints out randomly generated maps on either the CLI or saves it to a .txt file called `saved_shapes.txt` if you run `$ python save_to_txt.py`

code: [github.com/xjpa/pyperlinmap](https://github.com/xjpa/pyperlinmap)

<!-- more -->

<img src="https://raw.githubusercontent.com/xjpa/pyperlinmap/main/screenshot.png">
