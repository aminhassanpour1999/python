# Comments and Code Style

**Prerequisites:** Variables and Data Types; Expressions and Statements  
**Study time:** 60–90 minutes

## Purpose and learning outcomes

Readable code reduces defects and makes reasoning easier. Style is not decoration: it communicates intent and makes review, debugging, and maintenance more reliable.

You will choose meaningful names, use comments responsibly, distinguish comments from strings and docstrings, apply foundational PEP 8 conventions, represent units clearly, and refactor without changing behavior.

## 1. Readability is a correctness tool

Compare:

~~~python
x = 48000
y = 96000
z = (x + y) / 2
print(z)
~~~

with:

~~~python
first_sample_rate_hz = 48_000
second_sample_rate_hz = 96_000
average_sample_rate_hz = (
    first_sample_rate_hz + second_sample_rate_hz
) / 2
print(f"Average sample rate: {average_sample_rate_hz:.1f} Hz")
~~~

The second version communicates meaning and units. A reader can review the calculation without guessing what x, y, and z represent.

## 2. Naming identifiers

Use names that describe meaning, not merely type or position.

- Variables and functions conventionally use snake_case.
- Classes conventionally use CapWords (introduced in OOP).
- Constants conventionally use UPPER_SNAKE_CASE.
- Avoid single-letter names except for short, conventional local mathematics where the meaning is clear.
- Avoid vague names such as data, value, temp, or result when a more precise name is available.
- Do not shadow built-ins such as str, list, sum, type, print, or input.

Names are case-sensitive. Use units in names when they prevent ambiguity: distance_km, elapsed_seconds, voltage_v.

## 3. Comments, strings, and docstrings

A comment begins with # outside a string and is ignored by Python.

~~~python
# Convert elapsed time to seconds before calculating speed.
elapsed_seconds = elapsed_minutes * 60
~~~

A comment should explain intent, an assumption, a constraint, or a non-obvious decision. Avoid comments that merely repeat the code.

~~~python
# Weak: Add one to count.
count = count + 1

# Better: The external report numbers its first sample as 1.
sample_number = zero_based_index + 1
~~~

A string literal is a value. A docstring is a string literal placed in the designated position at the beginning of a module, class, or function body. Docstrings are documentation, not comments. Function and class docstrings are studied in detail later.

## 4. Whitespace and layout

PEP 8 recommends four spaces per indentation level. Do not mix tabs and spaces. Use spaces around binary operators and after commas. Keep related code visually grouped.

~~~python
average = (first_reading + second_reading) / 2
is_valid = 0.0 <= voltage_v <= 5.0
~~~

Avoid unnecessary alignment that makes edits fragile. Follow a consistent line-length convention and split long expressions where it improves readability. PEP 8 is a style guide, not a language syntax specification: code can run while violating style guidance.

## 5. Constants and magic numbers

A magic number is a literal whose meaning is unclear in context.

~~~python
CALIBRATION_FACTOR = 1.15
calibrated_value = raw_value * CALIBRATION_FACTOR
~~~

Uppercase is a convention; Python does not make the object immutable because the name is uppercase. Give a constant a name when it represents a meaningful rule, configuration value, or domain quantity. Do not create a named constant for every trivial literal.

## 6. Refactoring and behavior preservation

Refactoring improves internal structure without intentionally changing observable behavior.

A safe beginner refactoring process:

1. Understand what the original code is intended to do.
2. Record representative inputs and outputs.
3. Improve names and grouping in small steps.
4. Run the same tests after each change.
5. Investigate every difference rather than assuming it is harmless.

~~~python
# Original
a = 12
b = 8
c = (a + b) / 2
print(c)

# Refactored
first_reading = 12
second_reading = 8
average_reading = (first_reading + second_reading) / 2
print(average_reading)
~~~

Both calculate 10.0. The refactor changes clarity, not intended behavior.

## 7. Common style mistakes

1. Names that reveal no meaning.
2. Shadowing a built-in name.
3. Comments that restate the next line.
4. Comments that contradict the actual units or logic.
5. Inconsistent indentation or spacing.
6. Unexplained numeric literals that represent important rules.
7. Overly clever expressions that are hard to review.
8. Refactoring many things at once without checking behavior.

## 8. Coding lab — Refactor an unclear measurement script

Create style_lab.py using the following starting point:

~~~python
x=12.5
y=0.5
z=x/y
print("result",z)
~~~

1. Choose meaningful names that include units.
2. Add spaces and line breaks according to PEP 8 basics.
3. Format the output with a label and unit.
4. Add a comment only if it explains an assumption.
5. Run both versions with the same values.
6. Test another ordinary case and a boundary case.
7. Explain why the refactor preserves the calculation.

## 9. Independent exercises

### Level 1

1. Improve names such as x, y, z, and t for a speed calculation.
2. Name five built-ins that should not be shadowed.
3. Distinguish a comment, a string literal, and a docstring.
4. What indentation size does PEP 8 recommend?

### Level 2

5. Rewrite unclear measurement variables with units.
6. Split a long expression into readable intermediate values.
7. Identify comments that repeat code versus comments that explain intent.
8. Give a meaningful constant name for a calibration factor.

### Level 3

9. Review a short script and propose five improvements.
10. Does an uppercase name make a value immutable? Explain.
11. Find a mismatch between a comment and a unit in a sample program; propose a correction.
12. Explain how to verify a refactor preserves behavior.
13. Give an example of a useful comment that a long variable name cannot replace.

## Exercise solutions

Attempt the exercises and knowledge check before opening the separate [comments-and-code-style — Exercise Solutions](./08-comments-and-code-style-solutions.md).

## Knowledge check

1. What makes a name useful?
2. Why is shadowing a built-in harmful?
3. What should a useful comment explain?
4. What is a docstring?
5. What indentation does PEP 8 recommend?
6. What is a magic number?
7. What is refactoring?
8. How can you verify that refactoring did not change behavior?

## Summary and completion criteria

Readable code uses meaningful names, consistent layout, accurate units, and comments that explain intent. Style conventions do not change Python syntax, but they improve communication and reduce mistakes. Refactoring must be checked against expected behavior.

Complete the lab and review another person's short script for clarity before marking this lesson studied.

## Official references

- [PEP 8 — Style Guide for Python Code](https://peps.python.org/pep-0008/)
- [Lexical Analysis — Comments](https://docs.python.org/3/reference/lexical_analysis.html#comments)
- [Compound Statements — Indentation](https://docs.python.org/3/reference/compound_stmts.html)
- [PEP 257 — Docstring Conventions](https://peps.python.org/pep-0257/)
