# Basic Debugging

**Module:** Programming Fundamentals  
**Lesson:** 9 of 9 · **Level:** Beginner · **Study time:** 75–90 minutes  
**Prerequisites:** All previous Fundamentals lessons

## Purpose and learning objectives

Debugging is the disciplined process of finding and correcting defects. The goal is not to guess until code works; it is to collect evidence, form a hypothesis, test it, and verify the repair. By the end, you should be able to classify errors; read a traceback; recognize common exceptions; inspect values and types; create a minimal reproducible example; use breakpoints conceptually; and verify fixes with multiple tests.

## 1. Three broad categories of errors

### 1.1 Syntax errors

The source code does not follow Python's grammar:

    print("Hello"

Python cannot execute the code as written. IndentationError is a syntax-related error caused by invalid indentation.

### 1.2 Runtime exceptions

The code is syntactically valid, but an exceptional situation occurs while it runs:

    result = 10 / 0  # ZeroDivisionError

Common examples:
- NameError: a name is not defined in the current scope.
- TypeError: an operation or function receives an inappropriate type.
- ValueError: an argument has an acceptable general type but an invalid value.
- IndexError: a sequence index is out of range.
- KeyError: a mapping lookup uses a missing key (dictionaries come later).
- FileNotFoundError: a requested file cannot be found (file handling comes later).

### 1.3 Logic errors

The program runs but produces a result different from the intended result:

    first = 10
    second = 20
    average = first + second / 2  # Incorrect grouping
    correct_average = (first + second) / 2

Logic errors can be harder to find because Python cannot know what result you intended.

## 2. Read a traceback

An unhandled exception produces a traceback. It typically includes:
- The sequence of calls that led to the failure.
- File name and line number.
- The source line associated with the failure, when available.
- The exception type and message at the end.

Read from the bottom upward to identify the final exception, then use the file and line information to locate relevant code. The last line identifies the exception type and message; it does not always explain the complete cause.

Never share passwords, tokens, or private data in a traceback.

## 3. A repeatable debugging process

1. **Reproduce:** make the failure happen reliably.
2. **Observe:** record exact input, output, and error.
3. **Locate:** identify the relevant line and values.
4. **Hypothesize:** state one likely cause.
5. **Test:** inspect a value or change one thing to test the hypothesis.
6. **Repair:** make the smallest justified change.
7. **Verify:** rerun the original case and additional representative cases.
8. **Explain:** record why the defect occurred and why the fix works.

Changing many unrelated lines at once destroys useful evidence.

## 4. Inspect values and types

A print statement can reveal an unexpected value or type:

    reading_text = "12.5"
    print("reading_text:", repr(reading_text))
    print("type:", type(reading_text))

repr() displays a representation useful for debugging, including quotes and escaped whitespace. It differs from str() in purpose.

Inspect intermediate results, not only the final output:

    first = 10
    second = 20
    total = first + second
    average = total / 2

    print("first:", first)
    print("second:", second)
    print("total:", total)
    print("average:", average)

Remove or refine temporary debugging output when it is no longer needed.

## 5. Minimal reproducible examples

A minimal reproducible example is the smallest code and input that still demonstrates the problem. Include:
- Relevant code.
- Exact input or setup.
- Actual result or error.
- Expected result.
- Python version or environment if it may affect behavior.

Remove unrelated code while preserving the failure. Small examples are easier to reason about and easier for others to help with.

## 6. Debugger concepts

A debugger lets you pause execution and inspect state.

- **Breakpoint:** pauses execution at a chosen line.
- **Step over:** runs the current line without entering a called function.
- **Step into:** enters a function call.
- **Step out:** continues until the current function returns.
- **Variables/watch:** displays current values.
- **Call stack:** shows how execution reached the current point.

These concepts apply across editors and debuggers. Learn the interface of your chosen tool separately; the reasoning method matters more than a particular button.

## 7. Assertions are not general input validation

An assert statement checks an assumption during development:

    sample_count = 10
    assert sample_count > 0

If the condition is false, Python raises AssertionError. Assertions can document internal assumptions and catch bugs. They should not be the only validation for untrusted user input or security checks because Python can be run with assertions disabled.

## 8. Common debugging mistakes

1. Reading only the first line of a traceback.
2. Guessing without reproducing the failure.
3. Changing several things at once.
4. Inspecting only the final result.
5. Confusing syntax errors, exceptions, and logic errors.
6. Assuming code that runs is correct.
7. Testing only the input that originally worked.
8. Using assert instead of validating untrusted input.
9. Reporting a problem without exact error details or a minimal example.

## 9. Coding lab — Debug a measurement calculator

Create debug_lab.py with this intentionally flawed program:

    first_text = "12.5"
    second_text = "2"

    first = first_text
    second = float(second_text)
    average = (first + second) / 2
    print(f"Average: {average}")

Tasks:
1. Run it and identify the exception.
2. Inspect the types of first and second.
3. State a hypothesis about the cause.
4. Convert first_text correctly and rerun.
5. Introduce a logic error by changing the average formula; create a test case that reveals it.
6. Verify the repair with at least three pairs of values, including decimals.
7. Record symptom, hypothesis, change, and verification for each defect.

## 10. Independent exercises

1. Classify: missing closing parenthesis; division by zero; incorrect average grouping.
2. What information does a traceback provide?
3. Explain TypeError versus ValueError.
4. Why is repr() useful for inspecting text?
5. Define a minimal reproducible example.
6. Explain step over versus step into.
7. Why test a fix with more than the original input?
8. Why are assertions not a substitute for validating untrusted input?

## Answer guide

1. Syntax error; runtime exception; logic error.
2. Call sequence, file and line information, and final exception type/message.
3. TypeError concerns an inappropriate type; ValueError concerns an inappropriate value of an otherwise acceptable type.
4. repr() makes quotes, escapes, and whitespace visible.
5. The smallest code and input that still reproduces the problem, with expected and actual behavior.
6. Step over executes a call without entering it; step into enters the called function.
7. A fix may work only for one case; more cases reveal boundary and type assumptions.
8. Assertions can be disabled and are intended for internal development assumptions, not security or user-input guarantees.

## Knowledge check

1. How do syntax, runtime, and logic errors differ?
2. Which part of a traceback identifies the final exception?
3. Why change one thing at a time?
4. Why inspect types as well as values?
5. What makes an example reproducible?
6. What is a breakpoint?
7. When are assertions appropriate?

## Summary and completion criteria

Debugging is evidence-driven: reproduce, observe, locate, hypothesize, test, repair, verify, and explain. Tracebacks, print/repr inspection, and breakpoints are tools. A program that runs can still contain a logic error.

- [ ] I can classify syntax, runtime, and logic errors.
- [ ] I can read a traceback and locate relevant code.
- [ ] I can inspect values and types.
- [ ] I can create a minimal reproducible example.
- [ ] I can describe hypothesis-driven debugging.
- [ ] I understand breakpoint and stepping concepts.
- [ ] I tested a repair with multiple inputs and explained why it works.

## Official references

- [Python Tutorial — Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
- [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)
- [The assert statement](https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement)
