# Basic Debugging

> **Status:** Syllabus outline. We will expand this lesson into teaching notes, a coding lab, exercises, and a small project when we study it.

## Learning objectives

- Distinguish syntax errors, runtime exceptions, and logic errors.
- Read a traceback to locate the relevant file, line, and exception message.
- Use a minimal reproducible example to investigate a problem.
- Inspect intermediate values and test a hypothesis instead of guessing.
- Verify a fix with more than one representative input.

## Sections

1. **Three broad error categories** — syntax, runtime, and logic errors.
2. **Reading error messages** — filenames, line numbers, exception names, and traceback structure.
3. **Common beginner errors** — misspelled names, type errors, invalid conversions, and indexing mistakes.
4. **Print-based debugging** — inspect types and intermediate values with purposeful messages.
5. **Reproduce and isolate** — reduce a problem to the smallest example that still fails.
6. **Hypothesis-driven debugging** — predict the cause, test one change, and observe the result.
7. **Verify the repair** — rerun the original case and test at least one other representative case.
8. **Write a useful bug report** — expected result, actual result, steps, code, and error message.

## Coding lab

Debug a small measurement calculator with at least two planted bugs. Record the symptom, hypothesis, change, and verification for each bug.

## Exercises

- Classify short examples by error type.
- Read a traceback and identify the likely failing line.
- Diagnose a wrong result caused by incorrect arithmetic or conversion.
- Write a concise bug report for a reproducible problem.

## Knowledge check

Describe a repeatable debugging process and explain why changing many things at once makes diagnosis harder.

## References

- [Python Tutorial: Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
- [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)
