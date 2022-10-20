# Iteration & Loops in Python

<a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license"><img style="border-width: 0;" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" alt="Creative Commons License" /></a>This tutorial was written by Katherine Walden and is licensed under a <a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

## Lab Overview & Goals

This lab provides an overview of foundational programming concepts in the areas of control flow and functions, with a focus on Python syntax. Topics covered include:
- Control flow and control structures
- Event-controlled and count-controlled loops
- Looping structures in Python (`for` and `while`)

## Acknowledgements

When building this lab, the author consulted materials developed by:
- [Dr. Peter Bui](http://www3.nd.edu/~pbui/) for the [CSE 10101 "Elements of Computing I" course](https://www3.nd.edu/~pbui/teaching/cdt.30010.fa16/).
  * [Conditional and Alternative Execution](http://nbviewer.jupyter.org/urls/gitlab.com/snippets/25773/raw)
  * [Loops](http://nbviewer.jupyter.org/urls/gitlab.com/snippets/26115/raw)
- [Dr. Janet Davis](https://cs.whitman.edu/~davisj/) for the the [CSC 105 "The Digital Age" course](https://www.cs.grinnell.edu/~davisjan/csc/105/2012S/). 
  * [Laboratory: Programming in Python (Decisions and Repetition)](http://www.cs.grinnell.edu/~davisjan/csc/105/labs/python3.html)
- [Dr. Corey Pennycuff](https://www3.nd.edu/~cpennycu/) for the [CSE 10101 Elements of Computing (Fall 2019)](https://www3.nd.edu/~cpennycu/2019/fa-CSE10101-CDT30010.html).
  * [Control flow structures](https://www3.nd.edu/~cpennycu/2019/assets/fall/EOC/19.09.03.ipynb)
  * [Looping structures](https://www3.nd.edu/~cpennycu/2019/fa-CSE10101-CDT30010.html)
- [Dr. Lindsay K. Mattock](http://lindsaymattock.net/) for the the [SLIS 5020 Computing Foundations course](http://lindsaymattock.net/computingfoundations.html). 

Definitions and explanations in this lab are adapted from Kenneth Leroy Busbee and Dave Braunschweig, *[Programming Fundamentals: A Modular Structured Approach, 2nd Edition](https://press.rebus.community/programmingfundamentals/)* (Rebus Press, 2018)
- [Chapter V, Loops](https://press.rebus.community/programmingfundamentals/part/loops/)

# Table of Contents
- [Key Concepts](#key-concepts)
- [Lab Notebook Template](#lab-notebook-template)
- [Overview](#overview)
  * [Iteration Control Structures](#iteration-control-structures)
  * [Iteration in Python](#iteration-in-python)
- [Loops](#loops)
  * [Event-Controlled Loops](#event-controlled-loops)
  * [Count-Controlled Loops](#count-controlled-loops)
- [Additional Considerations](#additional-considerations)
  * [`range()`](#range)
  * [`enumerate()`](#enumerate)
  * [Infinite Loops](#infinite-loops)
  * [Break & Continue](#break--continue)
- [Putting It All Together](#putting-it-all-together)
- [How to Submit This Lab (and show your work)](#how-to-submit-this-lab-and-show-your-work)
- [Lab Notebook Questions](#lab-notebook-questions)

[Click here](https://colab.research.google.com/drive/1vyAHwOf76_byT1CY8ofFwBg67h3Sljuh?usp=sharing) to access this lab procedure as a Jupyter Notebook (Google CoLab, ND users)

# Key Concepts

[Click here](https://github.com/kwaldenphd/python-loops-iteration/blob/main/key-concepts.md) for a full list of key concepts and definitions from this lab.

# Lab Notebook Template

[Click here](https://replit.com/team/eoc-f22/Iteration-and-Loops-in-Python) to make a copy of the Replit template for this lab.

Alternatives:
- [`.py` template](https://drive.google.com/file/d/10Ze1JUafZUZb8vZVjcOKpjK7MF-Q9OL3/view?usp=sharing) (Google Drive, ND users)
- [Jupyter Notebook, `.ipynb`](https://colab.research.google.com/drive/1duVhsQ-jf6MZpMi0hyc8o4nSG61TJpI0?usp=sharing) (Google Colab, ND users)

## How to submit this lab (and show your work)

Moving forward, we'll submit lab notebooks as `.py` files. 

One option is to have a `.py` file that you use to run code and test programs while working through the lab. When ready to submit the lab notebook, you add comments and remove extraneous materials.

Another option is to have an "official" `.py` file that you are using as a lab notebook (separate from your working/testing file). Use comments in Python to note when you are starting a new question (as well as answering a question).
  * Example: `Lab_Notebook_Walden.py`

What gets submitted as the lab notebook is the `Lab_Notebook_Walden.py` file.
- When in doubt, use comments
- Be sure you are using comments to note what question you're responding to

# Overview

By this point, we've spent multiple labs thinking through control structures and control flow, with a focus on how we use them in Python.

From Busbee and Braunschweig's "[Structured Programming](https://press.rebus.community/programmingfundamentals/chapter/structured-programming/)," in *Programming Fundamentals*:
    
"One of the most important concepts of programming is the ability to control a program so that different lines of code are executed or that some lines of code are executed many times. The mechanisms that allow us to control the flow of execution are called control structures. Flowcharting is a method of documenting (charting) the flow (or paths) that a program would execute. There are three main categories of control structures:"
  * Sequence [executes in given sequence]
  * Selection [selects between two or more flows using condition or question]
  * Iteration [repeats same piece of code multiple times]

Examples of control structures in Python include:
- `if-then-else` (syntax: `if`, `else`, `elif`)
- `while` statements (syntax: `while`)
- functions (built-in and named)

We've also previously been introduced to the concept of **code blocks**. From Busbee and Braunschweig's "[Code Blocks](https://press.rebus.community/programmingfundamentals/chapter/code-blocks/)" from *Programming Fundamentals*:
- "A code block, sometimes referred to as a compound statement, is a lexical structure of source code which is grouped together. Blocks consist of one or more declarations and statements. A programming language that permits the creation of blocks, including blocks nested within other blocks, is called a block-structured programming language. Blocks are fundamental to structured programming, where control structures are formed from blocks."

## Iteration Control Structures

<p align="center"><img src="https://github.com/kwaldenphd/python-loops-iteration/blob/main/images/for-loop-meme.png?raw=true" width="500"></p>

From Busbee and Braunschweig's "[Iteration Control Structures](https://press.rebus.community/programmingfundamentals/chapter/iteration-control-structures/)," in *Programming Fundamentals*:

"In iteration control structures, a statement or block is executed until the program reaches a certain state, or operations have been applied to every element of a collection. This is usually expressed with keywords such as `while`, `repeat`, `for`, or `do..until`. The basic attribute of an iteration control structure is to be able to repeat some lines of code. The visual display of iteration creates a circular loop pattern when flowcharted, thus the word 'loop' is associated with iteration control structures."

Let's break down that definition:
- Iteration (repetition of a process) is a type of control structure
- In programming languages, iteration involves lines of code repeating until a condition is met of the end of a group of values has been reached.
- Because iteration in this context involves a circular pattern, many object-oriented programming languages refer to these structures as `loops`

### Iteration in Pyton

We've actually already seen iteration in action in previous Python labs.

```Python
# create string variable
message = "Hello world!"

# return number of characters in string
len(message)

# test if character x is in string
'x' in message # returns false

# test if symbol % is NOT in string
'%' not in message # returns true
```

These membership tests (using `in` and `not in`) involve iteration- the program goes left-to-right, starting at the first character in the string. You may remember we used `.index()` in the data storage lab to search for characters that appear multiple times in a string- Python only returned the first occurrence of the character because of how iteration impacted the `.index()` method.

Another example of iteration in action, this time using a `list`:

```Python
# list of string objects
fruits = ["apple", "banana", "blueberry", "cherry", "pear"]

# return index for cherry
print("The index for cherry is ", fruits.index("cherry"))

# return index for pear
print("The index for pear is ", fruits.index("pear"))

# test if apple is in list
print("apple" in fruits)

# test if blueberry is NOT in list
print("blueberry" not in fruits)
```

Iteration works similarly in a list- the program goes left-to-right, starting with the first element in the list. 

For more on the technical foundations of iteration in Python:
- W3Schools, "[Python Iterators](https://www.w3schools.com/python/python_iterators.asp)"

## Loops

Testing for membership or returning index values are a couple examples of tasks we can accomplish in Python using iteration.

But let's review the definition of iteration as a control structure. From Busbee and Braunschweig's "[Iteration Control Structures](https://press.rebus.community/programmingfundamentals/chapter/iteration-control-structures/)," in *Programming Fundamentals*:

"In iteration control structures, a statement or block is executed until the program reaches a certain state, or operations have been applied to every element of a collection. This is usually expressed with keywords such as `while`, `repeat`, `for`, or `do..until`. The basic attribute of an iteration control structure is to be able to repeat some lines of code. The visual display of iteration creates a circular loop pattern when flowcharted, thus the word 'loop' is associated with iteration control structures."

Breaking down that definition:
- Iteration (repetition of a process) is a type of control structure
- In programming languages, iteration involves lines of code repeating until a condition is met of the end of a group of values has been reached.
- Because iteration in this context involves a circular pattern, many object-oriented programming languages refer to these structures as `loops`

The power of iteration as a control structure comes from a programming concept called `loops`.

<p align="center"><img src="https://github.com/kwaldenphd/python-loops-iteration/blob/main/images/loop-comparison-diagram.png?raw=true" width="1000"></p>

Most high-level programming languages support two main types of loops: event-controlled and count-controlled
- **Event-controlled loops** test for an initial condition, and execution continues as long as the initial condition is `True`. How many times the loop will execute *is not known*.
- **Count-controlled loops** (sometimes called counter-controlled loops) continue executing for a pre-determined number of times. The number of times the loop will execute is known because the loop is iterating through a collection of objects/values (i.e. a string or list), or the iteration when the initial condition will no longer be `True` is known.

Let's break down each type.

### Event-Controlled Loops

<p align="center"><img src="https://github.com/kwaldenphd/python-loops-iteration/blob/main/images/while-loop-diagram.png?raw=true" width="500"></p>

In Python, event-controlled loops are written using a `while` statement and are called `while loop`. A `while` statement tests for an initial condition, and the lines of code indented under `while` run only when the initial condition is `True`.

In each iteration through the `while` loop, Python will:
- Evaluate the initial condition (which is a Boolean true/false expression)
- If the condition is `False`, exit the loop and continue the program
- If the condition is `True`, then execute other statements in the body of the loop and return to the beginning of the loop

The basic syntax for a `while` loop:

```Python
# while loop sample syntax
while condition:
	statement(s)
```

To express this logic another way:

```Python
# while loop sample syntax
while THIS CONDITION IS TRUE:
	DO THIS THING
```

For example, in a previous lab, you were asked to write a guessing game program that used a `while` statement. What this program might have looked like:

```Python
# correct answer
secret = 7

# guess
guess = int(input("Guess a number: "))

# while statement
while guess != secret:
  if guess > secret:
    print("Your guess is too high. Better luck next time")
    guess = int(input("Guess again. Enter another number: "))
  else:
    print("Your guess is too low. Better luck next time.")
    guess = int(input("Guess again. Enter another number: "))
  

print("Congrats, you guessed the secret number!")
```

This is an example of a `while` loop. Because the number of times the loop will execute is not known, this is an example of an event-controlled loop. That is, the loop will continue executing (looping) until the initial condition (`guess != secret`) is no longer true.

#### `While` Loop Comprehension Check

<table>
 <tr><td>
<img src="https://github.com/kwaldenphd/internet/blob/main/images/clipboard.png?raw=true" alt="Clipboard icon" width="50"/></td>
  <td><a href="https://docs.google.com/forms/d/e/1FAIpQLSfhrN-wLhsGhxnbEDjBNVkF35Z8p31OIJSDdBfgOtI_KzAlAg/viewform?usp=sf_link">Python While Loops Comprehension Check</a></td>
  </tr>
  </table>
  
#### `While` Loop Application

Q1: Given the following program:

```Python
# assign count variable
count = 1

# while loop
while count <= 5: # initial condition
   print ("Python") # print statement
   count = count + 1 # reassign count

# final print statement
print ("Done")
```

How would you modify the program to print or output the string nine (9) times and also include line numbers as part of the output? Answer to this question includes program + comments that document process and explain your code.

For example, your output might look like the following: 

```Python
1 Python
2 Python
3 Python
4 Python
5 Python 
6 Python
7 Python
8 Python
9 Python
IS FUN!
```

### Count-Controlled Loops in Python

<p align="center"><img src="https://github.com/kwaldenphd/python-loops-iteration/blob/main/images/for-loop-diagram.png?raw=true" width="500"></p>

In Python, count-controlled loops are written using a `for` statement and are called `for loop`. A `for loop` iterates over each value in a group of values- the lines of code nested under the initial statement run for each iteration.

`for` loops let us iterate through a definite set of objects. In each iteration through the `for` loop, Python will:
- Extract one element from the dataset
- Execute the body of the `for` loop using the item bound to the element
- Go back to the first step
- Keep iterating through the loop until reaching the end of the dataset

The basic syntax in a `for` loop:

```Python
# sample for loop syntax
for item in dataset:
 statement(s)
```

In this syntax, `item` is a placeholder for each element in `dataset`. We can replace `item` with another word or letter character.

```Python
# sample for loop syntax
for i in dataset:
	statement(s)
```

In this syntax, `dataset` stands for the group of items we want Python to iterate over. That group of items could be a list, a list variable, string, string variable, etc. 

We've encountered a few `for` loops in previous labs.

Iterating over items in a list:

```Python
# list of numbers
numbers = [1, 3, 5, 7, 9, 11, 13, 15, 17]

# sample for loop that iterates over items in list and outputs each number
for number in numbers:
 print(number)
 ```

Nesting `if-then-else` logic in a `for` loop:

```Python
# list of numbers
numbers = [1, 3, 5, 7, 9, 11, 13, 15, 17]

# for loop that iterates over numbers
for number in numbers:
  if number < 10:
    print(str(number) + " is less than 10")
  elif number > = 10 and number < 15:
    print(str(number) + " is greater than or equal to 10 and less than 15")
  else:
    print(str(number) + " is greater than 15")
```

A previous lab notebook question asked you to print out each sublist (in a nested list or list of lists) on its own line, and also print the individual values on their own lines.

An approach to that program that doesn't use iteration or a `for` loop:

```Python
# create list with sublists
numbers = [[0, 1], [2, 3], [4, 5]]

# print out each sublist
print(numbers[0])
print(numbers[1])
print(numbers[2])

# print out each number
print(numbers[0][0])
print(numbers[0][1])
# etc
```

Rewriting those programs to use `for` loops:

```Python
# print each sublist
for number in numbers:
  print(number)
  
# print each value in the sublist
for number in numbers:
  for n in number:
    print(n)
```

Another example with dictionary keys and values:

```Python
# create dictionary
states = {"Missouri": "MO", "Indiana": "IN", "Iowa":"IA", "Nebraska":"NE", "Kansas":"KS", "Illinois":"IL", "Ohio":"OH", "Michigan":"MI"}

# show keys
print(states.keys)

# alternate approach that uses for loop
for key in states.keys():
  print(key)

# show values
print(states.values)

# alternate approach that uses for loop
for value in states.values():
  print(value)
```

#### `For` Loop Comprehension Check

<table>
 <tr><td>
<img src="https://github.com/kwaldenphd/internet/blob/main/images/clipboard.png?raw=true" alt="Clipboard icon" width="50"/></td>
  <td><a href="https://docs.google.com/forms/d/e/1FAIpQLSePIOvFVTaQLTUh_xDFByNVUvvqY64sBt2NHpR17hXhF0S8Eg/viewform?usp=sf_link">Python For Loops Comprehension Check</a></td>
  </tr>
  </table>

#### `For` Loop Application

Q2: Let's return to the program we modified for Q1. How would you modify your Q1 answer to use a `for` loop instead of a `while` loop? Answer to this question includes program + comments that document process and explain your code.

```Python
# assign count variable
count = 1

# while loop
while count <= 5: # initial condition
   print ("Python") # print statement
   count = count + 1 # reassign count

# final print statement
print ("Done")
```

As a reminder, your output might look like the following: 

```Python
1 Python
2 Python
3 Python
4 Python
5 Python 
6 Python
7 Python
8 Python
9 Python
IS FUN!
```

Q3: In a previous lab, you were asked to modify the program below to search for the characters `q` and `u` in the string `turquoise`. 

Program you modified:
```Python
# assign string variable
color = "turquoise"

# get index number of t character
index_number = color.index("t")

# show index number as part of print statement
print ("The index number for the letter t within the word " + color + " is " + index_number)
```

Write a program that uses a `for` loop to return all instances of `q` and `u` in the string, not just the first occurrence. Answer to this question includes program + comments that document process and explain your code.

Q4: In a previous lab, you were asked to write a function that printed a string a specific number of times. Modify this program to use a `for` loop. Include the function definition as well as a sample function call. Answer to this question includes program + comments that document process and explain your code.
- NOTE: Modify the version of this program that accepted specific values as inputs (rather than getting inputs as part of the function definition).

# Additional Considerations

## `range()`

Python's `range()` function allows us to generate a list of integer values. The general syntax:

```Python
range(START VALUE, END VALUE, STEP INTERVAL)
```

The default start value for `range()` is `0`, and the default step interval is `1`.

So for example, `range(6)` would include the values `[0, 1, 2, 3, 4, 5]`. While `range(1, 6, 2)` would include the values `[1, 3, 5]`.

We can use `range()` in combination with `list()` to generate a list of numbers.
- `list(range(6))` would generate the list `[0, 1, 2, 3, 4, 5]`

We can also use `range()` as part of a `for` loop to iterate over a list of numeric values (without having to create that list manually).

For example: 

```Python
# for loop that iterates over values in range
for i in range(0, 3):
 print(i)
 ```

For more information on Python's `range()` function: 
- W3Schools, "[Python Range Function](https://www.w3schools.com/python/ref_func_range.asp)"
- Python documentation, "[4.3 The range() Function](https://docs.python.org/3/tutorial/controlflow.html#the-range-function)"

## `enumerate()`

In a previous lab, we talked about how each item in a list has an index, or a number that indicates its position in the list. We can use the `enumerate()` function to generate a list of pairs containing each item in the list and its index.

We can use the `enumerate()` function as part of a `for` loop.

```Python
# for loop that iterates over list index and values
for index, letter in enumerate('abc'):
 print(index, letter)
```

In this last example, `for index, letter` instructed Python to iterate over both components in the `enumerate()` output. `print(index, letter)` instructed Python to print both components for each element.

For more information on Python's `enumerate()` function: 
- W3Schools, "[Python Enumerate Function](https://www.w3schools.com/python/ref_func_enumerate.asp)"
- Python documentation, "[enumerate](https://docs.python.org/3/library/functions.html#enumerate)"

## Infinite loop

Loops that have no endpoint are called *infinite loops*.

For example, given the following program:

```Python
# assign count variable
count = 1

# while loop
while count <= 5: # initial condition
   print ("Python") # print statement
   count = count + 1 # reassign count

# final print statement
print ("Done")
```

What would happen if we removed `count = count + 1` from the loop? The value of `count` would never change, the initial condition's truth value (`count <= 5`) would never change (because `count` would always equal `1`), and we would have an infinite loop.

## Break & Continue

We can exit a loop immediately by using the `break` statement. `break` will stop or exit the `while` loop even if the condition is true.

For example:

```Python
# assign i variable 
i = 1

# while loop
while i < 6: # initial condition
	
	print(i) # print statement

	if i == 3: # if statement
		break # break statement
	
	i += 1 # reassign i
```

In this example, the loop breaks as soon as the `i == 3` condition is `True`.

We can skip the rest of the body of a loop and move on to the next iteration using `continue`. 

For example:

```Python
# assign the i variable
i = 0

# while loop
while i < 6: # initial condition

	i += 1 # reassign i
	
	if i ==3: # if statement
		continue # continue statement
	
	print(i) # print statement
```

In this example, the current iteration of the loop will stop when `i == 3` is true. Unlike with `break`, the loop will not end. Instead when `i == 3` is true, the loop will skip over the final nested `print` statement and return to the beginning of the loop for a new iteration.

For more on `break` and `continue`:
- W3Schools, "[Python break Keyword](https://www.w3schools.com/python/ref_keyword_break.asp)"
- W3Schools, "[Python For Break](https://www.w3schools.com/python/gloss_python_for_break.asp)"
- W3Schools, "[Python Continue For Loop](https://www.w3schools.com/python/gloss_python_for_continue.asp)"

## Additional Loop Considerations Comprehension Check

<table>
 <tr><td>
<img src="https://github.com/kwaldenphd/internet/blob/main/images/clipboard.png?raw=true" alt="Clipboard icon" width="50"/></td>
  <td><a href="https://docs.google.com/forms/d/e/1FAIpQLSdQCHB6tauQplugunNCqJrVJiZ0W-WqAHAizAft_izi_8X_1g/viewform?usp=sf_link">Additional Python Loop Considerations Comprehension Check</a></td>
  </tr>
  </table>

# Putting It All Together

Q5: Modify the following program to use a while loop instead of a for loop. Answer to this question includes program + comments that document process and explain your code.
```Python
numbers = [5, 4, 7, 0, 1]
count   = 0

for number in numbers:
  if count in numbers:
    print(count)
    count += 1
  else:
    break

print(count)
```

NOTE: For the following lab notebook questions, write two programs for each- one that uses a `while` loop and one that uses a `for` loop to accomplish the same task. 

Q6: Write a loop that prints out all numbers from 0 to 10. Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Q7: Write a program that prints a list of the first nine positive integers and their squares. Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Your output should look similar to the following:
```Python
Number Square
1        1
2        4
3        9
4        16
5        25
6        36
7        49
8        64
9        81
```

Q8: Write a program that counts from 10 down to 1, and then prints "Blastoff!" Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Your output should similar to the following:
```Python
10
9
8
7
6
5
4
3
2
1
Blastoff!
```

Q9: Write a program that asks the user to enter three numbers: a starting value, an ending value, and an increment. Your program should then "count" based on these criteria, as shown in the sample output below. Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

```Python
This program counts for you.
Enter the starting value: 3
Enter the ending value: 13
Enter the increment: 2
3
5
7
9
11
13
```

Q10: Write a program that prints the numbers 1 through 10, except that between 7 and 8 it should print the word "happy." Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Sample output for this program:
```
1
2
3
4
5
6
7
happy
8
9
10
```

HINT: How could an `if` statement be helpful to achieve this output? 

## How to submit this lab (and show your work)

Moving forward, we'll submit lab notebooks as `.py` files. 

One option is to have a `.py` file that you use to run code and test programs while working through the lab. When ready to submit the lab notebook, you add comments and remove extraneous materials.

Another option is to have an "official" `.py` file that you are using as a lab notebook (separate from your working/testing file). Use comments in Python to note when you are starting a new question (as well as answering a question).
  * Example: `Lab_Notebook_Walden.py`

What gets submitted as the lab notebook is the `Lab_Notebook_Walden.py` file.
- When in doubt, use comments
- Be sure you are using comments to note what question you're responding to

# Lab Notebook Questions

[Click here](https://replit.com/team/eoc-f22/Iteration-and-Loops-in-Python) to make a copy of the Replit template for this lab.

Alternatives:
- [`.py` template](https://drive.google.com/file/d/10Ze1JUafZUZb8vZVjcOKpjK7MF-Q9OL3/view?usp=sharing) (Google Drive, ND users)
- [Jupyter Notebook, `.ipynb`](https://colab.research.google.com/drive/1duVhsQ-jf6MZpMi0hyc8o4nSG61TJpI0?usp=sharing) (Google Colab, ND users)

Q1: Given the following program:

```Python
# assign count variable
count = 1

# while loop
while count <= 5: # initial condition
   print ("Python") # print statement
   count = count + 1 # reassign count

# final print statement
print ("Done")
```

How would you modify the program to print or output the string nine (9) times and also include line numbers as part of the output? Answer to this question includes program + comments that document process and explain your code.

For example, your output might look like the following: 

```Python
1 Python
2 Python
3 Python
4 Python
5 Python 
6 Python
7 Python
8 Python
9 Python
IS FUN!
```

Q2: Let's return to the program we modified for Q1. How would you modify your Q1 answer to use a `for` loop instead of a `while` loop? Answer to this question includes program + comments that document process and explain your code.

```Python
# assign count variable
count = 1

# while loop
while count <= 5: # initial condition
   print ("Python") # print statement
   count = count + 1 # reassign count

# final print statement
print ("Done")
```

As a reminder, your output might look like the following: 

```Python
1 Python
2 Python
3 Python
4 Python
5 Python 
6 Python
7 Python
8 Python
9 Python
IS FUN!
```

Q3: In a previous lab, you were asked to modify the program below to search for the characters `q` and `u` in the string `turquoise`. 

Program you modified:
```Python
# assign string variable
color = "turquoise"

# get index number of t character
index_number = color.index("t")

# show index number as part of print statement
print ("The index number for the letter t within the word " + color + " is " + index_number)
```

Write a program that uses a `for` loop to return all instances of `q` and `u` in the string, not just the first occurrence. Answer to this question includes program + comments that document process and explain your code.

Q4: In a previous lab, you were asked to write a function that printed a string a specific number of times. Modify this program to use a `for` loop. Include the function definition as well as a sample function call. Answer to this question includes program + comments that document process and explain your code.
- NOTE: Modify the version of this program that accepted specific values as inputs (rather than getting inputs as part of the function definition).

Q5: Modify the following program to use a while loop instead of a for loop. Answer to this question includes program + comments that document process and explain your code.
```Python
numbers = [5, 4, 7, 0, 1]
count   = 0

for number in numbers:
  if count in numbers:
    print(count)
    count += 1
  else:
    break

print(count)
```

NOTE: For the following lab notebook questions, write two programs for each- one that uses a `while` loop and one that uses a `for` loop to accomplish the same task. 

Q6: Write a loop that prints out all numbers from 0 to 10. Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Q7: Write a program that prints a list of the first nine positive integers and their squares. Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Your output should look similar to the following:
```Python
Number Square
1        1
2        4
3        9
4        16
5        25
6        36
7        49
8        64
9        81
```

Q8: Write a program that counts from 10 down to 1, and then prints "Blastoff!" Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Your output should similar to the following:
```Python
10
9
8
7
6
5
4
3
2
1
Blastoff!
```

Q9: Write a program that asks the user to enter three numbers: a starting value, an ending value, and an increment. Your program should then "count" based on these criteria, as shown in the sample output below. Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

```Python
This program counts for you.
Enter the starting value: 3
Enter the ending value: 13
Enter the increment: 2
3
5
7
9
11
13
```

Q10: Write a program that prints the numbers 1 through 10, except that between 7 and 8 it should print the word "happy." Answer to this question includes programs with a `while` loop and a `for` loop + comments that document process and explain your code.

Sample output for this program:
```
1
2
3
4
5
6
7
happy
8
9
10
```

HINT: How could an `if` statement be helpful to achieve this output? 
