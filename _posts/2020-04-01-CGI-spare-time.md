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

Source:

**main.py**

```
#main.py
# https://devdocs.io/pygame/

# import external modules
import pygame, random, sys, math
from pygame.locals import *
# import local scripts
from vector.classes import PVector

# initialize pygame
pygame.init()

# Window title
TITLE = "01. Bouncing ball with vectors"
pygame.display.set_caption(TITLE)

# screen
WIDTH = 640
HEIGHT = 360
screen = pygame.display.set_mode((WIDTH,HEIGHT))

# quitting msg
quitting_message = 'User is quitting the app'

# Clock obj -> to keep track of FPS
framerate = 60
clock = pygame.time.Clock()

# Global vars
location = PVector(100, 100)
velocity = PVector(2.5, 5)
size = 16


# SETUP
# starting background
background = (255, 255, 255)
screen.fill(background)
# custom objs

# Functions

def draw():
	global background, location, velocity, size

	# drawing background every frame helps simulate movement
	screen.fill(background)

	location += velocity # in processing would be location.add(velocity)

	#obj.values[0] == obj.x in Shiffman's book
	#obj.values[1] == obj.y in Shiffman's book

	if location.values[0] > (WIDTH-size+2) or location.values[0] < 0:
		velocity.values[0] *= -1
	if location.values[1] > (HEIGHT-size+2) or location.values[1] < 0:
		velocity.values[1] *= -1

	erect = pygame.Rect(int(location.values[0]), int(location.values[1]), size, size)
	fill = (175, 175, 175)
	pygame.draw.ellipse(screen, fill, erect)


def event_handler(): # requires importing locals
	pressed_key = []
	# EVENTS - cannot be placed in a function to be called here
	for event in pygame.event.get(): #all events in pygame
		if event.type == QUIT: # clicking QUIT button (X)
			print(quitting_message)
			running = False # stop running
			pygame.quit() # terminate pygame functionality
			sys.exit() # terminate program
		if event.type == KEYDOWN:
			pressed_key.append(pygame.key.name(event.key)) # pressed_key must be a list for the following to work
			print('pressed_key:', pressed_key)
			if 'left alt' in pressed_key and 'f4' in pressed_key:
				print(quitting_message)
				running = False # stop running
				pygame.quit() # terminate pygame functionality
				sys.exit() # terminate program


# MAIN LOOP

running = True

while running:

	# MOUSE
	mouseX, mouseY = pygame.mouse.get_pos()
	event_handler()


	# DRAW
	draw()


	# Set FPS
	clock.tick(framerate)
	# Update screen: last line of loop. Fires animation
	pygame.display.update()

```
**vector.classes.py**


```
# import the vector module by Mat Leonard, available here:
# URL: https://gist.github.com/mcleonard/5351452

import math

class PVector(Vector):

    def __init__(self, *args):
        """ Create a vector, example: v = Vector(1,2) """
        if len(args)==0: self.values = (0,0)
        else:
            self.values = args
            self.values = list(self.values)

    # magnitude method
    def mag(self, origin=(0,0,0)):
        origin = PVector(*origin)
        total = 0
        for i, v in enumerate(self):
            total += ((origin.values[i]-self.values[i])**2)
        return math.sqrt(total)

```
