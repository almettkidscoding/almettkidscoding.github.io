---
title: "Wrap up Exercise - List"
date: 2019-12-05T15:15:33+08:00
weight: 11
pre: "<b>11. </b>"
chapter: false
---

### Class objectives
- [**List Exercises**](#list-exercises)
- [**More on Lists**](#more-on-lists)
- [**Most common List functions**](#most-common-list-functions)
- [**Homework**](#homework)

### List Exercises

#### Exercise 1: Print common items in two lists

Given two empty lists `lst1` and `lst2`. `random.randint(1, 50)` generates random numbers from 1 to 50. Randomly add 10 numbers to each empty list, write a function to print common items.

```python
import random

lst1 = []
lst2 = []

def randomly_add_items(lst1, lst2):

def find_common_items(lst1, lst2):

```

#### Exercise 2: Remove duplicated items from a list

Given a lst of integers. Write a function to remove duplicated items and return in a new list.

```python
lst = [12, 23, 34, 23, 34, 25, 65, 32, 25]

# Implement this function to return [12,23,34,25,65,32]
def remove_dups(lst):

```

#### Exercise 3: Return the sum of list items

Given two lists with the same length of integer items. Write a function to return sum of list items in a new list.

```python
lst1 = [1,2,3,4,5]
lst2 = [2,3,4,5,6]

# Implement the function to return [3,5,7,9,11]
def add_list_items(lst1, lst2):

```

### More on Lists

#### Most common List functions

Following are some common Python functions to process data. Here it comes to level up in Python lists, do more fun and exciting exercises.

|  <center>Function name</center>  |  <center>description</center>  |
|:----------|:-------------:|
|  <center>append(item)</center>   | add object at end |
|  <center>insert(pos, item)</center>  | add object anywhere |
|  <center>remove(item), pop()</center>  | delete object |
|  <center>reverse()</center>  | reverse in-place , changes original list |
|  <center>sort()</center>  | sort in-place, changes original list |
|  <center>reversed()</center>  | copy of reversed |
|  <center>sorted()</center>  | copy of sorted |
|  <center>extend()</center>  | merger another list |
|  <center>count(item)</center>  | number of occurrences |
|  <center>index(item)</center>  | first index of a value |
|  <center>max(lst)</center>  | max value of list items |
|  <center>min(lst)</center>  | min value of list items |

Persumably, list is a box of chocolates in which chocolates in and out. Possible occasions are, chocolates are eaten, new ones are in or they are given to others. Basically, Python offers function to each of those occasions.

#### `append(item)`: Add a item to the end of the list

```python
lst = [1,2,3,4,5]
lst.append(6)

print(lst) # returns [1,2,3,4,5,6]
```

#### `insert(pos, item)`: Insert a item to a position

```python
lst = [1,2,3,4,5]
lst.insert(2, 6) # insert 6 to index 2

# returns [1,2,6,3,4,5]
# 6 becomes the item at index 2
print(lst)
```

#### `remove(item)` or `pop()`: Remove a item from the list

```python
lst = [1,2,3,4,5]
lst.remove(3) # remove item 3 from the list
print(lst) # returns [1,2,4,5]

an_item = lst.pop() # return 5
another_item = lst.pop() # return 4
print(lst) # return [1,2]
```

#### `reverse()`: Reverse a list

```python
lst = [1,2,3,4,5]
lst.reverse()

print(lst) # returns [5,4,3,2,1]
```

#### `sort()`: Sort a list

```python
lst = [3,1,4,2,5]
lst.sort() # sort the list
print(lst) # returns [1,2,3,4,5]
```

#### `count(item)`: Counts numbers of this item in the list

```python
lst = [1,2,3,3,4,5,6,6,7,6]
print(lst.count(6)) # returns 3
```

#### `index(item)`: Returns the index of the item

```python
lst = [1,2,3,4,5]
print(lst.index(4)) # returns 3
```

#### `max(lst)`: Returns the max value of list items

```python
lst = [12,34,432435,54,62,3232]
print(max(lst)) # returns 432435
```

#### `max(lst)`: Returns the min value of list items

```python
lst = [12,34,432435,54,62,3232]
print(min(lst)) # returns 12
```
> #### Homework

Given a unsorted list of integers. Write a function to return the biggest item.

```python
lst = [13,42,23,543,23,54,134]
def return_max(lst): # returns 543

```

>##### Hints

- Not allowed to use `max(lst)` function
- Not necessary to sort the list
- You are encouraged to solve the problem with algorithm(which basically means using loops, conditionals and mathmatical operations)
- Assume a random number A is the biggest number and loop through the list to find bigger the one one than A