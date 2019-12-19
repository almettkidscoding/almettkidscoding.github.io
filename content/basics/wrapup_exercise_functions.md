---
title: "Wrapup exercise - functions"
date: 2019-12-19T14:19:15+08:00
weight: 13
pre: "<b>13. </b>"
chapter: false
---

### Class objectives
- More on built-in functions and user defined functions
- More on arguments
- How Python treats more than one value return
- Three types of scopes

#### What is a function?

&nbsp;&nbsp;&nbsp;&nbsp;A function a sequence of statements which perform computation.Functions makes it possible to reuse the code.In Python we have two kinds of functions,<a href="https://docs.python.org/3/library/functions.html" target="_blank">built-in functions</a> and user defined function.The creators of Python, wrote a set of functions to address most common problems.And included them as a part of standard Python installation.

Examples:

`len(), abs(), int(), str(), print(), input(), open()` etc..

#### What are user defined functions?

&nbsp;&nbsp;&nbsp;&nbsp;Functions which are written by user, other than built-in functions,to solve a problem. A function is a reusable code,which takes arguments as inputs, does some computation, and returns a result. Some function takes arguments, some don’t,Like wise some function return result, and some don’t. Functions that do not return implicitly return the value None.

#### What is an argument?

&nbsp;&nbsp;&nbsp;&nbsp;An argument is a value passed to a function as an input during a function call. In Python its possible to have different options to pass arguments.

Four types of Arguments:


- [Required arguments](#required-arguments)
- [Optional arguments](#optional-arguments)
- [Variable positional arguments](#variable-positional-arguments)
- [Variable keyword arguments](#variable-keyword-arguments)

#### Required arguments

&nbsp;&nbsp;&nbsp;&nbsp;The calculator exercise is still fresh in our mind. Following code reminds us of the basic function.

```python
def add(num1, num2):
    return num1 + num2
 
 # Here both num1, num2, argument values are required at function call.
sum = add(10,20)
print(sum)
```

**Exercise 1: Simple calculator**

&nbsp;&nbsp;&nbsp;&nbsp;let's implement a calculator featured with addition, subtraction, multiplication and division.

#### Optional arguments

&nbsp;&nbsp;&nbsp;&nbsp;When funciton is defined with default values for arguments, passing values during function call is optional. Its possible to have default values for arguments.

```python
def add(num1=10, num2=30):
    return num1 + num2
 
#add called with no arguments
sum1 = add()
print("Sum is: ", sum1)

#add called with one arguments 
sum2 = add(30)
print("Sum is: ", sum2)

#add called with two arguments
sum3 = add(60, 50)
print("Sum is: ", sum3)
```

#### Variable positional arguments

&nbsp;&nbsp;&nbsp;&nbsp;Passing variable number of arguments. Most functions designed to work on fixed set of arguments. But some can handle any number of arguments. In Python its possible to pass varialbe arguments.

Lets see an example of this:

```python

def sum_numbers(*args):
    sum = 0
    for i in args:
        sum += i
    return sum
 
# Multiple arguments
sum_numbers(1,2,3,4,5,6)

# Or just two arguments
sum_numbers(1,2)

# Or no argument
sum_numbers()
```

**Exercise 2: Choose classes you like**

&nbsp;&nbsp;&nbsp;&nbsp;Given a funtion with two arguments, one of which is a positional argument, another is an optional argument. Postiional argument is class(es) available to choose, optional argument is a list of class(es) you have chosen. Please choose your favorite class(es) and return in the list.

```python
def favorite_class(*classes, my_favorite=[]):

	# Loop through the class(es), choose prefered classes by if...else conditionals

	return my_favorite
``` 

#### Variable keyword arguments

Variable number of keyword arguments, with key value pair passed to funciton.

```python
def user_details(**kwargs):
    for key, value  in kwargs.items():
        print("Keyword args : ".format(key, value))

# Pass single key value pair
user_details(name='Alim')

# Pass multiple key value pairs
user_details(name='Alim', age=28, country='China')
```

#### How Python treats more than one value return

&nbsp;&nbsp;&nbsp;&nbsp;Often a function takes arguments, does some computation, and returns a result. The return keyword is used for this. To get the result it has to be assigned to a variable, at the function call.

For example:

```python
def return_min_and_max(numbers):
	return min(numbers), max(numbers)

min_and_max_value = return_min_and_max([32,1,43,564,23,675,234])
print('Min value is: ', min_and_max_value[0]
print('Max value is: ', min_and_max_value[1]
```

**Exercise 3: Write an algorithm to return Min and Max in a single function**

```python
def min_max(numbers):
	min_value = 0
	max_value = 0

	# Write an algorithm to return two values together

	return min_value, max_value
```

#### Three types of scopes

1. Global scope

	Global variables can be accessed from anywhere

2. Local scope

	Local variables can be accessed only in block where defined

3. Nonlocal scope

	Accessible only in enclosing blocks(Inner functions, clousers)

Example 1:

```python
x = 2
 
def var_scope():
    y = 30
    print("I'm x and I'm global ", x)
 
    print("I'm y and I'm local ", y)
     
var_scope()
 
     
# output: 
"I'm x and I'm global  2"
"I'm y and I'm local  30"
```

Example 2:
 
```python
x = 2
 
def var_scope():
    y = 30
    x = 20
    print("I'm x and I'm local ", x)
 
    print("I'm y and I'm local ", y)
 
print("I'm x and I'm global ", x)
 
var_scope()

# Output:
"I'm x and I'm global  2"
"I'm x and I'm local  20"
"I'm y and I'm local  30"
```

> #### Homework: Students' score management system

&nbsp;&nbsp;&nbsp;&nbsp;Finals are coming, students are working hard on their exam preparation. Moreover, there is a big concern, it's becoming a challenge to manage student's scores. Headmaster made an announcement to let students who have coding skills to develop a 'Students exam score management system' to simplify the score management process. Could you please design a program which has arbitrary number of following features?

Required feature:

- Add student's exam score under their names

```python
def add_students_info(*names, *scores):

	# Do looping and adding


```

Optional features:

- Search student's score by name
- Categorize students by three leves and return in search result.

	For example:

	- score > 90 mark it as A
	- 90 > score > 60 mark it as B
	- score < 60 mark it as C

	Possible outputs:

	```python
	def students_info(student_name):
		# Do the searching

		return name, class, category
	# Outputs
	Frank Math A
	```