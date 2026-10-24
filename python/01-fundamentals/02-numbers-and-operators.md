# Numbers and Operators

**Module:** Programming Fundamentals  
**Lesson:** 2 of 9  
**Level:** Beginner  
**Suggested study time:** 75–90 minutes  
**Prerequisites:** Variables and Data Types (Lesson 1)  
**Study method:** Read one section at a time, predict results before running code, and explain why each result occurs.

## Lesson guide

This lesson builds directly on **Variables and Data Types**. In the previous lesson, you learned that names are bound to objects and that objects have types. Here, you will use numeric objects and operators to perform calculations, compare results, and understand why some numeric results need careful handling.

**Recommended workflow**

1. Review the short connection-to-the-previous-lesson note below.
2. Read one section at a time and type the examples yourself.
3. Predict each result before running the code; then explain any difference.
4. Complete the coding lab and independent practice without looking up solutions first.
5. Use the knowledge check to identify concepts that need another review.

**Purpose:** Learn how Python represents numbers, evaluates arithmetic expressions, compares values, and handles the precision limits of floating-point arithmetic. This lesson combines core language rules with practical measurement calculations.

## Learning objectives

By the end of this lesson, you should be able to:

- Distinguish integers (`int`) from floating-point numbers (`float`).
- Use Python's arithmetic operators correctly.
- Explain the difference between `/`, `//`, and `%`.
- Predict expression results using operator precedence and parentheses.
- Compare values and combine conditions with logical operators.
- Update variables with augmented assignment.
- Recognize floating-point representation limits and choose sensible rounding or formatting.
- Use common numeric tools such as `abs()`, `round()`, and selected functions from `math`.
- Write a small, readable program that calculates statistics from measurements while keeping units clear.

---

## 1. Numeric types

Before choosing an operator, understand the kind of number you are working with. Python's numeric type affects how a value is represented and what result an operation produces. The two everyday numeric types are `int` and `float`.

### Connection to Lesson 1: variables and types

In the previous lesson, you learned to assign values to names and inspect their types with `type()`. Those same ideas apply here:

```python
sample_count = 12
voltage = 3.3

print(sample_count, type(sample_count))
print(voltage, type(voltage))
```

Output:

```text
12 <class 'int'>
3.3 <class 'float'>
```

The names `sample_count` and `voltage` refer to objects; the objects have different types. That difference matters when you calculate with them. For example, dividing two integers with `/` still produces a floating-point result in Python 3. We will examine this and the other arithmetic operators in Section 2.

A practical rule: choose a numeric type that fits the meaning of the data, use readable variable names, and check a value's type when the result surprises you. Type conversion is covered below, but conversion should be deliberate rather than used to hide an unexplained result.

### 1.1 Integers: `int`

An integer represents a whole number without a fractional part.

```python
temperature = 18
number_of_samples = 12
offset = -4
zero = 0

print(type(temperature))  # <class 'int'>
```

Python integers can grow beyond a fixed machine-sized range, subject to available memory. This differs from many lower-level languages, where a particular integer type has a fixed range.

### 1.2 Floating-point numbers: `float`

A float represents a real-number approximation using binary floating-point.

```python
voltage = 3.3
gain = 1.0
temperature_change = -0.25

print(type(voltage))  # <class 'float'>
```

A decimal point makes a numeric literal a float, even when the fractional part is zero: `1.0` is a float, while `1` is an integer.

Floats are useful for measurements, averages, ratios, and many scientific calculations. However, most decimal fractions cannot be represented exactly in binary floating-point. See Section 7.

### 1.3 Numeric literals

Python supports several readable forms:

```python
count = 1_000_000       # Underscores improve readability
small_value = 0.00025
scientific = 2.5e-4     # 2.5 × 10**-4 = 0.00025
large_value = 6.02e23
```

An underscore can separate digits in a numeric literal; it does not change the value. Scientific notation uses `e` or `E` to indicate a power of ten.

### 1.4 Inspecting and converting numeric types

Use `type()` to inspect a value's type. Use `int()` and `float()` when a conversion is appropriate.

```python
reading = 7
reading_as_float = float(reading)  # 7.0
whole_part = int(7.9)              # 7
negative_part = int(-7.9)          # -7
```

