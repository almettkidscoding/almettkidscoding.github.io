---
title: "While and Function"
date: 2019-10-25T13:52:51+08:00
weight: 7
pre: "<b>7. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction**](#syntax-table)
- [**How does while loop work?**](#how-while-loop-works)
- [**How to define a function?**](#how-to-define-a-function)
- [**Define a function with default argument values**](#define-a-function-with-default-argument-values)
- [**Call a function in another function**](#call-a-function-in-another-function)
- [**Yin Yang example of function calls**](#yin-yang-example-of-function-calls)
- [**Homework**](#homework)

### Syntax table

|  <center>Keyword</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>def</center>   | The keyword def introduces a function definition. It must be followed by the function name and the parenthesized list of formal parameters. The statements that form the body of the function start at the next line, and must be indented. |
|  <center>while</center>  | A while loop statement in Python programming language repeatedly executes a target statement as long as a given condition is true. |

### How while loop works?

While loop works with a bool condition. Here are two eesentials of a while loop:

- Works when the condition is `True`
- MUST have a stop condition or it goes in a dead loop.

For example:

```python
num = 0
while num <= 10:
	print(num)
	num += 1
```

or

```python
num = 0
while True:
	if num > 10:
		break
	print(num)
	num += 1
```

### How to define a function?

The keyword `def` introduces a function definition. It must be followed by the function name and the parenthesized list of formal parameters. The statements that form the body of the function start at the next line, and must be indented. Following is how to define a basic function:

```python
def count_down(num):
	while num > 0:
		print(num)
		num -= 1
```

Following is how to call a fuction and pass an argument:

```python
count_down(10)
```

### Define a function with default argument values

The most useful form is to specify a default value for one or more arguments. This creates a function that can be called with fewer arguments than it is defined to allow. For example:

#### Example #1

```python
def add_new_value(value, lst=[]):
	lst.append(value)
	return lst
```

Following is how to call this function:

```python
print(add_new_value("hello")) # returns ['hello']
```

#### Example #2

```python
def reverse_a_string(str01, str02=""):
	for index in range(len(str01) - 1,-1, -1):
		str02 += str01[index]
	return str02
```

Following is how to call this function:

```python
print(reverse_a_string("hello"))
```

### Call a function in another function

Following example demonstrates how a function is called from another one:

```python
from turtle import *

def draw_circle(sides, length):
    for i in range(sides):
        right(360/sides)
        forward(length)

def draw_object(sides, length):
    for i in range(sides):
        pencolor("red")
        right(360/sides)
        draw_circle(sides, length)

def main():
    speed(100)
    hideturtle()
    bgcolor("black")
    pensize(6)
    draw_object(14, 80)
    done()

main()
```

![](/images/turtle/orbid.png)

### Yin Yang example of function calls

In Chinese philosophy, yin and yang (/jɪn/ and; Chinese: 陰陽 yīnyáng, lit. "dark-bright", "negative-positive") is a concept of dualism in ancient Chinese philosophy, describing how seemingly opposite or contrary forces may actually be complementary, interconnected, and interdependent in the natural world, and how they may give rise to each other as they interrelate to one another. In Chinese cosmology, the universe creates itself out of a primary chaos of material energy, organized into the cycles of Yin and Yang and formed into objects and lives. Yin is the receptive and Yang the active principle, seen in all forms of change and difference such as the annual cycle (winter and summer), the landscape (north-facing shade and south-facing brightness), sexual coupling (female and male), the formation of both men and women as characters, and sociopolitical history (disorder and order).

```python
from turtle import *

def yin(radius, color1, color2):
    width(3)
    color("black", color1)
    begin_fill()
    circle(radius/2., 180)
    circle(radius, 180)
    left(180)
    circle(-radius/2., 180)
    end_fill()
    left(90)
    up()
    forward(radius*0.35)
    right(90)
    down()
    color(color1, color2)
    begin_fill()
    circle(radius*0.15)
    end_fill()
    left(90)
    up()
    backward(radius*0.35)
    down()
    left(90)

def main():
    reset()
    yin(200, "black", "white")
    yin(200, "white", "black")

main()
```

![](/images/turtle/yin_yang.png)

> #### Homework

Given two functions `stair()` and `make_stairs()`. Please draw a stair with 8 stairs.

**Input**

```python
stair(length, height=50):

make_stairs(each_stair_length, stairs=8):
```

**Output**

![](/images/turtle/stair.png)