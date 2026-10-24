# Introduction — Final Assessment

This assessment checks whether you can explain the main ideas from the eight Introduction lessons and apply them to a small program.

**Suggested time:** 25–35 minutes  
**Total:** 20 points  
**Passing target:** 16/20 (80%), with no major misunderstanding in the practical task.

Try it without copying the lesson text. You may consult the official Python documentation for Question 8. Write your answers in a separate file or notebook; do not put personal answers in this repository unless you want them there.

## Part A — Core concepts (8 points)

Answer each question in 1–3 sentences. Each question is worth 1 point.

1. What is Python, and name one strength and one limitation of using it.
2. Give two different areas where Python is used. Name one relevant library or framework for either area.
3. Explain the difference between an algorithm and a program.
4. In the Input–Process–Output model, identify the input, process, and output for a program that calculates the average of two measurements.
5. At a high level, what happens when a Python source file is run by CPython? Why is saying “Python is interpreted” a useful simplification but not the whole implementation story?
6. What is the difference between a Python interpreter and a code editor? Can one application provide both?
7. Why should you predict a program's output before running it, and what should you do if the actual output differs from your prediction?
8. When reading the documentation for a function, name three details worth checking besides its name.

## Part B — Read and reason about code (5 points)

Consider this code:

```python
first_value = 18
second_value = 26
average = (first_value + second_value) / 2
print(average)
```

9. (2 points) Write the exact output and show the arithmetic used to verify it by hand.
10. (1 point) If `second_value` changes to `30`, what is the exact output?
11. (2 points) Identify the input values, processing step, and output in this program. State one limitation of the program as written.

## Part C — Practical task (7 points)

Create a file named `introduction_assessment.py` and write a small program that:

12. (2 points) Stores two numeric measurements in variables and calculates their average.
13. (1 point) Prints a clearly labelled result, such as `Average: 22.0`.
14. (1 point) Runs successfully from the terminal using the Python command available on your system.
15. (1 point) Is modified so that changing either measurement changes the result correctly.
16. (2 points) Includes a short explanation, in your own words, of how you verified the result independently and one limitation of your implementation.

You may choose your own measurement values. Do not copy the example values from the lesson as your only test.

## Scoring guide

- **18–20:** Strong foundation; proceed to Programming Fundamentals.
- **16–17:** Ready to proceed; review any missed concepts.
- **12–15:** Review the relevant Introduction lessons and retry the missed parts.
- **0–11:** Revisit the module before moving on.

A passing score is a useful checkpoint, not proof of mastery. You should be able to explain your reasoning and modify the program without copying a solution.

## Review checklist

- [ ] I answered the conceptual questions in my own words.
- [ ] I predicted outputs before running code.
- [ ] I verified a numerical result independently.
- [ ] I created, ran, and modified my own Python file.
- [ ] I reviewed every mistake before moving on.
