---
num: "Lecture 10"
desc: "Functions cont., While Loops"
ready: true
lecture_date: 2024-02-08 11:00:00.00-7:00
---

Recorded Lecture: [2_8_24](https://drive.google.com/file/d/1zm635qpmaZGa7S4d_fIfPJ8mwx8CuBUW/view?usp=drive_link)

# Dynamic Typing

* Python utilizes **dynamic typing** when determining what type a variable references at any given time
* We’ve seen this in action with general assignment operators. For example:

```python
x = 10 # x refers to an int type
x = "10" # x refers to a str type
```

* Pro: Python is considered more flexible than other languages that utilizes **static typing** (a variable can only refer to one type)
* (Big) Con: the programmer is responsible to always know what types are being used, because Python won’t check it for us
	* This can lead to some unintended / incorrect behavior. For example:

```python
def tripleParam(value):
	''' Triples the parameter value, and returns the tripled value '''
	return value + value + value

print(tripleParam(4)) # 12
print(tripleParam("4")) # 444
```

* In this case, Python just uses whatever argument type the parameter refers to
* So we might *think* we’re tripling a number, but if the parameter type is something other than an `int`, we may get a different behavior
* There are ways to write defensive code to ensure we’re dealing with the correct type, but this must be done by the programmer. For example:

```python
def tripleParam(value):
	''' Returns the triple of parameter value '''
	if type(value) == str: # explicitly check if value is a str
		value = int(value) # convert it to an int if necessary

	return value + value + value
```

# Calling Functions in Expressions

* Recall, function calls execute code that is defined in the function, but after the function is executed, we can think of the function call as a value (or `None`) based on whatever the function returns
* So we can piece function calls together to form larger general expressions. For example:

```python
def multiply(x, y):
	''' Returns the product of the parameters x and y '''
	return x * y

print(multiply(3,3)) # 9
print(multiply('4', 4)) # 4444
#print(multiply('4','4')) # Error

def cube(num):
	''' Returns the cube of parameter num '''
	return multiply(num, num) * num

print(cube(2)) # 8
print(cube(3)) # 27
```

# Functions as Objects

* Python functions are technically objects of type `function` under the hood

```python
print(type(cube)) # function
```

* This allows us to assign functions to variables and parameters, and use them in various places in our code
	* Under the hood, when a variable is referring to a function, it’s referring to where a function’s code is located in memory so it can be executed
* This might be useful if you are want to pass a function to be used in another function. For example:

```python
def compute(someFunction, value):
	return someFunction(value) # someFunction referring to the function passed in

userValue = int(input("Enter an integer: "))
userChoice = input("Enter 1 to triple. Enter 2 to cube: ")

if userChoice == "1":
	print(compute(tripleParam, userValue))
if userChoice == "2":
	print(compute(cube, userValue))
```

# Variable Scope

* Any variable defined within a function is only available within the function
	* Once the function exists, any variable in the function cannot be identified
	* These are known as **local variables**
* For example:

```python
def myFunction():
	name = "CSW8"
	print(name)
	return

myFunction()
print(name) # Error, name variable only exists in myFunction
```

* We could define variables outside of functions and use them within the function
	* These are called **global variables**
	* Global variables might make sense for things like constants (`pi`), but in general it’s best not use global variables
	* Think about the following:

```python
x = 100

def myFunction(x):
	print(x)

myFunction("CSW8") # No error, but what gets printed?
```

* In the above example, local variable names have higher precedence than global variables
* It would be clearer if either a different parameter value name was used, or we avoided global variables

# While Loops

* A looping construct we’ll use in this class is called a `while` loop
	* While loops are used when you want to repeat a set of statements indefinitely

```
Syntax:
while BOOLEAN_EXPRESSION:
	STATEMENT(S)


If BOOLEAN_EXPRESSION is true, perform statements in the body of the loop. Then check if BOOLEAN_EXPRESSION is True
or False (and repeat)
If BOOLEAN_EXPRESSION is false, skip the body of loop entirely and continue execution.
```

* Example: Infinite Loop

```python
# cntrl-c will terminate execution
while True:
	print("Weeee!")
```

* Example: Count to 10

```python
num = 1
while num <= 10:
	print("num =", num)
	num += 1
```

* Example: Continue until user input is correct

```python
value = input("Enter STOP: ")
while value != "STOP":
	print(f"You didn't do what I wanted! You typed '{value}'. Try again")
	value = input("Type STOP: ")

print(f"Hooray! You typed '{value}'!")
```

* Example: Roll a pair of dice until they sum up to 12

```python
import random

rollDie1 = 0
rollDie2 = 0
numRolls = 0
while (rollDie1 + rollDie2) != 12:
	numRolls += 1
	rollDie1 = random.randint(1,6)
	rollDie2 = random.randint(1,6)
	print(f"({rollDie1},{rollDie2}) = {rollDie1 + rollDie2}")

print("Congrats! You rolled a 12!")
print(f"It took {numRolls} attempts")
```


