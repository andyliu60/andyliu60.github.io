---
title: input和raw_input的比较
date: 2018-12-05 15:21:48
tags:
- Python
categories:
- 编程
---
**input会假设用户输入的是合法的Python表达式。**

例子

		>>> name = input("What is your name? ")
		What is your name? John
		Traceback (most recent call last):
		  File "<stdin>", line 1, in <module>
		  File "<string>", line 1, in <module>
		NameError: name 'John' is not defined

正确的输入应该是"John"

		>>> name = input("What is your name? ")
		What is your name? "John"
		>>> print name
		John

**raw_input会把所有的输入当作原始数据(raw data)，然后将其放入字符串中。**

例子

		>>> input("Enter a number: ")
		Enter a number: 3
		3
		>>> raw_input("Enter a number: ")
		Enter a number: 3
		'3'

**注意：由于raw_input会将原始数据放入字符串，因此，即使输入数字，也会转化为字符串。而input则不会将输入的数字转换为字符串。**

例子1

		>>> x = raw_input("x: ")
		x: 2
		>>> y = raw_input("y: ")
		y: 3
		>>> x * y
		Traceback (most recent call last):
		  File "<stdin>", line 1, in <module>
		TypeError: can't multiply sequence by non-int of type 'str'

例子2

		>>> x = input("x: ")
		x: 2
		>>> y = input("y: ")
		y: 3
		>>> x * y
		6