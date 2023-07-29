---
title: 'Multiplayer Stable Diffusion, Song of Life, and Simulating Rope'
author: Chris Ried
date: '2020-11-26'
slug: generative-arts-54
categories: 
featured: 
tags: ['generative']
---

_Originally posted on [Substack](https://generative.substack.com/p/multiplayer-stable-diffusion-song)_

> The need to be right all the time is the biggest bar there is to new ideas. -Edward D Bono


Good morning! 

Hope you have had a great week! 

This week I’ve a few links to some musical platforms. Hope you find some inspiration to make some interesting works by simply experimenting with various implementations. There are definitely way more ways to do this out there but I’d highlight some of the less frequently used visual programming platforms for your enjoyment. 

Much love, 

Chris Ried 

# 🖌️ Generative Music

![CleanShot 2022-11-26 at 08.27.31.png](#054%20-%20Creative%20Coding%20Generative%20Arts%20Weekly%20b577e6d4d0e3438492984c210494b955/CleanShot_2022-11-26_at_08.27.31.png)

## [Song of Life](https://songoflife.ukr.lk/#6614)

> Endless Generative Music Jukebox implmented with Conway's Game Of Life
> 

A simple implementation but always beautiful to merge music and something like Conway’s Game of Life into one implementation. 

Speaking of ways one might implement something like this, here are a few ways you might be able to complete that. 

## Pure Data

Unfortunately the library hasn’t seen much development over the last couple years; however a language doesn’t always need to be updated outside of operability between new OS releases or chipsets.  

> Pure Data is an open source visual programming environment that runs on anything from personal computers to embedded devices (ie [Raspberry Pi](https://puredata.info/docs/raspberry-pi)) and smartphones (via [libpd](https://puredata.info/downloads/libpd), [DroidParty (Android)](https://puredata.info/downloads/pddroidparty), and [PdParty (iOS)](http://github.com/danomatika/PdParty). It is a major branch of the family of patcherprogramming languages known as Max (Max/FTS, ISPW Max, [Max/MSP](http://cycling74.com/), etc), originally developed by Miller Puckette at [IRCAM](http://www.ircam.fr/).
> 

A couple neat examples of this are: 

[https://www.youtube.com/watch?v=I9_3CfRm8GE](https://www.youtube.com/watch?v=I9_3CfRm8GE)

[https://www.youtube.com/watch?v=yp3PnQMM3rA&feature=emb_rel_pause](https://www.youtube.com/watch?v=yp3PnQMM3rA&feature=emb_rel_pause)

The following is a straight forward comparison between Max MSP (closed source) and Pure Data (open source) visual programming languages geared toward sound programming.  

## [Max MSP](https://cycling74.com/products/max)

The following video shows the similarities between both languages.

[https://www.youtube.com/watch?v=s7Gv7SR0Nrk](https://www.youtube.com/watch?v=s7Gv7SR0Nrk)

> Let’s learn how to program music and synth using visual programming language. But what even is a visual programming language? And which language should we learn? Max MSP or Pure Data?
> 

There is definitely more to be read [here](http://www.pd-tutorial.com/english/ch01.html) and the author of Pure Data has a beautiful  [here](http://msp.ucsd.edu/techniques/latest/book.pdf).

## Orca

> Orca is a two-dimensional esoteric programming language in which every letter of the alphabet is an operator, where lowercase letters operate on bang, uppercase letters operate each frame.
> 

Essentially it has a basic interface to trigger notes, but then any soundclip or VST can be programmed to be used and thus making it an incredibly interesting instrument to create some beautiful innovation. 

[https://www.youtube.com/watch?v=DBI8eBMGyYs](https://www.youtube.com/watch?v=DBI8eBMGyYs)

## [Supercollider](https://supercollider.github.io/)

> **SuperCollider i**s an environment and [programming language](https://en.wikipedia.org/wiki/Programming_language) originally released in 1996 by James McCartney for [real-time](https://en.wikipedia.org/wiki/Real-time_computing) [audio synthesis](https://en.wikipedia.org/wiki/Audio_synthesis) and [algorithmic composition](https://en.wikipedia.org/wiki/Algorithmic_composition)
> 

[https://www.youtube.com/watch?v=vzspylL9Bh0](https://www.youtube.com/watch?v=vzspylL9Bh0)

# 📰 Happenings

- [Art Bazel Miami](https://www.artbasel.com/miami-beach)  Dec 1-3, 2022

I need to get around to putting together a better calendar for this year. 

# 🔖 Articles and Tutorials

[https://www.youtube.com/watch?v=qEp70jK8Az0](https://www.youtube.com/watch?v=qEp70jK8Az0)

> At the end of this video, you may have a broad concept of how to implement a cloth simulation algorithm in your own game. You can take a look at the webgl + js game engine I'm developing using the cloth simulation I implemented in the video
> 

![CleanShot 2022-11-26 at 01.04.38@2x.png](#054%20-%20Creative%20Coding%20Generative%20Arts%20Weekly%20b577e6d4d0e3438492984c210494b955/CleanShot_2022-11-26_at_01.04.382x.png)

## [Simulating a Rope](https://owlree.blog/posts/simulating-a-rope.html)

> The origin of rope dates back to prehistoric times, and through the years it played an important role in the development of humankind. Rope can be made by hand, but since about 4000 BC, people started using machines to make it. It is believed that the Egyptians were the first to invent such devices, probably because rope was indispensable to their agriculture and the building of their structures, including their temples and pyramids. They usually made rope out of materials such as water reed, date palms, flax, grass, papyrus, leather, or even camel hair.
> 

![https://miro.medium.com/max/1400/1*4QdaFan8lTK_w8kbwNFoMw.png](https://miro.medium.com/max/1400/1*4QdaFan8lTK_w8kbwNFoMw.png)

## [Generating 3D Models with Polygen and Pytorch](https://towardsdatascience.com/generating-3d-models-with-polygen-and-pytorch-4895f3f61a2e)

> There is a burgeoning field of deep learning research focused on applying DL techniques to 3D geometry and computer graphics applications, as evidenced by this [lengthy collection of recent research](https://github.com/timzhang642/3D-Machine-Learning). If you are interested in the subject, take a look. It’s quite a rabbit hole. For PyTorch users looking to try some 3D deep learning, the [Kaolin library](https://github.com/NVIDIAGameWorks/kaolin)
 is worth looking into. For TensorFlow users, there is also [TensorFlow Graphics](https://www.tensorflow.org/graphics). A particularly hot subfield is the generation of 3D models. Creatively combining 3D models, rapidly producing 3D models from images, and creating synthetic data for other machine learning applications and simulations are just a handful of the myriad use cases for 3D model generation.
> 

![https://www.bit-101.com/blog/wp-content/uploads/2022/11/out-21.png](https://www.bit-101.com/blog/wp-content/uploads/2022/11/out-21.png)

## [Arcs Circles and Ellipse](https://www.bit-101.com/blog/2022/11/coding-curves-03-arcs-circles-ellipses/)

> It’s likely that your platform’s drawing API has at least some of this built-in. For example, the HTML Canvas API does not have a `circle` method, but it does have an `arc` method as well as an `ellipse` method, either of which can be used to draw circles.
> 

This is chapter 3 from a book project called “Coding Curves” which eventually will be a complete book. Right now it still in the earlier stages but will quickly move into new areas. 

![Untitled](#054%20-%20Creative%20Coding%20Generative%20Arts%20Weekly%20b577e6d4d0e3438492984c210494b955/Untitled.png)

## [Multiplayer Stable Diffusion](https://huggingface.co/spaces/huggingface-projects/stable-diffusion-multiplayer/discussions/15#6365ee78f31ef76df4061050)

> Hey there! Me and my 2 friends made this isometric piece in room 21 and would love to see how you might add to it! Or you can destroy it, of that jiggles your mind ; If you decide to add to it - you can just write "isometric" along with anything else and it would fit right in!
> 

The idea to be able to mix stable diffusion and people together just was a really neat idea I thought I’d mention here. 

# 🎒Courses

![https://assets8.domestika.org/course-images/000/045/978/45978-big.gif](https://assets8.domestika.org/course-images/000/045/978/45978-big.gif)

## **[Intro to Creative Coding: Create Graphic Objects](https://www.domestika.org/en/courses/4034-intro-to-creative-coding-create-graphic-objects)**

> Julien Gachadoat grew up in the 1990s, witnessing the birth of the demoscene and a whole new discipline: creative programming. This passion never left him. Nowadays, he specializes in generative art and is based in Bordeaux. He also teaches creative coding at university and in workshops in France and abroad.
> 
> 
> He has developed his own creative tools from simple graphic rules and has built a strong international community of followers on social media. In addition to participating in numerous exhibitions, he cofounded the interactive digital art studio 2Roqs with Michaël Zancan, working on multiple interactive installations.
> 

Been a fan of [Julien](https://www.instagram.com/julienv3ga/) and his work for ages and I hope you can appreciate the talent and work that he continues to make. Do check his work out on [IG](https://www.instagram.com/julienv3ga/) as well.

# 📚Books

![https://m.media-amazon.com/images/I/31zKYnmadbL._SX333_BO1,204,203,200_.jpg](https://m.media-amazon.com/images/I/31zKYnmadbL._SX333_BO1,204,203,200_.jpg)

> *Concrete Poetry: A 21st-Century Anthology* is the first overview of concrete poetry in many years. Selective yet wide-ranging, this anthology re-evaluates the movement, singling out its most distinctive and influential works. Nancy Perloff, curator of an important Concrete Poetry exhibition at the Getty Research Institute, includes examples from the little-known Japanese concretists and the Wiener Gruppe—groups that, together with the Brazilian poet Augusto de Campos and the Scottish poet Ian Hamilton Finlay, have engaged with the most subtle possibilities of language itself—while also incorporating key poems by Eugen Gomringer, Dieter Roth, Henri Chopin, and others and including contemporary contributions by Cia Rinne and Susan Howe.
> 

It's just a great book to gain inspiration on taking more textual interpretations and then expounding on that… 

# Send me your inspirations...

---