---
num: "Lecture 6"
desc: "Assert Statements, Lists, Dictionaries"
ready: true
lecture_date: 2024-01-25 11:00:00.00-7:00
---

Recorded Lecture: [1_25_24](https://drive.google.com/file/d/16DDR1mE735PAGlVoIRyk1US0jMHd55qd/view?usp=drive_link)

# `assert` Statements

* When building anything, testing is an important part of a development process
	* Pilots test their planes before using them commercially (hopefully!)
* Software is complex. There’s a lot of code to do very complex things
	* Many engineers may be working on the same code to fix things, add features, improve performance, ...
* It’s up to the programmers to ensure their code is working
	* There isn’t an "autograder" to make sure functionality is working as it should
* A common way to ensure software is working properly is by writing checks to see if units of functionality are working according to the specification
	* zyBooks does this when you submit your code
* Python gives us the `assert` keyword to help us test the code we write
	* `assert` statements evaluate a boolean expression
		* If the expression evaluates to `True`, then the assert statement passes and code continues executing normally
		* If the expression evaluates to `False`, then an error is raised and program execution stops
* Example:

```python
print("Start")
assert 5 == 5
assert True
assert 6 <= 8
print("asserts pass so far!")
assert 4 == 5 # assert statement doesn't pass
print("4 == 5 doesn't pass") # doesn't print
```

* There are more formal ways to test our code, but `assert` statements are good "sanity checks" to make sure something isn’t wrong
* It’s common to use `assert` statements to test whether or not our function returns a correct value according to a specification
* Examples using `assert` to test a function:

```python
def isEven(value):
	''' Function that returns True if value is even,
		returns False otherwise '''
	if value // 2 == 0: # Error! Should use %
		return True
	else:
		return False

print("Checking isEven functionality")
assert isEven(3) == False # passes
print("passed isEven(3)")
assert isEven(2) == True # Fails, but should pass since 2 is even
print("passed isEven(2)")
```

* We can use assert statements to help us fix our problem

```python
def isEven(value):
	''' Function that returns True if value is even,
		returns False otherwise '''
	if value % 2 == 0: # Correct
			return True
	else:
		return False

print("Checking isEven functionality")
assert isEven(3) == False # pass
print("passed isEven(3)")
assert isEven(2) == True # pass
print("passed isEven(2)")
```

# Containers

* Our programs may want to have a variable refer to a collection of values, rather than just a single value
* Python provides several ways to store multiple values in a single object
* We’ve already seen some form of containers with strings
	* Strings are basically storing a container of characters
* Python’s `len()` function allows us to obtain the number of elements in a collection

## Lists

* A list is a collection of multiple values (similar to how a `str` is a collection of characters)
	* Note: Python Lists can consist of heterogenous (different) types
	* Lists can contain duplicate values
	* The bracket notation `[]` is used to represent a list type
	* We can extract specific elements in lists using an **index** value based on its position in the list
		* Note that the first value is referred to with index `[0]` (not 1)
* Example:

```python
evenNumbers = [2, "4", 6, "8", 6]
print(evenNumbers)
print(type(evenNumbers))
print(len(evenNumbers)) # 5
print(evenNumbers[2])  # gets t
print(evenNumbers[-1]) #gets the last element
evenNumbers[1] = "four" # replace index 1 with "four"
print(evenNumbers)
```

* Note that Python Lists are considered **mutable** types.
	* We can directly change a value in the List once it has been created
* **Immutable** types cannot directly change elements once it has been created

## Dictionaries

* A dictionary is a collection where we want a **unique** key mapping to another (non-unique) value
	* Works where a KEY (unique / immutable) maps to a VALUE (non-unique / immutable or mutable)
* Useful to make an association of a KEY : VALUE pair
* Dictionaries themselves are mutable (we can update a KEY : VALUE pair in the dictionary)
* Some examples could include Perm Numbers -> Grades, Zip Code -> City, Course Number -> Instructor, ...
* We can extract a KEY’s VALUE in dictionaries using the KEY
* General Syntax (notice curly braces are used instead of brackets), and notice the KEY:VALUE pairs are combined with `:`

```
{key1:value1, key2:value2, ... , keyN:valueN}
```

* Example:

```python
D = {} # Empty dictionary. Notice the curly braces instead of brackets ([])

# Dictionary (mapping unique PERM numbers to Grades)
D = { 1234567:'A+', 7654321:'A-', 5555555:'B+' }
print(type(D))
print(len(D)) # 3
print(D[7654321]) # returns value 'A+'
D[5555555] = 'A-' # updates KEY with new VALUE
print(D)
D[5463278] = 'A' # creates a new KEY : VALUE pair
print(D)
del D[1234567] # removes 1234567 KEY : VALUE pair
print(D)
```

## The `in` Operator

* Circling back to boolean operators, the `in` operator can be useful to detect if an element exists in the container
	* Returns `True` if the element is in the container, returns `False` if not
* For strings, we can check if a character (or substring) exists in a string
* For lists, we can check if an element exists in the list
* For dictionaries, we can check if an element is a key in the dictionary
* Examples:

```python
evenNumbers = [2, "4", 6, "8", 6]
D = { 1234567:'A+', 7654321:'A-', 5555555:'B+' }
s = "CMPSCW8"

print("4" in evenNumbers) #True
print(4 in evenNumbers) #False
print(7654321 in D) #True
print(9999999 in D) #False
print("SCW" in s) #True
print("CS" in s) #False
print(3 in [1, 2, 3]) # True
print(5 in [1, 2, 3]) # False
```

