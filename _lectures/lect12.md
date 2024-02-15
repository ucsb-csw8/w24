---
num: "Lecture 12"
desc: "More on loops"
ready: true
lecture_date: 2024-02-15 11:00:00.00-7:00
---

Recorded Lecture: [2_15_24](https://drive.google.com/file/d/1mRwpufpu2iyT7XA3Ixpgz33uc9DACTTN/view?usp=drive_link)

# Accumulator Pattern Example

```python
def countCapitalWords(listOfString):
	''' Returns the number of strings in listOfString that start
		with a capital letter (A - Z)'''
	counter = 0
	for s in listOfString:
		if len(s) > 0:
			if ord(s[0]) >= 65 and ord(s[0]) <= 90: # str.isupper() works too
				counter += 1
	return counter

assert countCapitalWords([]) == 0
assert countCapitalWords([""]) == 0
assert countCapitalWords(["1", "A1"]) == 1
assert countCapitalWords(["A", "b", "C"]) == 2
```

# Nested Loops

* Depending how data is organized, it’s common to see loops **within** loops
* For example, given a list of strings, we may want to manually count how many vowels exist in all of the lists
* A generic example, trace what the output will look like for the following code:

```python
for i in range(3):
	for j in range(10, 12):
		print(i, j)
```

* Another example: given a list of strings, count the number of vowels that exist in all the strings in the list:

```python
def countVowels(strList):
	vowels = "AEIOUaeiou"
	numVowels = 0
	for s in listOfStrings: # s is an element in listOfStrings
		for c in s:			# c is a character in s
			if c in vowels:
				numVowels += 1
	return numVowels

listOfStrings = "This is a list of strings".split()
assert countVowels(listOfStrings) == 6
```

# `break` and `continue`

* It’s possible to jump out of a loop using the `break` statement
* It’s also possible to also check and see if you want to stop the current iteration of a loop, and continue with the next iteration using the `continue` statement
* Examples (trace the code):

```python
x = 0
while True:
	x = x + 1
	print("Start of while body, x =", x)
	if x > 3:
		break
	print("End while body, x =", x)
print("outside while loop")
```

```python
x = 0
while True:
	x = x + 1
	print ("Start of while body, x =", x)
	if x % 2 == 0: # if x is even
		continue
	if x >= 5:
		break
	print("End of while body, x =", x)
print("Outside while loop")
```

* Note that `break` and `continue` both apply to `while` and `for` loops
* An example using `continue` in a for loop:

```python
for i in range(5):
	print("i at start of iteration:", i)
	if i % 2 == 1:
		continue
	print("i at end of iteration (even):", i)
print("Done with loop")
```

# Loop else

* Python allows `else` blocks to be used in looping constructs
* It’s used to execute code **IF** the loop terminates naturally (and does not terminate with a `break` statement)
* Examples:

```python
i = 0 # change this to 4 to see else statements execute

while i < 10:
	print("i =", i)
	if i == 3:
		break
	i += 1
else:
	print("only see this if break was not executed")

print("Continue execution")
```

```python
numbers = [1,2,3]

for i in numbers:
	print("i =", i)
	if i == 2: 	# change this to 4 to see else statements execute
		break
else:
	print("only see this if break was not executed")

print("Continue execution")
```

# Enumerate

* The `for` loop iterates through a collection and assigns each element value to a variable
* But sometimes we may want to get a value AND its index in the container
* `enumerate()` allows us to obtain an element’s index AND corresponding element at the same time
	* This uses the concept called **unpacking**. Basically, we can assign multiple assignments in one expression. For example:

```python
element1, element2 = ["A", "Z"]
print(element1) # A
print(element2) # Z
```

* `enumerate` example:

```python
letters = ["A", "B", "C"]
for (index, value) in enumerate(letters):
	print("index = ", index, ", value = ", value, sep="")
```

* But what happens with containers with elements like `set` or `dict`?
* `enumerate` will still run without an error, but index values seem arbitrary (and probably useless - what would we do with the index values?)
* Example:

```python
letters = {"A", "B", "C", "D", "E"}
for (index, value) in enumerate(letters):
	print("index = ", index, ", value = ", value, sep="")
```

# A Number Guessing Game Example

```python
magicNumber = 40
guess = input("Guessing Game!\nPlease enter an int between 0 - 100 \
(type 'exit' to end game): ")

while True:
	if guess == "exit":
		print("Game over!")
		break
	number = int(guess)
	if number < 0 or number > 100:
		guess = input("Invalid number. Please try again: ")
		continue
	if number < magicNumber:
		guess = input("Too small. Please try again: ")
		continue
	if number > magicNumber:
		guess = input("Too big. Please try again: ")
		continue
	if number == magicNumber:
		print("Winner winner chicken dinner! You guessed", magicNumber)
		break
print("Done.")
```
