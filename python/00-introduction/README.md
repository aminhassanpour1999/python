# Python Introduction

This section introduces Python, common application areas, basic programming concepts, how Python code runs, the development workflow, your first program, and the official documentation.

> **Module scope:** These eight lessons establish context and practical orientation. They are not a substitute for the later fundamentals curriculum. Variables, data types, conditions, loops, functions, data structures, modules, exceptions, testing, and projects receive deeper treatment in later modules. Publishing a note does not mean the lesson has been studied or mastered.

## Recommended order

1. [What Is Python?](./01-what-is-python.md)
2. [Python Applications](./02-python-applications.md)
3. [Programming Fundamentals](./03-programming-fundamentals.md)
4. [How Python Runs](./04-how-python-runs.md)
5. [Installation and Development Setup](./05-installation-and-setup.md)
6. [Running Python Code](./06-running-python-code.md)
7. [Your First Python Program](./07-first-python-program.md)
8. [Python Documentation](./08-python-documentation.md)

## How to study this section

- Study one lesson at a time and explain the main ideas in your own words.
- Predict the output of each code example before running it.
- Run examples where practical, then change an input or condition and explain what changed.
- Attempt exercises without copying solutions first; keep your answers separately.
- Use official documentation as a reference, not as a requirement to read every page linearly.
- Treat examples as experiments, not proof that a program works for every possible input.
- Review gaps after practice. Reading a lesson is not the same as mastering it.

## Scope

This is an orientation module. It introduces the vocabulary and workflow needed to begin learning Python deliberately; it does not attempt to teach every language feature in advance.

## End-of-section checkpoint

Complete this checkpoint without copying a solution. You may consult the notes when needed, but explain your reasoning.

- [ ] Explain what Python is used for and name one strength and one limitation.
- [ ] Break a small problem into inputs, processing, and expected output before coding.
- [ ] Explain, at a high level, how a Python implementation runs source code, and avoid treating CPython details as universal rules for every Python implementation.
- [ ] Identify the Python interpreter and version used by your project.
- [ ] Create, save, run, and modify a simple .py file.
- [ ] Predict a program's output before execution and explain any mismatch.
- [ ] Find an answer in official documentation, interpret a function's signature, and check relevant version notes.
- [ ] Describe one way to verify a small program's result independently.

### Final Practice Lab: Average Two Measurements

**Goal:** combine the introductory skills from this section: identify inputs and processing, write a small script, run it, predict output, and verify the result independently.

1. Create a file named `introduction_average.py` in your Python learning folder.
2. Write the following program and save the file:

```python
first_value = 18
second_value = 26

average = (first_value + second_value) / 2

print(average)
```

3. Before running the file, calculate the expected result by hand.
4. Run it from the folder containing the file:

```bash
python3 introduction_average.py
```

Use the Python command available on your system if it differs from `python3`.

Expected output:

```text
22.0
```

5. Change `second_value` to `30`. Predict the output before running the program again.
6. Explain the program using input, processing, and output.
7. State one limitation. For example, this version assumes both values are valid numbers and does not ask the user for input.

**Completion criteria:** you can explain each line, predict the output before execution, verify it with a hand calculation, modify one value without copying a solution, and describe a limitation. If a result differs from your prediction, investigate the reason before considering the lab complete.

If you can complete the checkpoint with only occasional reference to the notes, the Introduction section has done its job. You do not need to master later Python topics in advance.

## Final assessment

The module previously had an end-of-section checkpoint and a practice lab, but no separate formal exam. A dedicated assessment is now available: [Introduction — Final Assessment](./09-final-assessment.md).

Use the assessment to check your understanding and practical ability. Do not mark the skill checkpoint below complete merely because you have read the lessons; tick each item only after you can demonstrate it.

## Study progress

Progress recorded from the latest verifiable study history available in this project. This is a conservative record, not a claim that unmarked lessons have never been studied elsewhere. Update a checkbox only after confirming the study, practice, and review.

- [x] 01 — What Is Python
- [x] 02 — Python Applications
- [x] 03 — Programming Fundamentals
- [ ] 04 — How Python Runs
- [ ] 05 — Installation and Setup
- [ ] 06 — Running Python Code
- [ ] 07 — First Python Program
- [ ] 08 — Python Documentation
