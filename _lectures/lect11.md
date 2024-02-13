---
num: "Lecture 11"
desc: "For Loops, Range Function"
ready: true
lecture_date: 2024-02-13 11:00:00.00-7:00
---

Recorded Lecture: [2_13_24](https://drive.google.com/file/d/1Emp23ZC4p-Dn8NVhyKx_Dytb32UeapP2/view?usp=drive_link)

# For Loops

* A `for` loop is useful to go through a collection (lists, tuples, strings, sets, keys in Dict,... )

```
SYNTAX:
for VARIABLE in COLLECTION:
	STATEMENT(S)
```

* Assigns an element in the collection to the variable (starts with 1st item)
	* Executes STATEMENT(S)
* Assigns the next item in the collection to the variable
	* Executes STATEMENT(S)
* Continues program execution when there are no more items in the collection


* Example: Go through each element in a list

```python
numList = [10, 20, 30, 40]
for n in numList:
	print(n)
print("Done with loop")
```

* Example: Go through each character in a string

```python
s = "Python"
for char in s:
	print(char)
print("Done with loop")
```

* Example: print key / values in a dictionary

```python
D = {10:"ten", 20:"twenty"}
for k in D:
	print(k) # keys
	print(D[k]) # values
print("Done with loop")
```

* Example: Function that detects if an odd number exists in a list

```python
def hasOddNumber(intList):
	''' Returns True if the list has an odd number.
		Returns False otherwise.
	'''
	for x in intList:
		if (x % 2 != 0):
			return True
	return False		# common mistake. What does if / else: do?

numbers1 = [2,4,5,6,8]
numbers2 = [0,10,20,30]
numbers3 = []
print(hasOddNumber(numbers1))
print(hasOddNumber(numbers2))
print(hasOddNumber(numbers3))
```

# `range()` Function

* Sometimes, we may want to execute something a certain number of times (no more, no less)
	* We could write a while loop to utilize a variable to count the number of iterations
	* We can also generate a collection with a certain number of items using the `range()` function
* Assuming `x` and `y` are integers:
	* `range(x)`: generates a collection of positive integers from `[0, x)`
	* `range(x, y)`: generates a collection of integers from `[x, y)`
	* `range(x, y, z)`: generates a collection of integers starting from `[x,y)` every `z` steps
		* Note that if `z` is negative, it steps backwards from `x`
* Examples

```python
# Note that list() converts the range return to a list type to display each element
print(list(range(4))) # [0, 1, 2, 3]
print(list(range(2,5))) # [2, 3, 4]
print(list(range(5, 2))) # []
print(list(range(1, 7, 3))) # [1, 4]
print(list(range(7, 1, -2))) # [7, 5, 3]
```

* Examples using `range()` as a collection in `for` loops:

```python
# Example: count to 10
for i in range(10):
	print("num =", i+1)

# Also could do
for i in range(1, 11):
	print("num =", i)
```

```python
# Example: print first odd numbers up to 10
for i in range(1, 11, 2):
	print("num = ", i)

# Also could do
for i in range(11):
	if i % 2 == 1:
    	print("num = ", i)
```

# While Loops vs. For Loops
* It seems like we could either use for loops or while loops to solve the same problem. So when should we use one over the other?
	* It’s true that while loops and for loops can both be used to solve many of the same problems
	* But in general, if you **know** the number of iterations to traverse in a loop, for loops are preferred
	* If you **don’t know** the number of iterations (for example, user has to enter a certain input to terminate the loop), then a while loop is used

# Accumulator Pattern

* It’s very common to count occurrences of something in a collection
* We can use a for loop to go through each item and count the number of times something occurs in the collection
* We are **accumulating** (or counting) the number of occurrences in these cases
* Example, count odd numbers:

```python
def countOddNumbers(listOfNum):
	''' Returns the number of odd integers in listOfNum '''
	counter = 0
	for num in listOfNum:
		if num % 2 == 1:
			counter += 1
	return counter

numbers1 = [2, 4, 5, 6, 8, 9]
numbers2 = [0, 10, 20, 30]
print(countOddNumbers(numbers1)) # 2
print(countOddNumbers(numbers2)) # 0
```
