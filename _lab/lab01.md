---
layout: lab
num: lab01
ready: true
desc: "Getting Started, Python Functions"
assigned: 2024-02-05 11:00:00-7
due: 2024-02-11 23:59:59-7
---

# Introduction

Your first lab for this week is an introduction to writing Python code in `.py` files and making submissions to Gradescope's autograder. You may choose to work with a partner if you like (but this is not required). **If you choose to work with a partner, please follow the instructions on recording who your partner is (explained below). Both you and your partner MUST make individual submissions on the Gradescope system to receive credit.**

As stated in the syllabus, Gradescope labs will only have a 24-hour late window after the deadline. Submissions during the late window period will have an automatic 20% deduction from your assignment. We will only consider the most recent submission.

**Note: In general, it is a good idea that you start all assignments early so you can utilize our office hours and lab sections to seek assistance / ask clarifying questions before the deadline if needed**

## Goals for this lab

By the time you have completed this lab, you should have:
* installed Python
* created and run Python progams in IDLE
* submited your work using the Gradescope system

# Get setup with Gradescope

We will use Gradescope to autograde this lab assignment.

The lab assignment `Lab01` should appear in your Gradescope dashboard in CMPSCW 8. You will need to submit your code for Lab01 there.

# Install Python on your computer

The instructions on installing Python on your computer can be found here:

<https://www.python.org/downloads/>

Follow the appropriate links to install Python for your computer. In case you run into any issues, we will be happy to take a closer look during our office hours / lab sections.

# Create your Lab01 directory

In general, it's important to be organized when working on various assignments. For this lab, my recommendation is to create a `csw8` folder that will contain sub folders for each lab - for this lab, I would recommend creating a `csw8/lab01` folder on your computer where you can save your file. In general, I recommend creating a new folder for each lab assignment.

When creating or obtaining files to work with, you may use any editor of your choice. However, for now I will recommend IDLE since this comes with the installation of Python.

If you are encountering any issues or need help, feel free to ask a TA / ULA for assistance when getting started.

# Create a new `lab01.py` file

Using the editor of your choice, create a `lab01.py` file in your `lab01` directory. This `lab01.py` file will contain the python code you will submit for this lab assignment. Steps of creating this new file with IDLE are:

* Open IDLE on your computer
* Go to `File` -> `New File`, which will create an untitled file.
* Save this file by going to `File` -> `Save`, which will prompt you to save this file in a specified location
	* Name this file `lab01` (assuming the extension will automatically be saved as a `.py` file)
      * You must use the **exact** same name and casing when creating your file
	* Save this file under your `csw8/lab01` directory you created for this lab

# Copy the following code template into `lab01.py` and complete the function definitions

We will write four Python functions for this lab. **If you choose to work with a partner, you and your partner must create your own file, and both you and your partner must submit your work separately.**

