# Expressions and Statements

**Module:** Programming Fundamentals  
**Lesson:** 7 of 9 · **Level:** Beginner · **Study time:** 60–75 minutes  
**Prerequisites:** Variables and Data Types; Numbers and Operators; Booleans and None

## Purpose and learning objectives

Expressions produce values; statements perform instructions. By the end, you should be able to distinguish them; trace straight-line code; explain assignment and evaluation order; use parentheses and intermediate names for clarity; recognize syntax errors versus runtime behavior; and understand why readable expressions matter.

## 1. Expressions produce values

An expression is code that Python evaluates to produce a value.

Examples:
- A literal: 42, "hello", True
- A name: temperature
- Arithmetic: 3 + 4
- A comparison: temperature > 20
- A function call: len("Python")
- A combination: (first + second) / 2

    result = 3 + 4
    print(result)
    print(len("Python"))

## 2. Statements perform actions

A statement is an instruction Python executes. Assignment is a statement:

    temperature = 21.5
    print(temperature)

The right side of an assignment is an expression. Python evaluates it and binds the result to the target name. A function call such as print(...) is an expression used as an expression statement.

## 3. Assignment and evaluation order

For ordinary assignment, Python evaluates the right-hand side before binding the target:

    count = 5
    count = count + 1
    print(count)  # 6

This is not an algebraic equation. Python reads the current value, calculates a result, then rebinds the name.

Multiple assignment:

    x, y = 10, 20
    x, y = y, x
    print(x, y)  # 20 10

Sequence unpacking is explored further with data structures.

Chained assignment binds multiple names to the same resulting object:

    first = second = []

Both names initially refer to the same list. Mutating that list through one name is visible through the other. This is an early preview of aliasing and mutability.

## 4. Operator precedence and grouping

Precedence determines how an expression is grouped. Parentheses override the normal grouping:

    result = 2 + 3 * 4
    grouped = (2 + 3) * 4
    print(result)   # 14
    print(grouped)  # 20

The Numbers and Operators lesson covers the common precedence levels. The complete official table includes syntax introduced later. If an expression is hard to read, add parentheses or split it into named intermediate calculations:

    numerator = new_value - old_value
    relative_change = numerator / old_value
    percentage_change = relative_change * 100

The longer version is easier to inspect and debug.

## 5. Expressions can have side effects

Some expressions do more than calculate a value. A function call can display text, read input, modify an object, or interact with the outside environment. These are side effects.

    name = input("Name: ")

The call reads input and returns a string. It also interacts with the user.

For now, prefer simple expressions whose results are easy to predict. Pure functions and side effects are studied more deeply in the Functions module.

## 6. Syntax errors, runtime exceptions, and logic errors

- A **syntax error** means the source code does not follow Python's grammar.
- A **runtime exception** occurs while valid code is running, such as division by zero.
- A **logic error** occurs when code runs but produces a result different from the intended result.

    # Syntax error: missing closing parenthesis
    # print(2 + 3

    # Runtime exception:
    # result = 10 / 0

    # Logic error: incorrect grouping for an average
    first = 10
    second = 20
    wrong_average = first + second / 2
    correct_average = (first + second) / 2

The last example runs, but precedence makes the first formula incorrect for an average.

## 7. Trace a program line by line

Tracing means following execution and recording the values associated with names:

    first = 4
    second = first + 3
    first = 10
    total = first + second
    print(total)

Trace:
1. first becomes 4.
2. second becomes 7.
3. first is rebound to 10.
4. total becomes 17.
5. print displays 17.

| Executed statement | first | second | total |
|---|---:|---:|---:|
| first = 4 | 4 | — | — |
| second = first + 3 | 4 | 7 | — |
| first = 10 | 10 | 7 | — |
| total = first + second | 10 | 7 | 17 |

## 8. Readability rules

- Prefer meaningful intermediate variables over dense formulas.
- Use parentheses when they clarify grouping.
- Avoid expressions that require the reader to mentally simulate too many operations.
- Keep statements focused on understandable actions.
- Do not use clever syntax merely to reduce line count.
- Explain non-obvious intent with a useful comment, not one that repeats the code.

## 9. Coding lab — Trace and refactor a calculation

Create expression_trace.py:

    first_reading = 12.5
    second_reading = 15.5
    third_reading = 18.0

Tasks:
1. Predict the average before running the code.
2. Write a trace table for each assignment.
3. Calculate the average using clear grouping.
4. Rewrite the formula using intermediate variables for the sum and count.
5. Intentionally remove parentheses from another formula and observe how precedence changes the result.
6. Explain the difference between an expression and a statement.

## 10. Independent exercises

1. Classify as expression or statement: 5 + 2; name = "Ada"; len("abc"); print("Hi"); temperature > 20.
2. Trace: x = 3; y = x * 2; x = y + 1; print(x, y).
3. Explain why count = count + 1 is valid Python although it is not an algebraic identity.
4. Find and fix the logic error in average = first + second / 2.
5. Rewrite a long arithmetic expression into named steps without changing its result.
6. Explain why first = second = [] does not create two independent lists.
7. Give an example of an expression with a side effect.

## Answer key

1. Expressions: 5 + 2, len("abc"), temperature > 20. Statements: name = "Ada"; print("Hi") is an expression statement (the call is an expression used as a statement).
2. x is 7 and y is 6.
3. The right-hand expression uses the current value, computes a new value, and rebinds the name.
4. Use average = (first + second) / 2.
5. Answers vary; intermediate names should preserve operation order.
6. Both names refer to the same list object.
7. input("Name: ") or print("Hello") are examples.

## Knowledge check

1. What is an expression?
2. What is a statement?
3. Which side of an assignment is evaluated first?
4. How do parentheses affect precedence?
5. What is a side effect?
6. How do syntax errors, runtime exceptions, and logic errors differ?

## Summary and completion criteria

Expressions produce values; statements perform instructions. Assignment evaluates its right-hand expression before rebinding the target. Precedence determines grouping, while parentheses and intermediate variables improve clarity. Syntactically valid code can still contain runtime or logic errors.

- [ ] I can classify simple expressions and statements.
- [ ] I can trace variable values line by line.
- [ ] I can explain assignment evaluation order.
- [ ] I can use parentheses and intermediate variables for clarity.
- [ ] I can distinguish syntax, runtime, and logic errors.
- [ ] I completed the lab and exercises independently.

## Official references

- [Expressions](https://docs.python.org/3/reference/expressions.html)
- [Simple Statements](https://docs.python.org/3/reference/simple_stmts.html)
- [Assignment Statements](https://docs.python.org/3/reference/simple_stmts.html#assignment-statements)