**Important:** `int()` truncates a float toward zero; it does not round to the nearest integer. Therefore, `int(7.9)` is `7`, and `int(-7.9)` is `-7`.

A string containing a suitable numeric literal can also be converted:

```python
count = int("25")
voltage = float("3.3")
```

Conversion can fail if the string is not in a valid form for that type. For example, `int("3.3")` raises `ValueError`; convert to `float` first if a decimal value is intended.

---

## 2. Arithmetic operators

Python provides the following common arithmetic operators.

| Operator | Meaning | Example | Result |
| --- | --- | --- | --- |
| `+` | Addition | `12 + 5` | `17` |
| `-` | Subtraction | `12 - 5` | `7` |
| `*` | Multiplication | `12 * 5` | `60` |
| `/` | True division | `12 / 5` | `2.4` |
| `//` | Floor division | `12 // 5` | `2` |
| `%` | Remainder (modulo) | `12 % 5` | `2` |
| `**` | Exponentiation | `2 ** 3` | `8` |

### 2.1 Addition, subtraction, multiplication, and exponentiation

```python
signal_a = 12
signal_b = 5

print(signal_a + signal_b)  # 17
print(signal_a - signal_b)  # 7
print(signal_a * signal_b)  # 60
print(2 ** 3)               # 8
print(9 ** 0.5)             # 3.0
```

The `**` operator means “raise to a power.” For example, `2 ** 3` means 2³, or 2 × 2 × 2.

### 2.2 True division: `/`

The `/` operator performs ordinary division and returns a float, including when the result is mathematically a whole number.

```python
print(12 / 5)  # 2.4
print(12 / 4)  # 3.0
```

Use `/` when you need a quotient that may contain a fractional part, such as an average or a ratio.

### 2.3 Floor division: `//`

Floor division returns the quotient rounded **down toward negative infinity**.

```python
print(12 // 5)    # 2
print(12.0 // 5)  # 2.0
print(-12 // 5)   # -3
```

For positive operands, the result often looks like dropping the fractional part. That shortcut is not generally correct for negative values: `-12 / 5` is `-2.4`, and flooring `-2.4` gives `-3`, not `-2`.

The result type depends on the operands: integer operands produce an integer result, while a float operand can produce a float result.

### 2.4 Modulo: `%`

Modulo returns the remainder associated with floor division.

```python
print(12 % 5)   # 2
print(14 % 7)   # 0
print(9 % 2)    # 1
```

Common uses include checking divisibility and repeating patterns:

```python
number = 18
print(number % 2 == 0)  # True: even numbers have remainder 0
print(number % 5)       # 3
```

For integers, `number % divisor == 0` checks whether the number is divisible by the divisor (assuming the divisor is not zero).

Python's floor-division and modulo results are related by:

```python
a = 12
b = 5

print(a == (a // b) * b + (a % b))  # True
```

For a nonzero divisor, the relationship is `a = (a // b) * b + (a % b)`. The remainder follows the sign of the divisor under Python's modulo rules. For example, `-12 % 5` is `3`.

**Division by zero is invalid:** `/`, `//`, and `%` with a zero divisor raise `ZeroDivisionError`.

---

## 3. Operator precedence and grouping

Python does not simply evaluate every expression from left to right. Operators have precedence rules. Parentheses can make the intended order explicit.

### 3.1 Basic precedence

For the operators introduced here, a useful simplified order from higher to lower precedence is:

1. Parenthesized expressions: `(...)`
2. Exponentiation: `**`
3. Unary plus and minus: `+x`, `-x`
4. Multiplication, true division, floor division, modulo: `*`, `/`, `//`, `%`
5. Addition and subtraction: `+`, `-`
6. Comparisons: `==`, `!=`, `<`, `<=`, `>`, `>=`
7. Logical `not`, then `and`, then `or`

This is a learning aid, not the complete precedence table for every Python operator. Consult the official reference when working with unfamiliar operators.

```python
print(2 + 3 * 4)       # 14
print((2 + 3) * 4)     # 20
print(20 / 5 + 2)      # 6.0
print(2 ** 3 ** 2)     # 512
```

Multiplication happens before addition, so `2 + 3 * 4` is `2 + 12`. Exponentiation groups from right to left, so `2 ** 3 ** 2` is `2 ** (3 ** 2)`, or `2 ** 9`.

