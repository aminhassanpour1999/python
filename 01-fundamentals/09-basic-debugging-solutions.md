# Basic Debugging — Exercise Solutions

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
