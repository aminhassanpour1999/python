# Variables and Data Types — Exercise Solutions

**Open only after attempting the lesson.** Equivalent correct reasoning is acceptable.

## Exercise solutions

Use this only after attempting the exercises.

### Exercise 1

- a: int
- b: float
- c: str
- d: bool
- e: NoneType
- f: complex

### Exercise 2

```text
-7
-4
False
```

`saved_power` keeps the value assigned when `power_db` was `-4`. After reassignment, `-7` and `-4` are not equal.

### Exercise 3

Possible answers:

```python
second_reading = 15
signal_level = -9.2
average_value = 3.5
```

Other valid, readable identifiers are acceptable.

### Exercise 4

"25" is a string containing two text characters; 25 is an integer. They have different types, and Python does not automatically treat the string as a number in arithmetic.

### Exercise 5

One valid solution:

```python
sample_count = 100
print(sample_count, type(sample_count))

sample_count = "one hundred"
print(sample_count, type(sample_count))
```

### Exercise 6

1. Use `status == "ready"` to compare values.
2. Use `result is None` to check whether the name `result` is bound to the special singleton object `None`.

### Knowledge check — Suggested answers

Use these only after answering the questions from memory.

1. A **name** is an identifier in code that refers to an object. An **object** is a runtime entity with an identity, a type, and a value. For example, in `temperature = 42`, `temperature` is the name and it is bound to an integer object whose value is `42`.
2. Python evaluates the right-hand expression and binds the target name to the resulting object. Reassignment changes which object the name refers to; it does not automatically update other names.
3. `y = x` binds `y` to the object that `x` refers to at that moment. Reassigning `x` later does not rerun `y = x`, so `y` remains bound to the original integer object for `10`.
4. `int`, `float`, `complex`, `str`, `bool`, and `NoneType`. Examples include `12`, `12.0`, `3 + 4j`, `"12"`, `False`, and `None`, respectively.
5. Call `type(value)`, for example `type(12)` returns `<class 'int'>`.
6. `=` assigns or rebinds a name; `==` tests value equality; `is` tests object identity. In ordinary code, compare values with `==` and check for `None` with `is None`.
7. They are names of built-in types or functions. Reusing them for variables shadows the built-ins and can make later code confusing or break calls such as `str(12)` or `list(items)`.
8. The quotation marks make `"2400"` a string literal (`str`). The unquoted literal `2400` is an integer (`int`). Similar printed appearance does not make their types or behavior the same.