Unary operators and exponentiation have a subtle interaction:

```python
print(-2 ** 2)    # -4
print((-2) ** 2)  # 4
```

In the first expression, exponentiation happens before the leading minus. Use parentheses when a negative number is intended as the base.

### 3.2 Same-precedence operators

Many operators at the same precedence level group from left to right:

```python
print(20 / 5 * 2)  # 8.0
print(20 - 5 - 2)  # 13
```

Exponentiation is an important exception because it groups from right to left.

### 3.3 Write for clarity

Even when you know the precedence rules, use parentheses when they make a formula easier to read.

Less explicit:

```python
average = first + second + third / 3
```

Clearer and correct for the average of three values:

```python
average = (first + second + third) / 3
```

Parentheses are not merely cosmetic: they can change the result.

---

## 4. Comparison operators and Boolean results

Comparison operators compare values and produce a Boolean: `True` or `False`.

| Operator | Meaning |
| --- | --- |
| `==` | Equal to |
| `!=` | Not equal to |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |

```python
temperature = 24

print(temperature == 24)  # True
print(temperature != 24)  # False
print(temperature > 20)   # True
print(temperature < 20)   # False
print(temperature >= 24)  # True
print(temperature <= 23)  # False
```

### 4.1 Assignment is not comparison

- `=` assigns or rebinds a name.
- `==` tests value equality.
- `is` tests object identity (whether two references point to the same object).

```python
reading = 10
print(reading == 10)  # True
```

Do not use `is` as a replacement for `==` when comparing numeric values. Use `is None` for the conventional check that a value is `None`.

### 4.2 Chained comparisons

Python allows comparisons to be chained:

```python
temperature = 24
print(20 <= temperature < 30)  # True
```

This means the temperature is at least 20 and less than 30. It is equivalent in meaning to `20 <= temperature and temperature < 30`, except that the middle expression is evaluated only once.

### 4.3 Floating-point comparisons

Exact equality can be unreliable for results produced by floating-point calculations. For a practical tolerance-based comparison, see Section 7. Do not assume that every calculated decimal will equal a decimal literal exactly.

---

## 5. Logical operators

Logical operators combine or invert conditions.

| Operator | Meaning | Example |
| --- | --- | --- |
| `and` | True when both conditions are true | `voltage > 0 and voltage < 5` |
| `or` | True when at least one condition is true | `mode == "A" or mode == "B"` |
| `not` | Inverts truth value | `not is_valid` |

```python
voltage = 3.3
signal_is_present = True

within_range = voltage >= 0 and voltage <= 5
can_process = within_range and signal_is_present

print(within_range)  # True
print(can_process)   # True
print(not signal_is_present)  # False
```

### 5.1 Short-circuit evaluation

Python evaluates logical expressions from left to right and may skip evaluating the second operand when the result is already known:

- In `False and expression`, Python does not need to evaluate `expression`.
- In `True or expression`, Python does not need to evaluate `expression`.

This is called **short-circuit evaluation**. It can help avoid unnecessary work or protect an operation from an invalid input:

```python
divisor = 0
if divisor != 0 and 12 / divisor > 2:
    print("The condition is true")
```

The division is not evaluated because `divisor != 0` is false.

For the most readable beginner code, compare values explicitly and use parentheses when a compound condition becomes difficult to follow.

---

## 6. Augmented assignment

Augmented assignment combines an operation with reassignment.

```python
value = 10

value += 3   # Same numeric effect as value = value + 3
print(value) # 13

value -= 2   # Subtract 2
value *= 4   # Multiply by 4
value /= 2   # True division
print(value) # 22.0
```

Common forms include:

| Form | Numeric meaning |
| --- | --- |
| `x += y` | Add `y` to `x` |
| `x -= y` | Subtract `y` from `x` |
| `x *= y` | Multiply `x` by `y` |
| `x /= y` | Divide `x` by `y` |
| `x //= y` | Floor-divide `x` by `y` |
| `x %= y` | Assign the remainder |
| `x **= y` | Raise `x` to the power `y` |

Augmented assignment is useful for running totals, counters, and iterative calculations. The final type may change: for example, `value /= 2` produces a float for numeric values.

