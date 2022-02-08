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