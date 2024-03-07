---
num: "Lecture 17"
desc: "Recursion"
ready: true
lecture_date: 2024-03-05 11:00:00.00-7:00
---

Recorded Lecture: [3_5_24](https://drive.google.com/file/d/1y9FNYIXLhvi26oMyxLwtcyb7zIoIWUgt/view?usp=drive_link)

* I'm linking my previous written exams from past CMPSC 8 offerings for **additional practice**.
* **Important Notes / Disclaimer:**
	* These previous offerings of CMPSC 8 were using a different textbook at the time, and you should recognize their limitations (order of topics and emphasis are different)
	* Do not rely on adequately preparing for the exam by only reviewing these sample exams, and only use these for additional practice. These exams were in-person/written/closed book/notes, so the type of questions our final will have may be very different. I expect students to adequately prepare for our final by reviewing zyBooks, lecture notes / recordings, and Gradescope labs
* Link to Midterm 1 from W18: [M1](https://sites.cs.ucsb.edu/~richert/cs8/exams/W18_M1.pdf)
* Link to Midterm 2 from W18: [M2](https://sites.cs.ucsb.edu/~richert/cs8/exams/W18_M2.pdf)
* Link to Final from W18: [FINAL](https://sites.cs.ucsb.edu/~richert/cs8/exams/W18_FINAL.pdf)

# Recursion
* When a function contains a call to itself
* We’re mostly familiar with writing code in an iterative fashion (one statement after the other)
	* Some programming languages exist where it’s based purely on recursion
* Recursive problems are useful when the result is dependent on the result of sub-parts

# Properties of Recursion
* One or more base cases that providing the **stopping** condition
* One or more recursive calls, where the arguments are **closer** to the base case than the function input

# Example: Computing sum of first n numbers
* We can think of the smallest sub problem (`n == 0`) since we don’t have any work to do in this case (we just return 0)
	* If `n > 0`, we can break down the general problem as being dependent on the results of the sub problem
		* `summation(n) = n + summation(n-1)`
		* Note that `summation(n-1)` is getting closer to the base case (`n == 0`)
			* What happens when `n == -1`? The recursive calls are moving **away** from the base case

```python
def summation(n):
	''' Returns the sum of the first n numbers (assuming
		n >= 0) '''

	# Approach 1: While loops
	#temp = 0
	#result = 0
	#while temp <= n:
	#	result += temp
	#	temp += 1
	#return result

	# Approach 2: For loops
	#result = 0
	#for x in range(n+1):
	#	result += x
	#return result

	# Approach 3: Recursion
	if n == 0: # could also think of using n == 1
		return 0
	return n + summation(n-1)

print(summation(0))
print(summation(1))
print(summation(3))
print(summation(5))
```

# Recursive Search and Binary Search

* Finding an element in a collection is a common operation
	* Python already provides the `in` operator to do this
* We can approach the problem using loops, for example:

```python
def find(collection, item):
	for element in collection:
		if element == item:
			return True
	return False

assert find([1, 5, 3, 7, 4, 2], 1) == True
assert find([1, 5, 3, 7, 4, 2], 2) == True
assert find([1, 5, 3, 7, 4, 2], 7) == True
assert find([1, 5, 3, 7, 4, 2], 8) == False
```

* Recursively, we can think of searching for an element in the collection by checking if the first element is located at index 0
	* If index 0 doesn’t have what we’re looking for, then we run the same search algorithm but only look at the rest of the list (excluding index 0)
	* Repeat this recursively until we find what we’re looking for (or there are no more elements to check)

```python
def find(collection, item):
	if len(collection) == 0:
		return False

	if collection[0] == item:
		return True
	return find(collection[1:], item)
```

* **Binary Search** is an efficient algorithm used to find elements in a collection with SORTED elements
* Think of a number guessing game (guess number between [0 - 100])
* Where would you start to optimally reduce the number of guesses?
	* By starting in the middle, if we didn’t guess the right number, we can eliminate HALF of the search space elements in a single guess
		* If the guess was larger than what we’re trying to find, then we will need to recursively check [0 - 49]
		* If the guess was smaller than what we’re trying to find, then we will need to recursively check [51 - 100]
	* We repeat this until we find what we’re looking for OR we didn’t find it at all

```python
def binarySearch(intList, item):
	if len(intList) == 0: # base case
		return False

	mid = len(intList) // 2

	if intList[mid] == item:
		return True
	elif item < intList[mid]:
		return binarySearch(intList[0:mid], item)
	else:
		return binarySearch(intList[mid+1:], item)

assert binarySearch([1,2,3,4,5,6,7,8,9,10], 5) == True
assert binarySearch([1,2,3,4,5,6,7,8,9,10], -1) == False
assert binarySearch([1,2,3,4,5,6,7,8,9,10], 11) == False
assert binarySearch([1,2,3,4,5,6,7,8,9,10], 1) == True
assert binarySearch([1,2,3,4,5,6,7,8,9,10], 10) == True
```

# Accumulator Pattern with Recursion

* We can use recursion to traverse through a collection and accumulate values similar to what we’ve seen using loops
	* For example, we could count occurrences, build and return a new collection, etc.
* Let’s recursively count multiples of a number in a list

```python
def countMultiples(collection, num):
	if len(collection) == 0:
		return 0
	if collection[0] % num == 0:
		return 1 + countMultiples(collection[1:], num)
	return countMultiples(collection[1:], num)

assert countMultiples([1,2,3,4,5,6,7], 3) == 2
assert countMultiples([1,2,3,4,5,6,7], 2) == 3
assert countMultiples([1,2,3,4,5,6,7], 8) == 0
```

* If we change the problem and want to return a list that only contains multiples, we can accumulate a list recursively:

```python
def keepMultiples(collection, num):
	if len(collection) == 0:
		return []
	if collection[0] % num == 0:
		return [collection[0]] + keepMultiples(collection[1:], num)
	return keepMultiples(collection[1:], num)

assert keepMultiples([1,2,3,4,5,6,7], 3) == [3, 6]
assert keepMultiples([1,2,3,4,5,6,7], 2) == [2, 4, 6]
```

