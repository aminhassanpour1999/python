# Type Conversion

**Prerequisites:** Variables and Data Types; Numbers and Operators; Strings  
**Study time:** 60–90 minutes

## Purpose and outcomes

Programs receive values in one representation and use them in another. Terminal input is text; arithmetic needs numbers. A displayed result may need a formatted string. Conversion is not proof that a value is valid for a particular application.

You will distinguish conversion, parsing, validation, and formatting; use int(), float(), str(), and bool(); parse bases; explain information loss; and recognize conversion exceptions.

## 1. Four different operations

- **Conversion:** create a value of another type, such as float(3).
- **Parsing:** interpret text according to a representation, such as int("1010", 2).
- **Validation:** check application rules, such as whether a frequency lies in an allowed range.
- **Formatting:** create a display representation, such as f"{voltage:.2f} V".

A value may parse successfully and still be invalid for the application.

## 2. Integer conversion

int() creates an integer from a suitable value.

~~~python
print(int("42"))     # 42
print(int(42.9))     # 42
print(int(-42.9))    # -42
print(int(True))     # 1
~~~

Converting a float truncates toward zero; it does not round to the nearest integer.

~~~python
print(int(6.9))    # 6
print(int(-6.9))   # -6
print(round(6.9))  # 7
print(round(-6.9)) # -7
print(int(-6.2))   # -6
print(-6.2 // 1)   # -7.0
~~~

Floor division rounds down toward negative infinity. It is not the same as truncation.

### Bases

~~~python
print(int("1010", 2)) # 10
print(int("17", 8))   # 15
print(int("FF", 16))  # 255
print(int("0b1010", 0)) # 10
~~~

A base must be between 2 and 36. Base 0 asks Python to infer a recognized prefix. The base argument is for parsing string representations.

## 3. Floating-point conversion

~~~python
print(float("12.5"))  # 12.5
print(float(7))       # 7.0
print(float("-3e2"))  # -300.0
~~~

Python also accepts spellings for NaN and infinity. These are valid float values but may violate measurement requirements. Use math.isfinite() when a calculation requires finite values; domain and range checks remain separate.

## 4. Conversion to text

~~~python
count = 12
voltage = 3.3
print(str(count))    # '12'
print(str(voltage))  # '3.3'
print(f"Voltage: {voltage:.2f} V")
~~~

str() creates a string representation, not a guaranteed serialization format. Structured data needs a defined format and parser.

## 5. Boolean conversion

bool(value) applies Python truth-value rules.

~~~python
print(bool(0))        # False
print(bool(1))        # True
print(bool(""))       # False
print(bool("False")) # True
print(bool("0"))     # True
print(bool(None))     # False
~~~

A non-empty string is truthy, even when its contents spell "False" or "0". bool() is not a parser for yes/no input. Normalize and compare against an explicit accepted vocabulary instead.

~~~python
answer = " YES ".strip().casefold()
if answer in {"yes", "y"}:
    should_continue = True
elif answer in {"no", "n"}:
    should_continue = False
else:
    print("Unrecognized response.")
~~~

This previews if statements, taught in Control Flow.

## 6. Implicit numeric conversion

Some mixed numeric operations promote values to a compatible numeric type.

~~~python
result = 5 + 2.5
print(result)        # 7.5
print(type(result))  # <class 'float'>
~~~

Python does not automatically parse arbitrary numeric-looking strings.

~~~python
# "5" + 2.5 raises TypeError
~~~

Convert explicitly at the boundary where text becomes numeric data.

## 7. Information loss and type choice

Conversion may discard information:

- int(3.9) discards the fractional part.
- int("000731") loses leading zeroes.
- float cannot exactly represent every decimal fraction.
- Formatting to two decimal places changes the display, not the stored value.
- A complex value cannot safely be treated as a real value without deciding what to do with its imaginary component.

Choose types according to meaning: a serial number is an identifier (usually str); a voltage is numeric; an absent measurement may be None.

## 8. Conversion errors

- **ValueError:** the general type is suitable, but this particular value cannot be converted.
- **TypeError:** the supplied object type is not appropriate for the operation.

~~~python
# int("twelve") raises ValueError
# int(None) raises TypeError
~~~

Do not silently replace every conversion failure with zero. Zero may be a meaningful measurement and would hide invalid or missing data. Robust exception handling is taught later.

## 9. Parsing is not domain validation

Suppose an operating frequency must be from 470 through 694 MHz. The text "900" parses as an integer but violates the range. "five hundred" cannot be parsed as a number. These are different failures:

- Representation failure: text cannot be interpreted as the required type.
- Domain failure: parsed value violates an application rule.
- Unit failure: number uses a different unit than expected.
- Missing value: no value was supplied.

Write down these rules before implementing a conversion pipeline.

## 10. Coding lab — Convert and assess measurements

Create conversion_lab.py.

1. Define text for a decimal measurement, a binary integer, and an identifier with leading zeroes.
2. Convert the measurement to float.
3. Parse the binary text using base 2.
4. Keep the identifier as str.
5. Print each value and its type.
6. Compare int(-3.8), round(-3.8), and -3.8 // 1.
7. Check finiteness with math.isfinite().
8. Explain why successful parsing does not prove that a measurement is within its operating range.

## 11. Independent exercises

### Level 1

1. Predict value and type for int("17"), float("17"), str(17), bool("0"), and int(-3.8).
2. Which raises: int("25"), int("2.5"), float("2.5"), float("two"), int(None)?
3. Explain int(-6.8) versus -6.8 // 1.

### Level 2

4. Convert "11110000" from base 2 and display hexadecimal.
5. Parse yes/y/no/n after trimming whitespace and ignoring case.
6. Give a value that converts but is invalid for a domain-specific reason.
7. Repair a speed calculation that divides strings.
8. Format a float to two decimals without changing the original.

### Level 3

9. Why should "000731" remain text?
10. Why can float("nan") succeed but still be invalid?
11. How can converting readings to int before averaging change the result?
12. Distinguish type, representation, and validity with an example.

## Exercise solutions

Attempt the exercises and knowledge check before opening the separate [type-conversion — Exercise Solutions](./004-type-conversion-solutions.md).

## Knowledge check

1. Conversion versus parsing?
2. What does int() do to a float?
3. Why is round() not interchangeable with int()?
4. Why is bool("False") true?
5. ValueError versus TypeError?
6. Can a parsed value still be invalid?
7. Why can numeric conversion destroy an identifier?
8. Does formatting mutate a float?

## Summary and completion criteria

Convert deliberately at clear boundaries. int() truncates floats toward zero. bool() tests truthiness, not textual meaning. Parsing, validation, and formatting solve different problems. Preserve information by choosing types according to meaning.

Complete the lab and solve unfamiliar exercises. Explain the difference between a representation error and a domain error before marking the lesson studied.

## Official references

- [Built-in Functions: int, float, str, bool](https://docs.python.org/3/library/functions.html)
- [Numeric Types](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)
- [Floating-Point Arithmetic](https://docs.python.org/3/tutorial/floatingpoint.html)
- [math.isfinite()](https://docs.python.org/3/library/math.html#math.isfinite)
