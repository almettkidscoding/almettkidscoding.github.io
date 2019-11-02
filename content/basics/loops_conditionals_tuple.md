---
title: "Loops, If...else, Tuple"
date: 2019-09-29T20:43:07+08:00
weight: 3
pre: "<b>3. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction in this class**](#syntax-table)
- [**What is Loop statement?**](#what-is-loop-statement)
- [**What is if...else statement?**](#what-is-ifelse-statement)
- [**What is Tuple?**](#what-is-tuple)
- [**Exercises with little turtle**](#exercises-with-little-turtle)
- [**Homework**](#homework)

### Syntax table

|  <center>Keyword</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>width(integer)</center>   | Defines the width of the pen. Patameter - integer is a value type of int |
|  <center>if statement</center>   | is a conditional statement. |
|  <center>for statement</center>   | is a loop statement in which operations repeat itself for a limited amount of time |

### What is loop statement?

Look at the diagram below to know how does loop statement work.

![](/images/loop_diagram.png)

#### How to write the Python code?

```python
	# Define a list of apples
	box = ["appleA", "appleB", "appleC", "appleD", "appleE"]
	for apple in box: # Check if there is a next apple in the box
		print(apple) # If there is a next apple, print it out.
```

### What is ifelse statement?

Look at the diagram below to know how does if...else statement work

![](/images/apple_pear_if_else_check.png)

#### How to write the Python code?

```python
	# Define a list of fruits
	box = ["appleA", "pearB", "appleC", "appleD", "pearE"]
	# fruit_label is the label of fruits in the box which starts from 0
	for fruit_label in range(len(box)):
		if fruit_label == 1 or fruit_label == 4:
			print("This is a pear" + box[fruit_label])
		else:
			# If it's not pear, it's a apple since we only have two types of fruit in the box.
			print(box[fruit_label])
```

### Exercises with little turtle

#### Artistic shapes

Following example presents the usage of `For loops`, `value assignment`, `mathmatical incremention`.

```python
	import random
	from turtle import *
	colors  = ["red","green","blue","orange","purple","pink","yellow"]

	width(10)
	length = 5
	for count in range(100):
		speed(100)
		a_color = random.choice(colors)
		color(a_color)
		forward(length)
		right(135)
		length = length + 5

	done()
```

![](/images/turtle/artistic_shapes.png)

#### Artist turtle

Following example presents the usage of `For loops`, `range()`, `random.choice()` and `Lists`. 

```python
	from turtle import *
	import random

	shape("turtle")
	setup(800,600)
	colors = ["red","green","blue","orange","purple","pink","yellow"]
	titles = ["怎么这么好看！", "小乌龟是个艺术家唉！"]

	penup()
	setpos(0, 230)
	pendown()
	pencolor(random.choice(colors))
	write(random.choice(titles), align="center", font=("Arial", 28, "bold"))
	penup()

	for i in range(1,20):
		color(random.choice(colors))
		speed(100)
		width(5)
		circle(i*10)
		penup()
		sety(-i*10)
		pendown()
	 
	done()
```

![](/images/turtle/artist_turtle.png)

> #### Homework : Create the logo of Olympics

Given five lists with two items in each. First item is the coordinate of the circle, second item is the color of the circle. Please write a `for loop` to create logo of olympics.

**Input**

```python
	blue = [-120,0,"blue"]
	black = [0,0,"black"]
	red = [120,0,"red"]
	yellow = [-60,-60,"yellow"]
	green = [60,-60,"green"]
```

#### Tips

```python
	from turtle import *
	setup(800, 600)
```

- **setpos():** Sets the position that is passed as a argument. For example: `setpos(-120,0)`
- **pencolor()**: Sets the color of pen. Foe example: `pencolor("red")`
- **pensize()**: Size of the pen. For example: `pensize(5)`

**Output**

![](/images/turtle/olympics.png)

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>