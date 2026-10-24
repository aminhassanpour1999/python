# What Is Python?

## Lesson Purpose

This lesson introduces Python as a programming language and establishes the mindset needed to learn it well. It is a conceptual lesson: the goal is to understand the ideas, not to memorize a list of facts.

## Learning Objectives

By the end of this lesson, you should be able to:

- Define a programming language and explain what it means to call Python high-level and general-purpose.
- Explain how an algorithm differs from a program.
- Describe why readability matters and how meaningful names help readers.
- Summarize Python's origins and explain why new learners should use Python 3.
- Identify important strengths and trade-offs of Python.
- Distinguish learning a language's syntax from learning to solve problems with code.

## Prerequisites

No previous programming experience is required.

## 1. What Is a Programming Language?

A computer needs instructions represented in forms its software and hardware can process. A **programming language** gives people a defined way to express those instructions using rules for writing and interpreting code.

Python is a **high-level, general-purpose programming language**.

- **High-level** means the language provides abstractions that let us express ideas without managing every low-level detail of the machine directly. “High-level” does not mean “better for every task.”
- **General-purpose** means Python is not restricted to one narrow class of problems. It can be used for automation, web services, data analysis, scientific computing, testing, and many other tasks.

Consider this program:

```python
print("Hello, world!")
```

Expected output:

```text
Hello, world!
```

The code asks Python to display a piece of text. The text inside quotation marks is a **string literal**; `print()` is a function call. These terms will be studied in detail later, so for now focus on the relationship between the instruction and its visible result.

Python source code is written by a person and then run by a Python implementation. The implementation handles the language's execution rules. We will study execution separately rather than mixing those technical details into this first lesson.

### Algorithm versus program

An **algorithm** is a method consisting of steps for solving a problem. A **program** expresses instructions in a programming language so a computer can carry out a solution.

For example, an algorithm for finding the average of two temperatures is:

1. Add the two temperatures.
2. Divide the sum by two.
3. Report the result.

A Python program can implement those steps, but the algorithm itself is the underlying method—not the particular spelling of Python code.

**Check your understanding:** Could the same algorithm be implemented in more than one programming language? Yes. The steps can remain the same while the code differs.

## 2. Python's Design Philosophy and Readability

Python emphasizes readable code and clear expression. Indentation is meaningful in Python: it helps define the structure of compound statements. We will study its exact rules when we learn control flow.

Compare these snippets:

```python
total_price = 24
number_of_items = 3
price_per_item = total_price / number_of_items
print(price_per_item)
```

and:

```python
x = 24
y = 3
z = x / y
print(z)
```

Both calculate the same value and print `8.0` in Python 3. The first version communicates more clearly what the numbers represent. Names such as `total_price` and `number_of_items` reduce the amount of guesswork a reader must do.

Readability matters because programs are read, modified, debugged, tested, and maintained—not merely written once. Clear code can help a future reader, including your future self, understand intent and notice mistakes.

Readable code is not automatically correct. A clear-looking program can still implement the wrong algorithm, mishandle an edge case, or produce an incorrect result. Readability supports correctness; it does not replace testing.

### The Zen of Python

Python's design philosophy is often summarized by **The Zen of Python**, a collection of guiding aphorisms. You can display it in a Python interpreter with:

```python
import this
```

The principles favor ideas such as readability, simplicity, and explicitness. They are useful guidance, not a guarantee that every Python program is simple or well designed.

## 3. A Brief History: Python 2 and Python 3

Python was created by **Guido van Rossum**. Work began in the late 1980s, and Python was first publicly released in 1991.

Two major versions matter for understanding Python's history:

- Python 2.0 was released in 2000.
- Python 3.0 was released in 2008 and introduced changes that meant some Python 2 code needed modification to run on Python 3.
- Python 2 reached end of life on January 1, 2020. The Python project no longer provides official Python 2 bug fixes or security updates.

For example, Python 2 commonly allowed this print statement:

```python
print "Hello"
```

In Python 3, use a function call:

```python
print("Hello")
```

Division also differs in an important case. In Python 3:

