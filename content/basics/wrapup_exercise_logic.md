---
title: "Wrapup exercise - logic"
date: 2019-12-13T11:53:40+08:00
weight: 12
pre: "<b>12. </b>"
chapter: false
---

### Class objectives
- Practice loops and conditionals in different cases
- Advanced usage of variables
- List comprihension basics

#### Character counter

Given a string variable of a sentence. Write a function with two parameters, return the number of target character in the string.

**Input:**

```python
string = 'Practice makes perfect'
```

**Write a function**

```python
def character_counter(string, char):
	counter = 0

	# process the string to count character

	return counter
```

**Output:**

```python
print(character_counter(string, 'p')) # returns 2
```

#### Problem solving pattern

**Solution 1:**

- Step 1: Define a function with two parameters `character_counter(string, char)`
- Step 2: Define a variable initial value of 0 `counter = 0`
- Step 3: Loop through the string to get each character
- Step 4: Check if the character equels to the target character
- Step 5: Increment counter by 1 if it is, continue if it's not
- Step 6: Return the final result at the end

**Solution 2:**

Solve it with list comprihension.

- One line of code
- You may consider list and `len()`

#### Students info

Given a list of lists, each list has two items, first item is age and second item is grade.

|  <center>Data</center>  |  <center>Conditions</center>  |  <center>Category</center>  |
|:----------|:-------------:|:-------------:|
|  <center>[10, 4]</center>   | age < 15 and grade < 9 |  Junior |
|  <center>[11, 5]</center>   | age < 15 and grade < 9 |  Junior |
|  <center>[16, 10]</center>   | age > 15 and grade > 9 |  Senior |
|  <center>[17, 11]</center>   | age > 15 and grade > 9 |  Senior |
|  <center>[9, 3]</center>   | age < 15 and grade < 9 |  Junior |

Write a function to categorize students info.

**Input:**

```python
data = [[10, 4], [11, 5], [16, 10], [17, 11], [9, 3]]
```

**Output:**

```python
['Junior', 'Junior', 'Senior', 'Senior', 'Junior']
```

#### Problem solving pattern

**Solution 1:**

- Step 1: Define a function with a parameter
- Step 2: Loop through the list data and check if satisfies conditions.
- Step 3: Append the category in a new list and return

**Solution 2:**

Figure out a solution in list comprihension.

#### Multiplication table

Write a function to print multiplication table in following pattern.

![](/images/multiplication_table.jpg)

> ##### Hint

Try nested for loops

> #### Homework: Return factorial of 10

Factorial is the product of all positive integers less than or equal to N. In our case N = 10, therefore, the result is 10 * 9 * 8 * 7 * 6 * 5 * 4 * 3 * 2 * 1 = 3628800

Write a function to return the factorial of 10.

How many solutions do you have?

You are encouraged to figure out the easiest solution.