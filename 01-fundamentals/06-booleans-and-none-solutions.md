# Booleans and None — Exercise Solutions

Open only after attempting the lesson.

## Level 1
1. For 0, 1, -1, 0.0, "", " ", "False", None: False, True, True, False, False, True, True, False.
2. temperature == 18; temperature != 20; 10 <= temperature < 25; not (10 <= temperature < 25).
3. is None checks the None singleton; not value is true for every falsy value, including zero.
4. "" or "unknown" -> "unknown" (str); "online" and 1 -> 1 (int); 0 and 100 -> 0 (int).
## Level 2
5. Combine is_connected with a bounded numeric comparison after checking that the measurement is present.
6. is_connected.
7. denominator != 0 and numerator / denominator > 1.
8. bool(text.strip()), assuming text is a string.
## Level 3
9. Zero may be a valid reading; None means absent.
10. and performs logical truth testing and short-circuits; & combines integer bits and evaluates both operands.
11. and evaluates the right side only if the left is truthy; or evaluates it only if the left is falsy.
12. is tests identity, not string value equality. Use ==.
13. Test just below 10, 10, just above 10, just below 20, 20, and just above 20.
## Knowledge check
1. True and False.
2. Python's true/false test for an object in a Boolean context.
3. False, None, numeric zero, empty strings, empty containers.
4. It is non-empty.
5. A chain combines comparisons and evaluates the shared middle expression once.
6. Evaluation stops when the result is determined.
7. No; and/or return operands.
8. None is a singleton; identity is the intended test.
9. Zero, False, and empty text are also falsy.
10. Boundaries determine whether endpoints are included.
## Lab review
Check None explicitly, allow zero if specified, test endpoints and nearby values, and avoid comparing None numerically.
