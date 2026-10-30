# Numbers and Operators

**Module:** Programming Fundamentals  
**Lesson:** 2 of 9  
**Level:** Beginner  
**Suggested study time:** 75–90 minutes  
**Prerequisites:** Variables and Data Types (Lesson 1)  
**Study method:** Read one section at a time, predict results before running code, explain why each result occurs, and use the answer key only after an independent attempt.

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

- Distinguish integers (`int`), floating-point numbers (`float`), and complex numbers (`complex`).
- Use Python's arithmetic operators correctly.
- Explain the difference between `/`, `//`, and `%`.
- Predict expression results using precedence and associativity, and consult the complete official precedence table.
- Use all six bitwise operators (`&`, `|`, `^`, `~`, `<<`, `>>`) for integer bit operations and simple masks.
- Choose among common numeric built-ins and the `math`, `cmath`, `decimal`, and `fractions` modules.
- Compare values and combine conditions with logical operators.
- Update variables with augmented assignment.
- Recognize floating-point representation limits and choose sensible rounding or formatting.
- Use common numeric tools such as `abs()`, `round()`, `pow()`, `divmod()`, `min()`, `max()`, `sum()`, and selected functions from `math`.
- Explain when `cmath`, `decimal.Decimal`, or `fractions.Fraction` is appropriate.
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


### 1.5 Complex numbers: `complex`

A complex number has a real part and an imaginary part. Python uses `j` (not `i`) for the imaginary unit, where `j ** 2 == -1`.

```python
z = 3 + 4j
print(z)           # (3+4j)
print(type(z))     # <class 'complex'>
print(z.real)      # 3.0
print(z.imag)      # 4.0
print(abs(z))      # 5.0: magnitude
print(z.conjugate())  # (3-4j)
```

The real and imaginary parts are exposed as read-only numeric attributes. `abs(z)` gives the magnitude \\(\sqrt{a^2+b^2}\\) for `z = a + bj`; `z.conjugate()` changes the sign of the imaginary part.

Complex numbers support arithmetic such as addition, subtraction, multiplication, division, and exponentiation:

```python
first = 2 + 3j
second = 1 - 1j

print(first + second)  # (3+2j)
print(first * second)  # (5+1j)
print(first / second)  # (-0.5+2.5j)
```

Python does **not** define ordinary ordering comparisons between complex numbers: expressions such as `z < 2` raise `TypeError`. Equality (`==`) is supported. If a task needs ordering, compare a meaningful quantity such as the magnitude with `abs(z)`, provided that is what the problem requires.

For complex-valued mathematical functions, use `cmath`, not `math`. The `math` module is designed for real-valued functions and generally rejects complex arguments.


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

The `/` operator performs true division. With `int` and `float` operands, it returns a `float`, including when the result is mathematically a whole number. If a complex operand is involved, the result is complex.

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

For integer operands and a nonzero divisor, the relationship is exact: `a = (a // b) * b + (a % b)`. With floating-point operands, rounding can introduce tiny differences, so do not treat this identity as an exact-equality guarantee for every `float` calculation. The remainder follows the sign of the divisor under Python's modulo rules. For example, `-12 % 5` is `3`.

**Division by zero is invalid:** `/`, `//`, and `%` with a zero divisor raise `ZeroDivisionError`.


### 2.5 Bitwise operators (integer bit operations)

Bitwise operators work on the binary representation of integers. They are useful for flags, masks, packed fields, and low-level protocols; they are not a replacement for ordinary arithmetic on fractional measurements.

| Operator | Name | Example | Result |
| --- | --- | --- | --- |
| `&` | bitwise AND | `0b1100 & 0b1010` | `8` (`0b1000`) |
| `|` | bitwise OR | `0b1100 | 0b1010` | `14` (`0b1110`) |
| `^` | bitwise XOR | `0b1100 ^ 0b1010` | `6` (`0b0110`) |
| `~` | bitwise NOT / inversion | `~5` | `-6` |
| `<<` | left shift | `5 << 1` | `10` |
| `>>` | right shift | `5 >> 1` | `2` |