For immutable numeric objects such as integers and floats, these operations produce a result and bind the name to it. Do not infer from the shorthand that an integer object itself is being modified in place.

---

## 7. Floating-point precision

Computers store floats using binary floating-point, not as arbitrary-precision decimal fractions. Some familiar decimal fractions have repeating binary representations, so the stored value is only an approximation.

```python
print(0.1 + 0.2)  # Commonly displays 0.30000000000000004
print(0.1 + 0.2 == 0.3)  # False
```

This is normal floating-point behavior, not a Python arithmetic bug.

### 7.1 Avoid relying on exact float equality

When comparing calculated measurements, use an appropriate tolerance. The tolerance must fit the precision and scale of the problem.

```python
measured = 0.1 + 0.2
expected = 0.3
tolerance = 1e-9

print(abs(measured - expected) < tolerance)  # True
```

For general-purpose numerical comparisons, Python's `math.isclose()` supports relative and absolute tolerances:

```python
import math

print(math.isclose(0.1 + 0.2, 0.3))  # True
```

Default tolerances are not automatically suitable for every engineering problem. Choose tolerances based on units, instrument accuracy, scale, and the requirements of the calculation.

### 7.2 Rounding a value

`round(number, ndigits)` rounds a value to a requested number of decimal places (or to a position to the left of the decimal point when `ndigits` is negative).

```python
print(round(3.14159, 2))  # 3.14
print(round(1234, -2))    # 1200
```

Python's built-in `round()` uses **round half to even** for exact halfway cases: it chooses the nearest even result. For example:

```python
print(round(2.5))  # 2
print(round(3.5))  # 4
```

Because many decimal fractions are not represented exactly as floats, a decimal-looking input may not be an exact halfway value internally.

Rounding is not the same as formatting. Rounding changes the numeric result returned by `round()`; formatting controls how a value is displayed.

### 7.3 Formatting numeric output

F-strings provide convenient control over displayed precision:

```python
measurement = 3.14159265

print(f"{measurement:.2f}")  # 3.14
print(f"{measurement:.4f}")  # 3.1416
```

The `.2f` format displays two digits after the decimal point. It does not change the original variable.

### 7.4 When decimal arithmetic is required

For most measurements, scientific calculations, and general numeric work, `float` is appropriate when its precision is understood. For decimal quantities that require exact decimal behavior—such as many financial calculations—consider the standard-library `decimal.Decimal` type. Construct decimal values from strings when exact decimal input is important:

```python
from decimal import Decimal

price = Decimal("0.10")
tax = Decimal("0.20")
print(price + tax)  # 0.30
```

Do not construct `Decimal` from a float if the intention is to preserve the original decimal text; the float may already contain a binary approximation.

---

## 8. Useful numeric tools

### 8.1 Absolute value: `abs()`

`abs(number)` returns the non-negative magnitude of a number.

```python
print(abs(-8))       # 8
print(abs(3.5 - 5))  # 1.5
```

It is useful for differences, magnitudes, and tolerance checks.

### 8.2 The `round()` built-in

Use `round()` when a rounded numeric value is needed for a calculation or result. Use f-string formatting when only the display needs a fixed number of decimal places. Remember the round-half-to-even rule described above.

### 8.3 Selected functions from `math`

The `math` module supplies mathematical constants and functions for real numbers. Import it before using its members.

```python
import math

print(math.sqrt(81))   # 9.0
print(math.ceil(3.2))  # 4
print(math.floor(3.8)) # 3
print(math.pi)         # Approximately 3.141592653589793
```

- `math.sqrt(x)`: square root of a non-negative real number.
- `math.ceil(x)`: smallest integer greater than or equal to `x`.
- `math.floor(x)`: largest integer less than or equal to `x`.
- `math.pi`: an approximation of the mathematical constant π.

These functions solve different problems. In particular, `math.floor(x)` explicitly returns a floor value, while `int(x)` truncates toward zero; for negative non-integers, those results differ.

---

## 9. Engineering context: measurements, units, and readable calculations

Numeric code can produce a mathematically valid result that is physically meaningless if units are mixed accidentally. Keep track of units in variable names, comments, or documentation.

### 9.1 Use meaningful names

Prefer names that identify what a number represents and, where useful, its unit:

