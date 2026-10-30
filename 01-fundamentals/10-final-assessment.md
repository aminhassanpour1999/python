# Programming Fundamentals — Final Assessment

**Purpose:** Verify that you can use the nine Fundamentals lessons together, not merely recall definitions.  
**Suggested time:** 60–75 minutes  
**Total:** 50 points  
**Suggested passing score:** 40/50 (80%). A passing score is a checkpoint, not proof of mastery.

## Instructions

- Attempt every question before checking notes.
- Predict outputs before running snippets.
- Write your own code; do not copy a lesson solution.
- For practical tasks, test more than one input.
- Explain reasoning. Correct output without a sound explanation earns limited credit.

**Model answers:** The answer key is included at the end of this same file. Complete the assessment first; do not scroll to the answer key until you have submitted your own work.

## Part A — Core concepts (10 points)

Answer each in 1–3 sentences. Each is worth 1 point.

1. Explain the relationship between a name, an object, and a value.
2. How are assignment (=), equality (==), and identity (is) different?
3. Name the built-in scalar types introduced in Fundamentals.
4. Explain the difference between /, //, and %.
5. Why can 0.1 + 0.2 differ from 0.3?
6. What does it mean that strings are immutable?
7. What does input() return?
8. Explain why bool("False") is True.
9. How do an expression and a statement differ?
10. Distinguish a syntax error, a runtime exception, and a logic error.

## Part B — Predict and explain (15 points)

Each question is worth 3 points. Write exact output and explain the rules.

### 11. Names and types

    value = "12"
    number = int(value) + 3
    value = "changed"
    print(number)
    print(type(value).__name__)

### 12. Numeric operators

    print(7 / 2)
    print(7 // 2)
    print(-7 // 2)
    print(7 % 2)
    print(2 ** 3 ** 2)

### 13. Strings

    label = "  Python "
    cleaned = label.strip().upper()
    print(label)
    print(cleaned)
    print(cleaned[1:4])

### 14. Boolean logic

    reading = 0
    missing = None
    print(bool(reading))
    print(reading is None)
    print(missing is None)
    print("" or "unknown")

### 15. Input and conversion

Assume the user enters 12.5 when prompted:

    value_text = input("Value: ")
    print(type(value_text).__name__)
    value = float(value_text)
    print(value + 0.5)

Write the two output lines produced after the prompt and explain the type change.

## Part C — Find and repair defects (10 points)

### 16. Debug the calculator (5 points)

    first_text = input("First measurement: ")
    second_text = input("Second measurement: ")

    first = float(first_text)
    second = float(second_text)

    average = first + second / 2
    print("Average: " + average)

Identify two defects that prevent or compromise the intended result. Rewrite the relevant lines and explain how you would verify the repair.

### 17. Debug the text handling (5 points)

    label = "  receiver-01  "
    label.strip()
    label.replace("-", "_")
    print(label[50])

Identify the problems and rewrite the code to produce the cleaned label RECEIVER_01. Explain the difference between indexing and slicing if you use a slice.

## Part D — Practical task (15 points)

### 18. Build a command-line measurement summary

Create fundamentals_assessment.py. Your program must:

1. Ask the user for two measurements and state the expected unit. (2 points)
2. Convert the input strings to numeric values explicitly. (2 points)
3. Calculate the average with correct grouping. (2 points)
4. Print both inputs and the average using readable f-strings, labels, units, and sensible precision. (2 points)
5. Use meaningful names and consistent style. (2 points)
6. Include one useful comment only if it explains intent or an assumption. (1 point)
7. Test at least three pairs of values, including decimals and a boundary or unusual case. Predict each result before running. (2 points)
8. Write a short note describing one limitation and one improvement you would add in a later module. (2 points)

Do not add advanced exception handling; explain how invalid input currently behaves.

## Part E — Unseen transfer task (required for demonstrated mastery; unscored)

This task is intentionally not included in the 50-point score. It checks whether you can transfer the ideas to a slightly different situation rather than reproduce a familiar template.

A device report contains a channel identifier and two readings:

~~~python
raw_identifier = "  rx-007 "
first_text = "0.0"
second_text = "4.5"
~~~

Without using loops, functions, classes, collections, or exception handling:

1. Clean the identifier by trimming whitespace and converting letters to uppercase.
2. Preserve the identifier as text; explain why converting its numeric suffix to int would lose information.
3. Convert both reading strings to floats.
4. Calculate the average and the signed difference (second minus first).
5. Build a Boolean that checks whether both readings are present and finite. Treat zero as a valid reading.
6. Format a compact report with labels and units.
7. Deliberately write the average formula incorrectly, predict its result, diagnose the logic error, and repair it.
8. Change the readings to a second test pair and explain how the result changes.

**Transfer sign-off:** You can explain every line, preserve the identifier, distinguish zero from missing, calculate correctly, and justify your tests without copying the worked assessment task. If you cannot, revisit the relevant lessons and retry with different values.

## Scoring guide

| Score | Interpretation | Next action |
|---:|---|---|
| 45–50 | Strong independent command | Review minor errors, then continue |
| 40–44 | Ready with targeted review | Revisit missed topics before Control Flow |
| 32–39 | Partial understanding | Review relevant lessons and retry |
| 0–31 | Foundations need more practice | Re-study and complete labs |

## Review map

| Missed area | Revisit |
|---|---|
| Names, objects, assignment, types | Lesson 1 |
| Numeric operations, precedence, precision | Lesson 2 |
| Indexing, slicing, methods, formatting | Lesson 3 |
| Conversion and conversion errors | Lesson 4 |
| input(), print(), prompts, output | Lesson 5 |
| Truthiness, Boolean logic, None | Lesson 6 |
| Expressions, statements, tracing | Lesson 7 |
| Comments and readability | Lesson 8 |
| Tracebacks and debugging | Lesson 9 |

## Independent mastery checklist

- [ ] I answered concepts without copying.
- [ ] I predicted every snippet before running it.
- [ ] I repaired both defective programs and explained why.
- [ ] I wrote the practical program myself.
- [ ] I tested multiple inputs and reviewed every mistake.
- [ ] I can explain my code line by line.
- [ ] I can solve a similar new task without following the assessment template.

A score alone does not mark the module as demonstrated. Discuss missed questions, retry them later without notes, and demonstrate the skills in a new problem.


---

# Model answer key — open only after completing the assessment

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

The Part E transfer task is intentionally unscored and has no fixed answer. The learner must complete it with new values and explain the reasoning independently.
