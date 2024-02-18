---
layout: lab
num: lab02
ready: true
desc: "Python Functions / For Loops"
assigned: 2024-02-18 11:00:00-7
due: 2024-02-25 23:59:59-7
---

# Introduction

Your first lab for this week is an introduction to writing Python code in `.py` files and making submissions to Gradescope's autograder. You may choose to work with a partner if you like (but this is not required). **If you choose to work with a partner, please follow the instructions on recording who your partner is (explained below). Both you and your partner MUST make individual submissions on the Gradescope system to receive credit.**

As stated in the syllabus, Gradescope labs will only have a 24-hour late window after the deadline. Submissions during the late window period will have an automatic 20% deduction from your assignment. We will only consider the most recent submission.

**Note: In general, it is a good idea that you start all assignments early so you can utilize our office hours and lab sections to seek assistance / ask clarifying questions before the deadline if needed**

## Goals for this lab

By the time you have completed this lab, you should have:
* create and run Python code in IDLE
* practice various looping concepts (including accumulator patterns)
* submited your work using the Gradescope system

# Get setup with Gradescope

We will use Gradescope to autograde this lab assignment.

The lab assignment `Lab02` should appear in your Gradescope dashboard in CMPSCW 8. You will need to submit your code for Lab02 there.

# Create your Lab02 directory

In general, it's important to be organized when working on various assignments. For this lab, my recommendation is to create a `csw8` folder that will contain sub folders for each lab - for this lab, I would recommend creating a `csw8/lab02` folder on your computer where you can save your file. In general, I recommend creating a new folder for each lab assignment.

# Create a new `lab02.py` file

Using the editor of your choice, create a `lab02.py` file in your `lab02` directory. This `lab02.py` file will contain the python code you will submit for this lab assignment. As also stated in the previous lab, the steps of creating this new file with IDLE are:

* Open IDLE on your computer
* Go to `File` -> `New File`, which will create an untitled file.
* Save this file by going to `File` -> `Save`, which will prompt you to save this file in a specified location
	* Name this file `lab02` (assuming the extension will automatically be saved as a `.py` file)
      * You must use the **exact** same name and casing when creating your file
	* Save this file under your `csw8/lab02` directory you created for this lab

# Copy the following code template into `lab02.py` and complete the function definitions

We will write five Python functions for this lab. **If you choose to work with a partner, you and your partner must create your own file, and both you and your partner must submit your work separately.**

