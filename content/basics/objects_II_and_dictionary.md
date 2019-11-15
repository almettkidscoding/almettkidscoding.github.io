---
title: "Object II and Dictionary"
date: 2019-11-08T12:45:35+08:00
weight: 7
pre: "<b>7. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction**](#syntax-table)
- [**Dictionary**](#dictionary)
- [**Looping techniques**](#objects_in_game_design)
- [**Students information system design**](#students_information_system_design)
- [**Homework**](#homework)

### Syntax table

|  <center>Syntax</center>  |  <center>Description</center>  |
|:----------|:-------------:|
|  <center>Dictionary</center>   | It is best to think of a dictionary as a set of key: value pairs, with the requirement that the keys are unique (within one dictionary). A pair of braces creates an empty dictionary: {}. Placing a comma-separated list of key:value pairs within the braces adds initial key:value pairs to the dictionary; this is also the way dictionaries are written on output. |

### Dictionary

#### How to define a dictionary?

```python
dic = {'color':'颜色', 'name':'名字，名称', 'father':'父亲，爸爸', 'computer':'电脑，计算机'}
print(dic)
```

#### How to add a value to Dictionary?

```python
dic['program'] = '程序'
```

#### How to change the value of a key?

```python
dic['name'] = '名称'
```

#### How to delete a key/value?

```python
del dic['computer']
```


### Looping techniques

#### Print keys and values

```python
dic = {'color':'颜色', 'name':'名字，名称', 'father':'父亲，爸爸', 'computer':'电脑，计算机'}
for key, value in dic.items():
	print(key, value)
```

#### Print values only

```python
dic = {'color':'颜色', 'name':'名字，名称', 'father':'父亲，爸爸', 'computer':'电脑，计算机'}
for each_word in dic:
	print(dic[each_word])
```

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

### Students information system design

```python
# Code is coming soon
```

> #### Homework: Recall previous Python knowledge in a dictionary

Given a class with two functions `__init__()`, `add` and `show`.

- `__init__()`: Initializes the class
- `add()`: Adds a new key/value to the dictionary
- `show()`:  Shows all items in the dictionary

##### Basic skeleton of the code:

```python
class Students:
	def __init__(self, dic):

	def add(self, key, value):

	def show(self):
```

##### Expected result for example:

> Name: First class we have learnt: How to draw shapes in Turtle. How to use basic for loop.

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>