```python
print(5 / 2)
```

Expected output:

```text
2.5
```

Python 3's `/` operator performs true division, including when both operands are integers. Python 2 had different default behavior for integer division in that situation.

**Practical rule:** Use a supported Python 3 release for new learning and new projects. Python 2 is worth recognizing when reading legacy code, but it is not the right starting point for a new learner.

## 4. Core Strengths of Python

### 4.1 Readability and expressiveness

Python often lets people express an idea with relatively little code. This can make examples easier to follow and prototypes quicker to build. Clear names, sound structure, and tests remain necessary.

### 4.2 A broad ecosystem

Python includes a **standard library**: modules distributed with Python that support many common tasks. Third-party packages add specialized capabilities, including numerical computing, data analysis, web development, and machine learning.

Using an established library can save time, but a package should still be evaluated for maintenance, compatibility, security, licensing, and suitability for the task. More dependencies do not automatically make a project better.

### 4.3 Portability

Python is available on major operating systems, including Linux, macOS, and Windows. Much Python code can run across these systems with little or no change.

Portability is not guaranteed in every situation. Code may depend on operating-system-specific paths, external programs, environment variables, hardware, or packages that are not installed everywhere.

### 4.4 Productivity

Python can be effective for scripting, automation, experimentation, prototypes, and many production systems. Readable syntax and a rich ecosystem can help developers move from an idea to a working solution.

Productivity depends on the task, the developer's skills, and the quality of the solution. Shorter code is not necessarily better code, and calling a library does not remove the need to understand its behavior.

## 5. Trade-Offs and Limitations

No programming language is the best choice for every problem. Python's strengths come with trade-offs.

### 5.1 Execution speed

For some CPU-intensive workloads, ordinary Python code may run more slowly than carefully optimized native code written in languages such as C or C++. Actual performance depends on the implementation, algorithm, libraries, hardware, and workload.

Many scientific Python packages perform their expensive numerical operations in optimized native code. As a result, a Python program can still deliver strong performance when it uses suitable libraries.

**Good practice:** First define what “too slow” means, measure the program, identify the bottleneck, and then optimize the part that matters. Rewriting everything in another language before measuring is often wasted effort.

### 5.2 Memory use

Python objects can have more memory overhead than compact low-level representations. This can matter for very large datasets, embedded systems, or other environments with strict memory limits. Data structures and libraries should be chosen with the workload in mind.

### 5.3 Dynamic typing

Python is dynamically typed. A name is not permanently declared to refer to only one type, so this is valid Python:

```python
value = 10
value = "ten"
```

First, `value` refers to an integer; later, it refers to a string. The code is valid, but changing the kind of value unexpectedly can make a program harder to reason about or cause errors in later operations.

Clear naming, small functions, tests, and optional type annotations can help manage this flexibility. Type annotations will be covered when they become relevant.

### 5.4 Dependencies and deployment

A program may require specific packages, a compatible Python version, environment variables, files, or operating-system features. Sharing and deploying a program therefore requires clear setup instructions and reliable dependency management. We will cover these practical details in later lessons.

### 5.5 Choosing a tool

The right choice depends on requirements such as performance, memory, hardware access, available libraries, deployment constraints, security, team experience, and long-term maintenance. Python is a powerful tool, but it is not automatically the best fit for every situation.

## 6. Learning Python versus Learning to Program

Learning a language and learning to program are connected, but they are not identical.

**Learning Python** includes understanding its syntax, built-in data types, expressions, functions, modules, and conventions.

**Learning to program** includes defining a problem, identifying inputs and outputs, breaking the problem into steps, choosing an approach, handling edge cases, testing the result, and improving the solution.

Imagine two learners:

- Learner A can read a program and explain what each line does.
- Learner B can do that and can also analyze a new problem and build a solution without copying a complete example.

Learner B has practiced a broader skill: independent problem-solving. Reading code is useful, but independent implementation requires deliberate practice.

A useful practice loop is:

