---
title: "String problem solving"
date: 2019-09-24T15:24:05+08:00
weight: 1
pre: "<b>1. </b>"
chapter: false
---

### Class Objectives

- Practice problem solving in string data types.
- Learn how to interpret real world problem into computer problem
- More flexible usage of loops and conditionals
- Dive deeper to string data structure
- Process large and multi-dimensional string data in practice

### Problems
- [**Loop through strings**](#loop-through-strings)
- [**Character sorting**](#character-sorting)
- [**Type check**](#type-check)
- [**String reverse**](#string-reverse)
- [**Add suffix to string**](#add-suffix-to-string)

### Loop through strings

#### Requirements

&nbsp;&nbsp;&nbsp;&nbsp;Given a string consists of repeated characters. Write a function to process the string to return number of repeated characters in a dictionary.

- Not allowed to use `string.count(character)` function
- Your are encouraged to solve the problem with algorithms

**Input:**

```python
string = "The more that you read, the more things you will know, the more that you learn, the more places you willl go."
```

**Output:**

```python
{'T': 1, 'h': 7, 'e': 11, ' ': 21, 'm': 4, 'o': 10, 'r': 6, 't': 8, 'a': 5, 'y': 4, 'u': 4, 'd': 1, ',': 3, 'i': 3, 'n': 3, 'g': 2, 's': 2, 'w': 3, 'l': 7, 'k': 1, 'p': 1, 'c': 1, '.': 1}
```

#### Problem solving pattern

- Step 1: Define a function with a parameter
- Step 2: Define a dictionary
- Step 3: Loop through the string
- Step 4: Get keys of dictionary. `keys = dict.keys()` returns a list of keys
- Step 5: Check if each character in the string exists in the keys.
- Step 6: If it exists in the keys, increment it's value by 1, if not assign a value 1.

### Character sorting

#### Requirements

&nbsp;&nbsp;&nbsp;&nbsp;Given a string of random characters. Write a function to sort them in English alphabatical order.

- Noe allowed to use Python sort functions
- Solve the problem with algorithms

#### Problem solving pattern

**Input:**

```python
string = 'dsajlvwjeoijvdskavljwioenvjskdlahj'
```

**Output:**

```python
aaadddeehiijjjjjjkklllnoosssvvvvww
```

> #### Hint

- You may consider Python `chr()` and `ord()`

### Type check

#### Requirements

&nbsp;&nbsp;&nbsp;&nbsp;Given string of random letters, digits and symbols. Write a function to return them in different lists.

- You are encouraged to use regex

**Input:**

```python
import re 

string = 'fjsdlkajlv463247836ewiFJKS&*$^&#$JFIEfjdksljVLWEJKjdkfjkd'
```

**Output:**
```python
['f', 'j', 's', 'd', 'l', 'k', 'a', 'j', 'l', 'v', 'e', 'w', 'i', 'F', 'J', 'K', 'S', 'J', 'F', 'I', 'E', 'f', 'j', 'd', 'k', 's', 'l', 'j', 'V', 'L', 'W', 'E', 'J', 'K', 'j', 'd', 'k', 'f', 'j', 'k', 'd']

['4', '6', '3', '2', '4', '7', '8', '3', '6']

['&', '*', '$', '^', '&', '#', '$']
```
#### Problem solving pattern 

- Loop through the string by characters
- Check each character if it is the type of letters, digits or symbols.
- Return each list of result

### String reverse

#### Requirements

&nbsp;&nbsp;&nbsp;&nbsp;Write a function to reverse a given string.

- Your are encouraged to use algorithms
- Not allowed to Python embedded reverse functions

**Input:**

```python
string = "Children must be raught how to think, not what to think"
```

**Output:**

```python
"kniht ot tahw ton ,kniht ot woh thguar eb tsum nerdlihC"
```

### Problem solving pattern

- Step 1: Define a function with a parameter
- Step 2: Define a empty string variable
- Step 3: Loop through the string with for loop
- Step 4: Get the characters from the end until the beginning.
- Step 5: Add each character into the result string

### Add suffix to string

#### Requirements

&nbsp;&nbsp;&nbsp;&nbsp;Given a string consists of different words end with `ing`. Write a function to append `ly` to words end with `ing`, and `ing` to those are not end with `ing`, ignore those already are end with `ly`.

- Not allowed to use Python `endswith()`
- You are encouraged to use algorithms

**Input:**

```python
string = "He is fully absessed with eating. Eating and eating, don't stop forever!"
```

**Output:**
```python
"Heing ising fully absesseding withing eatingly. Eatingly anding eatingly, don'ting stoping forever!ing"
```

#### Problem solving pattern

- Step 1: Write a function with a parameter
- Step 2: Loop through the string to get each word
- Step 3: Check if each word ends with `ing` or `ly` by splitting the word
- Step 4: Add each word appropriate suffix and return the result 