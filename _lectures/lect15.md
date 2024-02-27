---
num: "Lecture 15"
desc: "More on Functions, More on Strings"
ready: true
lecture_date: 2024-02-27 11:00:00.00-7:00
---

Recorded Lecture: [2_27_24](https://drive.google.com/file/d/1pRnNZ5EO5YPSbfU0cIoMLZQbE9f6Tr1i/view?usp=drive_link)

# Mutable / immutable types as function parameters

* We’ve seen how in-place modifications can’t be done with immutable types and immutable types can only be used for Dictionary keys and elements in a set
	* Depending on whether or not something is mutable or immutable, it affects how the data is treated when passing it in a function
* When **IMMUTABLE** types are passed into a function, a COPY of that variable is made and used within the function
	* Once the function returns, the immutable parameter does not change
* When **MUTABLE** types are passed into a function, the actual parameter variable is used within the function (no copy is made)
	* Once the function returns, the mutable variable does change
* Example:

```python
def changeListParameter(x):
	x[0] = "!"
	print("inside changeListParamter:", x)
	return x

a = ["C","S","8"]
print(changeListParameter(a)) # ['!', 'S', '8']
print(a) # ['!', 'S', '8']

def changeStringParameter(x):
	x = x.replace("C", "!")
	print("inside changeStringParameter:", x)
	return x

b = "CS8"
print(changeStringParameter(b)) # !S8
print(b) # CS8
```

# Default Parameter Values

* Recall the `print` function and how we can add a string between items in the print function (using `sep`) and add something to the end (using `end`)
	* Python already has a space character assigned to `sep` and a newline character assigned to `end`, and we can change this if we want
	* These are known as **default parameter values**
* We don’t have to pass values in for default parameters when calling the function, because values have already been assigned to the parameters
* We’ve also seen a default parameter value in the `sort` function
	* `reverse=False` by default, but if we wanted the items sorted from greatest-to-least, then we can set `reverse=True`
* Example:

```python
def printMoney(amount=0.0, currency="dollars"):
	''' Function that takes an amount of money (float) and prints
	    out the amount and currency (str). '''
	print(f"{amount:.2f} {currency}")

printMoney() # 0.00 dollars (uses default parameters)
printMoney(12.5, "pesos") # 12.5 pesos (uses passed in parameter values)
printMoney(12.5) # 12.50 dollars (puts 12.5 in first parameter)
#printMoney("won") # error (puts won in first parameter, can't format a string)
printMoney(currency="won") # 0.00 won (uses default amount, currency set to won)
```

# Mutable Default Parameters

* Setting a default parameter with a mutable object will persist changes over multiple calls to the function
	* Might not be the intention if you want to keep the object state separate
* Example:

```python
def addElement(element, container=[]):
	container.append(element)
	return container

print(addElement(10)) # [10]
print(addElement(20)) # [10, 20] (still contains 10 from previous call
```

# Functions Returning Multiple Values

* Recall we can assign multiple values to multiple variables in a single expression using **unpacking**
* Example:

```python
x, y = 10, 20
print(x, y)
x, y, z = 10, 20, {30, 40}
print(x, y, z)
```

* We can return multiple values in a function, that can be unpacked
	* Note that when a function returns multiple values, they get packed into a tuple

```python
def getFullName():
	firstName = input("Enter first name: ")
	lastName = input("Enter last name: ")
	return firstName, lastName # packs into a tuple

first, last = getFullName()
print(first, last)
```

# String Slicing

* String slicing works the same way as list slicing, and each character in the string is considered an element in the container starting at index 0
* The slicing rules for strings are:
	* Creates a new substring based on elements between index values
	* `[i:j]` creates a substring containing characters at index `i` up to (not including) index `j`
	* Note that negative indices can be used (they count backwards from the end of the string)
	* Also note that not including `i` will start at the beginning of the string, and not including `j` will go to the end of the string
	* `[i:j:z]` can also be used where `z` is a step / stride when obtaining characters
* Examples:

```python
url = "https://www.ucsb.edu/"

# Get everything EXCEPT the last character
print(url[0:20]) # https://www.ucsb.edu
print(url[:-1]) # https://www.ucsb.edu

# get http
print(url[:4]) # http
# reverse url
print(url[-1:-22:-1]) # /ude.bscu.www//:sptth

print(url) # https://ucsb.edu/ (slicing only returns copies of the substring)
```

# String Methods

* Similar to lists, dictionaries, and other Python objects, strings have various methods that we can use
* However, strings are **immutable**, so they do not have an in-place modifications methods
	* If we want to change a value of a string, we need to reassign a new string value to the variable 
* Some string methods:

	* `.replace(old, new, count)` - replaces all occurrences of the old value with the new value. The parameter count is optional, but will replace the first count occurrences
	* Example:

```python
s = "one two three la la la"

print(s.replace("one", "1")) # 1 two three la la la
print(s) # one two three la la la

print(s.replace("la", "LA")) # one two three LA LA LA

s = s.replace("la", "LA", 2)  # s is reassigned
print(s) # one two three LA LA la
```
