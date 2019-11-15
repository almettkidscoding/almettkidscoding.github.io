---
title: "Modules"
date: 2019-11-15T14:07:53+08:00
weight: 8
pre: "<b>8. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction**](#syntax-table)
- [**Module**](#module)
- [**Standard Modules**](#standard-modules)
- [**Looking for more fun?**](#looking-for-more-fun)
- [**Homework**](#homework)

### Syntax table

|  <center>Syntax</center>  |  <center>Description</center>  |
|:----------|:-------------:|
|  <center>Module</center>   | A module is a file containing Python definitions and statements. |
|  <center>Standard Modules</center>   | Python comes with a library of standard modules, described in a separate document, the Python Library Reference (“Library Reference” hereafter). Some modules are built into the interpreter; these provide access to operations that are not part of the core of the language but are nevertheless built in, either for efficiency or to provide access to operating system primitives such as system calls. The set of such modules is a configuration option which also depends on the underlying platform. |
|  <center>dir()</center>   | The built-in function dir() is used to find out which names a module defines. |

### Module

A module is a file containing Python definitions and statements. The file name is the module name with the suffix .py appended. Within a module, the module’s name (as a string) is available as the value of the global variable `__name__`. For instance, use your favorite text editor to create a file called `toolbox.py` in the current directory with the following contents:

#### How to create a module?

```python
from turtle import *

def drawsquare(sidelength):
	for each_line in range(4):
		forward(sidelength)
		right(360/4)
	done()

def drawtriangle(sidelength):
	right(120)
	forward(sidelength)
	right(120)
	forward(sidelength)
	right(120)
	forward(sidelength)
	done()
```

#### How to import a module?

Now enter the Python interpreter and import this module with the following command:

```python
import toolbox
```

or

```python
from toolbox import *
```

or

```python
from toolbox import drawsquare, drawtriangle
```

#### How to call module functions?

Create another `.py` file for example is `modules.py`. Call `toolbox` functions from `modules.py`:

```python
from toolbox import *

drawsquare(100)
```

or

```python
import toolbox

toolbox.drawsquare(100)
```

or

```python
import toolbox

drawsquare = toolbox.drawsquare
drawsquare(100)
```

#### How to call a module from command line?

When you run a Python module with

```python
python3 modules.py <arguments>
```

the code in the module will be executed, just as if you imported it, but with the __name__ set to "__main__". That means that by adding this code at the end of your module:

```python
if __name__ == "__main__":
	import sys
	drawsquare(int(sys.argv[1]))
```

Execute the module from `Terminal` for example:

```python
python3 modules.py 100
```

Execution result will be a square with side length of 100.

### Standard Modules

#### The `dir()` Function

The built-in function dir() is used to find out which names a module defines. It returns a sorted list of strings:

```python
import toolbox, sys

print(dir(toolbox))
```

dir() lists the names you have defined currently:

```
['Pen', 'RawPen', 'RawTurtle', 'Screen', 'ScrolledCanvas', 'Shape', 'Terminator', 'Turtle', 'TurtleScreen', 'Vec2D', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'add', 'addshape', 'back', 'backward', 'begin_fill', 'begin_poly', 'bgcolor', 'bgpic', 'bk', 'bye', 'circle', 'clear', 'clearscreen', 'clearstamp', 'clearstamps', 'clone', 'color', 'colormode', 'degrees', 'delay', 'distance', 'divi', 'done', 'dot', 'down', 'drawsquare', 'drawtriangle', 'end_fill', 'end_poly', 'exitonclick', 'fd', 'fillcolor', 'filling', 'floordivi', 'forward', 'get_poly', 'get_shapepoly', 'getcanvas', 'getpen', 'getscreen', 'getshapes', 'getturtle', 'goto', 'heading', 'hideturtle', 'home', 'ht', 'isdown', 'isvisible', 'left', 'listen', 'lt', 'mainloop', 'mode', 'mul', 'numinput', 'onclick', 'ondrag', 'onkey', 'onkeypress', 'onkeyrelease', 'onrelease', 'onscreenclick', 'ontimer', 'pd', 'pen', 'pencolor', 'pendown', 'pensize', 'penup', 'pos', 'position', 'pu', 'radians', 'register_shape', 'reset', 'resetscreen', 'resizemode', 'right', 'rt', 'screensize', 'seth', 'setheading', 'setpos', 'setposition', 'settiltangle', 'setundobuffer', 'setup', 'setworldcoordinates', 'setx', 'sety', 'shape', 'shapesize', 'shapetransform', 'shearfactor', 'showturtle', 'speed', 'st', 'stamp', 'sub', 'textinput', 'tilt', 'tiltangle', 'title', 'towards', 'tracer', 'turtles', 'turtlesize', 'undo', 'undobufferentries', 'up', 'update', 'width', 'window_height', 'window_width', 'write', 'write_docstringdict', 'xcor', 'ycor']
```

### Looking for more fun?

We have a software called `pip`, from where we can install unlimited sources of Python modules and packages.

#### What is Pip?

pip is the package installer for Python. You can use pip to install packages from the Python Package Index and other indexes. Pip usually comes with Python3 by default. Look at the simple usage of pip below:

```python
pip3 install SomePackage
```

#### How to install a package?

Take [Freegames](http://www.grantjenks.com/docs/freegames/) package as an example. Open `Terminal`(in Mac) / `CMD`(in Windows) software copy/paste following command:

```python
python3 -m pip install freegames
```

Installation session ends with following information if it's succussful.

```
Collecting freegames
  Downloading https://files.pythonhosted.org/packages/73/ea/4139fe8661722f751a776c3cd46a807256cb74722799909edc8b0a42e4b0/freegames-2.3.1-py2.py3-none-any.whl (108kB)
    100% |████████████████████████████████| 112kB 413kB/s 
Installing collected packages: freegames
Successfully installed freegames-2.3.1

```

#### Let's try our first game

```python
python3 -m freegames.pacman
```

![](/images/games/pacman.png)

> #### Homework:

Create a calculator module `calculator.py`, import it from another Python file called `main.py`.

Required features of the calculator:

- Addition
- Subtraction
- Multiplication
- Division
- Floor division

`main.py` code probably looks like below:

```python
from calculator import add, sub, mul, divi, floordivi

print(add(8, 13))
...
...
...
```