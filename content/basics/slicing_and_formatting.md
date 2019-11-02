---
title: "Formatting, string and list slicing"
date: 2019-10-17T19:31:39+08:00
weight: 4
pre: "<b>4. </b>"
chapter: false
---

### Class objectives
- [**Key syntax introduction**](#syntax-table)
- [**String slicing and formatting**](#string-slicing-formatting)
- [**How to add items to a List?**](#how-to-add-items-to-a-list)
- [**List slicing**](#list-slicing)
- [**More on list**](#More-on-list)
- [**Homework**](#homework)

### Syntax table

|  <center>Keyword</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>str.format()</center>   | Perform a string formatting operation. The string on which this method is called can contain literal text or replacement fields delimited by braces {}. Each replacement field contains either the numeric index of a positional argument, or the name of a keyword argument. Returns a copy of the string where each replacement field is replaced with the string value of the corresponding argument. |
|  <center>str.isalpha()</center>   | Return true if all characters in the string are alphabetic and there is at least one character, false otherwise. Alphabetic characters are those characters defined in the Unicode character database as “Letter”, i.e., those with general category property being one of “Lm”, “Lt”, “Lu”, “Ll”, or “Lo”. Note that this is different from the “Alphabetic” property defined in the Unicode Standard. |
|  <center>str.isdigit()</center>   | Return true if all characters in the string are digits and there is at least one character, false otherwise. Digits include decimal characters and digits that need special handling, such as the compatibility superscript digits. This covers digits which cannot be used to form numbers in base 10, like the Kharosthi numbers. Formally, a digit is a character that has the property value Numeric_Type=Digit or Numeric_Type=Decimal. |
|  <center>str.islower()</center>   | Return true if all cased characters 4 in the string are lowercase and there is at least one cased character, false otherwise. |
|  <center>str.isspace()</center>   | Return true if there are only whitespace characters in the string and there is at least one character, false otherwise. |
|  <center>str.isupper()</center>   | Return true if all cased characters 4 in the string are uppercase and there is at least one cased character, false otherwise. |
|  <center>lst.append()</center>   | Add an item to the end of the list. Equivalent to a[len(a):] = [x].|
|  <center>str.split()</center>   | Return a list of the words in the string, using sep as the delimiter string. If maxsplit is given, at most maxsplit splits are done (thus, the list will have at most maxsplit+1 elements). If maxsplit is not specified or -1, then there is no limit on the number of splits (all possible splits are made).|

### String slicing and formatting

#### Slicing

```python
string = 'Hello, Python'
print(string[6:]) # Prints after index 6 which is Python

print(string[1:4]) # Prints from index 1 to index 4 

print(string[:-3]) # Removes the last three characters

print(string[::-1]) # Let's see what happens
```

#### Formatting

```python
name = 'Alex'
age = 9
string = "My name is {}, I'm {} years old".format(name, age)
print(string) # Let's see what is the result
```

#### Type converting

```python
print('I am ' + 9 + 'years old') # Let's see what happens
```

Valus of different types are not being able to added to one another. `str()` and `int()` are the functions convert `int` value to `string` and back.

```python
print('I am ' + str(9) + 'years old')

print('10' + str(6)) # 106

print(int('10' + 6)) # 16
```

> Look up [**Key syntax introduction**](#syntax-table) for more functions in String 

### How to add items to a list?

`append()` is the function to add items to a list. For example:

```python
a_list = ['Alex','Lucy', 'Andy']
a_list.append('Ryan')
print(a_list)
```

### List slicing

```python
a_list = ['Alex','Lucy', 'Andy', 'Ryan']

print(a_list[1:3]) # Prints the second the third item
```

> ### Homework: Separate items

Given a string and four empty lists:

#### Input

```python
str = "Today'S HOme WoRk iS abOuT SeparAtIng 12345 from chAraCterS"

lower_case_letters = []

upper_case_letters = []

digits = []

characters = []
```

Write a program to separate them into four empty lists and print.

#### Output

```python
['o','d','a','y'...]
['T','S','H','O'...]
[1,2,3,4,5]
['T','o','d','a','y','S'...]
```

<iframe src="https://trinket.io/embed/python/b9b4074bb7" width="100%" height="400" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>