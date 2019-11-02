---
title: "Numbers, strings, list I"
date: 2019-09-24T15:24:05+08:00
weight: 2
pre: "<b>2. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction in this class**](#syntax-table)
- [**Brief introduction to Numbers**](#brief-introduction-to-number)
- [**Brief introduction to Strings**](#brief-introduction-to-string)
- [**Brief introduction to List**](#brief-introduction-to-list)
- [**How to do it in turtle?**](#practice-them-in-turtle)
- [**Homework**](#homework)

### Syntax table

|  <center>Keyword</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>width(integer)</center>   | Defines the width of the pen. Patameter - integer is a value type of int |
|  <center>if statement</center>   | is a conditional statement. |
|  <center>for statement</center>   | is a loop statement in which operations repeat itself for a limited amount of time |

### Brief introduction to Number

#### What is Number?
Numbers in Python are the same as the numbers you have learnt in math class. We have four mathmatical operators.

- addition +
- subtraction -
- multiplication *
- division /
- floor division //
- remainder %
- assign sign =
- equal sign ==

```python
print(5 + 7) # 12
print(5 - 3) # 2
print(6 * 3) # 18
print(9 / 3) # 3
print(10 // 3) # 3
print(7 % 2) # 1
print(5 == 5) # True
print(6 == 7) # False

num = 12
print(num) # 12
```

### Brief introduction to String

#### What is String?
String is the text we print in console or in turtle screen.

```python
print("Happy coding!") # Happy coding!
```

### Brief introduction to List

#### What is List?
List is a box full of `Strings` or `Numbers`. For example:

```python
# List of Number
list_of_number = [2, 3, 5, 1, 6]
print(list_of_number) # [2, 3, 5, 1, 6]

# List of Number
list_of_number = ["Python", "kids", "fun"]
print(list_of_number) # ["Python", "kids", "fun"]
```

### Practice them in turtle

#### How to print a String in turtle?
We need `write()` function to print a String in turtle. For example:

```python
from turtle import *

write("Python is fun!", align='center', font=('Arial', 38, 'bold'))
```

#### How to practice Number in turtle?
It's easy to do a calculation and present the result on turtle screen. For example:

```python
write("{0} + {1} = {2}".format(5, 7, 5 + 7), align="center", font=("Arial", 48, "bold"))
penup()
goto(0, 200)
write("{0} - {1} = {2}".format(5, 7, 5 - 7), align="center", font=("Arial", 48, "bold"))
penup()
goto(0, 100)
write("{0} * {1} = {2}".format(5, 7, 5 * 7), align="center", font=("Arial", 48, "bold"))
penup()
goto(0, -100)
write("{0} / {1} = {2}".format(5, 7, 5 / 7), align="center", font=("Arial", 48, "bold"))
penup()
goto(0, -200)
write("{0} // {1} = {2}".format(5, 7, 5 // 7), align="center", font=("Arial", 48, "bold"))
penup()
goto(0, -300)
done()
```

![](/images/turtle/operators.png)

#### How to practice List in turtle?
Assume we have random colors in a list, paint each shape in a different color. For example:

```python
square = 4
triangle = 3
colors = ["green", "yellow", "red"]
def draw(sides):
	width(30)
	if sides == square:
		color(colors[0])
	elif sides == triangle:
		color(colors[1])
	for each_side in range(sides):
		forward(200)
		right(360/sides)
	done()
```

if `draw(4)`

![](/images/turtle/green_square.png)

if `draw(3)`

![](/images/turtle/yellow_triangle.png)

> #### Homework: Draw shapes in different color

**Input**

Given a `function` with a parameter of `sides`. If `sides` is even, draw the shape in red color. If `sides` is odd, draw the shape in green color.

**For example**

```python
def draw_even_odd(sides):
```

**Output**

if `draw_even_odd(8)`

![](/images/turtle/red_polygon.png)

if `draw_even_odd(5)`

![](/images/turtle/green_polygon.png)

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>