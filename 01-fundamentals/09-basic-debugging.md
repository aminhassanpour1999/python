# Basic Debugging

**Prerequisites:** Introduction; Variables and Data Types; Numbers and Operators; Strings; Type Conversion; Expressions and Statements  
**Study time:** 75–100 minutes

## Purpose and learning outcomes

Debugging is a disciplined process of finding why actual behavior differs from expected behavior. It is not random editing. You will classify errors, read tracebacks, inspect values and types, construct minimal reproductions, use breakpoints conceptually, and verify a fix with more than one test.

## 1. Three broad categories of errors

### Syntax errors

Python cannot parse the source code.

~~~python
# print("Hello"
~~~

The missing closing parenthesis prevents execution. Syntax errors are often detected before the program begins running.

### Runtime exceptions

The program starts but an operation raises an exception during execution.

~~~python
numerator = 10
denominator = 0
# result = numerator / denominator  # ZeroDivisionError
~~~

Other common exceptions at this stage include NameError, TypeError, ValueError, IndexError, and AttributeError.

### Logic errors

The program runs but does not implement the intended behavior.

~~~python
first = 10
second = 20
wrong_average = first + second / 2
correct_average = (first + second) / 2
print(wrong_average)    # 20.0
print(correct_average)  # 15.0
~~~

No exception is required for a logic error. Tests and reasoning are essential.

## 2. Read a traceback from the bottom up

A traceback reports the call path and the location where an exception occurred. The final line normally names the exception type and message. Earlier lines show how execution reached that point.

When reading one:

1. Identify the exception type and message at the bottom.
2. Find the final relevant file and line number.
3. Inspect the operation and the values involved.
4. Read earlier frames if the immediate line is only where a bad value was used.
5. Reproduce the issue before editing.

A traceback identifies where the failure surfaced, not necessarily where the bad value originated.

### 2.1 Example traceback, annotated

The following is an illustrative traceback. File names and line numbers depend on where you run the code.

~~~text
Traceback (most recent call last):
  File "calculator.py", line 4, in <module>
    result = numerator / denominator
             ~~~~~~~~~~^~~~~~~~~~~~~
ZeroDivisionError: division by zero
~~~

Read it from the bottom:

- The final line gives the exception type, ZeroDivisionError, and its message.
- The preceding frame identifies the file and line where the exception surfaced.
- The displayed source line shows the operation that failed.
- The traceback may contain several frames if one function called another.

A traceback is evidence about the failure path. It does not automatically explain why denominator became zero; inspect where that value was assigned and what input produced it.

### 2.2 Common beginner exceptions

| Exception | Typical cause at this stage | First thing to inspect |
|---|---|---|
| SyntaxError | Invalid source syntax, such as an unmatched quote | The indicated line and nearby delimiters |
| NameError | A name is not defined in the current scope | Spelling and assignment order |
| TypeError | An operation does not support the supplied type | type() of each operand |
| ValueError | A value has the right general type but invalid content | repr() of the value and conversion rule |
| ZeroDivisionError | A divisor is zero | The divisor and its origin |
| IndexError | A sequence index is outside its valid range | len(sequence) and the index |

The same exception can have different root causes. Diagnose the actual values and code path instead of memorizing a single fix.

### 2.3 Debugging with an IDE or pdb

A graphical debugger and the command-line debugger pdb provide the same essential ideas: pause at a chosen line, inspect variables, step through execution, and continue. In VS Code, a breakpoint can be set by clicking beside a line number; start the debugger and inspect the Variables and Debug Console panes.

For a simple script, print(), repr(), and type() may be enough. Use a debugger when the state changes across many lines or the failure is difficult to reproduce by inspection. Debugger controls vary by editor, but the concepts do not.

### 2.4 A compact defect report

When you ask someone to help debug a problem, include:

- **Expected:** what should have happened.
- **Actual:** what happened instead, including the complete traceback when relevant.
- **Reproduction:** the smallest code and exact input that reproduce it.
- **Environment:** Python version and operating system only when relevant.
- **Recent change:** what changed immediately before the problem appeared.
- **Attempted diagnosis:** what you inspected and what you learned.

Do not include passwords, API keys, or private data in a reproduction.

## 3. A repeatable debugging process

Use this sequence:

1. **Observe:** record the exact output, exception, and input.
2. **Expected behavior:** state what should happen.
3. **Reproduce:** find the smallest input and code that still show the problem.
4. **Classify:** syntax, exception, or logic error?
5. **Hypothesize:** name one likely cause.
6. **Inspect:** examine values, types, and execution order.
7. **Change one thing:** make the smallest justified repair.
8. **Retest:** run the original failing case and additional representative cases.
9. **Explain:** describe why the defect happened and why the fix works.

Changing many unrelated lines at once makes cause and effect difficult to establish.

## 4. Inspect values, types, and invisible characters

print() is useful, but it may hide important details. Use repr() and type() to inspect a suspicious value.

~~~python
value = " 12.5 "
print(value)
print(repr(value))
print(type(value).__name__)
~~~

Output:

~~~text
 12.5
' 12.5 '
str
~~~

This reveals surrounding whitespace and shows that the value is text, not a float.

For numeric calculations, inspect intermediate results and units. A plausible-looking number may still be wrong because of a type, unit, precedence, or rounding mistake.

## 5. Minimal reproducible examples

A minimal reproducible example contains the smallest code and input that still reproduce the issue. Include:

- The code needed to trigger the behavior.
- The exact input.
- The actual output or traceback.
- The expected behavior.
- Relevant environment details only when they affect the result.

