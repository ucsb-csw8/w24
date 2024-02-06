---
num: "Lecture 9"
desc: "Functions"
ready: true
lecture_date: 2024-02-06 11:00:00.00-7:00
---

Recorded Lecture: [2_6_24](https://drive.google.com/file/d/1KNbWcBt7zjFDm4lEFC2451ZgRROi2y8g/view?usp=drive_link)

# Function `return` Statement

* As discussed previously, a function may or may not have a `return` statement
* A function can only execute a `return` statement **ONCE**
* When a `return` statement is executed, Python stops executing code in the function, and the return value (or `None`) is returned back to the caller
* Example:

```python
def lotsOfReturns():
	print("before return 1")
	return 1
	print("after return 1") # will never print (might as well delete)
	return 2 # Will never execute (might as well delete)

print(lotsOfReturns()) # 1
```

* `return` statements don’t necessarily need to return a value (`None` is returned by default)
* But if a `return` statement with or without a value is executed, the function will stop executing

```python
def lotsOfReturns():
	print("before return 1")
	return # None is returned
	print("after return 1") # will never print (might as well delete)
	return # Will never execute (might as well delete)

print(lotsOfReturns()) # None
```

## Practice

* Let’s go back and consider the example of determining the class standing of a student, but in this case, we can put our logic into a function:

```python
def getClassStanding(units):
	''' Returns a string of either Freshman, Sophomore, Junior,
		Senior depending on the units '''

	if units < 50:
		return "Freshman"
	elif units < 90:
		return "Sophomore"
	elif units < 135:
		return "Junior"
	else:
		return "Senior"

numUnits = int(input("Enter number of units: "))
print(getClassStanding(numUnits))
```

* Note that the function definition must be declared before it is called
	* Python runs our code from top to bottom
	* If Python doesn’t see a function definition before it tries to call the function, it won’t know that the function exists
	* Try moving the function definition below the print statement, and see Python give you an error
* Also note, there are many ways we can structure our code to do the same thing
* Since the `getClassStanding(units)` immediately returns a value when a `return` statement is executed, we could possibly rewrite the function without `elif`s as:

```python
def getClassStanding(units):
	''' Returns a string of either Freshman, Sophomore, Junior,
		Senior depending on the units '''

	if units < 50:
		return "Freshman"
	if units < 90:
		return "Sophomore"
	if units < 135:
		return "Junior"
	else:
		return "Senior"
```

## `biggestInt` Example

* As an exercise, consider writing the `biggestInt(a, b, c, d)` function that returns the largest parameter value
* Assume we do a (very reasonable) attempt:

```python
def biggestInt(a, b, c, d):
	''' Function that will return the biggest value
		(a, b, c, or d) '''
	biggest = 0
	if a >= b and a >= c and a >= d:
		biggest = a
	if b >= a and b >= c and b >= d:
		biggest = b
	if c >= a and c >= b and c >= d:
		biggest = c
	else:
		biggest = d
	return biggest

assert biggestInt(1,2,3,4) == 4
assert biggestInt(1,2,4,3) == 4
assert biggestInt(1,4,2,3) == 4 # error
assert biggestInt(4,1,2,3) == 4 # error
```

* This above approach contained a logic error (try and see what went wrong)
	* Here, if `c` is not the biggest value, it will **always** assign `d` as the biggest value regardless of the value of `d`
* There are MANY ways we can correctly write this function
	* We could use `elif` appropriately to make sure conditions are checked correctly
	* Or we could immediately returning the largest value when one of the `if` statements returns `True`. For example:

```python
def biggestInt(a, b, c, d):
	''' Function that will return the biggest value
		(a, b, c, or d) '''

	if a >= b and a >= c and a >= d:
		return a
	if b >= a and b >= c and b >= d:
		return b
	if c >= a and c >= b and c >= d:
		return c
	return d
```


