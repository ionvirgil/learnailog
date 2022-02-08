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

1. Set g to some arbitrary value, e.g., 3. 
2. We decide that 3*3 = 9 is not close enough to 25. 
3. Set g to (3 + 25/3)/2 = 5.67.
4. We decide that 5.67*5.67 = 32.15 is still not close enough to 25.
5. Set g to (5.67 + 25/5.67)/2 = 5.04 
6. We decide that 5.04*5.04 = 25.4 is close enough, so we stop and declare 5.04 to be an adequate approximation to the square root of 25

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

**The flow of control:**

Data and the program are in memory. There is a program counter that points to a particular location in memory, then the computation starts by executing the instruction at that point. 

The interpreter goes to the next instruction or it performs a test. Based on that test it can jump to a different point in the sequence of instructions.

The **Church-Turing thesis** states that if a function is computable, a Turing Machine can be programmed to compute it.

The **Universal Turing Machine** (named by Alan Turing) had an unbounded memory in the form of a "tape" on which one could write zeroes and ones, and some very simple primitive instructions for moving, reading, and writing to the tape. 

**Not all problems have computational solutions:** 

> Turing showed, for example, that it is impossible to write a program that given an arbitrary program, call it P, prints true if and only if P will run forever. This is known as the **halting problem**.

A programming language is said to be Turing complete if it can be used to simulate a universal Turing Machine. All modern programming languages are Turing complete.  ***Anything programmed in Python can be programmed in any other language.***

**Modern programming languages have a much larger set of primitives.**

**Primitives** in Python: literals (3.2 and the string "abc") and infix operators (+ and /) - Examples

The **syntax** of a programming language is the same as the native language. You cannot write dog dog cat. Same in Python, you cannot write 3.2. 3.2, but you CAN write 3.2 + 3.2.

**Static semantics**: 3.2/abc -> written correctly but produces a static semantic error.

**Semantics**. Just like native languages, you can write something and mean a thing, but the result is that you insult the other person. This is the same in programming, a program must do the thing you want it to do. If it doesn't but still works, then it has failed. 

> **Finger exercise**: Computers can be annoyingly literal. If you don’t tell them exactly what you want them to do, they are likely to do the wrong thing. Try writing an algorithm for driving between two destinations. Write it the way you would for a person, and then imagine what would happen if that person were as stupid as a computer, and executed the algorithm exactly as written. How many traffic tickets might that person get?

**Low level vs. high-level**: program using instructions and data objects at the level of the machine (move 64 bits of data from this location to that location) or whether we program using more abstract operations (e.g. pop up a menu on the screen) that have been provided by the language designer. 

**General vs. targeted** to an application: e.g. Python - general, SQL - targeted - you cannot build an operation system with it.

**Interpreted vs. compiled:** Python - interpreted by the interpreter, C - compiled - it is first converted by a compiler in a sequence of machine-level primitive operations.

**Chapter 2.1. - The basic elements of Python**

**A python program, also called a script is a sequence of definitions and commands**

Computational thinking?

* Declarative knowledge
* Imperative knowledge

A command is a statement

```python
print('yankees rule!')
print("but not in boston")
print("yankees rule,","but not in boston!")

yankees rule!
but not in boston
yankees rule, but not in boston!
```

The print function takes a variable number of arguments separated by commas, and prints them separated by a space character

Every object has a type.
Types are scalar or non-scalar.
Scalar objects are indivisible.
Non-scalar objects, for example, strings, have internal structure.
Many types of objects can be denoted by literals: 
    the text 2 is a literal representing a number
    the text "abc" a literal representing a string
The 4 types of scalar objects in python:
    int - used to represent integers (2, -3, 5, 10002)
    float - used to represent real numbers (3.0, 3.17, -28.72)
    bool - used to represent the boolean values True and False
    None - type with a single value.
Objects and operators can be combined to form expressions.
The expression 3+2 denotes the object 5 of type int.
The expression 3.0 + 2.0 denotes the object 5.0 of type float.
The == operator is used to test whether two expressions evaluate to the same value.
The !- operator us used to test whether two expressions evaluate to different values.
A single = means something quite different (from what i know of this is the assignment operator)
The simbol >>> is a shell prompt indicating that the interpreter is expecting the user to type some python code in the shell.
The built in function "type()"can be used to find out the type of an object

```python
type(3) # this prints the type int
type(3.0)# this prints the type float
```

**Operators**: 

i+j is the sum of i and j. If i and j are both of type int, the result is an int. If
either of them is a float, the result is a float.

i–j is i minus j. If i and j are both of type int, the result is an int. If either of
them is a float, the result is a float.

i*j is the product of i and j. If i and j are both of type int, the result is an int.
If either of them is a float, the result is a float.

i//j is integer division. For example, the value of 6//2 is the int 3 and the value of 6//4 is the int 1. The value is 1 because integer division returns the quotient and ignores the remainder. If j == 0, an error occurs.

i/j is i divided by j. In Python 3, the / operator, performs floating point division. For example, the value of 6/4 is 1.5. 

If j == 0, an error occurs. (In Python 2, when i and j are both of type int, the / operator behaves the same
way as // and returns an int. If either i or j is a float, it behaves like the Python 3 / operator.)
i%j is the remainder when the int i is divided by the int j. It is typically pronounced “i mod j,” which is short for “i modulo j.”

i\*\*j is i raised to the power j. If i and j are both of type int, the result is an
int. If either of them is a float, the result is a float.

The comparison operators are == (equal), != (not equal), > (greater), >= (at
least), <, (less) and <= (at most).

**Operators order is the same as in math.**

**The primitive  operators** on type bool are and, or, and not:
    a and b is True if both a and b are True, and False otherwise
    a or b is True if at least one of a or b is True, and False otherwise
    not a is True if a is False, and False if a is True

**Variables and assignment**

```python
pi = 3 # binds pi to object of type int
radius = 11 # binds radius 
area = pi * (radius **2)
radius = 14 #this binds the value but to no effect to area because that line is already evaluated
# A VARIABLE IS JUST A NAME, NOTHING MORE. AN ASSIGNMENT STATEMENT ASSOCIATES THE NAME TO THE LEFT OF THE = SYMBOL WITH THE OBJECT DENOTED BY THE EXPRESSION TO THE RIGHT OF THE = 
```

**!!!!PYTHON IS CASE SENSITIVE**

There are built in words in Python called keywords, and cannot be used as variable names.
**The reserved words in python 3 are:** and, as, assert, break, class, continue, def, del, elif, else, except, False, finally, for, from, global, if, import, in, is, lambda, nonlocal, None, not, or, pass, raise, return, True, try, while, with, and yield.
Use variable names **TO BETTER UNDERSTAND THE CODE**.
Use **COMMENTS** for **YOU** and **OTHERS TO UNDERSTAND THE CODE**.

***Did not know:***
    Python allows multiple assignment
    x, y = 2, 3 binds x to 2 and y to 3.



***Assignment 0*** 

**Write A Very Simple Program: Raising a number to a power and taking a logarithm**

```python
import numpy as np#import numpy, using it as "np"

print("Enter number x: ")#where x is the number
x = input() #the value of input is str
number=int(x)# convert the value of input to int
print("Enter number y: ") #where y is the power
y = input()
power=int(y)
result_power=number**power # raise the number to power, USE the new variables in which you assigned x and y
print(result_power)
logvalue=np.log2(result_power)#calculate the log and assign to logvalue
print(logvalue)# print the value
```