# Expressions and Statements

**Prerequisites:** Variables and Data Types; Numbers and Operators; Booleans and None  
**Study time:** 60–90 minutes

## Purpose and learning outcomes

To understand a Python program, you must know what is evaluated to produce a value and what instruction changes program state or performs an action. This lesson builds the skill of tracing straight-line code, predicting output, and distinguishing syntax, runtime, and logic errors.

## 1. Expressions produce values

An expression is a piece of syntax Python evaluates to produce a value.

Examples include literals, names, arithmetic, comparisons, function calls, and combinations of these.

~~~python
42
temperature_c
2 + 3 * 4
temperature_c >= 0
len("Python")
~~~

The value may be stored, displayed, passed to another operation, or ignored. An expression does not have to be a single number.

## 2. Statements perform instructions

A statement is a complete instruction executed by Python. Assignment is a statement.

~~~python
temperature_c = 18
average = (12 + 16) / 2
print(average)
~~~

The expression on the right of an assignment is evaluated first. Its result is then bound to the target name.

Assignment is not a mathematical equation asserting equality. It changes a name binding.

## 3. Reassignment and evaluation order

~~~python
count = 3
saved_count = count
count = count + 1
print(count, saved_count)  # 4 3
~~~

The earlier assignment to saved_count does not create a live formula. It binds the name to the value that count referred to at that moment.

Multiple assignment can unpack values:

~~~python
first, second = 10, 20
first, second = second, first
print(first, second)  # 20 10
~~~

Chained assignment binds multiple names to the same object:

~~~python
left = right = 5
~~~

With immutable integers this is usually unremarkable. With mutable objects, shared references matter; mutability and containers are covered later.

## 4. Precedence and grouping

Operator precedence determines how an expression is grouped when parentheses are absent. Learn the common rules, but use parentheses when they improve clarity.

~~~python
print(2 + 3 * 4)   # 14
print((2 + 3) * 4) # 20
print(2 ** 3 ** 2) # 512
print(-3 ** 2)     # -9
print((-3) ** 2)  # 9
~~~

Exponentiation groups from right to left. Exponentiation binds more tightly than unary minus in the expression -3 ** 2.

Do not memorize a huge table before understanding the expression. When uncertain, add parentheses and verify the intended grouping.

## 5. Expressions can have side effects

A pure calculation produces a value without changing external state. Some expressions also perform actions.

~~~python
number_text = input("Number: ")
print(number_text)
~~~

input() reads from standard input; print() writes to an output stream. Their effects are not merely numeric results.

Side effects are not inherently bad. They should be placed where a reader expects interaction or state changes. Keep complex calculations separate from I/O when possible.

## 6. Trace a program line by line

Tracing means recording the relevant state after each statement.

~~~python
first = 4
second = first + 3
first = 10
total = first + second
average = total / 2
print(average)
~~~

| After statement | first | second | total | average |
|---|---:|---:|---:|---:|
| first = 4 | 4 | — | — | — |
| second = first + 3 | 4 | 7 | — | — |
| first = 10 | 10 | 7 | — | — |
| total = first + second | 10 | 7 | 17 | — |
| average = total / 2 | 10 | 7 | 17 | 8.5 |

Output: 8.5.

A trace table is especially useful when a program runs but produces an unexpected result.

## 7. Three broad error categories

- **Syntax error:** Python cannot parse the source code, for example an unmatched parenthesis.
- **Runtime exception:** execution reaches an operation that raises an exception, for example division by zero.
- **Logic error:** the program runs but does not implement the intended behavior, for example calculating (a + b / 2) instead of ((a + b) / 2).

A program can contain a logic error without raising an exception. Testing and reasoning are therefore necessary even when execution succeeds.

## 8. Common mistakes

1. Treating assignment as mathematical equality.
2. Assuming a later reassignment recalculates earlier variables.
3. Forgetting operator precedence.
4. Confusing a value-producing expression with an instruction.
5. Ignoring side effects in a function call.
6. Debugging by random edits rather than tracing.
7. Assuming a program is correct because it runs without an exception.

## 9. Coding lab — Trace and refactor a calculation

Create expression_lab.py.

1. Assign two numeric readings.
2. Calculate a total, average, and difference using intermediate names.
3. Reassign one original reading and predict which stored results change (and which do not).
4. Swap two names using multiple assignment.
5. Create one deliberate logic error in a formula.
6. Record expected and actual values, trace each assignment, and repair the expression.
7. Explain why a successful run does not prove correctness.

## 10. Independent exercises

### Level 1

1. Classify 5 + 2, name = "Ada", len("abc"), print("Hi"), and temperature > 20.
2. Trace x = 3; y = x * 2; x = y + 1; print(x, y).
3. Explain count = count + 1.
4. Predict 2 + 3 * 4, (2 + 3) * 4, and 2 ** 3 ** 2.

### Level 2

5. Write an average formula with correct grouping.
6. Refactor a long expression using meaningful intermediate names.
7. Explain why first = second = [] makes both names refer to the same list.
8. Identify the side effects in a short input/print program.

### Level 3

9. Explain why reassigning a name does not rerun old calculations.
10. Diagnose a plausible but incorrect average with no exception.
11. Explain the difference between rebinding a name and mutating a mutable object.
12. Guard division by zero with an explicit conditional.
13. Build a trace table for a short program and explain its final output.

## Exercise solutions

Attempt the exercises and knowledge check before opening the separate [expressions-and-statements — Exercise Solutions](./07-expressions-and-statements-solutions.md).

## Knowledge check

1. What is an expression?
2. What is a statement?
3. What happens to the right-hand expression before assignment?
4. Why is assignment not an equation?
5. Rebinding versus mutation?
6. Why use parentheses?
7. What is a side effect?
8. Syntax error versus runtime exception versus logic error?

## Summary and completion criteria

Expressions evaluate to values; statements perform instructions. Assignment evaluates the right-hand side before binding names. Reassignment does not update earlier results. Precedence affects grouping. Trace tables reveal state changes and help diagnose logic errors.

Complete the lab and explain a program's state after each statement before marking this lesson studied.

## Official references

- [Expressions](https://docs.python.org/3/reference/expressions.html)
- [Simple Statements](https://docs.python.org/3/reference/simple_stmts.html)
- [Operator Precedence](https://docs.python.org/3/reference/expressions.html#operator-precedence)
- [Built-in Functions](https://docs.python.org/3/library/functions.html)
