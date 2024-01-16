---
num: "Lecture 3"
desc: "Expressions, Math / Random Modules"
ready: true
lecture_date: 2024-01-16 11:00:00.00-7:00
---

Recorded Lecture: [1_16_24](https://drive.google.com/file/d/17R7poJskd6FOB_ZDR2rh761H6cxOKyxK/view?usp=drive_link)

# A note about signing up for Gradescope

* Note: Be sure to use your `@umail.ucsb.edu` address when signing up for Gradescope
    * If you have an account using your `@ucsb.edu` (or another email address), then you can add / link your `@umail.ucsb.edu` account (`Account` -> `Edit Account`)
    * CMPSCW 8 in Winter 2024 should appear on your dashboard
        * Be sure to confirm this before Friday's quiz!
    * A sample (ungraded) quiz is available for you to take and get familiar with how a quiz format would look like

# Objects and Types

* In Python, Objects are data that are classified as a specific type
* Think of the assignment `x = 2 * 3.0`
	* `6.0` is the resulting multiplication value of type float
	* `6.0` is an object of type `float`
	* `x` is a variable that is currently holding a float object
	* This data is stored in memory, which can be accessed or modified throughout program execution
		* We won’t go into too much detail on memory, but think of your data being stored in a specific address (your program needs to know the address of where data exists in order to use / modify it)
	* There’s a special `id()` function that can be used to see the memory address of where the data is being stored in computer memory
		* Note that the memory address will be different every time you restart your program
		* Example:

```python
print(id(100))
print(id(3.6))
```

# (Brief) Introduction to String Formatting (f-strings)

* Recall our tip-calculator example:

```python
TAX_RATE = 0.1
userName = input("Hi, please enter your name: ")

print("Hi,", userName, ". What’s the amount of your bill (not including tax and tip)?")
totalBill = float(input()) #take the input() string and convert it to a float.

print("What tip percentage would you like to leave?")
tipPercentage = float(input())

taxAmount = totalBill * TAX_RATE
tipAmount = totalBill * (tipPercentage / 100)
print("The total amount to pay is $", totalBill + taxAmount + tipAmount)
```

* The output for the total amount to pay was:

```
The total amount to pay is $ 130.0
```
* We could possibly fix this in several ways, but **f-strings** can be useful to display floating point numbers in a specific format
	* We’ll go more in-depth with f-strings later, but for now let’s talk a little about number representation as a string
* When using f-strings, think of `{}` as plugging in values you want to display in the string. For example:

```python
x = 130.0
print(f"${x}") #$130.0
```

* For floating point numbers, we can use f-strings to display a specific amount of decimal values. For example:

```python
x = 130.0
print(f"${x:.2f}") #$130.00
```

* The left side of the `:` represents the value we want to display. The right side of the colon represents the space / precision of the value.
* `.2f` is stating is used to display 2 spaces for the floating point portion of the value, so this will display `130.00`
* Also note if the floating point numbers exceed two spaces, this will round the number to two spaces. For example:

```python
x = 130.1299
print(f"${x:.2f}") #$130.13
```

* We can fix our formatting in the tip calculator example using f-strings with

```python
print(f"The total amount to pay is ${(totalBill + taxAmount + tipAmount):.2f}")
```

# Syntax vs. Runtime Errors

* Think of the following:
	* **Syntax** Grammar, how we construct something
	* **Semantics** Meaning, what we say
* For example:
	* Syntactically incorrect: `PI equals 3.14159 # invalid syntax`
	* Semantically incorrect: `PI = "apple" # valid syntax, incorrect meaning`
* We've probably seen Python complain before even running the program
* For example:

```python
print("Start")

PYTHON!

print( Hello )
```

* In this case, the program doesn't start executing if there is a syntax error
* Python basically is telling us that `PYTHON!` is a syntax error.
	* Identifiers cannot have `!`
* Before the Python script runs, it gets parsed through and there’s a simple check to make sure all expressions are valid
* If not, then it will state an error (Note that the program is not running at this time)
* If we remove the syntactically incorrect line:

```python
print("Start")
print( Hello )
```

* We get another type of error that happens **WHILE** the code is executing.
* Errors that happen during program execution is called a **runtime error**:

```python
Traceback (most recent call last):
  File "/Users/richert/Desktop/UCSB/CS9/lecture.py", line 5, in <module>
    print( Hello )
NameError: name 'Hello' is not defined
```

* The above message is basically saying `Hello` is a variable that hasn’t been defined, but we’re trying to use it in a `print` function.
* Syntactically, there is nothing wrong with the above lines of code (since `Hello` could be a valid variable name).

# Compound Operators

* Updating variables is commonly used, so Python provides special compound operators to simplify / shorten these assignment statements
* Note that there is no space between the compound operators (`+=`, `-=`, ...). For example:

```python
x += 1 #equivalent to x = x + 1
x -= 5 #equivalent to x = x - 5
x *= 2 #equivalent to x = x * 2
x /= 4 #equivalent to x = x / 4
x %= 3 #equivalent to x = x % 3
```

# Modules

* Python files (`.py`) contain our code that we want to execute, and we use this instead of the interactive shell
* It is not uncommon to have code in other files that can be included in the code we’re writing
	* A module is a file containing Python code that can be used by other modules or scripts
	* There are many benefits to separating code into modules and making things more modular
		* Maintenance is easier and code can be organized / reused in various places in our program
* An example of separating our code into two different `.py` files, and having one `.py` file import another module (note that these files must exist in the same folder in your file system):

```python
# myModule.py
name = "Richert"
course = "CMPSCW8"
print(name, course)
```

```python
# lecture.py
import myModule # Name of the file to import (without .py)

print("In lecture.py script")
print(myModule.name)
print(myModule.course)
```

* Note that we can run `myModule.py` and it will just execute its single `print` statement
* When we run `lecture.py`, it sees the `import` statement and will load and execute all statements in `myModule.py`
* In this situation, in order to tell Python to use variables defined in `myModule.py` within `lecture.py`, we use `myModule` (dot) variable name.
* This way Python knows the variable to use is in `myModule.py` (we didn’t define the variables `name` or `course` in `lecture.py`)

# `if __name__ == '__main__':`

* When a module is imported into another module, the entire imported module is executed
* In many cases, we may not want **ALL** the code from a module to be executed
	* For example, debugging print statements or running tests for the modules
* So Python allows us to not execute certain Python code **when it is imported into another module**
* All code in the `if __name__ == '__main__':` block will only be executed if we run this module directly
	* Note that all statements in this block must be indented within the `if __name__ == '__main__':` structure (this is how Python determines scope - more on this soon!)
	* But if this module is imported, then the code in the `if __name__ == '__main__':` block will not be executed
* Example

```python
# myModule.py
name = "Richert"
course = "CMPSCW8"

if __name__ == '__main__':
	print(name, course)
```

* Note that `print(name, course)` is not executed when we run `lecture.py` since this statement is in the `if __name__ == '__main__':` block
* But if we run `myModule.py` directly, then `print(name, course)` is executed (since it was run directly and not imported into another module)
* Consider this case...

```python
# myModule.py

if __name__ == '__main__':
	name = "Richert"
	course = "CMPSCW8"
	print(name, course)
```

* Running `myModule.py` directly will work fine, but when we run `lecture.py` we get an error
	* Since we ran `lecture.py` directly, `name` and `course` variables are not initialized since they exist in the `if __name__ == '__main__':` block in `myModule.py`
So when `lecture.py` is trying to execute `print(myModule.name)`, Python things this is undefined