Python's `0b` prefix writes an integer literal in binary. These operators return integers.

```python
a = 0b1100  # 12
b = 0b1010  # 10

print(a & b)   # 8
print(a | b)   # 14
print(a ^ b)   # 6
print(5 << 1)  # 10
print(5 >> 1)  # 2
```

#### Bit masks and flags

A mask selects or changes particular bits. For example, the lowest bit can be tested with `value & 1`:

```python
value = 13  # binary 1101
print(value & 1)  # 1: the lowest bit is set (odd)
print(value & 2)  # 0: the bit represented by 2 is not set
```

For a flag represented by one bit, use AND to test it and OR to set it:

```python
RECEIVE_ENABLED = 0b0001
TRANSMIT_ENABLED = 0b0010

flags = RECEIVE_ENABLED
print(bool(flags & RECEIVE_ENABLED))  # True

flags |= TRANSMIT_ENABLED             # Set the transmit flag
print(flags)                          # 3
flags &= ~TRANSMIT_ENABLED            # Clear the transmit flag
print(flags)                          # 1
```

#### Important details: inversion and shifts

For Python integers, `~x == -x - 1`. Python integers behave as if they had an unbounded two's-complement representation for these operations, so `~5` is `-6`, not a positive fixed-width bit pattern. To display a fixed-width pattern, explicitly mask it, for example `(~x) & 0xff` for the low eight bits.

Left shift by `n` corresponds to multiplication by `2**n` for non-negative integer `n`. Right shift by `n` is floor division by `2**n`; for negative integers, this rounds toward negative infinity. A negative shift count raises `ValueError`.

```python
print(3 << 2)    # 12
print(12 >> 2)   # 3
print(-3 >> 1)   # -2
print(~5)        # -6
print((~5) & 0xff)  # 250: low eight bits only
```

Do not use bitwise `&` or `|` as if they were Boolean `and` or `or`. Boolean operators work with truth values and short-circuit; bitwise operators work on integer bits (and can also be overloaded by other types).


---

## 3. Operator precedence and grouping

Precedence determines which operator binds more tightly. Associativity determines grouping when operators at the same precedence level occur together. Parentheses can make intent explicit and override the normal grouping.

### 3.1 Common precedence levels used in this lesson

From higher precedence to lower precedence, the main groups taught here are:

1. Parentheses used for grouping, function calls, attribute access, and indexing.
2. Exponentiation: `**` (right-associative; see the unary-sign caveat below).
3. Unary numeric operators: `+x`, `-x`, and bitwise inversion `~x`.
4. Multiplication, true division, floor division, and modulo: `*`, `/`, `//`, `%`.
5. Addition and subtraction: `+`, `-`.
6. Shifts: `<<`, `>>`.
7. Bitwise AND: `&`.
8. Bitwise XOR: `^`.
9. Bitwise OR: `|`.
10. Comparisons, including `<`, `<=`, `>`, `>=`, `==`, `!=`, `is`, `is not`, `in`, and `not in`.
11. Boolean `not`.
12. Boolean `and`.
13. Boolean `or`.

This is a focused guide to the operators taught in this lesson, not the complete language table. The full table also includes constructs such as conditional expressions, `lambda`, assignment expressions, and syntax introduced in later lessons.