1. Read a small program.
2. Predict its output before running it.
3. Run it and compare the actual output with your prediction.
4. Change one thing and predict how the behavior will change.
5. Solve a related problem without looking at a complete solution.
6. Test normal cases and edge cases.
7. Explain any mistake and what you learned from it.

You do not need to master every concept before writing programs. Learn a concept, use it in a small task, and revisit it as your projects become more complex.

## 7. Worked Example: From a Problem to a Program

**Problem:** Find the average of two temperature measurements.

**Inputs:** Two numerical measurements, here 18 and 26.

**Algorithm:**
1. Add the measurements.
2. Divide the sum by two.
3. Display the result.

**Python implementation:**

```python
first_temperature = 18
second_temperature = 26

average_temperature = (first_temperature + second_temperature) / 2

print(average_temperature)
```

Expected output:

```text
22.0
```

**Reasoning:** The sum is 44. Dividing 44 by 2 gives 22. In Python 3, the `/` operator returns a floating-point result here, so the displayed value is `22.0` rather than `22`.

This example uses fixed values written in the program. It does not ask the user to enter temperatures. Later, we will learn how to receive input from a user and how to validate it.

**Important limitation:** The program calculates the arithmetic mean of two numbers. It does not verify that the measurements are in the same unit or that they are valid temperature readings.

## Common Misconceptions

- **“High-level means faster.”** Not necessarily. High-level describes the abstractions offered by a language, not its execution speed.
- **“General-purpose means ideal for every task.”** No. A language can be broadly useful without being the best fit for every constraint.
- **“Readable code is always correct.”** Readability helps people reason about code, but correctness still requires suitable logic and testing.
- **“If code runs on my computer, it will run everywhere.”** It may depend on packages, paths, operating-system behavior, or other environmental details.
- **“Learning syntax means I can program.”** Syntax is necessary, but solving unfamiliar problems takes separate practice.

## Summary

- Python is a high-level, general-purpose programming language.
- An algorithm describes a method for solving a problem; a program expresses instructions in a programming language.
- Readability helps people understand, maintain, and debug code, but does not replace testing.
- Python 3 is the appropriate choice for new learning and projects; Python 2 is obsolete.
- Python's ecosystem, portability, and productivity are strengths, while speed, memory use, dynamic typing, and deployment constraints require judgment.
- Programming requires more than remembering syntax: it requires analysis, implementation, testing, and revision.

## Exercises

Try these without looking back at the lesson. Explain your reasoning in your own words; do not aim to reproduce the exact wording.

### Level 1 — Explain the concepts

1. What does “high-level” mean when describing Python?
2. What is the difference between an algorithm and a program?
3. Why can descriptive variable names be more helpful than names such as `x` and `y`?

### Level 2 — Apply the ideas

4. In the worked example, change the second temperature from 26 to 30. Before running the program, predict the output. Then run it and explain the result.
5. Give two strengths and two trade-offs of Python. For each one, describe a situation where it might matter.
6. A program runs slowly on a large calculation. Explain why measuring the bottleneck is a sensible first step before changing languages.

### Level 3 — Analyze and create

7. Someone says, “Python runs on Linux and Windows, so every Python program works identically on both.” Explain what is incomplete about this claim.
8. Describe an everyday problem you could solve with a program. Identify its inputs, expected output, and the steps of an algorithm. Do not write Python code yet.
9. Explain how you would test a program that calculates an average. Include at least one ordinary case and one case that might expose a problem.

## Knowledge Check

Before moving on, try to answer these from memory:

- What do “high-level” and “general-purpose” mean?
- How does an algorithm differ from a program?
- Why does readability matter beyond appearance?
- Why should a new project use Python 3 rather than Python 2?
- Why can no language be declared the best choice for every task?
- What steps help turn a problem into a tested program?

If an answer is unclear, revisit that section and explain the idea in your own words before continuing.

## References

- [Official Python website](https://www.python.org/)
- [The Python Tutorial](https://docs.python.org/3/tutorial/)
- [The Zen of Python — PEP 20](https://peps.python.org/pep-0020/)
- [Python 2.7 documentation (historical reference)](https://docs.python.org/2.7/)
