---
title: Day 5 - MIT OCW 6.0001 - Lecture 2 - Part 2
date: 2022-02-10T16:41:03.387Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Log: Today I learned that Control Flow is one of the fundamental pillars of programming. Control flow describes how a program validates conditions and executes expressions based on the conditions. Conditions and similar as those learned in uni, if, while, else, elif (this one will require some training, because I was used to else if).

Notes:

**CONTROL FLOW - BRANCHING (will come back to this after the course lecture)**

```python
if <exit right>:
<set background to woods_background>
if <exit right>:
<set background to woods_background>
if <exit right>:
<set background to woods_background>
and so on and on and on...
else:
<set background to exit_background>
else:
<set background to exit_background>
else:
<set background to exit_background>
```

if : if : if : and so on and on and on... else: else: else:

This code can be written as:

```python
while <exit right>:
  <set background to woods_background>
<set background to exit_background>
```

This makes a lot of sense. While you go right, you set the background to woods. 

**CONTROL FLOW - WHILE LOOPS (will come back to this after course lecture)**

`while <condition>:`

`       <expression>`

`        <expression>`

`       .....`

<condition> evaluates to a Boolean

if <condition> is True, do all the steps inside the while code block

check <condition> again

repeat until <condition> is False

**while LOOP EXAMPLE**

You are in the Lost Forest

`*************`

`*************`

` `

`************`

`************`

Go left or right?

**THE PROGRAM:**

`n = input("You're in the Lost Forest. Go left or right? ")`

`while n == "right":`

`      n = input("You're in the Lost Forest. Go left or right? ")`

`print ("You got out of the Lost Forest!")`

***You can only escape if you enter/go left!***

**CONTROL FLOW - while and for LOOPS (will come back to this after course lecture)**

iterate through numbers in a sequence 

**\# more complicated with while loop**

`n = 0`

`while n<5: `

`      print(n)`

`      n=n+1`

The program iterates while n is lower than 5.

**\# shortcut with for loop**

`for n in range(5): `

`       print(n)`

Less lines, still the same to understand but easier to write. Range is a specific function ( will learn more about it later)

**CONTROL FLOW - for LOOPS (will come back to this after course lecture)**

`for <variable> in range(<some_num>):`

`       <expression>`

`       <expression>`

`       .....`

each time through the loop, <variable> takes a value

first time, <variable> starts at the smallest value

next time, <variable> get the prev value + 1

etc.

***range(start, stop, step)***

**default values are start =0 and step =1  and optional**

**loop until value is stop - 1**

`mysum =0`

`for i in range(7, 10): `

`       mysum+=i`

`print(mysum)`



`mysum=0`

`for i in range(5,11,2):
    mysum+=i
    print(mysum)`

`5
12
21`

**Code explanation:**

i is 5, the starting point

mysum is 5

mysum+=i, mysum is 5, i is 7=> mysum is 12

mysum+=i, mysum is 12, i is 9=> mysum is 21

***NEED TO WORK SOME EXERCICES REGARDING CONTROL FLOW!!!!***



***break STATEMENT***

immediately exits whatever loop it is in 

skips remaining expressions in code block

exits only innermost loop!

`while <condition_1>:`

`         while<condition_2>:`

`         <expression_a>`

`          break`

`         <expression_b>`

`   <expression_c>`

**EXAMPLE**

mysum=0

for i in range(5, 11, 2):

\    mysum+=i

\    if mysum==5:

\    break

\    mysum+=1

print(mysum)

**Note: The program will stop at mysum==5, meaning the sum is 5, and not go to 12 and 21.**

**`for `vs `while `LOOPS**

`for`:

**know** number of iterations

can **end early** via `break`

uses a **counter**

**can rewrite** a `for `loop using a `while `loop

`while `loops:

**unbounded** number of iterations

can **end *early*** via `break`

can use a **counter but must initialize** before loop and increment it inside loop

**may not be able to rewrite** a `while `loop using a `for `loop