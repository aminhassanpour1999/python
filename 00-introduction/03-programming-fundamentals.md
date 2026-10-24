# Programming Fundamentals

## Learning Objectives

After this lesson, you should be able to explain what programs and algorithms are, describe input-processing-output, distinguish data from operations, recognize expressions and statements, explain variables as names bound to values, and identify sequence, selection, and repetition.

## 1. Programs, Instructions, and Algorithms

A **program** is a set of instructions expressed in a form a computer can execute. An **algorithm** is a finite, sufficiently precise method for solving a problem or completing a task.

An algorithm describes the approach; a program implements that approach in a programming language. More than one program can implement the same algorithm, and different algorithms can solve the same problem.

For example, to find the larger of two numbers, an algorithm could compare the values and choose the greater one. A Python implementation would express that comparison using Python syntax.

## 2. Input, Processing, and Output

Many simple programs can be understood using the **input-processing-output (IPO)** model:

- **Input:** information the program receives.
- **Processing:** calculations or decisions performed on that information.
- **Output:** results the program provides.

Suppose a program calculates the average of two numbers. The inputs are the two numbers, processing adds them and divides by two, and output presents the result.

IPO is a useful way to start analyzing a problem, although real programs may also store data, communicate with services, repeat operations, or produce several outputs.

## 3. Data and Operations

**Data** is information a program works with, such as numbers, text, or collections of values. **Operations** transform data or use it to make decisions.

Examples include arithmetic operations (`+`, `-`, `*`, `/`), comparisons (`<`, `==`), and operations that combine or inspect text. The meaning of an operation can depend on the types of values involved.

Do not confuse a value with its printed representation. The number `5` and the text `"5"` may look similar on screen, but they are different kinds of data.

## 4. Expressions and Statements

An **expression** is code that evaluates to a value. For example:

```python
8 + 12
```

The expression evaluates to `20`.

A **statement** is an instruction that Python executes. An assignment statement binds a name to the result of an expression:

```python
average = (8 + 12) / 2
print(average)
```

Python evaluates the expression on the right side of the assignment, associates the name `average` with the resulting value, and then executes the function call that displays it.

At the Python syntax level, `print(average)` passes the value associated with `average` as an argument to the `print` function. At the problem level, displaying that result is the output stage. These are two compatible ways to describe the same code at different levels.

## 5. Variables Are Names Bound to Values

A **variable** is a name that refers to a value. In Python, assignment uses `=`:

```python
score = 10
score = score + 5
print(score)
```

Output:

```text
15
```

The second assignment evaluates the old value of `score`, adds five, and binds the name to the new result. In mathematics, `=` usually states that two expressions are equal; in Python, `=` in an assignment statement binds a name to a value. The comparison operator `==` checks whether two values are equal. For example, `score = 10` assigns a value, while `score == 10` evaluates to a Boolean result.

Choose names that communicate purpose. Names such as `total_price` or `number_of_students` are often clearer than `x` or `n`, unless the shorter names are conventional and clear in context.

## 6. Three Fundamental Control Structures

Many algorithms can be described using three basic structures:

### Sequence

Instructions run in order.

```python
width = 4
height = 3
area = width * height
print(area)
```

### Selection

A program chooses what to do based on a condition. In Python, selection commonly uses `if`, `elif`, and `else`.

```python
temperature = 30

if temperature > 25:
    print("Warm")
else:
    print("Not warm")
```

### Repetition

A program repeats instructions. Python provides constructs such as `for` and `while`. Their detailed behavior belongs in the Control Flow lessons.

Sequence, selection, and repetition can be combined to express many useful algorithms.

## 7. Decomposing a Problem

A problem can feel difficult when treated as one large task. **Decomposition** means dividing it into smaller parts that are easier to understand, implement, and test.

Before coding, ask:

1. What exactly is the required result?
2. What information is available as input?
3. What rules or calculations transform the input?
4. What output format is expected?
5. What edge cases could cause problems?
6. How can the solution be checked?

For example, to calculate a final price after a discount, clarify whether the discount is a percentage or fixed amount, what happens with invalid prices, and how the result should be rounded. These details are part of problem analysis, not merely syntax.

## Summary

Programming combines clear problem definition, algorithm design, expression in a language, and testing. IPO is a useful initial model. Expressions produce values; statements instruct Python to do something. Variables are names bound to values, and sequence, selection, and repetition are core ways to organize a solution.

## Exercises

1. Explain the difference between an algorithm and a program.
2. For a program that converts Celsius to Fahrenheit, identify input, processing, and output.
3. What value does `(8 + 12) / 2` produce in Python 3? What does `print((8 + 12) / 2)` add?
4. In `count = count + 1`, why is the right-hand expression evaluated before the assignment updates the name?
5. Classify each idea as sequence, selection, or repetition: doing three steps in order; choosing a response based on a score; processing every item in a list.
6. Break down a program that calculates the average of three numbers into input, processing, and output steps.

## Knowledge Check

Can you explain each key term in your own words and analyze a small problem before writing Python code?

## References

- [The Python Tutorial: An Informal Introduction to Python](https://docs.python.org/3/tutorial/introduction.html)
- [The Python Tutorial: More Control Flow Tools](https://docs.python.org/3/tutorial/controlflow.html)