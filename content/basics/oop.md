---
title: "Object Oriented Programming"
date: 2019-12-27T13:05:20+08:00
weight: 14
pre: "<b>14. </b>"
chapter: false
---

#### What is Object Oriented Programming ?

&nbsp;&nbsp;&nbsp;&nbsp;OOP is a programming paradigm(style) for code organization and design.Object Oriented Programming concept developed in the 1960’s.The OOP paradigm breaks a program in to multiple cooperating objects.Then each object holds some data and functionality.

#### Characteristics of OOP Paradigm

1. Data and functionality are organized in object.
2. Perhaps most widely used programming paradigm
3. Better code re-usability and recycled.
4. Easily maintainable software
5. Promotes collaboration and code extension.

#### Why learn OOP?

1. Widely used programming paradigm
2.  With OOP its, Easier to use, read, collaborate, maintain and extend code
3. Complex software are to be managed, OOP helps in manage complex programs
4. Learning OOP is necessary next step to into the larger world of software development

#### What are OOP Three Pillars ?

1. Encapsulation
2. Inheritance
3. Polymorphism

#### What are the prerequisites for this course ?

1. Basic understanding Python syntax
2. Know how to write and debug small python functions
3. Knowledge of built in types like, numbers, strings, lists, tuples, dictionaries, sets, files
4. Understanding of how for and while loops work
5. Able to use conditional statements, if-elif-else

#### OOP in practice

Students' score management system involves two objects:

- Student
- Course

Following is the UML diagram:

![](/images/course_management_UML.png)

**Models**

```python
class Student:
	def __init__(self, name, grade):
		self.name = name
		self.grade = grade

class Course:
	def __init__(self, course, score):
		self.course = course
		self.score = score
```

**Controllers**

```python
from models import Student, Course


class Course_manager(Student, Course):
	result = {}
	scores = {}
	def __init__(self, name, grade, course, score):
		Student.__init__(self, name, grade)
		Course.__init__(self, course, score)

	def add_course(self):
		self.scores[self.course] = self.score
		self.result[self.name] = self.scores
		
	def show(self):
		print(self.result)
```

**Main**

```python
from models import Student
from controllers import Course_manager

math = Course_manager('Alex', 4, 'Math', 97)
math.add_course()
physics = Course_manager('Alex', 4, 'Physics', 90)
physics.add_course()
physics.show()
```

<hr>

> #### Homework: Design a simple Pong game

![](/images/turtle/pong.png)

Above is a screenshot of a simple Pong game. Please design a simple Pong game. Given requirements blow, try to fulfill as many requirements as possible.

- Draw a simple flowchart or UML diagram of the game. Illustrate Models and CLasses as explicit as possible.
- Try to create each components in Python. For example:

	- Create `models.py` for objects
	- Create 'Controllers.py' for functions
- Create a `main.py` to write the workflow of the game.

You are encouraged to accomplish each requirement to reach the end effect.

happy coding!