Copy the following code into your `lab01.py` file and complete the function definitions according to the comments. **Type your actual name (and your partner's name if you worked with one) at the top**:

```python
# Lab01, CSW 8
# [type your name here]
# [type your partner's name here if you worked with someone]

def isMultiple(num1, num2):
    ''' Function that takes two integers (num1) and (num2).
    Returns True if num2 is a multiple of num1, and returns
    False otherwise (you may assume num2 >= num1 for this function).
    * If num1 is equal to 0, your function should return None.
    '''
    # COMPLETE YOUR FUNCTION DEFINITION HERE

assert isMultiple(1,1) == True
assert isMultiple(1,10) == True
assert isMultiple(2,3) == False
assert isMultiple(4,16) == True
assert isMultiple(4,7) == False
assert isMultiple(0,3) == None
assert isMultiple(3,0) == True

def incrementKeyCount(D, key):
   ''' Function that takes in a Dictionary object (D) containing KEY:VALUE
   pairs where the VALUE is a count representing the number of times the KEY
   is incremented.
   * If the parameter key does not exist in D, then a new KEY:VALUE
   pair is created in D with key:1 (the first time the key is incremented).
   * If the parameter key does exist in D, then the key's VALUE is
   incremented by 1.
   * Note that since dictionaries are mutable, this function does
   not return a value.
   * Consider using the in operator to check if a key exists in a Dictionary
   * Assert examples below illustrate correct behavior for this function
   '''
   # COMPLETE YOUR FUNCTION DEFINITION HERE

dict1 = {}
assert len(dict1) == 0
assert incrementKeyCount(dict1, "CS8") == None
assert len(dict1) == 1
assert ("CS8" in dict1) == True
assert dict1["CS8"] == 1
assert incrementKeyCount(dict1, "CS8") == None
assert len(dict1) == 1
assert dict1["CS8"] == 2
assert incrementKeyCount(dict1, "MATH3A") == None
assert len(dict1) == 2
assert ("MATH3A" in dict1) == True
assert dict1["MATH3A"] == 1

def computeGrade(percentage):
   ''' Return the corresponding letter grade string based on the value of
   percentage using the following scale:
   [100 - 90]: 'A'
   (90 - 80] : 'B'
   (80 - 70] : 'C'
   (70 - 60] : 'D'
   (60 - 0]  : 'F'
   * If percentage is not a number type (int or float) OR if percentage is
   outside the range of [100 - 0], return an empty string ("").
   * Note, you can check if percentage is an int with
   type(percentage) == int, and a float with type(percentage) == float
   '''
   # COMPLETE YOUR FUNCTION DEFINITION HERE

assert computeGrade(90) == "A"
assert computeGrade("80") == ""
assert computeGrade(80) == "B"
assert computeGrade(79.9) == "C"
assert computeGrade(64) == "D"
assert computeGrade(60) == "D"
assert computeGrade(56) == "F"
assert computeGrade(101) == ""
assert computeGrade(-1) == ""
assert computeGrade(100) == "A"
assert computeGrade(0) == "F"

# Definition of a Book namedtuple object used for the following
# function below.
from collections import namedtuple

def updateBookPrice(percentIncrease, bookObject):
   ''' Function that takes in a namedtuple Book object (bookObject)
   and a psotive float (percentIncrease), and returns a new namedtuple
   Book object with the same values of bookObject except the price
   is increased by percentIncrease (inflation is real!)
   '''
   # COMPLETE YOUR FUNCTION DEFINITION HERE

Book = namedtuple("Book", ["title", "author", "price"])
b1 = Book("Title1", "Author1", 10)
b2 = Book("Title2", "Author2", 15)
b3 = Book("Title3", "Author3", 50)
assert updateBookPrice(0, b1) == Book("Title1", "Author1", 10)
assert updateBookPrice(0.2, b1) == Book("Title1", "Author1", 12)
assert updateBookPrice(1.1, b1) == Book("Title1", "Author1", 21)
assert updateBookPrice(0.1, b2) == Book("Title2", "Author2", 16.5)
assert updateBookPrice(0.5, b3) == Book("Title3", "Author3", 75)
```

Several `assert` statements are included after each function definition. Assert statements are a quick way to do simple testing. The goal is to run your code such that these `assert` statements do not produce any errors and your code successfully finishes execution.

In Python, statements are executed line-by-line from top to bottom. So if your code has an error and an `assert` statement doesn't pass, then you will see which `assert` statement failed and execution will stop (no other statements after the error will be executed).

In order to run your `lab01.py` file in IDLE, go to `Run` -> `Run Module`. This will start the execution of the file you're working on and the output will be displayed in IDLE's Interactive Shell.

Also note that Gradescope may not run your code if all `assert` statements in your file do not pass - in this case, you can comment out the `assert` statements in your code before submitting to Gradescope for partial credit (Gradescope will run its own `assert` statements when autograding your work, and assign points based on what `assert` statements are passing).

# Submitting to Gradescope

The lab assignment `Lab01` should appear in your Gradescope dashboard in CMPSCW 8. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. **Remember, if you worked with a partner, both you and your partner must make separate submissions in order to receive credit.**

This prompt is shown below:

![Gradescope_upload](Gradescope_upload.png)

You either can navigate to your file(s) or "drag-and-drop" them into the "Submit Programming Assignment" window.

If you already submitted something on Gradescope, it will take you to their "Autograder Results" page. There is a "Resubmit" button on the bottom right that will allow you to update the files for your submission.

If everything is correct, you'll see a successful submission passing all of the autograder tests shown below.

![Gradescope_results](Gradescope_results.PNG)

If the tests don't pass, you may get some error message that may or may not be obvious at this point. Don't worry - if the tests didn't pass, take a minute to think about what may have caused the error. If your tests didn't pass and you're still not sure why you're getting the error, feel free to ask your TAs or ULAs.

