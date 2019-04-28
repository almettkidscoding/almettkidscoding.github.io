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

**Forest** is where we play the game. In this step, we're going to define **title**, **background color**, **size** of the playground

	forest = turtle.Screen()
	forest.title("snake game")
	forest.bgcolor("black")
	forest.setup(width=700, height=700)

### Step 3: Set up the elements

**Snake** moves and extend itself by eating eggs that appears randomly on the screen. Let's define the **Turtle** object as **snake** in the following code.

	snake = turtle.Turtle()
	snake.speed(0)
	snake.shape("square")
	snake.color("green", 'yellow')
	snake.penup()
	snake.goto(0, 0)
	snake.direction = "stop"

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
	    snake.direction = "up"

	def down():
	    snake.direction = "down"

	def right():
	    snake.direction = "right"

	def left():
    	snake.direction = "left"

**Keys** are elemnts to control the direction os the moving **snake**. Mapping of the key and direction is below:

- **Up** -> Up 
- **Down** -> Down
- **Right** -> Right
- **Left** -> Left

See the code details below:

	def keys():
	    forest.listen()
	    forest.onkeypress(up, 'Left')
	    forest.onkeypress(down, "Down")
	    forest.onkeypress(right, "Right")
	    forest.onkeypress(left, "Left")

	keys()

### Step 5: Put them all together

	# Import the modules
	import turtle
	import random
	import time

	# Game screen
	forest = turtle.Screen()
	forest.title("snake game")
	forest.bgcolor("black")
	forest.setup(width=700, height=700)

	# Define the snake
	snake = turtle.Turtle()
	snake.speed(0)
	snake.shape("square")
	snake.color("green", 'yellow')
	snake.penup()
	snake.goto(0, 0)
	snake.direction = "stop"

	# Define the egg
	egg = turtle.Turtle()
	egg.speed(0)
	egg.shape("circle")
	egg.color("lightgreen")
	egg.penup()
	egg.goto(0, 120)

	# Direction moving functions
	def up():
	    snake.direction = "up"

	def down():
	    snake.direction = "down"

	def right():
	    snake.direction = "right"

	def left():
	    snake.direction = "left"

	# Define the direction keys
	def keys():
	    forest.listen()
	    forest.onkeypress(up, 'Left')
	    forest.onkeypress(down, "Down")
	    forest.onkeypress(right, "Right")
	    forest.onkeypress(left, "Left")

	keys()



