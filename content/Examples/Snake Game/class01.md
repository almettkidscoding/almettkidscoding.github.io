---
title: Set up the screen
weight: 1
pre: "<b>1. </b>"
chapter: false
---

> In this session, we're going to learn how to set up snake game playground.

### Step 1: import required modules

**Turtle** is a python feature like a drawing board, which lets you command a turtle to draw all over it! You can use functions like `turtle.forward(...)` and `turtle.left(...)` which can move the turtle around.

	import turtle

**Random** module implements pseudo-random number generators for various distributions.

	import random

**Time** module provides various time-related functions. For related functionality,

	import time

### Step 2: Set up the screen

**Screen** is where we play the game. In this step, we're going to define **title**, **background color**, **size** of the playground

	screen = turtle.Screen()
	screen.title("snake game")
	screen.bgcolor("black")
	screen.setup(width=700, height=700)

### Step 3: Set up the elements

**Turtle** moves and extend itself by eating eggs that appears randomly on the screen. Let's define the **Turtle** object as **head** in the following code.

	head = turtle.Turtle()
	head.speed(0)
	head.shape("square")
	head.color("green", 'yellow')
	head.penup()
	head.goto(0, 0)
	head.direction = "stop"

Define the egg:

	egg = turtle.Turtle()
	egg.speed(0)
	egg.shape("circle")
	egg.color("lightgreen")
	egg.penup()
	egg.goto(0, 120)

### Step 4: Define moving directions

We have four moving directions **Up**, **Down**, **Right** and **Left**. Each moving action is defined as a **Function**. A **Function** is a block of code which only runs when it is called.

	def up():
	    head.direction = "up"

	def down():
	    head.direction = "down"

	def right():
	    head.direction = "right"

	def left():
    	head.direction = "left"

**Keys** are elemnts to control the direction os the moving **Turtle**. Mapping of the key and direction is below:

- **Up** -> Up 
- **Down** -> Down
- **Right** -> Right
- **Left** -> Left

See the code details below:

	def keys():
	    screen.listen()
	    screen.onkeypress(up, 'Left')
	    screen.onkeypress(down, "Down")
	    screen.onkeypress(right, "Right")
	    screen.onkeypress(left, "Left")

	keys()

### Step 5: Put them all together

	# Import the modules
	import turtle
	import random
	import time

	# Game screen
	screen = turtle.Screen()
	screen.title("snake game")
	screen.bgcolor("black")
	screen.setup(width=700, height=700)

	# Define the turtle
	head = turtle.Turtle()
	head.speed(0)
	head.shape("square")
	head.color("green", 'yellow')
	head.penup()
	head.goto(0, 0)
	head.direction = "stop"

	# Define the egg
	egg = turtle.Turtle()
	egg.speed(0)
	egg.shape("circle")
	egg.color("lightgreen")
	egg.penup()
	egg.goto(0, 120)

	# Direction moving functions
	def up():
	    head.direction = "up"

	def down():
	    head.direction = "down"

	def right():
	    head.direction = "right"

	def left():
	    head.direction = "left"

	# Define the direction keys
	def keys():
	    screen.listen()
	    screen.onkeypress(up, 'Left')
	    screen.onkeypress(down, "Down")
	    screen.onkeypress(right, "Right")
	    screen.onkeypress(left, "Left")

	keys()



