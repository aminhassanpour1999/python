# Input and Output

> **Status:** Syllabus outline. We will expand this lesson into teaching notes, a coding lab, exercises, and a small project when we study it.

## Learning objectives

- Use `print()` to produce clear, readable output.
- Use `input()` to ask a user for text.
- Convert input when numeric operations are required.
- Format output with f-strings and useful labels.
- Design simple prompts and recognize the need for input validation.

## Sections

1. **Output with `print()`** — multiple arguments, `sep`, and `end` at an introductory level.
2. **Input with `input()`** — prompts and the returned string.
3. **Input-to-computation workflow** — receive text, convert it, calculate, and report.
4. **Readable output** — labels, units, f-strings, and appropriate numeric formatting.
5. **Basic validation concepts** — valid ranges, empty text, and values that do not make sense for the task.
6. **Interactive versus fixed-data scripts** — trade-offs in testability and repeatability.
7. **Common mistakes** — forgetting conversion, unclear prompts, and printing a value without context.

## Coding lab

Create a command-line measurement calculator that asks for two numeric values and prints their average with a label. Try ordinary values, decimals, and an invalid entry; document the current limitation in error handling.

## Exercises

- Predict the exact output of small `print()` examples.
- Convert a fixed-value script into an interactive one.
- Improve vague prompts and unlabeled results.
- Identify which inputs should be checked before a result is trusted.

## Knowledge check

Explain what `input()` returns and outline the steps from user input to a labelled numeric result.

## References

- [Built-in Functions: `print()` and `input()`](https://docs.python.org/3/library/functions.html#print)
- [Formatted String Literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)