```python
distance_m = 12.5
elapsed_time_s = 2.0
speed_m_per_s = distance_m / elapsed_time_s

print(speed_m_per_s)  # 6.25
```

The names make the units visible. The calculation divides meters by seconds to produce meters per second.

### 9.2 Convert units before combining quantities

For example, convert centimeters to meters before combining a length measured in meters with a length measured in centimeters:

```python
length_m = 1.2
extension_cm = 35
extension_m = extension_cm / 100
total_length_m = length_m + extension_m

print(total_length_m)  # 1.55
```

Never add measurements with incompatible units without converting them first.

### 9.3 Calculate an average and a difference

```python
first_reading_v = 4.8
second_reading_v = 5.2

average_v = (first_reading_v + second_reading_v) / 2
difference_v = abs(first_reading_v - second_reading_v)

print(f"Average: {average_v:.2f} V")
print(f"Absolute difference: {difference_v:.2f} V")
```

Both readings use volts, so their average and difference also use volts. The `abs()` call makes the difference non-negative.

### 9.4 Calculate percentage change carefully

Percentage change compares a new value with a nonzero original value:

```python
original_value = 80
new_value = 92

if original_value != 0:
    percentage_change = (
        (new_value - original_value) / original_value
    ) * 100
    print(f"Percentage change: {percentage_change:.1f}%")
else:
    print("Percentage change is undefined when the original value is zero.")
```

The result is positive for an increase and negative for a decrease. A percentage change relative to zero is undefined, so handle that case explicitly.

---

## 10. Common mistakes

1. **Confusing `/` with `//`.** Use `/` for ordinary division and `//` for floor division.
2. **Assuming floor division always truncates.** For negative values, floor division rounds down toward negative infinity.
3. **Confusing modulo with ordinary division.** `%` returns a remainder; it does not return the quotient.
4. **Ignoring precedence.** `2 + 3 * 4` is `14`, not `20`; use parentheses to express the intended grouping.
5. **Forgetting the average's parentheses.** Divide the sum by the number of readings, not just the final reading.
6. **Expecting every division result to be an integer.** The `/` operator returns a float.
7. **Using `is` for numeric equality.** Use `==` to compare numeric values.
8. **Expecting exact decimal float results.** Binary floating-point cannot represent every decimal fraction exactly.
9. **Treating display formatting as a change to the value.** `f"{value:.2f}"` formats output; it does not reassign a rounded value to `value`.
10. **Using `int()` as if it rounds.** It truncates toward zero.
11. **Dividing by zero.** Check the denominator when zero is possible.
12. **Mixing units.** Convert measurements to compatible units before combining them.
13. **Using unexplained constants.** Give important values meaningful names and document their units or purpose.

---

## 11. Coding lab: Measurement summary

### Goal

Write a small program that receives two measurement values (you may begin with hard-coded values), then calculates their average, signed difference, absolute difference, and percentage change when defined.

### Step 1 — Define the readings

Start with two numeric values in the same unit. Use names that make the unit clear, for example, `first_reading_v` and `second_reading_v`.

### Step 2 — Calculate the average

Use parentheses so that you add the readings before dividing by two.

### Step 3 — Calculate differences

Calculate both:

- **Signed difference:** second reading minus first reading.
- **Absolute difference:** the magnitude of the difference, using `abs()`.

### Step 4 — Calculate percentage change safely

Use the first reading as the original value. Check that it is not zero before dividing. If it is zero, print a clear message instead of attempting the calculation.

### Step 5 — Format the output

Use f-strings to display results with a consistent number of decimal places and include the unit in each relevant label.

### Step 6 — Test your program

Run the program with at least these cases:

- The second reading is greater than the first.
- The second reading is less than the first.
- Both readings are equal.
- The first reading is zero.
- One or both readings contain decimal values.

Check that the average, signs, units, and zero-denominator behavior are all correct. Do not round intermediate values unless the problem requires it; format values for display at the end.

---

## 12. Independent practice

Try each task before running your code. Write down your prediction first, then test it and explain any difference.

### Exercise 1 — Numeric types

Without running Python, predict the type of each expression:

1. `15`
2. `15.0`
3. `15 / 3`
4. `15 // 3`
5. `15 % 4`
6. `2 ** 4`
7. `int(-3.8)`

