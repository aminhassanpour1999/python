# Programming Fundamentals — Final Assessment

This assessment checks the core skills in the nine Fundamentals lessons. It is designed to test reasoning and independent practice, not memorization.

**Suggested time:** 40–50 minutes  
**Total:** 30 points  
**Suggested passing score:** 24/30 (80%). You should also be able to explain your practical code.

## Part A — Concepts (9 points)

Answer each question in 1–3 sentences. Each question is worth 1 point.

1. What does assignment do in Python, and how is `=` different from `==`?
2. Name four common built-in types and give a valid example of each.
3. Explain the difference between `/`, `//`, and `%`.
4. What does it mean that strings are immutable?
5. Why does `input()` usually need conversion before numeric arithmetic?
6. Explain the difference between `False`, `0`, an empty string, and `None`.
7. What is the difference between an expression and a statement?
8. Give two style practices that make a small program easier to read.
9. Distinguish a syntax error, a runtime exception, and a logic error.

## Part B — Predict and explain (9 points)

Predict the result of each snippet before running it. Each question is worth 3 points.

### 10. Assignment and types

```python
value = "12"
number = int(value) + 3
print(number)
print(type(value).__name__)
```

Write both output lines exactly and explain why the two variables have different types.

### 11. Strings and numbers

```python
label = "  Signal "
clean_label = label.strip().lower()
result = 7 // 2
remainder = 7 % 2
print(clean_label)
print(result, remainder)
```

Write the exact output and explain what `strip()`, `lower()`, `//`, and `%` do here.

### 12. Boolean reasoning

```python
reading = 0
missing = None
print(bool(reading))
print(reading is None)
print(missing is None)
```

Write the exact output and explain why zero is not the same as `None`.

## Part C — Find and fix the problems (5 points)

### 13. Debug this program (5 points)

```python
first_text = input("Enter the first measurement: ")
second_text = input("Enter the second measurement: ")

first_measurement = float(first_text)
second_measurement = float(second_text)

average = (first_measurement + second_measurement) / 2
print("Average: " + average)
```

Identify at least two problems that prevent the program from working as intended. Rewrite the relevant lines, then explain how you would test your fix. You should notice that text input must be converted to numbers, and that a number cannot be concatenated directly to a string with `+`. You do not need to add advanced exception handling.

## Part D — Practical task (7 points)

### 14. Build a measurement summary

Create `fundamentals_assessment.py` that:

- (1 point) Uses meaningful variable names and stores two measurements.
- (2 points) Correctly converts text input to numeric values and calculates their average.
- (1 point) Prints a clearly labelled result using an f-string.
- (1 point) Includes a short comment only where it adds useful context.
- (1 point) Is tested with at least two different pairs of values; you predict each result before running it.
- (1 point) Includes a short note describing one limitation and one improvement you would make next.

You may choose your own measurements. Do not use the lesson examples as your only test case.

## Scoring guide

- **27–30:** Strong command of the module's foundations.
- **24–26:** Ready to continue; review any missed concepts.
- **18–23:** Review the corresponding lessons and retry the missed questions.
- **0–17:** Revisit the module and practice each concept before moving on.

A passing score is a checkpoint, not proof of mastery. Explain your reasoning and make sure your program works for more than one test case.

## Review checklist

- [ ] I predicted the output before executing each snippet.
- [ ] I can explain the relevant types and operations.
- [ ] I identified and fixed the debugging task's problems.
- [ ] I wrote and ran my own practical program.
- [ ] I tested more than one input and reviewed my mistakes.
