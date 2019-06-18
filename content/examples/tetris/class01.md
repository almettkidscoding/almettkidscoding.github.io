---
title: Set up Tetris UI
date: 2019-05-08T09:30:27+08:00
weight: 1
pre: "<b>1. </b>"
chapter: false
---

![](/images/)

### Simply go over the previous class

|<center>Task</center> 	   |         <center>Time</center>                   |
---------- | -------------------------------- |
| <center>Quickly go through the [**Previous class**](/examples/snake)</center>  | <center>10 mins</center>  |

### Step 1: Create a Python file `tetris_game.py`

As we have already learned how to create a Python file, open Sublime text editor -> File -> New File -> press `CTRL + S` -> name the file as `tetris_game.py`

### Step 2: Import required libraries

Copy and Paste the code snippet below to import required libraries.

	import sys, random
	from PyQt5.QtWidgets import QMainWindow, QFrame, QDesktopWidget, QApplication, QHBoxLayout, QLabel
	from PyQt5.QtCore import Qt, QBasicTimer, pyqtSignal
	from PyQt5.QtGui import QPainter, QColor
	from tetris_model import BOARD_DATA, Shape

**Introduction to the new libraries**

- **sys** - System-specific parameters and functions. This module provides access to some variables used or maintained by the interpreter and to functions that interact strongly with the interpreter. It is always available. ... If no script name was passed to the Python interpreter, argv[0] is the empty string.
- **PyQt5** is a comprehensive set of Python bindings for Qt v5. It is implemented as more than 35 extension modules and enables Python to be used as an alternative application development language to C++ on all supported platforms including iOS and Android.
- **Qt** (pronounced "cute") is a free and open-source widget toolkit for creating graphical user interfaces as well as cross-platform applications that run on various software and hardware platforms such as Linux, Windows, macOS, Android or embedded systems with little or no change in the underlying codebase while still being a native application with native capabilities and speed. 

### Step 3: Create a Tetris class which is inherited `QMainWindow`

	class Tetris(QMainWindow):
	    def __init__(self):
	        super().__init__()
	        self.isStarted = False
	        self.isPaused = False
	        self.nextMove = None
	        self.lastShape = Shape.shapeNone

- `class Tetris():` This is how a class declared in Python.
- `class Tetris(QMainWindow):` This is how a `Inheritance` declared in Python. Pass `QMainWindow` as a attribute to the Tetris class because the class `QMainWindow` is inherited by the Tetris class.
- `__init__` - When a class defines an `__init__()` method, class instantiation automatically invokes `__init__()` for the newly-created class instance. 
- `super().__init__()` - `super()` lets you avoid referring to the base class explicitly, 

### Step 4: Instantiate the tetris UI

In this process, we instantiate the tetris user interface where we put all elements together.

	def initUI(self):
        self.setWindowTitle('Tetris')
        self.show()

`initUI` is the function defined inside the Tetris class to customize the tetris UI. In additionally, it must be instantiated in the `__init()__`.


	class Tetris(QMainWindow):
	    def __init__(self):
	        super().__init__()
	        self.isStarted = False
	        self.isPaused = False
	        self.nextMove = None
	        self.lastShape = Shape.shapeNone

	        self.initUI()

	    def initUI(self):
	        self.setWindowTitle('Tetris')
	        self.show()

### Step 5: Main function call

	if __name__ == '__main__':
	    app = QApplication([])
	    tetris = Tetris()
	    sys.exit(app.exec_())

- `__main__` is the name of the scope in which top-level code executes. A module’s `__name__` is set equal to `__main__` when read from standard input, a script, or from an interactive prompt. A module can discover whether or not it is running in the main scope by checking its own __name__, which allows a common idiom for conditionally executing code in a module when it is run as a script or with python -m but not when it is imported:

### Step 6: Put them all together

All valid code that is written in this class is given below:


	import sys, random
	from PyQt5.QtWidgets import QMainWindow, QFrame, QDesktopWidget, QApplication, QHBoxLayout, QLabel
	from PyQt5.QtCore import Qt, QBasicTimer, pyqtSignal
	from PyQt5.QtGui import QPainter, QColor
	from tetris_model import BOARD_DATA, Shape

	class Tetris(QMainWindow):
	    def __init__(self):
	        super().__init__()
	        self.isStarted = False
	        self.isPaused = False
	        self.nextMove = None
	        self.lastShape = Shape.shapeNone

	        self.initUI()

	    def initUI(self):
	        self.setWindowTitle('Tetris')
	        self.show()

	if __name__ == '__main__':
	    app = QApplication([])
	    tetris = Tetris()
	    sys.exit(app.exec_())