### Exercise 2 — Arithmetic predictions

Predict the result of each expression and explain the operator used:

1. `17 / 4`
2. `17 // 4`
3. `17 % 4`
4. `-17 // 4`
5. `-17 % 4`
6. `3 ** 2 ** 2`

### Exercise 3 — Parentheses and precedence

Rewrite each expression with parentheses that make the intended calculation explicit, then predict its result:

1. Add 8 and 4, then multiply the sum by 3.
2. Divide 100 by the sum of 5 and 5.
3. Calculate the average of 12, 15, and 18.
4. Square the negative number -3.

### Exercise 4 — Comparisons and logic

Let `x = 12` and `y = 5`. Predict each Boolean result:

1. `x > y`
2. `x == 12`
3. `x != y`
4. `x > 10 and y < 10`
5. `x < 10 or y == 5`
6. `not (x == y)`
7. `10 <= x < 15`

### Exercise 5 — Augmented assignment

Start with `value = 8`. Apply these operations in order and record the value and type after each line:

1. `value += 4`
2. `value *= 2`
3. `value //= 5`
4. `value /= 2`

### Exercise 6 — Floating-point behavior

1. Run `0.1 + 0.2` and compare it with `0.3`.
2. Explain why exact equality may fail.
3. Test `math.isclose(0.1 + 0.2, 0.3)`.
4. Display π to two and six decimal places using f-strings.

### Exercise 7 — Measurement calculator

Write a program that defines two voltages, calculates the average and signed difference, and prints both to two decimal places. Then add the absolute difference and a safe percentage-change calculation.

### Exercise 8 — Explain your choices

In your own words, explain:

1. When should you use `/`, `//`, or `%`?
2. Why is `int(-3.8)` different from `-3.8 // 1`?
3. Why should you avoid exact equality checks for many calculated floats?
4. What can go wrong if two values use different units?
5. When would `Decimal` be a better choice than `float`?

---

## 13. Knowledge check

Answer these without looking back at the notes:

1. What is the difference between `int` and `float`?
2. What are the results of `19 / 4`, `19 // 4`, and `19 % 4`?
3. What does floor division do for negative numbers?
4. Why does `2 + 3 * 4` differ from `(2 + 3) * 4`?
5. What is the difference between `=`, `==`, and `is`?
6. What is short-circuit evaluation, and how can it prevent division by zero?
7. Why can `0.1 + 0.2 == 0.3` be false?
8. What is the difference between `round(value, 2)` and `f"{value:.2f}"`?
9. Why should a percentage-change calculation check whether the original value is zero?
10. How can variable names and unit conversions make engineering calculations safer?

---

## 14. Summary

- `int` represents integers; `float` represents binary floating-point approximations.
- `+`, `-`, `*`, and `**` perform addition, subtraction, multiplication, and exponentiation.
- `/` performs true division; `//` performs floor division; `%` returns a remainder.
- Floor division rounds toward negative infinity, which matters for negative operands.
- Operator precedence controls evaluation order; parentheses improve clarity and can change results.
- Comparisons produce Boolean results; `and`, `or`, and `not` combine or invert conditions.
- Augmented assignment offers concise ways to update a numeric variable.
- Floating-point values have finite precision. Use tolerances for numerical comparisons when appropriate.
- Use `round()` for a rounded numeric result and formatting for display.
- Use `abs()` and selected `math` functions when they fit the problem.
- Name measurements clearly, keep units consistent, and guard against invalid operations such as division by zero.

## References

- [The Python Tutorial — Numbers](https://docs.python.org/3/tutorial/introduction.html#numbers)
- [The Python Tutorial — More on Control Flow Tools (comparisons and Boolean operations)](https://docs.python.org/3/tutorial/controlflow.html)
- [Built-in Types — Numeric Types](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)
- [Built-in Functions — `round()`, `abs()`, `int()`, and `float()`](https://docs.python.org/3/library/functions.html)
- [math — Mathematical functions](https://docs.python.org/3/library/math.html)
- [decimal — Decimal fixed-point and floating-point arithmetic](https://docs.python.org/3/library/decimal.html)
- [Floating-Point Arithmetic: Issues and Limitations](https://docs.python.org/3/tutorial/floatingpoint.html)
