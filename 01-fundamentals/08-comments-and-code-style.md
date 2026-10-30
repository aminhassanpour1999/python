# Comments and Code Style

**Module:** Programming Fundamentals  
**Lesson:** 8 of 9 · **Level:** Beginner · **Study time:** 45–60 minutes  
**Prerequisites:** Previous Fundamentals lessons

## Purpose and learning objectives

Readable code is easier to understand, debug, test, and maintain. Style does not replace correctness, but it helps people reason about a program. By the end, you should be able to write useful comments; choose meaningful names; apply basic PEP 8 conventions; distinguish comments, strings, and docstrings; and refactor a small script without changing its behavior.

## 1. Why style matters

Compare:

    x = 48000
    y = x / 1000
    print(y)

With:

    sample_rate_hz = 48_000
    sample_rate_khz = sample_rate_hz / 1_000
    print(sample_rate_khz)

The second version explains the meaning and units of the values. Programs are read and maintained, not merely executed once.

## 2. Comments

A comment begins with # outside a string. Python ignores comment text during execution:

    # Convert the sample rate from Hz to kHz.
    sample_rate_khz = sample_rate_hz / 1_000

A useful comment explains intent, assumptions, or a non-obvious decision. It should not merely repeat the code:

Poor:
    # Add one to count
    count += 1

Better, when the reason is not obvious:
    # Include the current batch in the running total.
    total_samples += current_batch_size

Comments can become misleading when code changes. Update or remove a comment when it no longer describes behavior.

## 3. Comments, strings, and docstrings

A string literal is data:

    message = "This is text, not a comment."

A docstring is a string literal used as documentation for a module, class, or function. Formal docstring practice is developed with functions:

    """A module-level description."""

A triple-quoted string is not automatically a comment. It is still a string literal and becomes a docstring only in the appropriate position.

## 4. Naming conventions

- Variables and functions: lowercase snake_case.
- Constants: uppercase words separated by underscores by convention.
- Class names: CapWords (covered in OOP).
- Avoid unexplained abbreviations and single-letter names outside short mathematical contexts.
- Avoid shadowing built-ins such as str, list, type, and sum.
- Choose names that describe meaning, not merely implementation.

    sample_count = 250
    maximum_retries = 3
    DEFAULT_TIMEOUT_SECONDS = 10

Names should be clear without becoming unnecessarily long. Consistency matters.

## 5. Whitespace and layout

PEP 8 recommends four spaces per indentation level. Do not mix tabs and spaces in the same block.

Use spaces around binary operators:

    average = (first + second) / 2

Use blank lines to separate logical groups. Keep related statements together. PEP 8 offers line-length guidance, but projects may adopt another consistent limit. When a line is too long, split it at a meaningful boundary:

    average = (
        first_measurement
        + second_measurement
        + third_measurement
    ) / 3

## 6. Constants and units

Python does not enforce constants. Uppercase names communicate that a value is intended to remain unchanged:

    SPEED_OF_LIGHT_M_PER_S = 299_792_458
    sample_rate_hz = 48_000

Use units in names when ambiguity is possible. Do not combine quantities with different units without an explicit conversion.

## 7. Basic refactoring

Refactoring improves code structure without intentionally changing behavior.

Before refactoring:
1. Understand the intended behavior.
2. Record output for representative inputs.
3. Change one aspect at a time.
4. Run the same tests after the change.

Useful beginner refactorings include renaming unclear variables, extracting intermediate calculations, removing redundant comments, adding labels and units, and splitting unrelated actions into separate statements.

## 8. Common style mistakes

1. Unclear names such as x1 or temp when meaningful names are easy.
2. Shadowing built-ins.
3. Comments that repeat code or no longer match it.
4. Inconsistent indentation.
5. Missing spaces around operators.
6. Lines that combine too many unrelated actions.
7. Unexplained numeric constants.
8. Treating style as a substitute for correctness or testing.

## 9. Coding lab — Refactor an unclear script

Refactor this program while preserving its behavior:

    x=48000
    y=96000
    z=(x+y)/2
    print("result",z)

Requirements:
1. Choose meaningful names.
2. Use consistent spacing and blank lines.
3. Include units in names or output.
4. Add a comment only if it explains intent not obvious from the code.
5. Run the original and revised versions with the same inputs and compare outputs.

## 10. Independent exercises

1. Rename a, b, and c in an average calculation.
2. Explain why a comment repeating the next line adds little value.
3. Distinguish a comment, string literal, and docstring.
4. Rewrite a long expression using parentheses and intermediate variables.
5. Identify three built-in names that should not be reused for variables.
6. Explain how you would verify a refactor did not change behavior.

## Answer guide

Answers may differ. A good refactor preserves the calculation, uses meaningful names, includes units where useful, and avoids misleading comments. Verify by comparing the original and refactored outputs with the same test inputs.

## Knowledge check

1. What makes a comment useful?
2. What is the difference between a comment and a docstring?
3. What is snake_case?
4. What indentation convention does PEP 8 recommend?
5. What is refactoring?
6. How can you verify that a refactor preserved behavior?

## Summary and completion criteria

Readable code uses meaningful names, consistent whitespace, clear layout, and comments that explain intent. PEP 8 is a style guide, not a substitute for correctness or judgment.

- [ ] I can choose clear snake_case names.
- [ ] I avoid shadowing built-ins.
- [ ] I can write useful comments and distinguish docstrings.
- [ ] I can apply basic indentation and whitespace conventions.
- [ ] I can refactor a short script and verify its behavior is unchanged.

## Official references

- [PEP 8 — Style Guide for Python Code](https://peps.python.org/pep-0008/)
- [Python Tutorial — Coding Style](https://docs.python.org/3/tutorial/controlflow.html#intermezzo-coding-style)
- [Lexical Analysis — Comments](https://docs.python.org/3/reference/lexical_analysis.html#comments)
