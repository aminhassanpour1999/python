# Variables and Data Types

**Module:** Programming Fundamentals  
**Lesson:** 1 of 9  
**Level:** Beginner  
**Suggested study time:** 60–75 minutes  
**Prerequisites:** Introduction module completed  
**Study method:** Read each section, predict outputs before running code, then complete the exercises

## Lesson guide

This lesson introduces the names Python uses to refer to values, the basic data types you will encounter, and simple ways to inspect and compare values. You do not need to memorize every example. Focus on explaining what each line does and predicting the result before running it.

**Recommended workflow**

1. Read one section at a time.
2. Type the examples yourself and predict their output before running them.
3. Change a value or a name and observe what changes.
4. Complete the coding lab and exercises without looking at the answer key.
5. Revisit any question you cannot explain in your own words.

## Learning objectives

By the end of this lesson, you should be able to:

- Explain the relationship between a value, an object, a name, and assignment.
- Create variables and reassign names to new values.
- Follow Python's identifier rules and use readable snake_case names.
- Recognize the built-in types `int`, `float`, `complex`, `str`, `bool`, and `NoneType`, and distinguish the introductory overview here from the detailed numeric treatment in Lesson 2.
- Use type() to inspect an object's type.
- Distinguish assignment (=), value equality (==), and object identity (is).
- Predict short assignment sequences and diagnose common beginner mistakes.

## 1. Values, objects, and names

Programs need to remember information so they can use it later. For example, a communications program might store a measured signal level, a frequency, or the name of a modulation scheme.

```python
temperature = 42
print(temperature)
```

Output:

```text
42
```

In this example:

- `temperature` is a **name** (the identifier written in the code).
- The name is bound to an **integer object** whose **value** is `42` and whose type is `int`.
- `=` performs assignment: Python evaluates the right-hand side (`42`) and binds the name on the left (`temperature`) to the resulting object.
- `print()` displays the value associated with the name; it does not display the object's type unless you ask for it.

These terms are related but not interchangeable:

- A **name** is how your code refers to an object.
- An **object** is a runtime entity Python works with. Every object has an identity, a type, and a value.
- A **value** is the information represented by the object—for example, the integer value `42`.

In beginner examples, people sometimes use *value* and *object* informally as if they were the same thing. The useful mental model is that a name is bound to an object, and that object has a value and a type. A variable is not a permanent box that owns a fixed type.

A name does not permanently belong to one value. A later assignment can bind the same name to a different object.

```python
temperature = 42
print(temperature)

temperature = 45
print(temperature)
```

Output:

```text
42
45
```

After the second assignment, the name `temperature` refers to the new integer object representing `45`.

### Assignment creates or updates a name binding

Consider this sequence:

```python
x = 10
y = x
x = 20

print(x)
print(y)
```

Output:

```text
20
10
```

Read it line by line:

1. `x = 10` binds the name `x` to the integer object representing `10`.
2. `y = x` evaluates the right-hand expression. Its current value is `10`, so `y` is bound to that same object at this point.
3. `x = 20` rebinds `x` to the integer object representing `20`. It does not automatically change `y`.

**Key idea:** Python evaluates the right-hand side of an assignment and then binds the target name to the resulting object. Reassigning one name does not automatically reassign other names.

## 2. Assignment and reassignment

The assignment operator is a single equals sign: `=`.

```python
frequency_hz = 100_000
frequency_hz = 200_000
```

The second statement reassigns `frequency_hz`. Underscores in numeric literals make long numbers easier to read; 100_000 has the same numeric value as 100000.

### The right-hand side is evaluated first

```python
count = 5
count = count + 1
print(count)
```

Output:

```text
6
```

Although `count = count + 1` may look unusual in ordinary algebra, it is valid programming syntax. Python first evaluates the right-hand expression using the current value of `count` (`5 + 1`), then assigns the result (`6`) to `count`.

Python also provides an augmented assignment form:

```python
count = 5
count += 1
print(count)
```

Output:

```text
6
```

For numeric values, `count += 1` is a concise way to add one and assign the result back to count. We will study operators in more detail in the next lesson.

