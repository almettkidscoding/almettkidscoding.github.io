---
title: List
weight: 3
pre: "<b>3. </b>"
chapter: false
---

&nbsp;&nbsp;&nbsp;&nbsp;Python knows a number of compound data types, used to group together other values. The most versatile is the list, which can be written as a list of comma-separated values (items) between square brackets. Lists might contain items of different types, but usually the items all have the same type.

Example

    squares = [1, 4, 9, 16, 25]

Lists can be indexed and sliced:

	first_value = squares[0]  # indexing returns the item
	last_value = squares[-1]  # Returns the last value
	last_three_values = squares[-3:]  # Slicing returns a new value

Lists also support operations like concatenation:

	after_concatenation = squares + [36, 49, 64, 81, 100]

Unlike strings, which are immutable, lists are a mutable type, i.e. it is possible to change their content:

	squares[4] = 36

	output:
		1, 4, 9, 16, 36

You can also add new items at the end of the list, by using the append() method (we will see more about methods later):
	
	cubes.append(216)  # add the cube of 6
	cubes.append(7 ** 3)  # and the cube of 7

It is possible to nest lists (create lists containing other lists), for example:

	a = ['a', 'b', 'c']
	n = [1, 2, 3]
	x = [a, n]

	output:
		[['a', 'b', 'c'], [1, 2, 3]]