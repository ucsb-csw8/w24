---
num: "Lecture 18"
desc: "Recursion cont., File IO"
ready: true
lecture_date: 2024-03-07 11:00:00.00-7:00
---

Recorded Lecture: [3_7_24](https://drive.google.com/file/d/1TDvKr4UYza5G5fdP-IaHl3jM8i_eFliz/view?usp=drive_link)

# Exploring All Possibilities with Recursion

* Walkthrough zyBooks 9.6.1

![scramble.jpeg](scramble.jpeg)

# Files

* Files are a valuable tool to help us solve many other types of problems
* Files give us **persistence**
	* Our data can be saved between each program execution

## File Basics
* We can read from files
* We can write to files
* We can store files in many different forms
	* Example: `.xls`, `.docx`, `.pdf`, `.jpg`
* On our computers, you can think of:
	* File: A document
	* Directory: A folder containing files and other folders
	* File System: Collection of all the files and folders on the computer

## File I/O:

* I/O stands for **Input / Output**
* Steps for File I/O

1. Open the file (creates a *connection* between your program and the file)
	* Choose if the connection will be for reading, writing, or appending to a file
2. Read the data / write the data
3. Close the file (close the *connection*). This needs to be done once per opened file
	* Note that your code will probably run OK if you forget to close the file for small programs not dealing with a lot of file IO
	* However, your computer uses resources to keep track of all open files. Forgetting to close a file will be problematic if your program is performing a lot of file IO during runtime

## Common Ways to Read Data From Files
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
