---
title: MIT OCW 6.0001 - Lecture 2 - Part 3 - Branching programs - Chapter 2.2.
date: 2022-02-16T13:31:46.793Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Log: Lecture 2 Readings - Chapted 2.2. Branching programs

The simplest branching statement is a conditional.

A conditional has three parts

1. a test i.e. an expression that evaluates to either true or false
2. a block of code that is executed if the test evaluates to true, and
3. an optional block of code that is executed if the test evaluates to false
   .
   Just like test hypothesis in statistics: test, if h1 accepted, h0 is not, else 
   h1 is rejected, h0 is accepted

After a conditional statement is executed, execution resumes at the code following the statement.

```
if boolean expression:
  block of code
else:
 block of code
 
or 
if boolean expression:
  block of code
```

Boolean expression indicates that any expression that evaluates to True or False can follow the reserved word if block of code indicates that any sequence of Python statements can follow else:

Identation is semantically meaningful in python.
When either the true block or the false block of a conditional contains 
another conditional, the conditional statements are said to be nested.

```python
if x%2==0:
    if x%3==0:
        print ('Divisible by 2 and 3')
    else:
        print('Divisible by 2 and not by 3')
elif x%3==0:
    print('Divisible by 3 and not by 2')
```

The elif in the above code stands for elseif
It is often convenien to use a compunt boolean expression in the test of a conditional, for example

```python
if x<y and x<z:
    print('x is least')
elif y<z:
    ('y is least')
else: 
    print('z is least')
```

Conditional allow us to write programs that are more interesting than straight -line programs
The class branching programs is still quite limited
Constant time programs are quite limited in what they can do
The topic of computational complexity - we will return to this topic

**Finger exercise:** write a program that examines three variables x, y, and z and prints the largest odd number among them. If none of them are odd it should print a message to that effect.

**Solution:**

```python
x = int(input("Introdu x:"))
y = int(input("Introdu y:"))
z = int(input("Introdu z:"))
if x%2==1 or y%2==1 or z%2==1:
    if x>y and x>z:
        print("X is the largest odd number")
    elif y>x and y>z:
        print("Y is the largest odd number")
    elif z>x and z>y:
        print("Z is the largest odd number")
elif x%2==0 or y%2==0 or z%2==0:
    print("None of them are odd")
```