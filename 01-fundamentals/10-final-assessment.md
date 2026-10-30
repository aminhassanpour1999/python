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
