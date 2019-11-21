---
title: "String 2"
date: 2019-11-13T13:54:13+08:00
weight: 2
pre: "<b>2. </b>"
chapter: false
---

#### String Exercises

Given a string below:

```python
str01 = 'This is a sample string'
```

#### Exercise 1

Check if string `am` exists in string `str01`, print `am is exist` if it's exist.


> ##### 【Hint】
- Step 1: Do `if...else` check if string `am` exists in the string `str01`
- Step 2: Print `am is exist` if it does.

#### Exercise 2

Write a program to convert the following list to string.

```python
# Input
['This', 'is', 'a', 'sample', 'string']

# Output
"This is a sample string"
```

> ##### 【Hint】
- Step 1: Define a function with a parameter lst. 
```python
def convertor(lst):
```
- Step 2: Define a empty string variable `string` to store the result string.
- Step 3: Loop through the `lst`, add each item to the `string` list with a space following behind.
- Step 4: If it comes to the last item, skip adding the space.
- Step 5: Return the result

#### Exercise 3

Reverse the given string:

```python
# Input
'This is a sample string'

# Output
'gnirts elpmas a si sihT'
```
> You're encouraged to accomplish this exercise with algorithms (with `for, while` loops and `if...else` conditionals). If it's out of your ability, you're allowed to use `Python` build-in functions such as `reverse()`

> ##### 【Hint】
- Step 1: Define a function with a parameter
```python
def rev(string):
```
- Step 2: Iterate through the string by `for` loop.
- Step 3: Define a empty string variable `result`
- Step 4: Add iterated items to the `result` variable from the end to the beginning.
Please pay close attention to the usage of `range`.
