---
num: "Lecture 13"
desc: "More on Lists"
ready: true
lecture_date: 2024-02-20 11:00:00.00-7:00
---

Recorded Lecture: [2_20_24](https://drive.google.com/file/d/1hQx7yqiyLqxq7vSG-eYR2GDDPaccxMFe/view?usp=drive_link)

# More on Lists

* `list()` function can convert a container into a `list` type
* Basically, anything that can be iterated through (used in a `for` loop) can be converted to a `list`
* Examples:

```python
print(list({1, 2, 3})) # set to a list of ints
print(list((1, 2, 3))) # tuple to a list of ints
print(list({"1":10, "2":20, "3":30})) # dict to a list of its keys (strings)
print(list("123")) # string to a list of characters (strings)
```

## List Operations / Methods

* Recall, Lists are **mutable**
* Certain list operations / methods directly modify the list, while other operations / methods provide an updated copy **without** changing the list
	* We’ve seen that `del` and assignment (`=`) to an element (`[index]`) modifies the original list
	* Changing the actual list is called an **in-place modification**

### Some examples of operations that won't do an in-place modification, but provide a **copy** of the updated list:

* `+` (concatenation)

```python
list1 = [1,2]
list2 = ['a', 'b']
print(list1 + list2) # [1, 2, 'a', 'b']
print(list2 + list1) # ['a', 'b', 1, 2]
print(list1) # [1, 2]
print(list2) # ['a', 'b']
```

* `:` (list slicing)
	* Creates a new sublist based on elements between index values
	* `[i:j]` creates a list containing elements at index `i` up to (not including) index `j`
	* Note that negative indices can be used in Python (they count backwards from the end of the list)
	* Also note that not including `i` will start at the beginning of the list, and not having `j` will go to the end of the list
	* `[i:j:z]` can also be used where `z` is a step / stride when obtaining elements
	* Note: this slicing mechanic also applies to tuples and strings

```python
list1 = [10, 20, 30, 40]
print(list1[1:3]) # [20, 30]
print(list1[-3:-1]) # [20, 30]
print(list1[1:]) # [20, 30, 40]
print(list1[:3]) # [10, 20, 30]
print(list1[:]) # [10, 20, 30, 40]
print(list1[0:4:2]) # [10, 30]
print(list1) # [10, 20, 30, 40]
```

* `sorted()` function
	* Python function that can take an iterable collection (including lists), and returns a copy with elements sorted from least-to-greatest (by default)
	* We can specify we want greatest-to-least by setting `reverse=True`
	* Note that all elements in the list must be comparable (support `<` operation) with each other or else an error occurs

```python
list1 = [30, 20, 40, 10] 
print(sorted(list1)) # [10, 20, 30, 40]
print(list1) # [30, 20, 40, 10]
print(sorted(list1, reverse=True)) # [40, 30, 20, 10]
print(list1) # [30, 20, 40, 10]
list1 = [30, 20, 40, '10']
print(sorted(list1)) # ERROR (can’t compare int and str)
```

### Some examples of list methods that do an **in-place modification** of the list

* `list.append(x)` - adds an element to the end of the list

```python
list1 = [10, 20, 30, 40]
print(list1.append(50)) # None
print(list1) # [10, 20, 30, 40, 50]
```

* `list.extend([x])` - appends all items in `[x]` to the list

```python
list1 = [10, 20, 30, 40]
list2 = ['a', 'b']
print(list1.extend(list2)) # None
print(list1) # [10, 20, 30, 40, 'a', 'b']
```

* `list.insert(i, x)` - insert element `x` into list **before** index `i` (everything currently at index `i` or greater gets shifted)

```python
list1 = [10, 20, 30, 40]
print(list1.insert(2, 25)) # None
print(list1) # [10, 20, 25, 30, 40]
```

* `list.remove(x)` / `list.pop(i)`
	*  `remove` method will remove first item that has the value `x`
	* `pop` method will remove element at index `i`
		* Note that if `i` is not used, then `pop()` will remove the last element in the list

```python
list1 = [10, 20, 30, 40, 30]
print(list1.remove(30)) # None
print(list1) # [10, 20, 40, 30]
print(list1.pop()) # 30
print(list1) # [10, 20, 40]
print(list1.pop(1)) # 20
print(list1) # [10, 40]
```

* `list.sort()`
	* Similar to the `sorted` function, but will change the list to have elements sorted from least-to-greatest (by default)
	* We can also use `reverse=True` to get elements from greatest-to-least
	* Note that all elements in the list must be comparable (support `<` operation) with each other or else an error occurs

```python
list1 = [30, 20, 40, 10]
print(list1.sort()) # None
print(list1) # [10, 20, 30, 40]
print(list1.sort(reverse=True)) # None
print(list1) # [40, 30, 20, 10]
```

## Common calculations on lists

* Common calculations on lists could be finding the min element, max element, sum of all elements, etc.
	* We could do this ourselves and write our own functions, but some of these operations are so common that Python provides functions that do this for us!
	* For example, we could write our own function for getting the max value in a list

```python
def ourMax(collection):
	if collection == []:
		return None

	maxElement = collection[0]
	for item in collection:
		if item > maxElement:
			maxElement = item

	return maxElement

list1 = [30, 20, 40, 10]
print(ourMax(list1)) # 40
```

* Python’s `max` function will return the maximum element in our list
	* Note that elements in the list must be comparable or else an error will occur

```python
list1 = [30, 20, 40, 10] # change 10 to "10" to see an error
print(max(list1))
```

* Examples of `min`, `sum`

```python
list1 = [30, 20, 40, 10]
print(min(list1)) # 10
print(sum(list1)) # 100
```

### A note on how Python interprets `True` and `False`

* We’ve seen the `True` and `False` boolean values, and use them in boolean expressions
* Technically, Python interprets values as False with `False`, `0`, `None`, or an empty collection
	* Anything else is considered `True`
* Rapid prototype example:

```python
# change to 0, None, [], (), {} to see x is False
# change to any other value to see x is True
x = False 

if x:
	print("x is True")
else:
	print("x is False")
```

* Python provides an `all()` function that returns `True` if every element in a list is considered `True` (or if the list is empty) 
* The `any()` function will return `True` if any element in the list is considered `True`
