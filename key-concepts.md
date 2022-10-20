# Key Concepts

Python syntax that shows up in this lab:
- `for` and `while` loops
- `range()` and `enumerate()` functions
- `break` and `continue` keywords

### **`break` & `continue`**
- We can exit a loop immediately by using the `break` statement. `break` will stop or exit the `while` loop even if the condition is true. We can skip the rest of the body of a loop and move on to the next iteration using `continue`. 
- For more on `break` and `continue`:
  * W3Schools, "[Python break Keyword](https://www.w3schools.com/python/ref_keyword_break.asp)"
  * W3Schools, "[Python For Break](https://www.w3schools.com/python/gloss_python_for_break.asp)"
  * W3Schools, "[Python Continue For Loop](https://www.w3schools.com/python/gloss_python_for_continue.asp)"

### **Control Flow, Control Structures**

From Busbee and Braunschweig's "[Structured Programming](https://press.rebus.community/programmingfundamentals/chapter/structured-programming/)" from *Programming Fundamentals*
    
"One of the most important concepts of programming is the ability to control a program so that different lines of code are executed or that some lines of code are executed many times. The mechanisms that allow us to control the flow of execution are called control structures. Flowcharting is a method of documenting (charting) the flow (or paths) that a program would execute. There are three main categories of control structures:"
  * Sequence [executes in given sequence]
  * Selection [selects between two or more flows using condition or question]
  * Iteration [repeats same piece of code multiple times]
    
Examples of control structures in Python include:
- `if-then-else` (syntax: `if`, `else`, `elif`)
- `while` statements (syntax: `while`)
- functions (built-in and named)

### **Count-Controlled Loops**
- Count-controlled loops (sometimes called counter-controlled loops) continue executing for a pre-determined number of times. The number of times the loop will execute is known because the loop is iterating through a collection of objects/values (i.e. a string or list), or the iteration when the initial condition will no longer be `True` is known.

### **`enumerate()`**
- Python function that generates a list of pairs containing each item in the list and its index
- For more information on Python's `enumerate()` function: 
  * W3Schools, "[Python Enumerate Function](https://www.w3schools.com/python/ref_func_enumerate.asp)"
  * Python documentation, "[enumerate](https://docs.python.org/3/library/functions.html#enumerate)"

### **Event-Controlled Loops**
- Event-controlled loops test for an initial condition, and execution continues as long as the initial condition is `True`. How many times the loop will execute *is not known*.

### **`for` Loops**
- In Python, count-controlled loops are written using a `for` statement and are called `for loop`. A `for loop` iterates over each value in a group of values- the lines of code nested under the initial statement run for each iteration.

<p align="center"><img src="https://github.com/kwaldenphd/python-loops-iteration/blob/main/images/for-loop-diagram.png?raw=true" width="500"></p>

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

### **Infinite Loops**
- Loops that have no endpoint

### **Iteration**
- "In iteration control structures, a statement or block is executed until the program reaches a certain state, or operations have been applied to every element of a collection. This is usually expressed with keywords such as `while`, `repeat`, `for`, or `do..until`. The basic attribute of an iteration control structure is to be able to repeat some lines of code. The visual display of iteration creates a circular loop pattern when flowcharted, thus the word 'loop' is associated with iteration control structures." (Busbee and Braunschweig's "[Iteration Control Structures](https://press.rebus.community/programmingfundamentals/chapter/iteration-control-structures/)," in *Programming Fundamentals*)

Let's break down that definition:
- Iteration (repetition of a process) is a type of control structure
- In programming languages, iteration involves lines of code repeating until a condition is met of the end of a group of values has been reached.
- Because iteration in this context involves a circular pattern, many object-oriented programming languages refer to these structures as `loops`

### **Loops**
- Most high-level programming languages support two main types of loops: event-controlled and count-controlled
  * **Event-controlled loops** test for an initial condition, and execution continues as long as the initial condition is `True`. How many times the loop will execute *is not known*.
  * **Count-controlled loops** (sometimes called counter-controlled loops) continue executing for a pre-determined number of times. The number of times the loop will execute is known because the loop is iterating through a collection of objects/values (i.e. a string or list), or the iteration when the initial condition will no longer be `True` is known.

<p align="center"><img src="https://github.com/kwaldenphd/python-loops-iteration/blob/main/images/loop-comparison-diagram.png?raw=true" width="1000"></p>

### **`range()`**
- "The range() function returns a sequence of numbers, starting from 0 by default, and increments by 1 (by default), and stops before a specified number" (W3Schools, "[Python Range Function](https://www.w3schools.com/python/ref_func_range.asp)")
- For more information on Python's `range()` function:
  * W3Schools, "[Python Range Function](https://www.w3schools.com/python/ref_func_range.asp)"
  * Python documentation, "[4.3 The range() Function](https://docs.python.org/3/tutorial/controlflow.html#the-range-function)"

### **`while` Loops**
- In Python, event-controlled loops are written using a `while` statement and are called `while loop`. A `while` statement tests for an initial condition, and the lines of code indented under `while` run only when the initial condition is `True`.

In each iteration through the `while` loop, Python will:
- Evaluate the initial condition (which is a Boolean true/false expression)
- If the condition is `False`, exit the loop and continue the program
- If the condition is `True`, then execute other statements in the body of the loop and return to the beginning of the loop

<p align="center"><img src="https://github.com/kwaldenphd/python-loops-iteration/blob/main/images/while-loop-diagram.png?raw=true" width="500"></p>

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
