---
num: "Lecture 16"
desc: "More on Strings cont."
ready: true
lecture_date: 2024-02-29 11:00:00.00-7:00
---

Recorded Lecture: [2_29_24](https://drive.google.com/file/d/1CkpTOE7EsYEBiTGrh08HoyeMMfjlxYnx/view?usp=drive_link)

# String methods cont.

* `.find(x, start, end)` - returns the index of the first occurrence of x in the string. The parameters start and end are optional, but can be used to restrict the index range for finding x. If x is not found, -1 is returned
* `.rfind(x)` - same as find, but returns the index value of the last occurrence in the string.
* Example:

```python
s = "how much wood can a woodchuck chuck"

print(s.find("wood")) # 9
print(s.find("wood", 13)) # 20
print(s.rfind("wood")) # 20
print(s.find("WOOD")) # -1
```

* `.count(x)` - returns the number of times x appears in the string
* Example:

```python
s = "how much wood can a woodchuck chuck"

print(s.count("wood"))
print(s.count("w"))
print(s.count("z"))
```

* `strip()` - returns a string with leading and trailing whitespace removed
* Example:

```python
s1 = "it's a lovely day"
s2 = "\n\t   Hello!\n\n "
print(s2.strip()) # Hello!
```

# String Comparison (Lexicographical Order)

* We can determine if two strings are less than, equal to, or greater than each other
	* It uses ASCII values for each character to make this determination
* Python looks at the first character of each string to make the determination if one string is less than or greater than the other using ASCII values
	* If the first characters are equal, it goes on to the second character, and so on
* If one string is shorter than another string (but the shorter string contains all the same characters), then the shorter string is considered less than the longer string
* If all characters are equal in both strings, then Python considers these strings as equivalent
* Note that upper and lower case characters have different ASCII values, so `"a" != "A"`
	* If we didn’t want to compare cases and just alphanumeric characters, we could convert both strings to all upper case (using `.upper()`) or all lower case (using `.lower()`
* Example:

```python
s1 = "abcd" 
s2 = "aeiou"
print(s1 < s2) # True
print(s1 > s2) # False
print(s1 == s2) # False
s1 = "abcd" 
s2 = "abc"
print(s1 < s2) # False
print(s1 > s2) # True
print(s1 == s2) # False

s1 = "ABC"
s2 = "abc"
print(s1 < s2) # True
print(s1 > s2) # False
print(s1 == s2) # False

print(s2.upper()) # ABC
print(s1.lower()) #abc
print(s1.upper() < s2.upper()) # False
print(s1.upper() > s2.upper()) # False
print(s1.upper() == s2.upper()) # True

s3 = "ant"
s4 = "Apple"

print(s3 < s4) # True
print(s3 > s4) # False
print(s3 == s4) # False
print(s3.lower() < s4.lower()) # False
print(s3.upper() > s4.upper()) # True 
print(s3.upper() == s4.upper()) # False
```

# Boolean String Methods

* `isalnum()` - returns True if all characters are alphanumeric, returns False otherwise
* `isdigit()` - returns True if all characters are digits [0-9], returns False otherwise
* `islower()` - returns True if all alpha characters are lower case, returns False otherwise
* `isupper()` - returns True if all alpha characters are upper case, returns False otherwise
* `isspace()` - returns True if all characters are whitespace (includes `\t` and `\n`), returns False otherwise
* `startswith(x)` - returns True if the string starts with x, returns False otherwise
* `endswith(x)` - returns True if the string ends with x, returns False otherwise
* Example:

```python
alpha = "ABCD"
num = "1234"
mixed = "AB12 ?!"
whitespaces = "\n \t"

print(alpha.isalnum()) # True
print(mixed.isalnum()) # False
print(alpha.islower()) # False
print(mixed.isupper()) # True
print(whitespaces.isspace()) # True
print(mixed.isspace()) # False
print(alpha.startswith("AB")) # True
print(mixed.endswith("!")) # True
```

# `split` and `join` methods
* We’ve seen the string’s `split()` method that separates characters by whitespaces into elements in a list
* We can add a **separator** character (or sequence of characters) to split the string into elements separated by the separator
* Example:

```python
s = "This is a sentence"
print(s.split()) # ['This', 'is', 'a', 'sentence']
print(s) # This is a sentence

# csv (or comma separated values)
s = "First,Last,CS8,100,90"
print(s.split(",")) # ['First', 'Last', 'CS8', '100', '90']

s = "Mississippi"
print(s.split("is")) # ['M', 's', 'sippi']
```

* The `join()` method is the inverse of the `split()` method. It takes a list of items and returns a single string that combines each element with a string
* Example:

```python
s = "Mississippi"
splitList = s.split("is")
print(splitList) # ['M', 's', 'sippi']
newString = "IS".join(splitList)
print(newString) # MISsISsippi
```
