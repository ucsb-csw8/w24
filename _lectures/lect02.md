---
num: "Lecture 2"
desc: "Basic Input / Output, Variables and Assignments, Python Data Types"
ready: true
lecture_date: 2024-01-11 11:00:00.00-7:00
---

Recorded Lecture: [1_11_24](https://drive.google.com/file/d/1FhVHtXFxxUoU_wig0o0QfW-p4aPK8iYG/view?usp=drive_link)

# Print Functions

* In general, functions are pieces that perform a specific functionality.
* For example, the `print()` function will display contents inside its parenthesis (`()`)
	* We will go more in-depth in various functions and creating our own later in this course

* Example

```python
print("Hello CSW8!")
print("Python is amazing!")
```

* The  text in between double-quotes (`"`) is what we call a `string`
	* Think of a string as a collection of characters (something we can type on the keyboard)
	* Technically, single quotes (`'`)can also be used to represent a string (and the interactive shell will display strings with single quotes, but print functions display strings without quotes)
* Note that each of these print statements display on a separate line
* There's a special character called a **newline** character (`\n`) inserted at the end of the print function by default (more on some other special characters later)
* So, we could achieve the same output with the following single print function:

```python
print("Hello CSW8!\nPython is amazing!")
```

* Whenever a newline character is displayed, it moves the rest of the string to a new line in the output
* We can also print multiple strings in a single print function:

```python
print("Hello CSW8!", "Python is amazing!", "Keep the strings going!")
```

* Note that each string separated by commas in the print function is separated by a single whitespace (`" "`) character in the outout by default
* Sometimes, we may not want a newline character at the end of our print function, so we can explictly tell Python what we want at the end (or nothing). For example:

```python
print("Hello CSW8!", end="") # note: "" is an empty string
print("Python is amazing!")
```

* Also, we may not want a whitespace character separating our strings in a print function, so we can explicitly tell Python not to use anything. For example:

```python
print("Hello CSW8!", "Python is amazing!", "Keep the strings going!", sep="")
```

# Python Data Types

* Python gives us many types to use out-of-the-box
	* Types are important depending on what you need to do with data
	* Some types support certain functionality while others don't
	* Using certain types can affect the accuracy / performance of your program

## Some Common Python Data Types
* `int`: integers representing non-decimal value (whole numbers)
* `float`: floating point numbers representing a fractional value
* `str`: string representing a collection of characters (or no characters (empty string (`""`)))
	* Examples: `"A"`, `"a"`, `"1"`, `"-"`, "`abc`"
* And many more types we'll cover soon!

## `type()` Function

* We can use the `type()` function to determine what type a value is
* Example (don't worry about the `class` keyword for now):

```python
print(type(1)) #int
print(type("1")) #str
print(type(1.0)) #float
```

# Some Numerical Operators

* Python gives us certain operators to perform on numerical types
	* Examples: `+`,`-`,`*`,`/`,`**`,`//`,`%`
* Follows algebraic order-of-operations (https://docs.python.org/3/reference/expressions.html#operator-precedence)
* Either ints or floats are returned depending on the values used
* Example

```python
print(2 + 2) #4 (int)
print(2 + 2.0) #4.0 (float)
print(2 - 1) #1 (int)
print(2 - 1.0) #1.0 (float)
print(2 * 3) #6 (int)
print(2 * 3.0) #6.0 (float)
print(1 / 2) #0.5 (float)
print(2 / 2) #1.0 (float - doesn't matter if using only ints)
print(2 ** 3) #8 (int)
print(2 ** 3.0) #8.0 (float)
print(10 // 3) #3 (int)
print(10.0 // 3) #3.0 (float)
print(10 % 3) #1 (int)
print(10.0 % 3) #1.0 (float)
```

# Variables and Assignments

* Variables are useful for assigning values of any type
* Names of variables (known as identifiers) must:
	* Start with a letter or underscore (`_`) (former is more common)
	* Remaining letters in variable names can consist of letters, numbers, or underscores
* Variable names are case-sensitive (`x` and `X` are considered two different variables)
* Assigning values to variables can be broken into left-hand-side (variable) and right-hand-side (expression) using the assignment operator (`=`)
	* Right-hand-side expressions are computed first to produce a value
	* This value then gets assigned to the variable (left-hand-side)
* Example

```python
x = 10
print(x)
x = x * 10 #10 * current value of x replaces existing value of x
print(x) #100
```

# Another Note on Operators and Types

* Some operators work with non-numerical types like strings. For example:

```python
print("CSW" + "8") #CSW8 (concatenation)
```

* But what happens when we add a number to a string?

```python
print("CSW" + 8) #ERROR!
```

* Always knowing the types you're working with are extremely important in Python!
* If you're not careful, this can lead to unintended side-effects / errors

# Conversion Functions

* We can convert some types to other types using conversion functions
	* Such as `int()`, `float()`, `str()`
* Example

```python
x = "10.0"
print(type(x)) # string type
x = float(x)
print(type(x)) # float type
x = int(x) #OK, removes decimal from float number
print(type(x)) # int type
x = "10.0"
x = int(x) # Error
# When converting a string to an int, it doesn't expect the decimal portion
# in the string
```

# Input Function

* Useful programs generally require input from the user
	* Imagine if your web browser ONLY took you to <https:://www.ucsb.edu>!
* There are many forms of input into a program (keyboard, mouse movement / clicks, files, ...)
* For an interactive shell application, we can accept user keyboard input using the input function (`input()`)
	* When the input function is called, it displays what’s inside, then waits until the user enters something and hits return
	* Whatever the user typed before hitting return is inputted into the program as a `string` type
		* Important to convert this string type to an appropriate numerical type if necessary

* A tip calculator example (our first program!):

```python
TAX_RATE = 0.1
userName = input("Hi, please enter your name: ")
print("Hi,", userName, ". What’s the amount of your bill (not including tax and tip)?")
# be careful, if input is not a float, program will crash
# This is telling Python take the input() and "convert" it to a float.
totalBill = float(input())
print("What tip percentage would you like to leave?")
tipPercentage = float(input())
taxAmount = totalBill * TAX_RATE
tipAmount = totalBill * (tipPercentage / 100)
print("The total amount to pay is $", totalBill + taxAmount + tipAmount)
```