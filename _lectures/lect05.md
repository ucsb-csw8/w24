---
num: "Lecture 5"
desc: "Boolean Expressions, Conditions / Branching"
ready: true
lecture_date: 2024-01-23 11:00:00.00-7:00
---

Recorded Lecture: [1_23_24](https://drive.google.com/file/d/17zq09-tSJLu22ZelBZ1cRBhb49rhYrAY/view?usp=drive_link)

# Boolean Type

* In programming languages, the ability to tell the computer to perform one thing in a situation vs. another thing in another situation enables programmers to customize the program’s flow of execution
* There is a specific type to represent a `True` or `False` value called `Boolean`
* We can program logic in our computer programs based on Boolean logic
* Example:

```python
x = True
y = False

print(x)
print(type(x))
print(y)
print(type(y))
```

# Relational Operators

* Python provides specific operators that will return a Boolean value
* Examples: `==` (equality), `!=` (inequality), `<` (less than), `<=` (less than or equal), `>` (greater than), `>=` (greater than or equal)
* Example:

```python
print(4 < 6) # True
print(4 == 4) # True
print(4 != 4) # False
print(4 >= 5) # False
print(4 <= 4) # True
```

# Branching with `if` Statements

* The basic construct to tell a program to do one thing or another is an `if` statement

```
Syntax:
if BOOLEAN_EXPRESSION:
	STATEMENT(S) # note these statements are tab indented
```

* The steps are to first evaluate the BOOLEAN_EXPRESSION (evaluates to `True` or `False`)
	* If `True`, execute the STATEMENT(S)
	* If `False`, skip STATEMENT(S) and continue execution
	* Indentation is important! It tells Pytho which statements belong to a specific block
* Example:

```python
milesDriven = 250
print("Should you pull over and fill up your gas tank?")

if milesDriven > 200:
	print("Yes, you need gasoline") # indented (part of the if block)

print("Drive safe") # not part of if block since not indented
```

# Branching With `if-else` Statements

* What if we want to do something specific i the event that the BOOLEAN_CONDITION is `False`?
* We can pair `if` statements with an `else` portion

```
Syntax:
if BOOLEAN_EXPRESSION:
	STATEMENT(S) #1
else:
	STATEMENT(S) #2
```

* The steps are to first evaluate the BOOLEAN_EXPRESSION (evaluates to `True` or `False`)
	* If `True`, **only** execute STATEMENT(S) #1
	* If `False`, **only** execute STATEMENT(S) #2
* Example:

```python
milesDriven = 50
print("Should you pull over and fill up your gas tank?")
if milesDriven > 200:
	print("Yes, you need gasoline")
else:
	print("No, you can keep driving")
print("Drive safe")
```

* You can nest expressions / functions to form your boolean expression. For example:

```python
if int(input("Enter your age (in years): ")) >= 21:
	print("You can drink alcohol, but do so responsibly")
else:
	print("Can’t drink alcohol yet ... how about some OJ?")

print("Enjoy the party!")
```

# Multi-branch / `elif` Statements

* An example of using multi-branches to determine class standing based on units

```python
numUnits = int(input("Enter number of units: "))

if numUnits < 50:
	print("Freshman status")
else:
	if numUnits < 90:
		print("Sophomore status")
	else:
		if numUnits < 135:
			print("Junior status")
		else:
			print("Senior status")
print("Done!")
```

* Note we will only print out one status and can embed multiple `if / else` statements in a block
* Also note if we had many conditions to check, our code could get messy (leans to the right)
* `else: if` patterns are common, so Python allows us to combine these together into `elif` statements.
* We can rewrite the same code in the following (cleaner) way:

```python
numUnits = int(input("Enter number of units: "))

if numUnits < 50:
	print("Freshman status")
elif numUnits < 90:
	print("Sophomore status")
elif numUnits < 135:
	print("Junior status")
else:
	print("Senior status")

print("Done!")
```

# Logical Operators

* Python provides specific operators that use Boolean values to return a Boolean value
* Logical operators include `and`, `or`, `not` 
* When using logical `or` operator
	* `True` `or` anything → `True`
	* `False` `or` `False` → `False`
* When using logical `and` operator
	* `False` `and` anything → `False`
	* `True` `and` `True` → `True`
When using the `not` operator, it turns `True` → `False`, and `False` → `True`

* High level language example:
	* Think of two given facts like:
		* I am hungry
		* I am cold
	* [I am hungry] `or` [I am warm] → `True or False` → `True`
	* [I am hungry] `and` [I am warm] → `True and False` → `False`
	* `not` [I am hungry] → `not True` → `False`

## Detecting Numberical Ranges with Logical Operators

* Logical operators can be useful when detecting valid ranges of numbers
* Example:

```python
x = 10
print((x >= 10) and (x < 15)) # True
print((x < 10) and (x < 15)) # False
print((x < 4) or (x <= 10)) # True
print((x < 15) or (x <= 10)) # True
```
