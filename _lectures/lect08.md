---
num: "Lecture 8"
desc: "Sets, String Formatting cont, Binary Representation and Text"
ready: true
lecture_date: 2024-02-01 11:00:00.00-7:00
---

Recorded Lecture: [2_1_24](https://drive.google.com/file/d/10lJXHxA5xxkA5qTAb2WLsr9OQKn_Ygwl/view?usp=drive_link)

## Sets
* Sets are useful when we need to store unique elements in a collection
* Sets are unordered (no indexing)
* Sets use curly braces (`{}`) similar to dictionaries, but do not have a `KEY:VALUE` pair for the elements
* Sets are **mutable**, but elements in sets must be **immutable** types
* Example:

```python
s1 = set() # create empty set
print(s1)
print(type(s1))
s1 = {1, 3, 5}
print(s1)
s1 = {1, 3, 5, 3, 1}
print(s1) # only stores unique items
```

* We can also convert a list collection into a set with `set()`

```python
intList = [1,2,3,4,5,4,3,2,1]
print(intList)
setList = set(intList)
print(setList)
```

## Note on methods vs. functions
* We’ve seen functions can be called using the function identifier and passing in the appropriate parameter values
* **Methods** are similar to functions, but they are usually called with an instance of an object
* Sets have methods such as `add()`, `remove()`, `pop()` to update the contents of the set
* Some methods may return a value, or may return `None`
* Example:

```python
s = {2, 4, 6, 8}
print(s)
print(s.pop()) # removes and returns a random element
print(s)
print(s.add(10)) # adds an element but returns None
print(s)
s.add(10) # does nothing since 10 exists
print(s)
print(s.remove(6)) # removes 6 but returns None
print(s)
```

# More on String formatting

* We’ve seen the concept of f-strings for providing floating point precision
* There are many other features we can utilize to make our code more readable
	* For example, we can use the `=` sign to output and evaluate an expression
* Example:

```python
print(f'{5*5=}')
x = 25
print(f'{x=}')
print(f'{x}=') # what would this be?
print(f'x={x=}') # and this?
print(f'x={x}') # and this?
```

* Format specification can interpret a value as a specific type
	* `s` (str), `d` (decimal integer), `f` (float), `e` (exponent notation), ...
	* There are many small tweaks we can utilize to do lots of things, but we won’t cover all of them (we’ll focus on what’s covered in zyBooks)
* Some examples:

```python
course = "CSW8"
print(f'{course:s}') # s - string (not necessary)

value = 1234
print(f'{value:d}') # d - decimal (int)
print(f'{value:,d}') # ,d inserts commas
print(f'{value:05d}') # 0[int]d inserts leading 0's to create total [int] chars
print(f'{value:e}') # e - exponent notation
print(f'{value:.3f}') # 3 floating point numbers
print(f'{value:,.3f}') # 3 floating point numbers with commas

value = 12.34
#print(f'{value:s}') # error
#print(f'{value:d}') # error
print(f'{value:.4f}') # 12.3400
print(f'{value:e}') #1.234000e+01
```

# Binary Number Representation

* We are used to dealing with numbers in decimal (base 10) notation
* Computers deal with numbers in Binary (base 2) notation (0’s and 1’s)
	* This is a physical property of the underlying hardware that our computers use
		* `1` is a positive charge, `0` is a neutral charge
	* Each binary value is called a **bit**
	* Eight bits make up a **byte**
* For positive integer values, we can think of each bit representing a power of 2
	* And the combination of bits can represent a unique positive integer
	* For example, 3 bits can form 8 unique values (2^3):

```
000 -> 0	100 -> 4
001 -> 1	101 -> 5
010 -> 2	110 -> 6
011 -> 3	111 -> 7
```

* Example of converting a binary (base 2) number to decimal (base 10):

```
111 (base 2) = 1 * (2^2) + 1 * (2^1) + 1 * (2^0) = 7 (base 10)
101 (base 2) = 1 * (2^2) + 0 * (2^1) + 1 * (2^0) = 5 (base 10)
```

* Converting a positive base 10 (decimal) to base 2 (binary) number can use the **best-fit** algorithm:
	* See which largest power of two is less than the number
	* Write a `1` in the appropriate place, and a `0` for any powers of 2 that are larger
	* Replace the number by subtracting it by the largest power of 2 less than the current number
	* Repeat until the value is 0
* Examples:

```
2510 (base 10) = 11001 (base 2)

___1___  | ___1___ | ___0___ | ___0___ | ___1___ 
2^4 (16) | 2^3 (8) | 2^2 (4) | 2^1 (2) | 2^0 (1)

25-16 = 9
9-8 = 1
1-1 = 0
```
```
8510 (base 10) = 1010101 (base 2)

___1____ | ____0___ | ___1___  | ___0___ | ___1___ | ___0___ | ___1___ 
2^6 (64) | 2^5 (32) | 2^4 (16) | 2^3 (8) | 2^2 (4) | 2^1 (2) | 2^0 (1)

85-64 = 21
21-16 = 5
5-4 = 1
```

# Representing Text

* The combination of 0’s and 1’s in computer memory can be interpreted to have various meanings
	* A color of a pixel in an image, a pitch in an audio file, floating point and negative numbers, etc.
* This is why there are various files storing these bits of information to be interpreted in certain ways (`.mp3` / `.mp4` / `.wav` / `.jpg` / `.pdf` / ...)
* Characters (under-the-hood) are actually assigned specific numerical values represented with binary numbers
	* Plain text (.txt) files use ASCII (American Standard Code for Information Interchange) and can represent all English alpha / numeric characters with 8 bits of information (256 unique values)
	* Unicode uses more bits (more unique values) to represent characters in various languages
* Lowercase / upper-case characters are represented with different numerical values, which is why:

```python
print('a' == 'A') # False
```
* The `==` operator is comparing the numerical representation of characters when checking for equivalency
* We can find the underlying numerical value of a single character string using the ordinal (`ord()`) and the character of a numerical value with `chr()`

```python
print(ord('A')) #65
print(ord('a')) #97
print(chr(65)) # A
print(chr(97)) # a
```

## Escape Characters
* We’ve seen an example of an escape character (newline `\n`)
* This is a special character representing a break in the string so it can continue to the next line
* We use `\` to let python know an escape character will should be interpreted
* Examples of escape characters: `\\` (backslash), `\'` (single quote), `\"` (double quote), `\n` (newline), `\t` (tab)

```python
print("Python\nmakes\nme\nsmile!")
print("\t10\n\t20\n\t30")
print("10\\20\\30")
print("\"Hello!\"")
print("Won\'t stop, can\'t stop!")
```

## Raw Strings
* Raw strings are used to ignore all escape characters in a string

```python
print(r"Python\nmakes\nme\nsmile!")
print(r"\t10\n\t20\n\t30")
print(r"10\\20\\30")
print(r"\"Hello!\"")
print(r"Won\'t stop, can\'t stop!")
```

