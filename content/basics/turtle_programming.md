---
title: "Turtle programming"
date: 2019-09-18T13:10:47+08:00
weight: 1
pre: "<b>1. </b>"
chapter: false
---

### Class objectives
- [**Learn key syntax in turtle**](#syntax-table)
- [**Draw the first turtle graphic**](#draw-the-first-turtle-graphic)
- [**Draw shapes in practice**](#draw-shapes-in-practice)

### Syntax table

|  <center>Keyword</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>import</center>   | import statement is the most common way of invocking the required modules |
|  <center>star mark(*)</center>  |  stands for everything  |
|  <center>forward(distance)</center>  |  Parameter: distance- is a number (integer or float). Move the turtle forward by the specified distance, in the direction the turtle is headed.  |
|  <center>backward(distance)</center>  |  Parameter: distance- is a number (integer or float). Move the turtle backward by the specified distance, in the direction the turtle is headed.  |
|  <center>right(angle)</center>  |  Parameter: angle- a number (integer or float). Turn turtle right by angle units.(Units are by default degrees)  |
|  <center>left(angle)</center>  |  Parameter: angle- a number (integer or float). Turn turtle left by angle units.(Units are by default degrees)  |
|  <center>goto(x, y=None)</center>  |  Parameters:	x and y are numbers. y can be None  |
|  <center>pendown()</center>  |  Pull the pen down – drawing when moving.  |
|  <center>penup()</center>  |  Pull the pen up – no drawing when moving.  |
|  <center>color(color1, color2)</center>  |  color1 is fill color. color2 is pen color.  |
|  <center>shape(name=None)</center>  |  Parameter: name - a string which is a valid shapename. Set turtle shape to shape with given name or, if name is not given, return name of current shape.   |
|  <center>done()</center>  |  Must be the last statement that finalize the program   |

### Draw the first turtle graphic

#### Square programs in comparison

1. Square program in Scratch

![](/images/turtle/square_in_scratch.png)

2. Square program in Python

```python
shape("turtle")
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
```

- `forward()`: 
- `right()`:

#### Square program in comparison (with loop)

1. Square program in Scratch

![](/images/turtle/square_loop.png)

2. Square program in Python

```python
for each_time in range(4):
	shape("turtle")
	forward(100)
	right(90)
```

### Write a square program in Python

#### Step 1: Create Python file
 Open `Sublime Text` editor, create a file by clickng `File -> New File` at the left top, name it as `turtle_program.py`.

#### Step 2: Import turtle module
Import Turtle module to the `turtle_program.py` file.
	
	from turtle import *

> Look at [**syntax table**](#syntax-table) for more introduction about `import`

#### Step 3: Draw a square
Draw a square of which 100 pixels each side.

```python
shape("turtle")
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
```

> Look at [**syntax table**](#syntax-table) for more introduction about `forward()` and `right()`

#### Step 4: Finalize the program
Finalize the program with `done()` statement at the last line

```python
done()
```

> Look at [**syntax table**](#syntax-table) for more introduction about `done()` statement

#### Step 5: Complete code for square

```python
from turtle import *

# Square program without loop
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)

done()
```

#### Step 6: Run the square program
Run the program by pressing `Ctrl + B` if it presents the result as below:

![](/images/turtle/result.png)

### Draw shapes in practice

#### Draw a triangle

```python
from turtle import *

# Triangle program with a loop
for each_time in range(3):
	forward(100)
	right(120)

done()
```

![](/images/turtle/01.png)

#### Draw a Polygon

```python
from turtle import *

# Polygram program with a loop
for each_time in range(6):
	forward(100)
	right(60)

done()
```

![](/images/turtle/02.png)

#### Draw polygons

```python
for each_square in range(18):
	color("red", "green")
	speed(100)
	for each_line in range(6):
		forward(100)
		right(60)
	left(20)

done()
```

![](/images/turtle/03.png)

#### Draw more polygons

```python
for each_square in range(36):
	color("red", "green")
	speed(100)
	for each_line in range(6):
		forward(100)
		right(10)
	left(20)

done()
```

![](/images/turtle/04.png)

#### Draw a symbol

```python
from turtle import *

reset()
Screen()
up()
goto(-320,-195)
width(70)

for i in range(7):
	color("green")
	down()
	forward(640)
	up()
	backward(640)
	left(90)
	forward(66)
	right(90)

width(25)
color("white")
goto(0,-170)
down()

circle(170)
left(90)
forward(340)
up()
left(180)
forward(170)
right(45)
down()
forward(170)
up()
backward(170)
left(90)
down()
forward(170)
up()
goto(0,300)

done()
```

![](/images/turtle/05.png)

> #### Homework: Draw different shapes at different position

Given following part of code with three coordinates `(-400, 100)`,`(0, 100)` and `(400, 100)`.Please complete this code to draw shapes below:

**Example code:**

```python
from turtle import *

width(10)
speed(100)
penup()
goto(-400, 100)
pendown()
forward(100)

done()
```

**Output:**

![](/images/shapes.png)

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>