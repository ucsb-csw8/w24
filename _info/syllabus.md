---
title: "Syllabus, CMPSCW 8, Winter 2024"
layout: handout
ready: true
---

Basic Facts
-----------

* **Course Web Site**: <https://ucsb-csw8.github.io/w24/>
* **Instructor**: Richert Wang
   * Please use [Piazza](https://piazza.com/ucsb/winter2024/cmpscw8) for course related communication.
* **Lecture**: Tu, Th 11:00am-12:15pm on Zoom
* **TAs**:  {{site.ta_list_full}} (contact via Piazza)
* **ULAs**: {{site.mentors_list}} (contact via Piazza)
* **Lab** (50 minute lab sections): Wednesdays 10am, 11am, 12pm, 1pm, 2pm, 3pm, 4pm, 5pm [https://ucsb.zoom.us/j/88499822812](https://ucsb.zoom.us/j/88499822812)
* **Office Hours**: See <https://ucsb-csw8.github.io/w24/info/office_hours/>

# Required Resources

* Textbook:
  * [zyBooks](https://www.zybooks.com/)

Official UCSB Catalog Description
---------------------------------

<div style="background-color:#eee; border: 8px inset #333; font-size:90%; margin:1em; width:45em; padding: 0.5em;" markdown="1">

**CMPSC 8/8W: Introduction to Computer Science**<br><br>
**Enrollment Comments:** Not open for credit to students who have completed Computer Science 16 or Engineering 3 or ECE 3.<br>
**Repeat Comments:** Legal repeat for CMPSC 5AA-ZZ.<br><br>
Introduction to computer program development for students with little to no programming experience. Basic programming concepts, variables and expressions, data and control structures, algorithms, debugging, program design, and documentation.

</div>

# A few course policies in brief

* If you are registered for another UCSB course that overlaps with this one, you are responsible for any work or material you may miss. I am within my rights to not give credit on any work you miss as a result, and WILL NOT make accomodations.
* Collaboration is only permitted when specifically allowed for — otherwise, you must do your own work independently. **Students are responsible for educating themselves on UCSB's academic integrity policies and abide by them.** [UCSB Academic Integrity](https://studentconduct.sa.ucsb.edu/academic-integrity). Any violation of academic integrity in this course will result in an automatic F and be reported to UCSB's Office of Student Conduct. If you have any questions regarding academic integrity, I'll be happy to discuss them.
* We will use the online interactive textbook [zyBooks](https://www.zybooks.com/).
  * Instructions on purchasing the version for our course will be provided.
* We will use the [Gradescope](https://gradescope.com) this quarter for certain lab assignments, quizzes, and the final exam.
* We will use the [Piazza](https://piazza.com/ucsb/winter2024/cmpscw8)

# What this course is about 

This class serves as an <strong>introduction to programming and computer science</strong>. We will use the Python language and write Python programs throughout the course. We will be using Python 3 in the class. The Python Interpreter can be downloaded for free from Python's download page <http://python.org/downloads/>. I encourage everyone to install Python on their local computer in order to practice programming in your own time.

If you find yourself working on a computer that doesn't have Python installed, you can run simple Python code (along with several other languages) on the web with tools such as [IDEOne](https://ideone.com). This is not a requirement for the course, but you may find it to be a useful tool.

Learning how to program requires <strong>A LOT</strong> of practice like learning any new skill. Making mistakes is an essential part of learning as long as you learn from them! Questions like "I wonder what will happen if I do this..." or "How will Python behave in this case..." is a great way to investigate and observe the functionality and limitations of a programming language (there are many programming languages available to software developers and each have their specific pros and cons that may or may not be the best choice for the problems you are trying to solve).

I find the best way to practice is to <strong>rapid prototype</strong> constantly. Writing simple snippets of code to test and confirm your understanding allows you to 1) practice typing out code, which makes you more comfortable with the language and 2) solidify your understanding of the specific behavior of the programming language functionality.

Programming is the study of <strong>algorithms</strong>, i.e. step-by-step instructions telling the computer what it needs to do. There are <strong>MANY</strong> algorithms that can solve a problem and it's important to consider the computational time, memory space, and correctness of the algorithms you create.

# Why Python?

* Python is a popular choice for introductory programming courses since it arguably easier to learn than C/C++ and Java.
* Python is a largely supported language and is widely used in academia and industry.
* There is a lot of support for Python that comes with the language itself and 3rd party libraries other developers created that you can use for many types of applications.

# What you need to learn to become a skilled beginning level programmer

So, what is it that you need to know to be a skilled beginning-level programmer in Python? Here's the list of what you'll need to be ready for CMPSC 9 / 16 (the next programming courses):

<table border="1" cellspacing="1" cellpadding="1" id="topicTable">
  <tr>
    <td><ul class="style11">
      <li>Problem solving
        <ul>
            <li>breaking down a problem into a sequence of steps</li>
          <li>abstracting specific problems into general ones<br />
            and finding general solutions</li>
        </ul>
      </li>
      <li>Memory concepts
        <ul>
            <li>variables, primitive vs. reference variables, name, type, value</li>
          <li>assignment statements</li>
          <li>scope of variables</li>
        </ul>
      </li>
      <li>Control structures
        <ul>
            <li>for loops, if/else, while loops</li>
        </ul>
      </li>
      <li>Lists in Python (similar to arrays in other languages)
        <ul>
            <li>index vs. value, finding sum, min, max, average, count of elements matching some condition, making a new list of elements containing only those that match some condition</li>
        </ul>
      </li>
    </ul>    </td>
    <td><ul class="style11">
      <li>Functions
        <ul>
            <li>function call vs. function definition</li>
          <li>formal vs. actual parameters (arguments)</li>
        </ul>
      </li>
      <li>Testing
        <ul>
            <li>How to test your code</li>
        </ul>
      </li>
      <li>Input/output concepts
        <ul>
            <li>Writing to the terminal</li>
          <li>Reading from the keyboard</li>
          <li>Reading and writing to files</li>
          <li>Neatly formatting output</li>
        </ul>
      </li>
      <li>Program style
        <ul>
            <li>How to write code that other people can read and understand</li>
        </ul>
      </li>
    </ul>    </td>
  </tr>
</table>

## Piazza Etiquette

Here are some general rules about Piazza, to keep it from getting cluttered, make sure you can benefit the most from having this forum, and to make it easier for us to answer your questions. Class communication will be done through this platform (reminders / announcements / etc).

So, when you have a question:

1. Search through existing Piazza questions to make sure your question hasn't been answered before.
2. Use the filters (lab, lecture, logistics, etc.) to navigate between questions easily.
3. If you believe that other students will benefit from the answer, make the question public. Else, make it private.
4. Please **DO NOT** post your code in your public questions. Snippets of code are generally fine, but should be framed in a generic way not specific to an assignment.
5. We do our best to get to your questions answered in a timely manner. However, if you find a question that you can help with, please do! We encourage students' participation in answering questions.
6. Remember that Piazza has a feature that will allow you to post anonymously - this will not reveal the author of a question/contribution to other students (but will be known to the course staff).

# Course Grades

Letter grades will be determined by the end of the course after all components have been computed. I can say that I will not grade harder than a traditional straight scale (90% = A-, 80% = B-, etc.). However, I will adjust the letter grades accordingly based on the class' overall performance at the end of the course. If you are concerned about your grade in the class, I encourage you to discuss the matter with me during my office hours. Please come talk to me sooner rather than later so there can be some time where we can help you succeed in the course.

Your course grade will be determined as follows:

| Grade Item                                    | Percentage of Final Grade |
|-----------------------------------------------|---------------------------|
| Quizzes (Fridays, Week 2,4,6,8,10)            | 25 %                      |
| Final (Wednesday 3/20), 12pm - 2pm            | 25 %                      |
| zyBooks Participation Activities (PA)         | 5 %                       |
| zyBooks Challenge Activities (CA)             | 15 %                      |
| zyBooks Lab Activities (LA)                   | 20 %                      |
| Gradescope Labs                               | 10 %                      |

# Workload

Programming, like all subjects, takes a lot of time and practice to master. UCSB estimates that a 4-unit course is equivalent to approximately 12 hours of work per week <https://catalog.ucsb.edu/academicsandpolicies/policies/academicpoliciesprocedures#units-of-credit1>. 

* In general, there will be zyBook assignments where each week corresponds to one chapter in zyBooks (with the exception of the first week being due at the end of week 2). zyBook assignments are due on Sundays by 11:59PM PST.
  * Refer to the calendar on when assignments are due [Calendar](https://ucsb-csw8.github.io/w24/info/calendar/).
  * Each chapter has three categories of assignments. Participation Activities (PA), Challenge Activities (CA), and Lab Activities (LA).
* In order to gain experience with writing native Python code outside of zyBooks, there will be a few Gradescope autograded labs (where you will submit .py files) assigned throughout the quarter (more on these labs will be posted throughout the quarter).
  * Gradescope labs are autograded and your score is based on Gradescope's recorded score.
* We will have timed 30 minute bi-weekly quizzes on Gradescope given on Fridays of even weeks (Fridays on Weeks 2,4,6,8,10), and are open to complete from 8am - 8pm PST.
* We will have a remote synchronous 2 hour final exam on Gradescope during the scheduled final exam time.

# Late Policy and Regrade Requests

I will consider late submissions / accommodations <strong>only</strong> for medical or family emergencies **and only when formal documentation can be provided**. This **does not** include overwhelming workload from other courses, scheduling conflicts, technical difficulties, or vacation plans.

I recognize that some absences (e.g. minor illnesses, mishaps, etc.) are unavoidable. Litigating whether each of these is "excused" or not isn't a good use of anyone's time. The late work policy below accounts for absences (or failure to submit work) in a way that does not unduly penalize your grade unless it becomes excessive. The policy (unless stated otherwise) are:

* Your zyBook activities are based on the work you complete by the deadline. However, you can receive partial credit for work submitted to zyBooks past the deadline **within one week of the original deadline**.
  * You still receive full credit for any work in zyBooks completed **before** the deadline, but any portion of incomplete work that is submitted **within one week after the deadline** will only receive 50%.
  * No credit will be given for any work in zyBooks submitted **one week after** the deadline.
* Your lowest quiz score will be dropped automatically.
* Gradescope labs must be submitted by the due date. There will be a 24-hour late window open on Gradescope for each lab. Submissions during the late window period will have an automatic **20%** deduction from your grade. We will only consider the most recent submission.
* **I highly encourage students not to wait until the last-minute to complete assignments.** We generally will not be available to provide assistance over the weekend, and there is a risk of encountering technical difficulties (internet outages for example) that prevent an on-time submission. **Please plan accordingly.**
* For any manually graded component (Quizzes / Final Exam), regrade requests must be made on Gradescope and we will not consider a regrade request one week after the assignment grades are distributed back to students (except stated otherwise).

Accommodations for disabilities
-------------------------------

Students with disabilities may request academic accommodations for exams online through the UCSB Disabled Students Program at [http://dsp.sa.ucsb.edu/](http://dsp.sa.ucsb.edu/). Please make your requests for exam accommodations through the online system as early in the quarter as possible to ensure proper arrangement.

Managing stress
---------------

Personal concerns such as stress, anxiety, relationships, depression, cultural differences, can interfere with the ability of students to succeed and thrive. For helpful resources, please contact UCSB Counseling & Psychological Services (CAPS) at 805-893-4411 or visit [http://counseling.sa.ucsb.edu/](http://counseling.sa.ucsb.edu/).

Responsible scholarship
-----------------------

Honesty and integrity in all academic work is essential for a valuable educational experience. The Office of Judicial Affairs has policies, tips, and resources for proper citation use, recognizing actions considered to be cheating or other forms of academic theft, and students’ responsibilities, available on their website at: <https://studentconduct.sa.ucsb.edu/academic-integrity>. **Students are responsible for educating themselves on the policies and abide by them.**

Furthermore, for general academic support, students are encouraged to visit Campus Learning Assistance Services (CLAS) early and often. CLAS offers instructional groups, drop-in tutoring, writing and ESL services, skills workshops and one-on-one consultations. CLAS is located on the third floor of the Student Resource Building, or visit <http://clas.sa.ucsb.edu>

Standard Disclaimer
-------------------

This syllabus is as accurate as possible, but is subject to change at the instructor's discretion, within the bounds of UC policy.
