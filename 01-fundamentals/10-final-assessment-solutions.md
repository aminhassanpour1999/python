# Programming Fundamentals — Final Assessment Solutions

**Use this file only after completing the assessment independently.** The explanations below are model answers. Equivalent answers are acceptable when they are technically correct and sufficiently explained.

## Part A — Core concepts

1. A name is an identifier bound to an object. An object has identity, type, and value.
2. `=` assigns or rebinds; `==` compares values; `is` compares identity.
3. `int`, `float`, `complex`, `str`, `bool`, and `NoneType`.
4. `/` is true division, `//` is floor division, and `%` returns the modulo remainder.
5. Most decimal fractions have no exact finite binary floating-point representation.
6. A string's contents cannot be changed in place; methods return new strings.
7. `input()` returns a string.
8. Every non-empty string is truthy; `"False"` is non-empty.
9. Expressions produce values; statements are instructions executed by Python.
10. Syntax errors prevent parsing, runtime exceptions occur during execution, and logic errors produce incorrect results without necessarily raising an exception.

## Part B — Predict and explain

### 11. Names and types

Output:

```text
15
str
```

The integer result is computed before `value` is rebound to the string `"changed"`. The type name of the new value is `str`.

### 12. Numeric operators

Output:

```text
3.5
3
-4
1
512
```

True division returns a float. Floor division rounds toward negative infinity. The remainder is 1. Exponentiation groups right-to-left: `2 ** (3 ** 2)`.

### 13. Strings

Output (the first line contains two leading spaces and one trailing space):

```text
  Python 
PYTHON
YTH
```

`strip()` returns a new string without surrounding whitespace; `upper()` returns an uppercase string. The slice includes index 1 and excludes index 4.

### 14. Boolean logic

Output:

```text
False
False
True
unknown
```

Zero is falsy but is not None. The empty string is falsy, so the `or` expression returns the second operand.

### 15. Input and conversion

After the prompt, output:

```text
str
13.0
```

`input()` returns text. `float()` creates a float, and adding 0.5 produces 13.0.

## Part C — Find and repair defects

### 16. Debug the calculator

Two defects:
- The average formula has incorrect grouping.
- A string cannot be concatenated directly with a float using `+`.

One repair:

```python
average = (first + second) / 2
print(f"Average: {average:.2f}")
```

Verify with at least three pairs, such as (10, 20) → 15, (1.5, 2.5) → 2, and (0, 8) → 4. Predict before running.

### 17. Debug the text handling

String methods return new strings, so their results were discarded. Index 50 is outside the string's range and raises IndexError.

Repair:

```python
label = "  receiver-01  "
cleaned_label = label.strip().replace("-", "_").upper()
print(cleaned_label)
```

Output:

```text
RECEIVER_01
```

Indexing selects one position and may raise IndexError when out of range. Slicing extracts a range and clips out-of-range boundaries.

## Part D — Practical task rubric

There is no single required implementation. A valid solution should resemble this structure:

```python
first_text = input("First measurement in volts: ")
second_text = input("Second measurement in volts: ")

first_voltage = float(first_text)
second_voltage = float(second_text)

average_voltage = (first_voltage + second_voltage) / 2

print(f"First measurement: {first_voltage:.2f} V")
print(f"Second measurement: {second_voltage:.2f} V")
print(f"Average: {average_voltage:.2f} V")
```

This is an example of the expected structure, not a template to copy. The learner must write their own version and test multiple inputs.

Suggested test cases:
- 10 and 20 → average 15
- 1.5 and 2.5 → average 2
- 0 and 8 → average 4

A suitable limitation: non-numeric input raises `ValueError` and is not handled. A later improvement would be to add explicit validation and exception handling.

## Scoring guidance

Use the point allocations in the assessment. For open-ended answers, award points for correct reasoning, not exact wording. For the practical task, verify behavior by running it with the learner's stated test cases. Do not award full points for copied code that the learner cannot explain.