### Assignment is not mathematical equality

Do not confuse these three operators:

| Syntax | Meaning | Example |
|---|---|---|
| = | Assign a value to a target name | score = 90 |
| == | Test whether two values are equal | score == 90 |
| is | Test whether two references point to the same object | value is None |

The expression `score == 90` asks a question and produces a Boolean result (`True` or `False`). By itself, it does not assign `90` to `score`.

```python
score = 90
print(score == 90)
```

Output:

```text
True
```

## 3. Naming rules and conventions

Names help people understand what a program means. A good name is clear, specific, and consistent.

### Rules for valid identifiers

A Python identifier (a name used for a variable, function, or other program element) must follow these rules:

- It may contain letters, digits, and underscores (`_`).
- It cannot begin with a digit.
- It cannot contain spaces or punctuation such as hyphens.
- It is case-sensitive: `signal`, `Signal`, and `SIGNAL` are different names.
- It cannot be a reserved Python keyword such as `if`, `for`, or `class`.

Valid examples:

```python
temperature = 25
signal_level = -12.5
measurement2 = 18
_private_value = 7
```

Invalid examples (each line is invalid syntax):

```python
2nd_measurement = 18
signal level = -12.5
signal-level = -12.5
```

The first name starts with a digit, the second contains a space, and the third uses a hyphen. In Python, a hyphen is the subtraction operator, not part of an identifier.

### Use snake_case

Python's common convention for variable and function names is **lowercase words separated by underscores**, called `snake_case`.

Prefer:

```python
sample_rate = 48_000
average_temperature = 23.5
device_name = "receiver_01"
```

Avoid unclear or unnecessarily abbreviated names:

```python
sr = 48000
at = 23.5
dn = "receiver_01"
```

Short names such as x and y are fine in small mathematical examples. In a real program, choose names that make the code easier to understand.

### Avoid shadowing built-in names

Do not use names such as list, str, type, or print for your own variables. These names refer to useful Python built-ins. Reusing them can make those built-ins harder to access and can cause confusing errors.

Avoid:

```python
list = [1, 2, 3]
type = "temperature"
```

Prefer:

```python
measurements = [1, 2, 3]
measurement_type = "temperature"
```

### Keywords and checking names

Python keywords have special syntactic meaning. You can inspect the interpreter's keyword list with the standard-library `keyword` module:

```python
import keyword

print(keyword.iskeyword("if"))
print(keyword.iskeyword("temperature"))
```

Output:

```text
True
False
```

This module is not needed for everyday variable declarations, but it helps explain why some names cannot be used as identifiers.

## 4. Core built-in data types

A **data type** describes the kind of value an object represents and helps determine which operations are meaningful for it. Python has many built-in types. This lesson introduces `int`, `float`, `complex`, `str`, `bool`, and `NoneType`. The complex type receives a short introduction here; Lesson 2 develops complex-number arithmetic and its practical uses in more detail.

These are the types of the example values in this lesson, not a complete list of Python's types. Lists, dictionaries, tuples, sets, and other types will be introduced when the course reaches them. The dedicated **Booleans and None** lesson will explore Boolean logic and truth-value testing in more depth.

### 4.1 Integers: int

An integer represents a whole number without a decimal point.

```python
transmitter_count = 3
temperature_offset = -2
number_of_samples = 1_000_000

print(transmitter_count)
print(type(transmitter_count))
```

Output:

```text
3
<class 'int'>
```

Python integers can represent very large whole numbers, limited in practice by available memory. Use underscores rather than commas to group digits in a numeric literal, for example `1_000_000`.

### 4.2 Floating-point numbers: float

A float represents a number using floating-point arithmetic. Floats are commonly used for measurements and values with fractional parts.

```python
frequency_mhz = 99.5
temperature_c = 21.75
gain_db = -3.0

print(frequency_mhz)
print(type(frequency_mhz))
```

Output:

```text
99.5
<class 'float'>
```

A number written with a decimal point is normally a float, even if its fractional part is zero: -3.0 is a float, while -3 is an integer.

