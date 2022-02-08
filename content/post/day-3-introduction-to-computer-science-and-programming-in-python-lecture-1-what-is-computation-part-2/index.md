---
title: Day 3 - Introduction to Computer Science and Programming in Python -
  Lecture 1 - What is computation - Part 2
date: 2022-02-08T09:16:36.823Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Log: Today I solved the exercices from Lecture 1 discussed in class. Also, I read and absorbed the chapters from 1 to 2.1 from the textbook Introduction to Computation and Programming Using Python with Application to Understanding Data.

## In class questions and video solutions

Exercise 1. Running the code below from the editor

```python
    type(5)
    print(3.0-1)
```

Will print 2.0

Exercise 2. Python vs. Math 

Which is allowed in Python?

* x + y = 2
* x*x=2
* 2=x
* xy=2
* None of the above

The correct answer is xy=2, where 2 is assigned to "xy".

Exercise 3. Bindings

You run the code below from the file editor

```python
    usa_gold = 46
    uk_gold = 27
    romania_gold = 1
    
    total_gold = usa_gold + uk_gold + romania_gold
    print(total_gold)
    
    romania_gold += 1
    print(total_gold)
```

The program will print 74 then 74 because the value of total_gold has not increased. The only values that increased of that of romania_gold, which is now 2. 

Calculating again the total_gold will print 75.

```python
    usa_gold = 46
    uk_gold = 27
    romania_gold = 1
    
    total_gold = usa_gold + uk_gold + romania_gold
    print(total_gold)
    
    romania_gold += 1
    # RECALCULATE AGAIN total_gold
    total_gold = usa_gold + uk_gold + romania_gold
    print(total_gold)
```

## Readings - Chapters 1 - 2.1.

Computational thinking can be described in Declarative Knowledge and Imperative Knowledge.

**Declarative knowledge** is simply a statement of fact. One good example is "the square root of x is a number y, such as y*y = x". 

**Imperative knowledge** is the "how to" knowledge. How do you do this, or how do you do that. Heron of Alexandria is the first person who documented how a square root can be extracted from a number.

Method of finding the square root:

1. Start with a guess called g
2. If g*g is close enough to x, stop and say that g is the answer
3. Otherwise create a new guess by averaging g and x/g, i.e., (g+x/g)/2
4. Using this new guess, which we again call g, repeat the process until g*g is close enough to x

**Example**

<!--StartFragment-->

Consider, for example, finding the square root of 25. 1. Set g to some arbitrary value, e.g., 3. 2. We decide that 3\*3 = 9 is not close enough to 25. 3. Set g to (3 + 25/3)/2 = 5.67.3 4. We decide that 5.67\*5.67 = 32.15 is still not close enough to 25. 5. Set g to (5.67 + 25/5.67)/2 = 5.04 6. We decide that 5.04*5.04 = 25.4 is close enough, so we stop and declare 5.04 to be an adequate approximation to the square root of 25

<!--EndFragment-->