~~~python
label = "cat"
print(label[3])
~~~

The valid indexes are 0, 1, and 2. Index 3 is outside the string, so this example raises IndexError.

A small example removes unrelated code and makes a hypothesis easier to test.

## 6. Debugger concepts

A debugger lets you pause execution and inspect program state.

- **Breakpoint:** a selected location where execution pauses.
- **Step over:** execute the current line without entering a called function.
- **Step into:** enter a called function.
- **Step out:** finish the current function and return to its caller.
- **Continue:** resume until the next breakpoint or program end.
- **Watch / variable inspection:** observe values as execution proceeds.

You do not need to memorize a particular IDE's buttons yet. Learn what information a debugger provides and when it is useful.

## 7. Assertions are not general input validation

An assert statement checks an internal assumption during development.

~~~python
voltage_v = 3.3
assert voltage_v >= 0
~~~

Assertions can be disabled when Python runs with optimization. They are not a substitute for explicit validation of untrusted user input or external data. Robust input validation and exception handling belong later.

## 8. Common debugging mistakes

1. Editing before understanding the failure.
2. Treating the last traceback line as the full root cause.
3. Looking only at printed appearance instead of type and repr().
4. Fixing one example but not testing boundaries.
5. Changing several unrelated things simultaneously.
6. Assuming no exception means correct behavior.
7. Catching or suppressing an error without understanding it.
8. Using assert to validate untrusted input.

## 9. Coding lab — Debug a measurement calculator

Create debugging_lab.py from this intentionally defective program:

~~~python
distance_text = "12.5"
time_text = "2"
distance = distance_text
time = float(time_text)
average_speed = distance + time / 2
print("Speed: " + average_speed)
~~~

Tasks:

1. Predict what happens before running.
2. Identify the type of each variable.
3. Find the first runtime failure.
4. Repair conversion and formula grouping.
5. Add a clear unit to the output.
6. Test at least four inputs, including a decimal, zero, and an invalid representation.
7. Record the original defect, root cause, fix, and test evidence.

Do not add advanced exception handling or loops yet. Explain what would be needed for a robust interactive version.

## 10. Independent exercises

### Level 1

1. Classify a missing parenthesis, division by zero, and an incorrect average formula.
2. What information does a traceback provide?
3. Distinguish TypeError from ValueError.
4. When is repr() more useful than print()?

### Level 2

5. Define a minimal reproducible example for an IndexError.
6. Explain step over versus step into.
7. Trace a short program with reassignment and intermediate values.
8. What does a breakpoint do?
9. How should you verify a fix?

### Level 3

10. A program prints a plausible but incorrect average. Describe a systematic investigation.
11. Why might the failing line not be where the bad value originated?
12. Why are many simultaneous edits harmful?
13. Why should assert not validate external input?
14. Create a minimal example for an out-of-range string index and explain the traceback.

## Exercise solutions — open after attempting the exercises

Open only after attempting the lesson.

## Level 1
1. Missing parenthesis: syntax error; division by zero: ZeroDivisionError; wrong average: logic error.
2. A traceback shows the call path, file and line, and final exception type/message.
3. TypeError means inappropriate type; ValueError means unacceptable value of an otherwise suitable type.
4. repr() exposes quotes, escapes, and whitespace.
## Level 2
5. label = "cat"; print(label[3]) is a minimal IndexError example.
6. Step over runs a call without entering; step into enters the called function.
7. Record each relevant name after every statement.
8. A breakpoint pauses execution so state can be inspected.
9. Retest the original failure and ordinary, boundary, and invalid cases.
## Level 3
10. Reproduce, calculate expected output independently, inspect intermediate values/types, check units and grouping, then test one hypothesis.
11. The bad value may have been created earlier; the failing line may only expose it.
12. Multiple edits make cause and effect difficult to isolate.
13. Assertions can be disabled with optimization and are for internal assumptions, not untrusted input.
14. label = "cat"; print(label[3]). Valid indexes are 0, 1, 2; index 3 is out of range.
## Knowledge check
1. Syntax errors prevent parsing; runtime exceptions occur during execution; logic errors produce wrong behavior.
2. Exception type and message.
3. Reproduction creates a reliable test and prevents random edits.
4. A value may have the wrong type or hidden whitespace.
5. Smallest code/input that reproduces the issue plus expected and actual behavior.
6. A selected pause location.
7. Step over does not enter the call; step into does.
8. For internal development assumptions.
9. A fix may fail at boundaries or with other types.
10. Symptom, input, expected/actual behavior, reproduction, cause, repair, and test evidence.
## Lab review
Convert both raw values, correct the formula grouping, label the unit, and test ordinary, boundary, and invalid representations. State that invalid input is not yet handled gracefully.

## Knowledge check

1. Syntax error versus runtime exception versus logic error?
2. What does the final traceback line usually identify?
3. Why reproduce a problem?
4. Why can a value look right but have the wrong type?
5. What makes an example minimal and reproducible?
6. What is a breakpoint?
7. Step over versus step into?
8. When are assertions appropriate?
9. Why is one successful test insufficient?
10. What evidence should a defect report include?

## Summary and completion criteria

Debug systematically: observe, define expected behavior, reproduce, classify, hypothesize, inspect, make one focused change, and retest. Tracebacks identify where exceptions surface; inspecting types and representations reveals hidden causes. Logic errors require deliberate tests even when code runs.

Complete the lab and explain the root cause of each defect before marking this lesson studied.

## Official references

- [Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
- [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)
- [The assert statement](https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement)
- [Python Debugger — pdb](https://docs.python.org/3/library/pdb.html)
