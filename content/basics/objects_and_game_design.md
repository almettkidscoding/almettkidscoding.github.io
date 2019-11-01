---
title: "Objects I"
date: 2019-11-01T14:25:57+08:00
weight: 8
pre: "<b>8. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction**](#syntax-table)
- [**What is an object?**](#what_is_an_object)
- [**Objects in game design**](#objects_in_game_design)
- [**Guessing game**](#Guessing_game)
- [**Homework**](#homework)

### Syntax table

|  <center>Keyword</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>class</center>   | A class is a code template for creating objects. Objects have member variables and have behaviour associated with them. In python a class is created by the keyword class. An object is created using the constructor of the class. |

### What is an object?

In computer science, an object can be a variable, a data structure, a function, or a method, and as such, is a value in memory referenced by an identifier. In the class-based object-oriented programming paradigm, object refers to a particular instance of a class, where the object can be a combination of variables, functions, and data structures.

![](/images/objects.jpeg)

#### How to define an object in Python?

```python
from turtle import *

class Car:
	def __init__(self, color, brand, model):
		self.color = color
		self.brand = brand
		self.model = model

	def draw(self):
		pencolor(self.color)
		forward(100)
		done()

ford = Car('Red', 'Ford', 'Mustang')
print(ford.color, ford.brand, ford.model)
ford.draw()
```

### Objects in game design

#### Turtle race

Once upon a time, four turtles come together to race. All of them are good at running, therefore, winner of each race is different. Let's see how does Python make it happen.

```python
from turtle import *
from random import randint

speed(0)
penup()
goto(-140, 140)

for step in range(15):
  write(step, align='center')
  right(90)
  for num in range(8):
    penup()
    forward(10)
    pendown()
    forward(10)
  penup()
  backward(160)
  left(90)
  forward(20)

red = Turtle()
red.color('red')
red.shape('turtle')

red.penup()
red.goto(-160, 100)
red.pendown()

for turn in range(10):
  red.right(36)

blue = Turtle()
blue.color('blue')
blue.shape('turtle')

blue.penup()
blue.goto(-160, 70)
blue.pendown()

for turn in range(72):
  blue.left(5)

green = Turtle()
green.shape('turtle')
green.color('yellow')

green.penup()
green.goto(-160, 40)
green.pendown()

for turn in range(60):
  green.right(6)

yellow = Turtle()
yellow.shape('turtle')
yellow.color('turquoise')

yellow.penup()
yellow.goto(-160, 10)
yellow.pendown()

for turn in range(30):
  yellow.left(12)

for turn in range(100):
  red.forward(randint(1,5))
  blue.forward(randint(1,5))
  green.forward(randint(1,5))
  yellow.forward(randint(1,5))

done()
```

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

### Guessing game

Guess a number from 1 to 99.

```python
import random

random_number = random.randint(1,99)
name = input('Hi, This is robot. What is your name? :')
print('Nice to meet you ' + name)
guess = input('Please guess a number from 1 to 99')

while 1 <= int(guess) <= 99:
	if int(guess) < random_number:
		print('Guess is too low')
		guess = input('Please try again')
	elif int(guess) > random_number:
		print('Guess is too hight')
		guess = input('Please try again')
	else:
		print('Yeay! You guessed it!')
		break
```

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

> #### Homework: Draw a phone

Given a class `Phone` with a function `draw_phone`. Please write the code to draw an iPhone.

**Code skeleton is below:**

```python
from turtle import *

class Phone:
	def __init__(self, name, brand):

	def draw_phone(self):
```

**Output:**

![](/images/turtle/iPhone.png)