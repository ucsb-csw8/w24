---
num: "Lecture 14"
desc: "Nested Lists, More on Dictionaries"
ready: true
lecture_date: 2024-02-22 11:00:00.00-7:00
---

Recorded Lecture: [2_22_24](https://drive.google.com/file/d/1DDtAimL-0-C8HQqOTSGwyes4kV5KcEuY/view?usp=drive_link)

# List Nesting

* Organizing data using tools Python provides can be useful in solving various problems
* So far, we’ve seen Lists contain various elements of various types
* It is possible for Lists to have elements that are Lists!
	* List nesting allows us to create a **multi-dimensional data structure**
* Example:

```python
nestedList = [[1,2], [3,4,5], [6]]
print(nestedList) # [[1,2], [3,4,5], [6]]
print(nestedList[1]) # [3, 4, 5]
print(nestedList[1][2]) # 5
nestedList[1][2] = 500
print(nestedList[1][2]) # 500

y = [[1,2], [[3,4]], [5]]
print(y[0]) # [1, 2]
print(y[1]) # [[3, 4]]
print(y[1][1]) #ERROR!
print(y[1][0]) # [3, 4]
print(y[1][0][1]) # 4
```

* Example: Traversing through a multidimensional (2D) list

```python
nestedList = [[1,2], [3,4,5], [6]]
for i, element in enumerate(nestedList):
	for j, innerElement in enumerate(element):
		print(f"nestedList[{i}][{j}] =", nestedList[i][j])
```

# More on Dictionaries

* Similar to lists, we can create dictionaries many ways including using the `dict()` function

```python
D = dict()
print(D)
D = dict(A=1, B=2) # converts identifiers to keys
print(D)
D = dict([['A', 1], ['B', 2]]) # converts collection of pairs
print(D)
```

* Remember, dictionaries keys must be immutable, and values can be any type (including containers like lists). For example:

```python
D = {"CS8":[90, 85, 95, 100], "CS9":[85, 90, 95, 100]}
print(D) # {'CS8': [90, 85, 95, 100], 'CS9': [85, 90, 95, 100]}
print(D["CS8"]) # [90, 85, 95, 100]
print(D["CS8"][2]) # 95
```

* Similar to Lists, dictionaries provide various methods that can perform in-place modifications

* `clear()` - removes all items in the dictionary
```python
D = {'A':1, 'B':2}
print(D) # {'A': 1, 'B': 2}
print(D.clear()) # None
print(D) # {}
```

* `pop(key, default)` - removes the key/value pair from the dictionary and returns the value for the parameter key. If the key doesn’t exist, an error occurs, but we can optionally set a default parameter value to be returned)

```python
D = {'A':1, 'B':2}
print(D.pop('A')) # 1
print(D) # {'B': 2}
print(D.pop('A')) # Error
print(D.pop('A', ':(')) # :( (No error)
```

* `update(dict)` - merges two dictionaries together (duplicate keys will be overwritten by the dictionary parameter)

```python
D1 = {'A':1, 'B':2}
D2 = {'B':200, 'C':3}
print(D1.update(D2)) # None
print(D1) # {'A': 1, 'B': 200, 'C': 3}
print(D2) # {'B': 200, 'C': 3}
```

* Dictionaries can provide methods that do not perform in-place modifications. For example:

* `get(key, default)` - returns the value of the key parameter. Returns `None` by default if the key doesn’t exist (or optionally another default parameter value)

```python
D = {'A':1, 'B':2}
print(D.get('A')) # 1
print(D.get('a')) # None
print(D.get('a', ":(")) # :(
```

* Notice that `[key]` also returns the value, but if we use `[]` and the key doesn’t exist, then we get an error.
* Using the `get()` method, if the key doesn’t exist, no error occurs

## Dictionary Views

* Dictionaries provide **view objects** that are read-only access to dictionary keys and values
	* Can be useful for performance reasons (no need to create copies of the dictionary) and safety reasons (prevents code from altering data when reading content from the dictionary)
* `items()` - provides (key, value) tuples for each element
* `keys()` - provides dictionary keys
* `values()` - provides dictionary values
* View objects reflects any updates made to a dictionary, even after being created
* These can be useful when traversing dictionary elements in a for loop
* Examples:

```python
# using .items() object view to iterate through key / value pairs
D = {"CS8": "Zoom", "CS9":"ILP", "CS16":"BUCHN"}
pairs = D.items()
print(pairs)

for key, value in pairs:
	print("Course: ", key, " | Location: ", value, sep="")

D["CS8"] = "HFH" # Change key’s value to HFH

for key, value in pairs:
	print("Course: ", key, " | Location: ", value, sep="") # change persists
```

```python
# using .keys() object view to iterate through keys
D = {"CS8": "Zoom", "CS9":"ILP", "CS16":"BUCHN"}
keys = D.keys()
print(keys)

for key in keys:
	print("Course: ", key, " | Location: ", D[key], sep="")
```

```python
# using .values() object view to iterate through values
D = {"CS8": "Zoom", "CS9":"ILP", "CS16":"BUCHN"}
values = D.values()
print(values)

print("Locations: ", end="")
for value in values:
	print(value, " ", end="")
print()
```

## Dictionary Nesting
* Similar to nesting lists, we can have dictionaries contain other dictionaries
	* Note that dictionaries themselves are mutable, so we cannot use them as keys in a dictionary
	* But we can use dictionaries as values
* Example: Modeling a university with a dictionary

```python
UCSB = {
	"CS8": {
		"Location": "Zoom",
		"Capacity": 300,
		"Quiz Grades": [20, 18, 19]
	},
	"MATH3A": {
		"Location": "BUCHN",
		"Capacity": 150,
		"Final Scores": [100, 100, 99, 100]
	}
}

print(UCSB.get("PSTAT120A")) # None
print(UCSB.get("CS8"))
print(UCSB.get("CS8").get("Quiz Grades")) # [20, 18, 19]
print(UCSB.get("CS8").get("Quiz Grades")[2]) # 19
```
