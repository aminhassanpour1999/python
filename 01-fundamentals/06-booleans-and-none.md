# Booleans and None

**Prerequisites:** Variables and Data Types; Numbers and Operators; Type Conversion  
**Study time:** 60–90 minutes

## Purpose and learning outcomes

Programs need to reason about whether a condition is satisfied and whether a value is present. Python uses Boolean logic, but many objects can also be tested for truth. You will distinguish Boolean values, truthiness, and None; use comparisons; and explain short-circuit behavior.

## 1. Boolean values and comparisons

The bool type has exactly two values: True and False. Capitalization matters.

~~~python
is_connected = True
is_overloaded = False
print(type(is_connected))  # <class 'bool'>
~~~

Comparisons return Boolean results.

| Operator | Meaning |
|---|---|
| == | Equal |
| != | Not equal |
| < | Less than |
| <= | Less than or equal |
| > | Greater than |
| >= | Greater than or equal |

~~~python
temperature_c = 18
print(temperature_c >= 0)  # True
print(temperature_c < 25)  # True
print(temperature_c == 18) # True
~~~

### Chained comparisons

~~~python
temperature_c = 18
is_in_range = 0 <= temperature_c < 25
print(is_in_range)  # True
~~~

This is equivalent to checking both comparisons with and, while evaluating the middle expression once.

## 2. Truth-value testing (truthiness)

Python can test many objects in Boolean contexts. Common falsy values include False, None, numeric zero (0, 0.0, 0j), empty strings, and empty containers such as [], (), {}, and set(). Most other objects are truthy.

~~~python
print(bool(0))        # False
print(bool(-1))       # True
print(bool(""))       # False
print(bool(" "))      # True
print(bool("False"))  # True
print(bool(None))     # False
~~~

The string "False" is truthy because it is not empty. Truthiness does not inspect the meaning of its characters.

### Truthiness is not equality or presence

~~~python
measurement = 0.0
print(not measurement)      # True
print(measurement == 0.0)   # True
print(measurement is None)  # False
~~~

A zero reading may be valid. Do not use if measurement to check whether a numeric measurement exists if zero is allowed.

## 3. Boolean operators

- not x negates the truth value.
- x and y returns the first falsy operand, or y if x is truthy.
- x or y returns the first truthy operand, or y if x is falsy.

~~~python
connected = True
has_signal = False
print(not connected)            # False
print(connected and has_signal) # False
print(connected or has_signal)  # True
~~~

For Boolean operands, results match familiar logical operations. But and/or do not necessarily return a bool object.

## 4. Short-circuit evaluation

Python evaluates logical expressions left to right and may skip the right operand when the result is already determined.

~~~python
denominator = 0
is_safe = denominator != 0 and 100 / denominator > 1
print(is_safe)  # False
~~~

The division is skipped because the left operand is false. With or, a truthy left operand means the right side is skipped.

~~~python
name = "Amin"
display_name = name or "Anonymous"
print(display_name)  # Amin
~~~

Short-circuiting matters when the right side could raise an exception or perform an action. Avoid hiding important side effects in complicated logical expressions.

## 5. and and or return operands

~~~python
print("" or "unknown")  # unknown
print("online" and 1)   # 1
print(0 and 100)        # 0
~~~

The operators use truthiness to choose an operand. They do not convert the result to True or False. This is useful for simple fallbacks, but can be dangerous when a valid value such as zero or empty text must be preserved.

## 6. The meaning of None

None is a singleton representing absence of a value or a deliberate no-result state.

~~~python
measurement = None
print(measurement is None)      # True
print(measurement is not None)  # False
~~~

Use identity checks for None. This previews conditionals, taught in Control Flow.

| Value | Possible meaning |
|---|---|
| None | No value / not supplied |
| 0 | Numeric zero |
| False | Boolean false |
| "" | Empty text |
| [] | Empty list |

They may all be falsy, but they are not interchangeable. Meaning comes from the program's data model.

## 7. Logical and bitwise operators differ

For Boolean conditions, use and, or, and not. For integer bit manipulation, use &, |, ^, and ~ (plus shifts).

~~~python
print(True and False)  # False
print(0b0101 & 0b0001) # 1
~~~

and short-circuits; bitwise & evaluates both operands and combines bits. Use the operator appropriate to the task.

## 8. Common mistakes

1. Using is instead of == for string or numeric equality.
2. Treating "False" as a false Boolean.
3. Using truthiness to detect presence when zero is valid.
4. Assuming and/or always return bool.
5. Assuming the right operand always executes.
6. Using & instead of and for ordinary logic.
7. Comparing with None using == instead of the conventional is None.
8. Writing 0 <= x >= 10 when the intended interval is 0 through 10.

## 9. Coding lab — Measurement status checker

Create boolean_lab.py.

1. Define a connection status and a voltage measurement.
2. Represent a missing measurement with None.
3. Define a valid range from 0.0 through 5.0 inclusive.
4. Combine connection status with a present, in-range measurement.
5. Treat 0.0 as present, not missing.
6. Use short-circuiting to avoid comparing a missing value numerically.
7. Test None, zero, both boundaries, an interior value, and values outside the range.
8. Explain why if measurement is not a correct presence test.

## 10. Independent exercises

### Level 1

1. Predict bool() for 0, 1, -1, 0.0, "", " ", "False", and None.
2. Write comparisons for equal to 18, not equal to 20, between 10 inclusive and 25 exclusive, and outside that interval.
3. Explain measurement is None versus not measurement.
4. Predict exact value and type of "" or "unknown", "online" and 1, and 0 and 100.

### Level 2

5. Combine a connection Boolean and bounded voltage check.
6. Simplify not (is_connected == False).
7. Guard a division using short-circuit evaluation.
8. Check whether text contains non-whitespace characters.

### Level 3

9. Why must zero and None be distinguished in a sensor application?
10. Compare Boolean and with bitwise &.
11. When is a function call on the right side of and/or evaluated?
12. Why is status is "ready" incorrect?
13. Design boundary tests for a range that includes 10 but excludes 20.

## Exercise solutions

Attempt the exercises and knowledge check before opening the separate [booleans-and-none — Exercise Solutions](./06-booleans-and-none-solutions.md).

## Knowledge check

1. What are the two Boolean values?
2. What is truthiness?
3. Name common falsy values.
4. Why is a one-space string truthy?
5. What is a chained comparison?
6. What is short-circuit evaluation?
7. Do and/or always return Boolean values?
8. Why use is None?
9. Why is not value not a reliable missing-value check?
10. Why are boundary tests important?

## Summary and completion criteria

Comparisons produce Booleans. Many other objects have truth values. Falsy does not mean missing. Use is None for absence. and/or short-circuit and return operands. Logical operators and bitwise operators serve different purposes.

Complete the lab and explain truthiness, absence, operand-return behavior, and short-circuiting before marking this lesson studied.

## Official references

- [Boolean Operations](https://docs.python.org/3/reference/expressions.html#boolean-operations)
- [Truth Value Testing](https://docs.python.org/3/library/stdtypes.html#truth-value-testing)
- [Comparisons](https://docs.python.org/3/reference/expressions.html#comparisons)
- [Built-in Constants](https://docs.python.org/3/library/constants.html)
