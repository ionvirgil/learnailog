---
title: Day 4 - MIT OCW 6.0001 - Part 3
date: 2022-02-09T14:05:20.952Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Log: In the remaining time of the day I skimmed through the lecture notes and slides of the 2nd Lecture of 6.0001.

Notes

**Strings**

Strings are letters, special characters, spaces, digits

```python
#Strings are enclosed in quotation marks or single quotes
hi="hello there"

# You can concatenate strings
name="ana"
greet=hi + name
greeting = hi + " " + name


# You can do some operations on a string as defined in Python
silly=hi + " " + name * 3
# This will output 
"hello there anaanaana"

```

**INPUT/OUTPUT: print**

print is used to output stuff to console

keyword is `print`

```python
x = 1

print (x)
1

x_str = str(x)

x_str
Out[15]: '1'

type(x_str)
Out[16]: str
# this print function uses the integer 1, as seen using x 
print("my fav num is", x, ".", "x =", x)
my fav num is 1 . x = 1

# this print function uses the str x_str, which is 1, as seen using x 
print("my fav num is" + x_str + "." + "x =" + x_str)
my fav num is1.x =1

```

**INPUT/OUTPUT: input("")**

prints whatever is in the quotes

user types in something and hits enter

binds what value to a variable

```python
text = input ("Type anything... ")
# this will let the user enter something.
print (5*text)
# this will print the value entered * 5
# this means that if a user enters 3 for example
# the console will print 33333
# the value is not an integer because text was not defined

```

input gives you a string so must cast if working with numbers 



```python
num = int(input("Type a number..."))
# this line will let the user enter a value 
# the value is defines as int 
print (5*num)
# this line will print the value entered * 5
# if the used enters 3 
# the console will print 15, 3*5

```

**Comparison operators on int, float, string**

i and j are variable names

comparisons below evaluate to a boolean 

i>j

i>=j

i<j

i<=j

i==j -> the equality test, True if i is the same as j

i!= j -> the inequality test, True if i not the same as j

**Logic operators on bools**

a and b are variable names ( with boolean values)

not a-> True if a is False; False if a is True

a and b -> True if both are True

a or b -> True if either or both are True