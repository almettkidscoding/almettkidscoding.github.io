---
title: Connect all elements
weight: 2
pre: "<b>2. </b>"
chapter: false
---

> In this session, we're going to connect all elements togther. Implement snake's move, eating eggs and grow long.

> - Spend 3 to 5 minutes to explain each step/component. Another 5 minutes to practice and QA.
> - Redirect to the new knowledge of Python to the other session.

### Step 1: Move the snake

**moves** is another **Function** to move the snake **Up**, **Down**, **Right** and **Left**.

	def moves():
	    if snake.direction == "up":
	        y = snake.ycor()
	        snake.sety(y + 20)

	    if snake.direction == "down":
	        y = snake.ycor()
	        snake.sety(y - 20)

	    if snake.direction == "left":
	        x = snake.xcor()
	        snake.setx(x - 20)

	    if snake.direction == "right":
	        x = snake.xcor()
	        snake.setx(x + 20)

- **direction** is a variable holds the value of which direction the snake is moving.
- **x** and **y** are the variables that are holding the value of x and y coordinates.
- **xcor()** and **ycor()** are the methods that retrieves the x and y coordinate values.
- **setx()** and **sety()** are the methods that set the x and y coordinate values.

### Step 2: Define a **List** to store the collection of the eggs that the snake has eaten.

	length=[]

### Step 3: Screen update

Screen must keep updating itself after each action, otherwise game progress stops refresh.

	forest.update()

- **update()** is a method that refreshes the latest status of the snake.

### Step 4: Moving spreed

Define the moving speed of the snake by set the sleep timeout after each moving step.

	time.sleep(0.1)

- **sleep()** is the method to set the timeout of each step. The smaller the value is, the faster the snake moves.

### Step 5: Define the moving scope of the snake in the screen

As long as the snake runs out of the scope of screen in width of 340px and in the height of 340px, game stops.

	if snake.xcor() > 340 or snake.xcor() < -340 or snake.ycor() > 340 or snake.ycor() < -330:
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

- **speed()** is the method to set the speed of the snake. Game over, set the speed value to 0.
- **penup()** is the method to stop drawing on the screen.
- **hideturtle()** is the method to hide the turtle.
- **goto()** is the method to set the position coordinate of the snake.
- **write()** is the method to write text to the screen.

### Step 6: Randomly populate the eggs

Each egg will be randomly populated where 20 steps away from the snake.

	if snake.distance(egg) < 20:
        a = random.randint(-320, 320)
        b = random.randint(-320, 320)
        egg.goto(a, b)

- **randomint()** is a method to randomly generates a coordinate.

### Step 7: Snake eat eggs

Whenever the snake eats a new egg, it extends it's length by 1.

	eaten_egg = turtle.Turtle()
        eaten_egg.speed(0)
        eaten_egg.shape("circle")
        eaten_egg.color("yellow", 'green')
        eaten_egg.penup()
        length.append(eaten_egg) # One egg extends the length of the snake by 1

### Step 8: The extended part follows behind the snake

One egg extends the snake by 1, the extended part should be followed behind the snake.

	for i in range(len(l)-1, 0, -1):
        a = length[i-1].xcor()
        b = length[i-1].ycor()
        length[i].goto(a, b)

### Step 9: The snake is always run at the front

Set the position coordinate of the snake to the front. It always run at the front.

	if len(l) > 0:
        a = snake.xcor()
        b = snake.ycor()
        length[0].goto(a, b)

### Step 10: Whole work flow of the game

	# Import the modules
	import turtle
	import random
	import time

	# Game forest
	forest = turtle.Screen()
	forest.title("snake game")
	forest.bgcolor("green")
	forest.setup(width=700, height=700)

	# Define the turtle
	snake = turtle.Turtle()
	snake.speed(0)
	snake.shape("square")
	snake.color("green", 'yellow')
	snake.penup() # Stop drawing
	snake.goto(0, 0)
	snake.direction = "stop"

	# Define the egg
	egg = turtle.Turtle()
	egg.speed(0)
	egg.shape("circle")
	egg.color("lightgreen")
	egg.penup()
	egg.goto(0, 120)

	# Game over
	def game_over():
	    death = turtle.Turtle()
	    death.speed(0)
	    death.shape("square")
	    death.color("white")
	    death.penup()
	    death.hideturtle() # hide turtle from the screen
	    death.goto(0, 0)
	    death.write("GAME OVER", align="center", font=("Ariel", 28, "normal"))

	# Direction moving functions
	def up():
	    snake.direction = "up"

	def down():
	    snake.direction = "down"

	def right():
	    snake.direction = "right"

	def left():
	    snake.direction = "left"

	# Turtle move function
	def moves():
		if snake.direction == "up":
		    y = snake.ycor()
		    snake.sety(y + 20)

		if snake.direction == "down":
		    y = snake.ycor()
		    snake.sety(y - 20)

		if snake.direction == "left":
		    x = snake.xcor()
		    snake.setx(x - 20)

		if snake.direction == "right":
		    x = snake.xcor()
		    snake.setx(x + 20)

	# Define the direction keys
	def keys():
	    forest.listen()
	    forest.onkeypress(up, 'Up')
	    forest.onkeypress(down, "Down")
	    forest.onkeypress(right, "Right")
	    forest.onkeypress(left, "Left")

	keys()

	length=[]
	while True:
	    forest.update()
	    time.sleep(0.1)

	    if snake.xcor() > 340 or snake.xcor() < -340 or snake.ycor() > 340 or snake.ycor() < -330:
	        time.sleep(1)
	        snake.direction = "stop"
	        game_over()
	        time.sleep(3)

	    if snake.distance(egg) < 20:
	        a = random.randint(-320, 320)
	        b = random.randint(-320, 320)
	        egg.goto(a, b)

	        eaten_egg = turtle.Turtle()
	        eaten_egg.speed(0)
	        eaten_egg.shape("circle")
	        eaten_egg.color("yellow", 'green')
	        eaten_egg.penup()
	        length.append(eaten_egg) # One egg extends the length of the snake by 1

	    for i in range(len(length)-1, 0, -1):
	        a = length[i-1].xcor()
	        b = length[i-1].ycor()
	        length[i].goto(a, b)

	    if len(length) > 0:
	        a = snake.xcor()
	        b = snake.ycor()
	        length[0].goto(a, b)

	    moves()

	    for i in length:
	        if i.distance(snake) < 5:
	            time.sleep(1)
	            snake.direction = "stop"
	            game_over()
	            time.sleep(3)

	forest.mainloop()


