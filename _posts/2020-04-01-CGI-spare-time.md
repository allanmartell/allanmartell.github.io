---
layout: post
title: "CGI during my spare time"
date: 2020-04-01
---

I've been doing trying the tutorials from *[The Nature of Code](https://natureofcode.com/book/)* by [Daniel Shiffman](https://shiffman.net/).

I fell in love with Computer-Generated Graphics (CGI) during my masters in Digital Media at Georgia Tech. In fact, I first learned to program in [Processing](https://processing.org/). However, outside of the programming courses I teach at Michigan, I've not had much time to actually dive into CGI after I finished my masters. It's been eight years and I wanted to hone my skills. So, I took advantage of my social distancing time productively.

I first started to adapt scripts from the processing tutorials into `pygame` on my own. However, I quickly realized this was not getting me far. For once, I was just translating code from `Java` (processing is after all `Java`). I felt like I was translating a math paper from English to Spanish. Sure, I could make every sentence syntactically and grammatically correct, but this was not helping me grasp the argument, or in this case, the logic underpinning the commands. Thus, I decided to go back to the origins. I learned that Shiffman had an online version of his book and grabbed onto it.

It probably would be much faster if I just followed the instructions with Processing, but that's too easy. More importantly, Processing is explicitly designed to abstract away the heavy lifting of setting up the environment for CGI. `Pygame` does the same to an extent, but much lesser. If I want, for instance, to instantiate a Euclidean vector object in python, there is no built-in `PVector` class. I have to search for vector classes, and sometimes still extend them with additional functionality of my own. In so doing, I'm making sure I master the ins and outs of python syntax structure, and getting a healthy reminder about basic trigonometry and physics. These learning outcomes will help me in the future, if I want to write a CGI script in a different language.

In the mid-term, my hope is to use my learning to extend available options for information visualization through other python libraries like `numpy`. If I get away with this, I can actually link my current experiments with my plans to combine data-driven storytelling and my dissertation research on social memory. The way is long, but I'm not in a rush. After all, the priority right now is my dissertation. The good thing about CGI is that I find it so absorbing that it completely takes my mind out of my research-related concerns at the end of the day. So, I deepen my skills as a programmer, learn new ways to generate graphics, decompress, and make cool graphics. Thanks, Daniel Shiffman!

If you want to check out the scripts I'm producing, stop by my [repo](https://github.com/allanmartell/Nature-of-Code-with-Pygame) here. I would love feedback to make better scripts.

Here is the very first script of this experiment, the classic *[bouncing ball](https://github.com/allanmartell/Nature-of-Code-with-Pygame/raw/documentation/01%20-%20Vectors/1.1_bouncing_ball_with_vectors.py)*:

<iframe width="560" height="315" src="https://www.youtube.com/embed/bqudDkDHw6E" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
