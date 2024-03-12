---
num: "Lecture 19"
desc: "File IO cont."
ready: true
lecture_date: 2024-03-12 11:00:00.00-7:00
---

Recorded Lecture: [3_12_24](https://drive.google.com/file/d/16miYSd-8ky6gYRTMZCDMBv5VsAEnXzgs/view?usp=drive_link)

# Common Ways to Read Data From Files (cont.)
* `read()` method – Reads the entire file into one string
* `readline()` method - Read everything from the current position to the next `\n` (or to the end of the file, `EOF`). If nothing left to read, returns an empty string.
* `readlines()` method - Read all the lines in the file into a list
* `for` loop - Read a line of text (separated by `\n`) each iteration
* Examples reading from file (`example.txt`) located in the same directory as our `.py` file:

```
This is Line 1
This is Line 2
This is Line 3
```

```python
# Reading entire contents of file into program
infile = open('example.txt') 
data = infile.read()
print(data)
infile.close()
```
```python
# Reading a single line (up to and including \n) in file
infile = open('example.txt')
data = infile.readline()
print(data)
data = infile.readline()
print(data)
data = infile.readline()
print(data)
infile.close()
```
```python
# Creating a list where elements are a line (includes \n)
infile = open('example.txt')
data = infile.readlines()
print(data)
infile.close()
```
```python
# Traversing through the file line-by-line in a for loop (includes \n)
infile = open('example.txt')
for line in infile:
	print(line)
infile.close()
```

# Writing to Files

* We can write contents from our program into a file
* When writing to a file, we need to pass `'w'` into the open function
	* If the file doesn’t exist, then Python will create a new file
	* If the file does exist, then writing to the file will clear all the existing content and write new content to the file
* Examples:

```python
# Example writing to a new file `example2.txt`
outfile = open('example2.txt', 'w')
outfile.write("This is something new!")
outfile.close()
```
```python
# Example of overwriting contents of a file
outfile = open('example2.txt', 'w')
outfile.write("Completely new text ... old text is gone!\n")
outfile.write("This is a new new line")
outfile.close()
```

# Appending to Files

* If we don’t want to overwrite the contents of the file, we can choose to add on to the contents by appending more information
	* We need to pass the `'a'` into the open function to append contents

```python
# Example of appending contents of a file
outfile = open('example2.txt', 'a')
outfile.write("Something new!\n")
outfile.write("Another line!")
outfile.close()
```
```python
# Example copying / writing from a file to another file.
infile = open(‘example.txt’, ‘r’)
outfile = open(‘copy.txt’, ‘w’)
for line in infile:
	outfile.write(line)
infile.close()
outfile.close()
```

# `with` Statement

* As we mentioned before, it’s good practice to close a file after we open it
* For File IO, we can use the `with` statement
	* This allows us to open a file, execute some code within the `with` block, and automatically closes the file once the statements in the `with` block are done executing
* Example:

```python
with open('example.txt', 'w') as outfile:
	outfile.write("Writing to the file - line 1\n")
	outfile.write("Exiting with block")

# After with block is finished executing, outfile is automatically closed
print("Done")
```

# The `os` Module

* Python provides a module that interfaces with the Operating System (OS) running the Python program
* The OS module can be useful for many things. One thing is file paths may look different between Macs and Windows machines and are separated with different characters
	* Mac: `/`
	* Windows: `\`
* We can determine the path separator with `os.path.sep`
* So if we want to create a file path programmatically, we can join the correct separator with the folders / subfolders appropriately
* Example:

```python
print(os.path.join("Users", "richert", "Desktop", "UCSB", "CS8W", "lecture.py")) # Users/richert/Desktop/UCSB/CS8W/lecture.py
# Note that the file separator would be different if I ran this on Windows
```

# The CSV Reader
* A common file format for spreadsheets is **comma separated values (csv)** and are usually stored with a `.csv` extension
* Python has the `csv` module to help us read and process `csv` files
* For example, we can create the following `csv` file with the following data for student grades (`sample.csv`):

```
Student 1,100,98,100
Student 2,100,100,95
Student 3,100,95,90
```

* Note that if we open this with a spreadsheet editor, the data separated with commas are stored in individual cells
* The `csv` module has the method `reader` that takes in the `csv` opened file and an optional delimiter (`,` is used by default)
	* It returns an iterable object where each element is a list containing each data piece separated by commas
	* Note that each piece of data is a string, so we may need to convert the data into numerical types to do numerical computations
* Example:

```python
import csv

with open('sample.csv', 'r') as csvFile:
	csvReader = csv.reader(csvFile) # could use a different delimiter param
	for row in csvReader:
		print(row)
```

* Another example: Calculate the average score for each student

```python
import csv

with open('sample.csv', 'r') as csvFile:
	csvReader = csv.reader(csvFile)

	for row in csvReader:
		total = 0
		for i in range(1, len(row)):
			total += float(row[i])
		print(f"{row[0]}: average = {total / 3:.2f}")
```

* Another example: Drop the lowest score from the list of grades (there could be any ways to solve this)

```python
import csv

def dropLowest(fileName):
	with open(fileName, 'r') as csvFile:

		with open("updatedSample.csv", 'w') as outFile:
			csvReader = csv.reader(csvFile)
			for row in csvReader:
				maxValue = 1000
				minIndex = -1
				for i in range(1, len(row)):
					if float(row[i]) < maxValue:
						maxValue = float(row[i])
						minIndex = i
				row.pop(minIndex)

				newRow = ""
				for element in row:
					newRow += element + ","
				newRow = newRow[:-1]
				outFile.write(newRow + "\n")

dropLowest("sample.csv")
```
