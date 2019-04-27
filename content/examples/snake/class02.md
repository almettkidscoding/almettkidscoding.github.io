---
title: Connect all elements
weight: 2
pre: "<b>2. </b>"
chapter: false
---

> In this session, we're going to connect all elements togther. Implement turtle's move, eating eggs and grow long.

### Step 1: Move the turtle

**moves** is another **Function** to move the turtle **Up**, **Down**, **Right** and **Left**.

	def moves():
	    if head.direction == "up":
	        y = head.ycor()
	        head.sety(y + 20)

	    if head.direction == "down":
	        y = head.ycor()
	        head.sety(y - 20)

	    if head.direction == "left":
	        x = head.xcor()
	        head.setx(x - 20)

	    if head.direction == "right":
	        x = head.xcor()
	        head.setx(x + 20)

- **direction** is a variable holds the value of which direction the turtle is moving.
- **x** and **y** are the variables that are holding the value of x and y coordinates.
- **xcor()** and **ycor()** are the methods that retrieves the x and y coordinate values.
- **setx()** and **sety()** are the methods that set the x and y coordinate values.

### Step 2: Define a **List** to store the length value of the eggs that the turtle has eaten.

	length=[]

### Step 3: Screen update

Screen must keep updating itself after each action, otherwise game progress stops refresh.

	screen.update()

- **update()** is a method that refreshes the latest status of the turtle.

### Step 4: Moving spreed

Define the moving speed of the turtle by set the sleep timeout after each moving step.

	tiime.sleep(0.1)

- **sleep()** is the method to set the timeout of each step. The smaller the value is, the faster the turtle moves.

### Step 5: Define the moving scope of the turtle in the screen

As long as the turtle runs out of the scope of screen in width of 340px and in the height of 340px, game stops.

	if head.xcor() > 340 or head.xcor() < -340 or head.ycor() > 340 or head.ycor() < -330:
        time.sleep(1)
        head.direction = "stop"
        game_over()
        time.sleep(3)

Returns **GAME OVER** to the screen.

	def game_over():
	    death = turtle.Turtle()
	    death.speed(0)
	    death.shape("square")
	    death.color("white")
	    death.penup()
	    death.hideturtle()
	    death.goto(0, 0)
	    death.write("GAME OVER", align="center", font=("Ariel", 28, "normal"))

- **speed()** is the method to set the speed of the turtle.Game over, set the speed value to 0.
- **penup()** is the method to stop drawing on the screen.
- **hideturtle()** is the method to hide the turtle.
- **goto()** is the method to set the position coordinate of the turtle.
- **write()** is the method to write text to the screen.

### Step 6: Randomly populate the eggs

Each egg will be randomly populated where 20 steps away from the turtle.

	if hd.distance(ft) < 20:
        a = random.randint(-320, 320)
        b = random.randint(-320, 320)
        ft.goto(a, b)

- **randomint()** is a method to randomly generates a coordinate.

### Step 7: Turtle eat eggs

Whenever the turtle eats a new egg, it extends it's length by 1.

	bd = turtle.Turtle()
        bd.speed(0)
        bd.shape("square")
        bd.color("yellow", 'green')
        bd.penup()
        l.append(bd)

### Step 8: The extended part follows behind the turtle

One egg extends the turtle by 1, the extended part should be followed behind the turtle.

	for i in range(len(l)-1, 0, -1):
        a = l[i-1].xcor()
        b = l[i-1].ycor()
        l[i].goto(a, b)

### Step 9: The turtle is always run at the front

Set the position coordinate of the turtle to the front. It always run at the front.

	if len(l) > 0:
        a = hd.xcor()
        b = hd.ycor()
        l[0].goto(a, b)

### Step 10: Whole work flow of the game

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

	# Turtle move function
	def moves():
	    if head.direction == "up":
	        y = head.ycor()
	        head.sety(y + 20)

	    if head.direction == "down":
	        y = head.ycor()
	        head.sety(y - 20)

	    if head.direction == "left":
	        x = head.xcor()
	        head.setx(x - 20)

	    if head.direction == "right":
	        x = head.xcor()
	        head.setx(x + 20)

	# Define the direction keys
	def keys():
	    screen.listen()
	    screen.onkeypress(up, 'Up')
	    screen.onkeypress(down, "Down")
	    screen.onkeypress(right, "Right")
	    screen.onkeypress(left, "Left")

	keys()

	length=[]
	while True:
	    screen.update()
	    time.sleep(0.1)

	    if head.xcor() > 340 or head.xcor() < -340 or head.ycor() > 340 or head.ycor() < -330:
	        time.sleep(1)
	        head.direction = "stop"
	        game_over()
	        time.sleep(3)

	    if head.distance(egg) < 20:
	        a = random.randint(-320, 320)
	        b = random.randint(-320, 320)
	        egg.goto(a, b)

	        body = turtle.Turtle()
	        body.speed(0)
	        body.shape("circle")
	        body.color("yellow", 'green')
	        body.penup()
	        length.append(body)

	    for i in range(len(length)-1, 0, -1):
	        a = length[i-1].xcor()
	        b = length[i-1].ycor()
	        length[i].goto(a, b)

	    if len(length) > 0:
	        a = head.xcor()
	        b = head.ycor()
	        length[0].goto(a, b)

	    moves()

	screen.mainloop()