**Official complete reference:** [Python Language Reference — Operator precedence](https://docs.python.org/3/reference/expressions.html#operator-precedence).

### 3.2 Associativity and edge cases

Exponentiation groups from right to left:

```python
print(2 ** 3 ** 2)    # 512, equivalent to 2 ** (3 ** 2)
```

The unary sign on the right of exponentiation has a special relationship with `**`:

```python
print(-3 ** 2)        # -9: interpreted as -(3 ** 2)
print((-3) ** 2)      # 9
print(2 ** -2)        # 0.25
```

Most arithmetic operators at the same level group from left to right:

```python
print(20 / 5 * 2)     # 8.0: (20 / 5) * 2
print(20 - 5 - 2)     # 13: (20 - 5) - 2
```

Comparisons can be chained:

```python
x = 12
print(10 <= x < 15)   # True
```

A chained comparison behaves like comparisons joined with `and`, with each middle expression evaluated only once. Do not confuse this with bitwise operators, whose precedence is different.

### 3.3 Write for clarity

Even when precedence is known, parentheses can help readers understand a formula:

```python
average = (reading_1 + reading_2 + reading_3) / 3
percentage_change = ((new_value - old_value) / old_value) * 100
```

Use parentheses when they clarify the intended calculation. Do not add them mechanically to every expression; aim for readable, conventional code.


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


### 8.4 Quotients and remainders together: `divmod()`

`divmod(a, b)` returns a pair `(a // b, a % b)`. It is useful when both the quotient and remainder are needed.

```python
quotient, remainder = divmod(17, 5)
print(quotient, remainder)  # 3 2
```

It follows Python's floor-division and modulo rules, including for negative operands. Division by zero raises `ZeroDivisionError`.

### 8.5 Powers and aggregate functions: `pow()`, `min()`, `max()`, and `sum()`

```python
print(pow(2, 5))            # 32; equivalent to 2 ** 5
print(min(4, -2, 9))        # -2
print(max(4, -2, 9))        # 9
print(sum([2, 3, 5]))       # 10
```

- `pow(base, exponent)` calculates exponentiation; for ordinary two-argument use, it is equivalent to `base ** exponent`. A three-argument form, `pow(base, exponent, modulus)`, computes modular exponentiation efficiently for integer arguments.
- `min()` returns the smallest item, and `max()` the largest item, among the supplied arguments or in an iterable.
- `sum(iterable, start=0)` adds items from an iterable. It is suitable for numeric totals; do not use it to join strings.

### 8.6 Choosing a suitable numeric tool

Python's standard library offers different numeric models for different needs:

- **`float` and `math`:** default choices for many measurements, ratios, and real-valued calculations when finite binary precision is acceptable. Use `math.isclose()` to compare calculated floats with a suitable tolerance.
- **`complex` and `cmath`:** use complex numbers for values with real and imaginary parts; `cmath` provides complex-valued functions such as square roots and phase-related operations.
- **`decimal.Decimal`:** useful when decimal arithmetic and decimal rounding rules matter, such as financial amounts. Construct from strings (for example, `Decimal("0.10")`) when preserving the intended decimal input matters.
- **`fractions.Fraction`:** represents rational numbers as exact ratios of integers, useful when exact fractions are important and values can be represented as ratios. Construct from integers or strings such as `Fraction("1/10")` to avoid importing a float approximation.

```python
import cmath
from fractions import Fraction
from decimal import Decimal

print(cmath.sqrt(-1))            # 1j
print(Fraction("1/3") + Fraction("1/6"))  # 1/2
print(Decimal("0.10") + Decimal("0.20")) # 0.30
```

These types are not interchangeable in every operation. Choose based on the meaning and precision requirements of the problem, and consult the linked documentation for their rules and limitations.

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
6. **Assuming `/` always returns a float.** For `int` and `float` operands it returns a float; with complex operands, true division returns a complex result.
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

### Step 7 — Numeric-tool mini-experiments

In a separate short script, try these small experiments and explain the output:

- Use `divmod(17, 5)` and verify the quotient and remainder.
- Use `min()`, `max()`, and `sum()` on a short list of measurements.
- Calculate `abs(3 + 4j)` and inspect the real part, imaginary part, and conjugate of the complex number.
- Use a bit mask to test whether the lowest bit of an integer is set.
- Compare `0.1 + 0.2`, `Decimal("0.1") + Decimal("0.2")`, and `Fraction("1/10") + Fraction("2/10")`.

Use these as short demonstrations; the independent exercises below require you to apply the ideas without a worked template.

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

### Exercise 9 — Complex numbers

Without running the code first, predict the results and explain each one:

1. `z = 3 + 4j`; what are `z.real`, `z.imag`, and `abs(z)`?
2. What does `z.conjugate()` return?
3. Why does `z < 5` raise `TypeError`, while `z == 3 + 4j` is valid?
4. Which module would you choose for a complex square root: `math` or `cmath`?

### Exercise 10 — Bitwise operators and masks

1. Convert decimal 12 and 10 to binary, then predict `12 & 10`, `12 | 10`, and `12 ^ 10`.
2. Predict `~5` and explain the rule `~x == -x - 1`.
3. Predict `3 << 2`, `12 >> 2`, and `-3 >> 1`.
4. Write an expression that checks whether the bit represented by `0b0100` is set in `flags`.
5. Given `flags = 0b0001`, write statements to set `0b0010` and then clear that flag.

### Exercise 11 — Built-ins and numeric types

1. Predict `divmod(23, 4)`.
2. Use `pow()` to calculate 2 to the fifth power; then explain the difference between `pow(2, 5)` and `pow(2, 5, 7)`.
3. Use `min()`, `max()`, and `sum()` to summarize `[4, 7, -2, 5]`.
4. Choose `float`, `complex`, `Decimal`, or `Fraction` for each task and justify the choice: a sensor ratio, an AC signal calculation, a decimal currency amount, and an exact one-third.

### Exercise 12 — Precedence and associativity

Predict each result and add parentheses to show the grouping:

1. `2 ** 3 ** 2`
2. `-3 ** 2`
3. `(-3) ** 2`
4. `12 + 8 >> 1`
5. `1 | 2 & 4`
6. `not 2 == 2 and 3 < 4`

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
11. What is a complex number in Python, how do you inspect its parts, and why are ordering comparisons unsupported?
12. What do the six bitwise operators do, and why is `~5` equal to `-6`?
13. How does bitwise `&` differ from Boolean `and`?
14. What is the difference between `pow()`, `divmod()`, `min()`, `max()`, and `sum()`?
15. When might `cmath`, `Decimal`, or `Fraction` be a better fit than `math` or `float`?
16. Where can you find the complete official operator-precedence table, and why are parentheses useful?

---

## Solutions — open after attempting the independent practice

### Exercise answers The solutions below are reference answers, not the only acceptable solutions to open-ended programming tasks. For code-writing exercises, equivalent solutions are correct when they meet the requirements, handle the stated edge cases, and produce the expected behavior.

### Exercise 1 — Numeric types

1. `15` → `int`
2. `15.0` → `float`
3. `15 / 3` → `float` (the value is `5.0`)
4. `15 // 3` → `int` (the value is `5`)
5. `15 % 4` → `int` (the value is `3`)
6. `2 ** 4` → `int` (the value is `16`)
7. `int(-3.8)` → `int` (the value is `-3`; `int()` truncates toward zero rather than flooring)

### Exercise 2 — Arithmetic predictions

1. `17 / 4` → `4.25`
2. `17 // 4` → `4`
3. `17 % 4` → `1`
4. `-17 // 4` → `-5`, because floor division rounds toward negative infinity (`-17 / 4` is `-4.25`)
5. `-17 % 4` → `3`, because the remainder follows the sign of the divisor
6. `3 ** 2 ** 2` → `81`; exponentiation groups from right to left, so this is `3 ** (2 ** 2)`, or `3 ** 4`

For integer operands and a nonzero divisor, `a == (a // b) * b + (a % b)` holds exactly.

### Exercise 3 — Parentheses and precedence

1. `(8 + 4) * 3` → `36`
2. `100 / (5 + 5)` → `10.0`
3. `(12 + 15 + 18) / 3` → `15.0`
4. `(-3) ** 2` → `9`. Parentheses make the negative number the base. Without them, `-3 ** 2` means `-(3 ** 2)` and evaluates to `-9`.

### Exercise 4 — Comparisons and logic

Given `x = 12` and `y = 5`:

1. `x > y` → `True`
2. `x == 12` → `True`
3. `x != y` → `True`
4. `x > 10 and y < 10` → `True`
5. `x < 10 or y == 5` → `True`
6. `not (x == y)` → `True`
7. `10 <= x < 15` → `True`

A chained comparison checks both bounds and evaluates the middle expression only once.

### Exercise 5 — Augmented assignment

| Statement | Value afterward | Type |
| --- | ---: | --- |
| `value = 8` | `8` | `int` |
| `value += 4` | `12` | `int` |
| `value *= 2` | `24` | `int` |
| `value //= 5` | `4` | `int` |
| `value /= 2` | `2.0` | `float` |

The final type changes because `/` with these numeric operands performs true division.

### Exercise 6 — Floating-point behavior

1. `0.1 + 0.2` commonly displays as `0.30000000000000004`, and `0.1 + 0.2 == 0.3` is `False`.
2. Most decimal fractions cannot be represented exactly as finite binary floating-point values. The stored approximations can therefore differ slightly from the decimal values written in source code.
3. One valid test is:

   ~~~python
   import math

   print(math.isclose(0.1 + 0.2, 0.3))  # True
   ~~~

   `math.isclose()` uses tolerances; choose explicit tolerances when the default does not fit the problem's scale or accuracy requirements.
4. Display π to two and six decimal places:

   ~~~python
   import math

   print(f"{math.pi:.2f}")  # 3.14
   print(f"{math.pi:.6f}")  # 3.141593
   ~~~

### Exercise 7 — Measurement calculator

One valid solution:

~~~python
first_reading_v = 4.8
second_reading_v = 5.2

average_v = (first_reading_v + second_reading_v) / 2
signed_difference_v = second_reading_v - first_reading_v
absolute_difference_v = abs(signed_difference_v)

print(f"Average: {average_v:.2f} V")
print(f"Signed difference: {signed_difference_v:.2f} V")
print(f"Absolute difference: {absolute_difference_v:.2f} V")

if first_reading_v != 0:
    percentage_change = (
        (second_reading_v - first_reading_v) / first_reading_v
    ) * 100
    print(f"Percentage change: {percentage_change:.1f}%")
else:
    print("Percentage change is undefined when the original value is zero.")
~~~

For these inputs, the average is `5.00 V`, the signed difference is `0.40 V`, the absolute difference is `0.40 V`, and the percentage change is approximately `8.3%`. A different valid solution may use other variable names or equivalent formatting. It must preserve the sign of the signed difference and avoid dividing by zero.

### Exercise 8 — Explain your choices

1. Use `/` for true division, `//` when the floor quotient is required, and `%` when the remainder is required.
2. `int(-3.8)` is `-3` because `int()` truncates toward zero. `-3.8 // 1` is `-4.0` because floor division rounds toward negative infinity.
3. Floating-point values are approximations for many decimal fractions, so calculated values that are mathematically equal may not compare exactly. Use an appropriate tolerance when comparing computed floats.
4. Combining incompatible units can produce a meaningless result even when Python evaluates the expression successfully. Convert to compatible units first and use names that communicate the units.
5. `Decimal` is useful when decimal arithmetic and decimal rounding rules matter, such as currency calculations. Create values from strings (for example, `Decimal("0.10")`) when the intended decimal input must be preserved. It is not automatically the best choice for every scientific calculation.

### Exercise 9 — Complex numbers

Given `z = 3 + 4j`:

1. `z.real` is `3.0`, `z.imag` is `4.0`, and `abs(z)` is `5.0`.
2. `z.conjugate()` returns `(3-4j)`.
3. Complex numbers have no general ordering relation in Python, so `z < 5` raises `TypeError`. Equality is defined, so `z == 3 + 4j` is `True`.
4. Use `cmath` for a complex square root, for example `cmath.sqrt(-1)` returns `1j`. The `math` module is intended for real-valued functions.

### Exercise 10 — Bitwise operators and masks

1. Decimal `12` is `0b1100`; decimal `10` is `0b1010`.

   - `12 & 10` → `8` (`0b1000`)
   - `12 | 10` → `14` (`0b1110`)
   - `12 ^ 10` → `6` (`0b0110`)

2. `~5` → `-6`, because Python integer inversion follows `~x == -x - 1`.
3. `3 << 2` → `12`; `12 >> 2` → `3`; `-3 >> 1` → `-2`.
4. Test whether the `0b0100` bit is set:

   ~~~python
   if flags & 0b0100:
       print("The bit is set.")
   ~~~

   An explicit Boolean result can be obtained with `bool(flags & 0b0100)`.
5. Set and then clear `0b0010`:

   ~~~python
   flags = 0b0001
   flags |= 0b0010
   print(flags)  # 3

   flags &= ~0b0010
   print(flags)  # 1
   ~~~

   `|=` sets the selected bit; `&= ~mask` clears it while preserving other bits.

### Exercise 11 — Built-ins and numeric types

1. `divmod(23, 4)` → `(5, 3)`
2. `pow(2, 5)` → `32`. `pow(2, 5, 7)` → `4`, the remainder when `32` is divided by `7`; the three-argument form performs modular exponentiation.
3. For `[4, 7, -2, 5]`, `min(...)` is `-2`, `max(...)` is `7`, and `sum(...)` is `14`.
4. Reasonable choices:
   - **Sensor ratio:** often `float`, provided its precision is suitable for the sensor and calculation.
   - **AC signal calculation:** `complex` for a representation with real and imaginary components.
   - **Decimal currency amount:** `Decimal` when decimal arithmetic and rounding rules are required.
   - **Exact one-third:** `Fraction(1, 3)` when an exact rational representation is needed.

   The correct choice depends on the requirements; explain the trade-off rather than memorizing a single label.

### Exercise 12 — Precedence and associativity

1. `2 ** 3 ** 2` → `512`; grouping: `2 ** (3 ** 2)`
2. `-3 ** 2` → `-9`; grouping: `-(3 ** 2)`
3. `(-3) ** 2` → `9`
4. `12 + 8 >> 1` → `10`; grouping: `(12 + 8) >> 1`, or `20 >> 1`
5. `1 | 2 & 4` → `1`; grouping: `1 | (2 & 4)`, so `1 | 0`
6. `not 2 == 2 and 3 < 4` → `False`; comparisons bind more tightly than `not`, so the expression is `(not (2 == 2)) and (3 < 4)`, or `False and True`

### Knowledge check — Suggested answers

1. `int` represents integers; `float` represents binary floating-point values, which approximate many real numbers.
2. `19 / 4` → `4.75`; `19 // 4` → `4`; `19 % 4` → `3`.
3. Floor division rounds toward negative infinity, so `-19 // 4` is `-5`, not `-4`.
4. Multiplication has higher precedence than addition: `2 + 3 * 4` is `14`, while `(2 + 3) * 4` is `20`.
5. `=` assigns, `==` compares values, and `is` compares object identity.
6. Short-circuit evaluation skips an unnecessary operand when `and` or `or` already has a determined result. For example, `divisor != 0 and 12 / divisor > 2` does not evaluate the division when `divisor` is zero.
7. Decimal fractions such as `0.1` and `0.2` generally have no exact finite binary representation, so their floating-point sum may not equal the stored value of `0.3`.
8. `round(value, 2)` returns a rounded numeric result; `f"{value:.2f}"` creates a string formatted with two digits after the decimal point without reassigning the original value.
9. Percentage change divides by the original value. When the original value is zero, the calculation is undefined, so the program should handle that case explicitly.
10. Names such as `distance_m` and `elapsed_time_s` communicate the quantities and units. Convert values to compatible units before combining them, and avoid rounding intermediate values without a reason.
11. A complex number has real and imaginary parts, accessible through `.real` and `.imag`; `abs(z)` returns its magnitude. Python does not define ordinary ordering comparisons for complex numbers.
12. `&` is bitwise AND, `|` is bitwise OR, `^` is bitwise XOR, `~` inverts integer bits, and `<<` / `>>` shift bits. For Python integers, `~x == -x - 1`, so `~5` is `-6`.
13. Bitwise `&` operates on integer bits. Boolean `and` evaluates truth values and short-circuits; the two operators serve different purposes.
14. `pow()` calculates powers (and optionally modular powers), `divmod()` returns quotient and remainder, `min()` finds the smallest item, `max()` finds the largest, and `sum()` adds items in an iterable.
15. Use `cmath` for complex-valued mathematical functions, `Decimal` when decimal arithmetic requirements matter, and `Fraction` when an exact rational representation is useful.
16. The complete table is in the [official Python Language Reference — Operator precedence](https://docs.python.org/3/reference/expressions.html#operator-precedence). Parentheses can override default grouping and make an expression's intent easier to read.

---

## 14. Summary

- `int` represents integers, `float` represents binary floating-point approximations, and `complex` represents values with real and imaginary parts.
- `+`, `-`, `*`, and `**` perform addition, subtraction, multiplication, and exponentiation.
- `/` performs true division; `//` performs floor division; `%` returns a remainder.
- Floor division rounds toward negative infinity, which matters for negative operands.
- Operator precedence and associativity control expression grouping; use parentheses to clarify intent and consult the [complete official precedence table](https://docs.python.org/3/reference/expressions.html#operator-precedence).
- The six bitwise operators (`&`, `|`, `^`, `~`, `<<`, `>>`) operate on integer bits; inversion and right shifts have important negative-integer behavior.
- Comparisons produce Boolean results; `and`, `or`, and `not` combine or invert conditions.
- Augmented assignment offers concise ways to update a numeric variable.
- Floating-point values have finite precision. Use tolerances for numerical comparisons when appropriate.
- Use `round()` for a rounded numeric result and formatting for display.
- Use `abs()`, `round()`, `pow()`, `divmod()`, `min()`, `max()`, `sum()`, and selected `math` functions when they fit the problem.
- Use `cmath` for complex-valued functions, `Decimal` for decimal arithmetic requirements, and `Fraction` for exact rational values when appropriate.
- Name measurements clearly, keep units consistent, and guard against invalid operations such as division by zero.

## References

- [The Python Tutorial — Numbers](https://docs.python.org/3/tutorial/introduction.html#numbers)
- [The Python Tutorial — More on Control Flow Tools (comparisons and Boolean operations)](https://docs.python.org/3/tutorial/controlflow.html)
- [Built-in Types — Numeric Types](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)
- [Built-in Functions — `round()`, `abs()`, `int()`, and `float()`](https://docs.python.org/3/library/functions.html)
- [Expressions — complete operator precedence table](https://docs.python.org/3/reference/expressions.html#operator-precedence)
- [cmath — Mathematical functions for complex numbers](https://docs.python.org/3/library/cmath.html)
- [fractions — Rational numbers](https://docs.python.org/3/library/fractions.html)
- [math — Mathematical functions](https://docs.python.org/3/library/math.html)
- [decimal — Decimal fixed-point and floating-point arithmetic](https://docs.python.org/3/library/decimal.html)
- [Floating-Point Arithmetic: Issues and Limitations](https://docs.python.org/3/tutorial/floatingpoint.html)
