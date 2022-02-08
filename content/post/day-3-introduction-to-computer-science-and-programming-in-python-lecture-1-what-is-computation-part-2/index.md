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

Notes:

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

Consider, for example, finding the square root of 25. 

1.  Set g to some arbitrary value, e.g., 3. 
2.  We decide that 3*3 = 9 is not close enough to 25. 
3.  Set g to (3 + 25/3)/2 = 5.67.
4.  We decide that 5.67*5.67 = 32.15 is still not close enough to 25.
5.  Set g to (5.67 + 25/5.67)/2 = 5.04 
6.  We decide that 5.04*5.04 = 25.4 is close enough, so we stop and declare 5.04 to be an adequate approximation to the square root of 25

<!--EndFragment-->



This example describes an **algorithm**. An algorithm is a finite list of instructions that describe a **computation.**

The computation is executed on a set of inputs and will proceed through a set of well-defined states and eventually produse an output.

The process is perfectly described as a recipe from a cookbook.

1. Prepare food.
2. Add condiments. 
3. Taste
4. If the taste is good, stop.
5. Otherwise, repeat.

If you were to create a computer that finds the square root of a number it would be a **fixed-program computer**. This computer is only going to do this task.

The first modern computer was a **stored-program computer** (Manchester Mark 1). This computer would store and manipulate a sequence of instructions, and with components will execute any instruction in that sequence.

By creating an instruction-set architecture and detailing the computation as a sequence of instructions (i.e. program) we will get a highly flexible machine. By treating those instructions in the same way as data, a stored-program machine can easily change the program and can do so under program control. 

The heart of the computer then becomes a program = interpreter that can execute any legal set of instructions.

The flow of control:

Data and the program are in memory. There is a program counter that points to a particular location in memory, then the computation starts by executing the instruction at that point. 

The interpreter goes to the next instruction or it performs a test. Based on that test it can jump to a different point in the sequence of instructions.

The **Church-Turing thesis** states that if a function in computable, a Turing Machine can be programmed to compute it.

The **Universal Turing Machine** (named by Alan Turing) had an unbounded memory in the form of a "tape" on which one could write zeroes and ones, and some very simple primitive instructions for moving, reading, and writing to the tape. 

**Not all problems have computational solutions:** 

> Turing showed, for example, that it is impossible to write a program that given an arbitrary program, call it P, prints true if and only if P will run forever. This is known as the **halting problem**.

A programming language is said to be Turing complete if it can be used to simulate a universal Turing Machine. All modern programming languages are Turing complete.  ***Anything programmed in Python can be programmed in any other language.***

**Modern programming language have a much larger set of primitives.**

**Primitives** in Python: literals (3.2 and the string "abc") and infix operators (+ and /) - Examples

The **syntax** of a programming language is the same as the native language. You cannot write dog dog cat. Same in Python, you cannot write 3.2. 3.2, but you CAN write 3.2 + 3.2.

**Static semantics**: 3.2/abc -> written correctly but produces a static semantic error.

**Semantics**. Just like native languages, you can write something and mean a thing, but the result is that you insult the other person. This is the same in programming, a program must do the thing you want it to do. If it doesn't but still works, then it has failed. 

> **Finger exercise**: Computers can be annoyingly literal. If you don’t tell them exactly what you want them to do, they are likely to do the wrong thing. Try writing an algorithm for driving between two destinations. Write it the way you would for a person, and then imagine what would happen if that person were as stupid as a computer, and executed the algorithm exactly as written. How many traffic tickets might that person get?