**Important:** floating-point numbers use a finite binary representation. Some decimal fractions cannot be represented exactly, so calculations may produce tiny rounding differences. We will examine numeric operations and precision in the next lesson.

### 4.3 Complex numbers: complex

Python also has a built-in numeric type called `complex`. A complex number has a real part and an imaginary part. Python uses `j` to write the imaginary unit, where \(j^2 = -1\).

~~~python
impedance = 3 + 4j

print(impedance)
print(type(impedance))
print(impedance.real)
print(impedance.imag)
~~~

Output:

~~~text
(3+4j)
<class 'complex'>
3.0
4.0
~~~

The `.real` and `.imag` attributes expose the real and imaginary parts as floating-point values. The `j` notation is Python's convention; in mathematics and electrical engineering, the imaginary unit is often written as `i` or `j`. Complex values are useful in areas such as AC circuit analysis and signal processing. Their arithmetic, magnitude, and related functions are covered in **Numbers and Operators**.

A value such as `3` has type `int`, `3.0` has type `float`, and `3 + 0j` has type `complex`. They may represent closely related mathematical quantities, but they are objects of different types.

### 4.4 Strings: str

A string represents text. String literals can be written with single or double quotes.

```python
device_name = "receiver_01"
modulation = 'QPSK'
message = "Signal received"

print(device_name)
print(type(device_name))
```

Output:

```text
receiver_01
<class 'str'>
```

The quote characters mark the beginning and end of the string; they are not part of the displayed text.

A string containing digits is still text:

```python
frequency_text = "2400"
frequency_number = 2400

print(type(frequency_text))
print(type(frequency_number))
```

Output:

```text
<class 'str'>
<class 'int'>
```

The string `"2400"` and the integer `2400` may look similar when printed, but they have different types. Python does not automatically treat every string of digits as a number. Converting between types is a separate topic in Lesson 4, **Type Conversion**.

### 4.5 Booleans: bool

A Boolean represents one of two truth values: True or False. Boolean values are often used for yes/no conditions and status flags.

```python
is_connected = True
error_detected = False

print(is_connected)
print(type(is_connected))
```

Output:

```text
True
<class 'bool'>
```

Capitalize the first letter exactly as shown: `True` and `False`. The lowercase names true and false are not Python Boolean literals.

We will study comparisons, truthiness, and Boolean logic more thoroughly in the lesson on **Booleans and None**.

### 4.6 The absence of a value: None

Python uses the special value `None` to represent the absence of a value or a value that has not been provided.

```python
measurement = None

print(measurement)
print(type(measurement))
```

Output:

```text
None
<class 'NoneType'>
```

Notice the distinction:

- `None` is the special value.
- `NoneType` is the name of its type.

Use `None` when it meaningfully represents “no value available yet.” It is not the same as zero (`0`), an empty string (`""`), or `False`; those values have different meanings and types.

To check specifically whether a value is None, use identity:

```python
measurement = None

if measurement is None:
    print("No measurement is available.")
```

Output:

```text
No measurement is available.
```

The if statement is a preview; control flow will be studied later.

## 5. Inspecting values with type()

The built-in `type()` function reports the type of an object.

```python
count = 4
level = -8.5
label = "RSSI"
is_valid = True
result = None

print(type(count))
print(type(level))
print(type(label))
print(type(is_valid))
print(type(result))
```

Output:

```text
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
<class 'NoneType'>
```

The output uses Python's class notation, for example `<class 'int'>`. At this stage, focus on recognizing the type name inside the angle brackets.

### A useful inspection pattern

When you are unsure what a variable contains, print both its value and its type:

```python
sample_count = 250
print(sample_count)
print(type(sample_count))
```

This is a simple debugging technique. It is especially useful when data comes from a user, a file, a sensor, or another system, because the value may not have the type you expected.

### Names do not have a permanent type

Python is **dynamically typed**: a name can be rebound to objects of different types at different points in a program.

```python
value = 10
print(value, type(value))

value = "ten"
print(value, type(value))
```

Output:

```text
10 <class 'int'>
ten <class 'str'>
```

