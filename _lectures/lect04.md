---
num: "Lecture 4"
desc: "Math / Random Modules, Function Basics"
ready: true
lecture_date: 2024-01-18 11:00:00.00-7:00
---

Recorded Lecture: [1_18_24](https://drive.google.com/file/d/1935uKjxESdSp5E54YdUINoxWebtZHoyL/view?usp=drive_link)

# Math and Random Modules

* Python contains certain modules that can be useful in our programs, such as `math` and `random`
	* These modules will need to be imported in our code in order to use them
	* Python already allows us to use certain things like `print()` and `input()` without needing to import anything since this functionality is common
	* But certain functionality (like math functionality) may only be needed in certain programs
	* Instead of having Python load ALL modules it can provide, it requires programmers to explicitly import them for performance reasons
* Examples of some math functionality in the `math` module:

```python
import math

print(math.ceil(3.1)) # 4
print(math.floor(3.9))# 3
print(math.factorial(4)) # 4*3*2*1 -> 24
print(math.pow(4, 2)) # 4 ** 2 -> 16
print(math.pi) # 3.141592653589793
print(math.sqrt(81)) # 9.0
```

* Examples of some functionality in the `random` module

```python
import random
print(random.random()) # [0, 1)
print(random.randrange(2, 8)) # [2, 8)

print(random.randint(2, 4)) # [2, 4]
print(random.randrange(2, 5)) # same as random.randint(2,4)
```

* Example of simulating a six-sided die roll and a pair of dice:

```python
import random

# Rolling one six-sided die
print(random.randrange(1, 7)) 

# Rolling two six-sided dice
print(random.randrange(1, 7) + random.randrange(1, 7))
```

# Introduction to Functions
* We’ve seen how we can call functions that Python provides (`print()`, `input()`, `type()`, ...)
* Functions are great when:
	* We have common code that is used in various places in our code
	* Instead of copy / pasting the same code in various places, we can write a single function to be used and called in various places in our code
		* Can you imagine how our code would look if we had to copy / paste code that makes the `print()` function work in every place we use it!
* Let’s write a simple function definition, something that takes in an integer and doubles it:

```python
def double(n):
	''' Returns 2 times the parameter''' # Good to comment functions!
	print("In double function. n =", n)
	print(2 * n)
```

* The `def` keyword let's Python know we are about to define a function
* `double` is name (identifier) of the function
* The `(n)` denotes the parameter(s) that this function will accept. In this case, it takes in a single value and is used in the function
	* Note that a function may have zero or more parameters
* The `:` is necessary to tell Python we’re about to define the body of the function (statements belonging to the function)
* The parameter(s) of a function is referred to as a function **signature**
* The actual statements in the function are called the **body** of the function
* All statements in the function body need to be **indented** (single tab) so python can associate these instructions as part of the function definition
* A function may or may not have a `return` statement
	* If a `return` statement returning an actual value exists, then the value is returned to the caller and can be used
	* If no `return` statement exists (or a `return` statement exists, but doesn't return an actual value), then a special `None` value is returned
	* Depending on the situation, a function may or may not want to have an explicit value returned
	* For example, if a function should print something, then it just needs to print something and exit the function (without passing any data back to the caller of the function)
		* Note that `print()` does not have a return value
	* But if the function needs to compute a value and return this computation back to the caller (like our `double` function example), then an explicit `return` statement is needed
* Example of having a `return` statement:

```python
def double(n):
	'''Returns 2 times the parameter''' # Good to comment functions!
	print("In double function. n =", n)
	return 2 * n
```

* Examples of how we can call functions (see if you can trace the flow of function calls and how return values are used):

```python
print(double(10)) # -> print(20)
print(double(double(2)) # -> print(double(4)) -> print(8)
value = double(5) + double(6) # -> 10 + double(6) -> 10 + 12 -> 22
print(value)
```

