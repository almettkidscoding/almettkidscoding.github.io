---
title: "Wrap up Exercise - string"
date: 2019-11-28T13:53:32+08:00
weight: 10
pre: "<b>10. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction**](#syntax-table)
- [**Basic Exercises**](#basic-exercises)
- [**String exercises**](#string-exercises)
- [**Homework**](#homework)

### Syntax table

|  <center>Keyword</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>replace(target_value, new_value)</center>   | Python string method replace() returns a copy of the string in which the occurrences of old have been replaced with new, optionally restricting the number of replacements to max. |
|  <center>split()</center>  | Python string method split() returns a list of all the words in the string, using str as the separator (splits on all whitespace if left unspecified), optionally limiting the number of splits to num. |

### Basic Exercises

#### Exercise 1: Print even numbers below 100

```python
# Solution #1: Using while loop

# Solution #2: Using range(start, end, step)
```

#### Exercise 2: Print odd numbers below 50, in descending order

```python
# Solution #1: Using while loop

# Solution #2: Using range(start, end, step)
```

#### Exercise 3: Print biggest number

Write a function that takes three integer parameters, return the biggest.

```python
# Return the biggest number
def biggest_number(num1, num2, num3):

```

### String Exercises

#### Exercise 1: Check if 'is' presents in the string

```python
# Given a string
string = 'Python is a powerful programming language'

# Check if 'is' prsents in the string
def if_presents(substring):

```

Check if 'me' not presents in the string

#### Exercise 2: Get a new string from another string

```python
# Given a function `replace(target, value)` and a string
string = 'Hello Python'

# Write a function to return 'Hello World'
def replace_string(string):

```

#### Exercise 3: Return substring

```python
# Return the substring of the given string
string = 'Hello Python'
def return_substring(string):

# Return 'Hello P'
return_substring(string)
```

#### Exercise 4: Get certain values from a string

```python
# Given a string
string = '10,20,30,40,50,60,70'

# Return '40,50'
def return_certain_values(string):

```

> #### Homework

Write two functions one of which reverse the given string, another will check if the first string is reverse of the second string:

For Example:

```python
# Reverse the given string
def reverse_string(string):

# CHeck if the first string is reverse of the second string
# Return True of False
def reverse_check(string1, string2):

```