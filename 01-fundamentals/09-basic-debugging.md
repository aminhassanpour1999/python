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

## Exercise solutions

Attempt the exercises and knowledge check before opening the separate [basic-debugging — Exercise Solutions](./09-basic-debugging-solutions.md).

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