Copy the following code into your `lab02.py` file and complete the function definitions according to the comments. **Type your actual name (and your partner's name if you worked with one) at the top**:

```python
# lab02.py, CSW8
# [Type your name here]
# [Type your partner's name here if you worked with someone]

def getNumChars(listOfElements):
    ''' Function that takes in a list of elements, and returns
    the number of characters for all strings in listOfElements.
    * listOfElements can contain values of any type.
        * Note you can check if an element is a string with
        type(value) == str
    * If no elements in listOfElements are strings, return 0.
        * Note that an empty string ('') is considered to have
        0 characters.
    '''
    # COMPLETE YOUR FUNCTION DEFINITION HERE

assert getNumChars([]) == 0
assert getNumChars([1, 2.4, True]) == 0
assert getNumChars(["", None]) == 0
assert getNumChars(["", "\n", " "]) == 2
assert getNumChars(["Python", "is", "awesome"]) == 15
assert getNumChars(["one", 2, "three", 4.0]) == 8
assert getNumChars(["one", "two", 3, "four", "five"]) == 14

def countMultiples(listOfElements, x):
    ''' Function that takes in a list of elements and an integer > 0 (x),
    and returns the number of items in listOfElements that are
    multiples of x.
    * listOfElements can contain values of any type.
    * If no elements exist in listOfElements, return 0.
    * If no numerical elements exist in listOfElements, return 0.
    '''
    # COMPLETE YOUR FUNCTION DEFINITION HERE

assert countMultiples([], 1) == 0
assert countMultiples([4, 8, 12, 16, 20], 4) == 5
assert countMultiples([-2, 3, 4, -5, 6.1, 9], 3) == 2
assert countMultiples(["one", 2, "three", 4.0], 2) == 2
assert countMultiples(["Python", "is", "awesome"], 5) == 0

def getLongestString(listOfElements):
    ''' Function that takes in a list of elements, and returns
    the string with the most number of characters.
    * listOfElements can contain values of any type.
    * If no elements in listOfElements are strings, return
    None.
    * If two or more largest strings have the same number of
    characters, return the first string in the order it
    appears in listOfElements (lower index).
    '''
    # COMPLETE YOUR FUNCTION DEFINITION HERE

assert getLongestString([]) == None
assert getLongestString([1, 2.4, True]) == None
assert getLongestString(["", None]) == ""
assert getLongestString(["Abcd", "abc", "bc"]) == "Abcd"
assert getLongestString(["Python", "is", "awesome"]) == "awesome"
assert getLongestString(["one", 2, "three", 4.0]) == "three"
assert getLongestString(["one", "two", "four", "five"]) == "four"
assert getLongestString(["one", "two", 3, "four", "five"]) == "four"


def removeMultiples(listOfElements, x):
    ''' Function that takes in a list of elements and an integer > 0 (x),
    and returns a new list containing all elements in listOfElements
    EXCEPT the items that are multiples of x.
    * listOfElements can contain values of any type.
    * Elements in the returned list must occur in the order they
    appear in listOfElements
    * Hint, think of the accumulator pattern, but instead of counting
    we're accumulating a collection
    '''
    # COMPLETE YOUR FUNCTION DEFINITION HERE

assert removeMultiples([], 1) == []
assert removeMultiples([4, 8, 12, 16, 20], 4) == []
assert removeMultiples([-2, 3, 4, -5, 6.1, 9], 3) == [-2, 4, -5, 6.1]
assert removeMultiples(["one", 2, "three", 4.0], 2) == ["one", "three"]
assert removeMultiples(["Python", "is", "awesome"], 5) == ["Python", "is", "awesome"]

def organizeWords(listOfStr):
    ''' Function that takes in a list of strings, and returns a dictionary
    where the keys are capital characters, and each key's corresponding 
    value is a list containing all strings in listOfStr (in all capital
    letters) that start with the key character in capital letters in the order that they appear in listOfStr.
    * An empty listOfStr should return an empty dictionary
    * You may assume listOfStr ONLY contains string elements (or is empty)
    * The empty string ('') should not be stored in the dictionary
    * Consider using the string's .upper() method when creating keys in
    the dictionary, and creating list values in the dictionary.
    '''
    # COMPLETE YOUR FUNCTION DEFINITION HERE

assert organizeWords([]) == {}

D = organizeWords(["CS8"])
assert ("C" in D) == True
assert ("c" in D) == False
assert D["C"] == ["CS8"]

D = organizeWords(["Python", "is", "awesome", ""])
assert ("i" in D) == False
assert ("P" in D) == True
assert ("I" in D) == True
assert ("A" in D) == True
assert ("a" in D) == False
assert ("" in D) == False
assert D["P"] == ["PYTHON"]
assert D["I"] == ["IS"]
assert D["A"] == ["AWESOME"]

D = organizeWords(["Ant", "antler", "ART", "Car", "", "bee", "can"])
assert ("b" in D) == False
assert ("B" in D) == True
assert ("a" in D) == False
assert ("A" in D) == True
assert ("C" in D) == True
assert ("" in D) == False
assert D["A"] == ["ANT", "ANTLER", "ART"]
assert D["C"] == ["CAR", "CAN"]
assert D["B"] == ["BEE"]
```

Several `assert` statements are included after each function definition. Remember, assert statements are a quick way to do simple testing. The goal is to run your code such that these `assert` statements do not produce any errors and your code successfully finishes execution.

In Python, statements are executed line-by-line from top to bottom. So if your code has an error and an `assert` statement doesn't pass, then you will see which `assert` statement failed and execution will stop (no other statements after the error will be executed).

In order to run your `lab02.py` file in IDLE, go to `Run` -> `Run Module`. This will start the execution of the file you're working on and the output will be displayed in IDLE's Interactive Shell.

Also note that Gradescope may not run your code if all `assert` statements in your file do not pass - in this case, you can comment out the `assert` statements in your code before submitting to Gradescope for partial credit (Gradescope will run its own `assert` statements when autograding your work, and assign points based on what `assert` statements are passing).

# Submitting to Gradescope

The lab assignment `Lab02` should appear in your Gradescope dashboard in CMPSCW 8. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. **Remember, if you worked with a partner, both you and your partner must make separate submissions in order to receive credit.**

You either can navigate to your file(s) or "drag-and-drop" them into the "Submit Programming Assignment" window.

If you already submitted something on Gradescope, it will take you to their "Autograder Results" page. There is a "Resubmit" button on the bottom right that will allow you to update the files for your submission.

If everything is correct, you'll see a successful submission passing all of the autograder tests.

If the tests don't pass, you may get some error message that may or may not be obvious at this point. Don't worry - if the tests didn't pass, take a minute to think about what may have caused the error. If your tests didn't pass and you're still not sure why you're getting the error, feel free to ask your TAs or ULAs.