The integer object did not turn into a string. The name `value` was rebound to a different object whose type is `str`.

This flexibility is useful, but reusing a name for unrelated kinds of data can make a program confusing. Choose names and assignments that keep the program easy to reason about.

## 6. Equality (==) versus identity (is)

These operators answer different questions:

- **Equality (`==`)** asks whether two objects have equal values.
- **Identity (`is`)** asks whether two references point to the very same object.

For ordinary value comparisons, use ==:

```python
first_reading = 25
second_reading = 25

print(first_reading == second_reading)
```

Output:

```text
True
```

To check whether a value is None, use is None:

```python
reading = None
print(reading is None)
```

Output:

```text
True
```

Do not use `is` as a general replacement for `==`. Python may reuse some objects internally, so identity results for values such as small integers or strings should not be used to decide whether their values are equal.

Practical rule:

- Compare ordinary values with `==`.
- Check for the special value `None` with `is None` (or `is not None`).

## 7. Common beginner mistakes

### Mistake 1: Using a name before assigning it

```python
print(temperature)
```

If no binding for `temperature` exists in the current scope, Python raises a `NameError`.

Fix:

```python
temperature = 22.5
print(temperature)
```

### Mistake 2: Misspelling a variable name

```python
sample_rate = 48_000
print(smaple_rate)
```

The two names are different. Python does not automatically correct spelling mistakes, so this normally raises a `NameError`.

Fix:

```python
sample_rate = 48_000
print(sample_rate)
```

### Mistake 3: Assuming assignment changes every related name

```python
a = 3
b = a
a = 7

print(a, b)
```

Output:

```text
7 3
```

Reassigning `a` does not reassign `b`.

### Mistake 4: Confusing text with a number

```python
age_text = "27"
age_number = 27

print(type(age_text))
print(type(age_number))
```

The first value is a string; the second is an integer. If a calculation requires a number, the string must be converted appropriately. We will learn explicit conversion in Lesson 4.

### Mistake 5: Using an invalid variable name

Names cannot start with a digit or contain spaces and hyphens. Use sample_2, not 2sample; use signal_level, not signal-level.

### Mistake 6: Overwriting a built-in name

Avoid assignments such as str = "hello" or type = 5. Choose names such as message or measurement_type instead.

### Mistake 7: Using is for ordinary value comparisons

Use `count == 3` to check whether the value of `count` equals three. Reserve identity checks for cases where object identity matters, especially `value is None`.

## 8. Coding lab: Measurement summary

**Goal:** Create a small, readable summary of two measurements, inspect their types, and observe reassignment.

### Step 1 — Create the variables

Type this code yourself rather than copying it without reading:

```python
measurement_1 = 18.5
measurement_2 = 21.0
unit = "degrees Celsius"

print("First measurement:", measurement_1)
print("Second measurement:", measurement_2)
print("Unit:", unit)
```

### Step 2 — Inspect the types

Add these lines to the end of your program:

```python
print(type(measurement_1))
print(type(measurement_2))
print(type(unit))
```

Before running the program, predict the three type names.

### Step 3 — Calculate an average

Add:

```python
average = (measurement_1 + measurement_2) / 2
print("Average:", average)
print("Average type:", type(average))
```

The average is calculated from the two measurements. Notice that the division operator `/` produces a floating-point result in Python 3, even when the result is mathematically a whole number.

### Step 4 — Reassign one variable

Add:

```python
measurement_1 = 20.0
print("Updated first measurement:", measurement_1)
print("Previously calculated average:", average)
```

**Think before running:** Does `average` automatically change when `measurement_1` is reassigned? Explain why. If you want a new average, you must calculate and assign it again.

At this point, `average` still contains the result calculated from `18.5` and `21.0`, which is `19.75`. Reassigning `measurement_1` does not rerun the earlier calculation.

### Step 5 — Recalculate the average

Now explicitly calculate the average again by adding these lines:

```python
average = (measurement_1 + measurement_2) / 2
print("New average:", average)
```

Expected output for the new average:

```text
New average: 20.5
```

