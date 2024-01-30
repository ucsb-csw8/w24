---
num: "Lecture 7"
desc: "Strings, Tuples, Namedtuples"
ready: true
lecture_date: 2024-01-30 11:00:00.00-7:00
---

Recorded Lecture: [1_30_24](https://drive.google.com/file/d/1UMwQa8PRHbDi4bZuHnieUCaYnCD6P70L/view?usp=drive_link)

## `not in` operator

* `not in` can be used and returns `True` if the element is not in the container, and `False` otherwise
* Example:

```python
evenNumbers = [2, "4", 6, "8", 6]
D = { 1234567:'A+', 7654321:'A-', 5555555:'B+' }
s = "CMPSCW8"

print("4" not in evenNumbers) #False
print(4 not in evenNumbers) #True
print(7654321 not in D) #False
print(9999999 not in D) #True
print("SCW" not in s) #False
print("CS" not in s) #True
print(3 not in [1, 2, 3]) #False
print(5 not in [1, 2, 3]) #True
```

## Strings
* Recall, a string represents a contains a collection of characters
* Similar to a list, each character (`str`) is an element in the collection
	* And each character has a position that can be indexed like a list
* Unlike lists, strings are **immutable** - we cannot directly replace a character once a string is created
* Example:

```python
s = "CMPSW8"
print(s[0])
print(s[3])
s[5] = "9" # error
s = "CMPSW9" # Ok
```

## Tuples
* Tuples are very similar to Python Lists, but they are **immutable**
	* Once a tuple is created, you cannot change its values
* Syntactically, tuples use `()` instead of `[]`
* Example:

```python
x = (1,3,5,7)
print(x)
print(type(x))
print(x[2])
x[2] = 15 # error
```

* Since tuples are immutable, if we need to update a value in the tuple, we have to create a new object with the updated value and reassign it to the variable

```python
x = (1,3,5,7)
print(x)
print(type(x))
print(x[2])
x = (1, 3, 15, 7) # replace value with new object
print(x)
```

## Namedtuples

* Lists and tuples are good when we want to extract values based on the index (position) of where it belongs in the container
* However, it can be easier to think of containers with values that can be accessed with an attribute name
* We can package things (attributes) into a namedtuple where each value in the namedtuple has an attribute name associated with it
* Having objects contain attributes is the basis for **Object-Oriented Programming (OOP)** (won’t get much into this, but CS 9 covers this in depth)
* Example:
	* A Student has a collection of many attributes like name, PERM, major, GPA, ...
	* So we can create a namedtuple representing a Student

```python
# Step 1: Allow your program to use namedtuples.
# Note: collections is a module that contains functionality for
# collection types, including namedtuples.
# Here we are simply using the namedtuple in this entire collection
from collections import namedtuple

# Step 2: Design what your object looks like
Student = namedtuple("Student", ["name", "ID", "major", "GPA"])
# Parameters of function, 1st is name of the namedTuple type – Student
# 2nd is a list containing the names of the attributes.

# Step 3: Create distinct student objects
# s1 and s2 refer to INSTANCES of Student namedtuples (each have their
# own values)
s1 = Student("John Doe", 12345678, "MUSIC", 3.5)
s2 = Student("Jane Doe", 87654321, "CS", 3.7)

# Step 4: Refer to specific fields within these namedtuples with '.'
print("Name of s1: ", s1.name)
print("ID of s1: ", s1.ID)
print("Major of s1: ", s1.major)
print("GPA of s1: ", s1.GPA)
print("Name of s2: ", s2.name)
print("ID of s2: ", s2.ID)
print("Major of s2: ", s2.major)
print("GPA of s2: ", s2.GPA)
```

* Namedtuples (like tuples) are immutable types
* So we can’t replace an attribute value once it has been created
* In order to update an attribute, we need to create a new namedtuple with the updated value
* Example:

```python
print(s1.GPA)
s1.GPA = s1.GPA + 0.1 # error
s1 = Student(s1.name, s1.ID, s1.major, s1.GPA + 0.1) # OK
print(s1.GPA)
```

## A brief note about `import` vs. `from`
* We can specify specific components we want to use in a module
	* `from [module] import [component]
* Similar to just using `import`, but now we don’t need the `[module].` syntax when using the component in our code
* Example:

```python
import math # gives us access to functionality in the math library
print(math.sqrt(4)) # how to use a math library function.

# "from" Example:
from math import sqrt
print(sqrt(4)) # no need to use "math." when calling sqrt function
```
