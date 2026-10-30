# Numbers and Operators — Exercise Solutions

**Open only after attempting the lesson.** Equivalent correct reasoning is acceptable.

## Exercise solutions

Attempt the independent practice and knowledge check before reading this section. The solutions below are reference answers, not the only acceptable solutions to open-ended programming tasks. For code-writing exercises, equivalent solutions are correct when they meet the requirements, handle the stated edge cases, and produce the expected behavior.

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

