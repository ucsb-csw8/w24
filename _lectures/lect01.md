---
num: "Lecture 1"
desc: "Introduction"
ready: true
lecture_date: 2024-01-09 11:00:00.00-7:00
---

Recorded Lecture: [1_9_24](https://drive.google.com/file/d/1KrWATZoKohsTngkBrXDptJLVV7q20xrL/view?usp=drive_link)

# Logistics

* Course webpage: [https://ucsb-csw8.github.io/w24/](https://ucsb-csw8.github.io/w24/)
	* Please read and understand the syllabus: [https://ucsb-csw8.github.io/w24/info/syllabus/](https://ucsb-csw8.github.io/w24/info/syllabus/)
* Sign up for Piazza (invite should be sent to all enrolled students)
* Purchase our version of zyBooks
	* (see Piazza `Welcome! Useful Links and Purchasing ZyBooks` note)
* Sign up for Gradescope (invite should be sent to all enrolled students)
* Let us know if you encounter any issues or have questions

# Installing Python and the Interactive Shell

* It's good to have Python3 installed on your computer (and you'll need it later in this quarter)
	* [https://www.python.org/downloads/](https://www.python.org/downloads/)
* IDLE comes with Python and is used to execute code and display your output
* The Interactive Shell is good for observing output and executing simple instructions
	* But we don't write Python code in the interactive shell
	* If you close IDLE or turn off your computer, the interactive shell won't remember what you wrote
	* So we want to create a new Python file (`.py`) in your file system that contains your code.
		* `File` -> `New File`
		* `Save As...` -> (somewhere on your file system)
	* You can execute your file with `Run` -> `Run Module`, and the interactive shell will display your output
	* Note that you don't need this to do your zyBooks work
* If you have any questions about installing / running Python, we'll be happy to help in lab sections / office hours!

# Comments

* In Python, we can separate English text ("comments") from source code by:
	* Preceding a single line with a `#` sign
	* Enclosing multiple lines with ```'''``` or ```"""```
* Example

```python
# This is a single line comment.

'''
This is
a multi-line
comment
'''

"""
This works
too
"""
```

# Some Basic Computer Terminology

* PROCESSOR: Does computations
* MEMORY/STORAGE: Contain information to act on or instructions to execute
* SOFTWARE: is the instructions that the processor follows
* ALGORITHM is a step-by-step procedure to do something
    * A chef's recipe is an algorithm
	* We will use Python to construct algorithms to tell our computer to solve various problems