The distinction is important: changing `measurement_1` does not automatically update `average`; running the assignment to `average` again performs a new calculation using the current measurement values.

### Lab checklist

- [ ] I typed and ran the program.
- [ ] I predicted the types before checking them.
- [ ] I explained why the average does not update automatically.
- [ ] I changed one measurement and recalculated the average myself.
- [ ] I verified that the old average stayed at `19.75` until I recalculated it, and that the new average became `20.5`.

## 9. Exercises

Try these without looking at the answers. Write down your predictions first, then run the code to check them.

### Exercise 1 — Identify the types

For each assignment, name the type of the assigned value. Remember that `complex` is introduced briefly in this lesson and explored in more detail in Numbers and Operators.

```python
a = 12
b = 12.0
c = "12"
d = False
e = None
f = 3 + 4j
```

### Exercise 2 — Predict the output

```python
power_db = -4
saved_power = power_db
power_db = -7

print(power_db)
print(saved_power)
print(power_db == saved_power)
```

Write all three output lines in order and explain the final Boolean result.

### Exercise 3 — Repair the names

Each line below contains an invalid identifier. Rewrite each as a valid, readable variable name.

- `2nd_reading = 15`
- `signal level = -9.2`
- `average-value = 3.5`

### Exercise 4 — Explain the difference

In your own words, explain why `"25"` and `25` are different even though they look similar when printed.

### Exercise 5 — Inspect and reassign

Write a short program that:

1. Assigns the integer `100` to `sample_count`.
2. Prints its value and type.
3. Reassigns `sample_count` to the string `"one hundred"`.
4. Prints its new value and type.

### Exercise 6 — Equality and identity

Choose the correct operator for each task and explain your choice:

1. Check whether `status` has the same value as `"ready"`.
2. Check whether `result is None`.

## 10. Knowledge check

Answer these from memory before moving on:

1. What is the difference between a name and the object it refers to?
2. What happens when a name is assigned a new value?
3. Why does y remain 10 after x is reassigned to 20 in the earlier example?
4. Which six types are introduced in this lesson? Name them and give an example of a value for each.
5. How can you inspect the type of a value?
6. How do =, ==, and is differ?
7. Why should you avoid naming a variable list, str, or print?
8. Why is "2400" not an integer?

You are ready to move on when you can answer these questions clearly and complete the exercises without relying on memorized output.

## Answer key

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

## Summary

- A variable name is bound to an object; it is not a permanently typed box.
- Assignment (=) binds or rebinds a name to the result of an expression.
- Reassigning one name does not automatically reassign other names.
- Follow readable naming conventions, especially snake_case, and avoid shadowing built-ins.
- The types introduced here are `int`, `float`, `complex`, `str`, `bool`, and `NoneType`; complex-number arithmetic is developed further in Lesson 2.
- Use type() to inspect an object's type.
- Use == for value equality and is None to check for None.

## Completion criteria

Before moving to Lesson 2, make sure you can do all of the following without copying the examples:

- [ ] Explain assignment and reassignment using your own words.
- [ ] Correctly identify `int`, `float`, `complex`, `str`, `bool`, and `NoneType` values.
- [ ] Choose readable, valid variable names.
- [ ] Predict the output of the exercises and explain why.
- [ ] Explain when to use `==` and when to use `is None`.

You do not need to get every exercise right on the first attempt. Fix your mistakes and make sure you understand the reason for each correction. Reading this file is not, by itself, evidence that you have mastered the lesson; use the completion criteria below to check what you can do independently.

## Official references

- [Python Tutorial — An Informal Introduction to Python](https://docs.python.org/3/tutorial/introduction.html)
- [Python Standard Library — Built-in Types](https://docs.python.org/3/library/stdtypes.html)
- [Python Standard Library — Built-in Functions (type)](https://docs.python.org/3/library/functions.html#type)
- [Python Language Reference — Identifiers and Keywords](https://docs.python.org/3/reference/lexical_analysis.html#identifiers)
- [PEP 8 — Style Guide for Python Code](https://peps.python.org/pep-0008/)
