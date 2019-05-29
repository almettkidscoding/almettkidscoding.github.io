---
title: Fully functioning game
date: 2019-05-08T09:30:27+08:00
weight: 3
pre: "<b>3. </b>"
chapter: false
---

![](/images/new_flowchart.png)

### Simply go over the previous class

|<center>Task</center> 	   |         <center>Time</center>                   |
---------- | -------------------------------- |
| <center>Quickly go through the [**previous class**](/examples/snake/class02)</center>  | <center>10 mins</center>  |

### Step 1: What if the snake runs out of the screen?

Both `X` and `Y` coordinates ranges from 340 to -340. Once the snake runs out of this range, game is over. Code snippet is given below:

	# Out of screen
	def out_of_screen():
		if snake.xcor() > 340 or snake.xcor() < -340 or snake.ycor() > 340 or snake.ycor() < -330:
			time.sleep(1)
			snake.direction = "stop"
			game_over()
			time.sleep(3)

### Step 2: What happens it the snake hits itself?

Calculate the distance of the snake from it's tail. If it's less than 5 steps, game is over. Code snippet is below:

	# Snake hits itself
	def hits_itself():
		for i in length:
			if i.distance(snake) < 5:
				time.sleep(1)
				snake.direction = "stop"
				game_over()
				time.sleep(3)

### Step 3: Game is over

Whenever game is over, game will stop processing and "GAME OVER" displays on the screen.

	# Game over
	def game_over():
	    death = turtle.Turtle()
	    death.speed(0)
	    death.penup()
	    death.hideturtle()
	    death.goto(0, 0)
	    death.write("GAME OVER", align="center", font=("Ariel", 28, "normal"))