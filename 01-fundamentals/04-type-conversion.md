# Type Conversion

**Prerequisites:** Variables and Data Types; Numbers and Operators; Strings  
**Study time:** 60–90 minutes


**Module:** Programming Fundamentals  
**Lesson:** 4 of 9  
**Level:** Beginner  
**Study method:** Predict the resulting value and type before running each conversion. Keep raw input separate from parsed data until validation is complete.

## Lesson guide

This lesson explains how values cross type and representation boundaries. The central idea is that conversion, parsing, validation, and formatting are different operations. A conversion succeeding does not prove that the resulting value is suitable for a program's purpose.

Work through the examples in order, then complete the lab and exercises without opening the answer section. The lesson previews conditional statements for explicit validation; full control flow is taught later.

## Learning objectives

By the end of this lesson, you should be able to:

- Distinguish conversion, parsing, validation, and formatting.
- Use `int()`, `float()`, `str()`, `bool()`, and `complex()` within their supported boundaries.
- Explain truncation toward zero and distinguish it from rounding and floor division.
- Parse integer text in bases 2 through 36 and understand base 0 prefix detection.
- Explain implicit numeric promotion and why numeric-looking strings are not automatically numbers.
- Recognize `ValueError` and `TypeError` conversion failures.
- Preserve information such as leading zeroes and fractional parts when choosing types.
- Handle truth-value conversion correctly and parse yes/no text using explicit rules.
- Separate representation checks, finite-number checks, unit checks, and domain validation.
- Build a small conversion pipeline and test ordinary, boundary, and invalid input.


## Purpose and outcomes

Programs receive values in one representation and use them in another. Terminal input is text; arithmetic needs numbers. A displayed result may need a formatted string. Conversion is not proof that a value is valid for a particular application.

You will distinguish conversion, parsing, validation, and formatting; use int(), float(), str(), and bool(); parse bases; explain information loss; and recognize conversion exceptions.

## 1. Four different operations

### 1.1 A conversion pipeline

A reliable program makes each boundary explicit:

1. **Receive** the original representation, often text from `input()`.
2. **Parse or convert** it into the type needed for calculation.
3. **Validate** whether the parsed value satisfies the application's rules.
4. **Calculate** using values that have passed the required checks.
5. **Format** a result for display or output.

Do not overwrite the raw representation too early. Keeping it available helps debugging, reporting, and explaining rejected input.

| Operation | Question it answers | Example |
|---|---|---|
| Conversion | Can I create a value of another type? | `float(12)` |
| Parsing | Can I interpret this text using a defined grammar? | `int("1010", 2)` |
| Validation | Does the value meet the application's rules? | `470 <= frequency <= 694` |
| Formatting | How should the value be displayed? | `f"{frequency:.2f} MHz"` |

These stages can fail for different reasons and should not be collapsed into one vague idea of “converting input.”


- **Conversion:** create a value of another type, such as float(3).
- **Parsing:** interpret text according to a representation, such as int("1010", 2).
- **Validation:** check application rules, such as whether a frequency lies in an allowed range.
- **Formatting:** create a display representation, such as f"{voltage:.2f} V".

A value may parse successfully and still be invalid for the application.

## 2. Integer conversion

### 2.1 What int() accepts

The built-in `int()` can create an integer from an integer-like value, a Boolean, a float, or a valid integer string. The exact accepted arguments differ: the optional base is used for string parsing, not for converting a float.

~~~python
print(int(12))        # 12
print(int(12.99))     # 12
print(int(True))      # 1
print(int("  -42 "))  # -42
~~~

A Boolean is a subclass of `int`, so `int(True)` is `1` and `int(False)` is `0`. This is a language relationship, not a recommendation to treat status values as counts in application design.

### 2.2 Truncation, rounding, and floor are different rules

- `int(x)` truncates a float toward zero.
- `round(x)` applies Python's rounding rule; for exact halfway cases, ties are rounded to the even choice.
- `x // y` performs floor division, rounding the quotient down toward negative infinity.

~~~python
print(int(2.5))    # 2
print(int(-2.5))   # -2
print(round(2.5))  # 2
print(round(3.5))  # 4
print(round(-2.5)) # -2
print(-2.5 // 1)   # -3.0
~~~

Do not select one of these operations because its output “looks close.” Choose the rule required by the problem. If a value represents a measured quantity, truncating every reading before calculating a mean may discard meaningful information.


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

#### Base prefixes and explicit parsing

The base argument controls how digits are interpreted. A base of 2 uses binary digits, base 8 uses octal digits, base 10 uses decimal digits, and base 16 uses hexadecimal digits. For bases above 10, letters represent digit values after 9.

~~~python
print(int("1010", 2))   # 10
print(int("17", 8))     # 15
print(int("FF", 16))    # 255
print(int("Z", 36))     # 35
~~~

Base 0 asks Python to infer a base from a recognized prefix such as `0b`, `0o`, or `0x`. It is not a general-purpose “guess what the user meant” option. Without a recognized prefix, base-0 parsing does not behave like ordinary decimal parsing.

~~~python
print(int("0b1010", 0))  # 10
print(int("0xFF", 0))    # 255
# int("1010", 0) raises ValueError
~~~

The base must be in the supported range 2 through 36, or be 0. The text must contain valid digits for the selected base.


~~~python
print(int("1010", 2)) # 10
print(int("17", 8))   # 15
print(int("FF", 16))  # 255
print(int("0b1010", 0)) # 10
~~~

A base must be between 2 and 36. Base 0 asks Python to infer a recognized prefix. The base argument is for parsing string representations.

## 3. Floating-point conversion

### 3.1 Accepted forms and precision

`float()` accepts integer and floating-point values and parses valid floating-point text, including exponent notation and surrounding whitespace.

~~~python
print(float(7))           # 7.0
print(float(" 12.5 "))    # 12.5
print(float("1.25e2"))    # 125.0
print(float("-3E-2"))     # -0.03
~~~

Parsing a decimal string into a float does not make the decimal fraction exactly representable in binary. The same floating-point precision limitations discussed in Numbers and Operators still apply after conversion.

### 3.2 Special floating-point values

The strings `"nan"`, `"inf"`, and `"-inf"` are accepted spellings for special float values. They are valid floating-point values, but many applications require finite measurements.

~~~python
import math

value = float("nan")
print(math.isfinite(value))  # False
~~~

Check finiteness before ordinary range validation when non-finite values are possible. A NaN can make comparisons surprising because it is not equal to itself and ordinary ordered comparisons with it do not behave like comparisons with finite values.


~~~python
print(float("12.5"))  # 12.5
print(float(7))       # 7.0
print(float("-3e2"))  # -300.0
~~~

Python also accepts spellings for NaN and infinity. These are valid float values but may violate measurement requirements. Use math.isfinite() when a calculation requires finite values; domain and range checks remain separate.

## 4. Conversion to text

### 4.1 str() is not a serialization protocol

`str(value)` creates a human-readable string representation according to that object's string-conversion behavior. It is useful for display and simple text composition, but it does not guarantee that the result can be parsed back into the original type or that it forms a stable file/network format.

~~~python
count = 12
voltage = 3.3

print(str(count))           # 12
print(str(voltage))         # 3.3
print(f"Voltage: {voltage:.2f} V")
~~~

For debugging, `repr()` often provides a more explicit representation, such as showing quotation marks or escape characters. For structured interchange, use a defined serialization format such as JSON rather than assuming `str()` is sufficient; serialization is a later topic.


~~~python
count = 12
voltage = 3.3
print(str(count))    # '12'
print(str(voltage))  # '3.3'
print(f"Voltage: {voltage:.2f} V")
~~~

str() creates a string representation, not a guaranteed serialization format. Structured data needs a defined format and parser.

## 5. Boolean conversion

### 5.1 Truthiness rules

`bool(value)` asks whether Python considers the value true or false in a Boolean context. It does not interpret the semantic meaning of text.

Common false values include `False`, `None`, numeric zero values, and empty strings or containers. Most other objects are true. This lesson focuses on the values already introduced; collection truthiness is revisited when collections are taught.

~~~python
forbidden_preview = "False"
print(bool(forbidden_preview))  # True: the string is not empty
~~~

The word `"False"` is text, not the Boolean value `False`. Likewise, `"0"` is a non-empty string and is truthy. Use explicit accepted words when parsing user intent.


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

### 6.1 Numeric promotion is not text parsing

Python permits some mixed numeric operations by promoting compatible numeric values to a suitable common numeric type. For example, combining an integer and a float produces a float result.

~~~python
result = 5 + 2.5
print(result, type(result).__name__)  # 7.5 float
~~~

This behavior does not mean Python automatically parses arbitrary strings:

~~~python
# "5" + 2.5  # TypeError
~~~

The string must be parsed explicitly at the point where text becomes numeric data. Keep that boundary visible in the code so invalid input can be diagnosed.


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

### 7.1 Questions to ask before converting

Before converting a value, ask:

- Is the original value a measurement, a count, a label, an identifier, or a status?
- Will the conversion discard fractional information, leading zeroes, sign, or precision?
- Is the text format unambiguous, and is the chosen parser appropriate?
- Does the application require finite values or a specific range?
- Are units known and consistent?
- Is the result intended for calculation or display?

For example, a channel label such as `"007"` should normally remain text. The integer `7` no longer preserves the original identifier spelling.


Conversion may discard information:

- int(3.9) discards the fractional part.
- int("000731") loses leading zeroes.
- float cannot exactly represent every decimal fraction.
- Formatting to two decimal places changes the display, not the stored value.
- A complex value cannot safely be treated as a real value without deciding what to do with its imaginary component.

Choose types according to meaning: a serial number is an identifier (usually str); a voltage is numeric; an absent measurement may be None.

## 8. Conversion errors

### 8.1 Diagnose the exception, do not hide it

A `ValueError` commonly means the operation accepts the general input type but cannot interpret this particular value. A `TypeError` commonly means the object type is not supported by the operation.

~~~python
# int("twelve")  # ValueError: text is not an integer representation
# int(None)      # TypeError: None is not a supported input here
~~~

The exception message provides evidence, but you must still inspect the actual input and the conversion rule. Do not catch every failure and substitute zero: zero may be a legitimate measurement and would hide missing or malformed data. Structured exception handling is taught later.


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

### 9.1 A reliable conversion pipeline

#### Keep each stage explicit

For a beginner program, name each intermediate result. This makes it easier to inspect where the input stopped meeting the requirements.

~~~python
import math

raw_text = " 562.5 "
parsed_frequency_mhz = float(raw_text)
finite = math.isfinite(parsed_frequency_mhz)
within_allowed_range = 470 <= parsed_frequency_mhz <= 694
accepted = finite and within_allowed_range

print("Raw:", repr(raw_text))
print("Parsed:", parsed_frequency_mhz)
print("Finite:", finite)
print("Within range:", within_allowed_range)
print("Accepted:", accepted)
~~~

This is an illustrative rule for a particular application. The numeric range is not a property of `float()` or of Python itself.


For numeric input, keep the original text long enough to inspect it, parse it once, then validate the parsed value against the application's rules.

~~~python
import math

raw_text = " 562.5 "
frequency_mhz = float(raw_text)

is_finite = math.isfinite(frequency_mhz)
is_in_range = 470 <= frequency_mhz <= 694
is_acceptable = is_finite and is_in_range

print(repr(raw_text))
print(frequency_mhz)
print(is_acceptable)
~~~

The string parses successfully and the resulting value is finite and within this example's stated range. The range is an application rule, not a rule built into float().

Do not treat conversion as validation. The following values demonstrate different outcomes:

| Input text | Parsing result | Possible application result |
|---|---|---|
| "562.5" | Parses as float | May be valid |
| "900" | Parses as float | Outside a 470–694 MHz rule |
| "five" | float() raises ValueError | Invalid representation |
| "nan" | Parses as NaN | Not a finite measurement |
| "" | float() raises ValueError | Missing/empty representation |

### 9.2 Numeric conversion boundaries

~~~python
print(int(" 42 "))       # 42
print(int("1010", 2))     # 10
print(float("1.25e2"))    # 125.0
print(complex("3+4j"))    # (3+4j)
~~~

The numeric constructors accept different input forms. In particular, int("3.0") raises ValueError: the text is a floating-point spelling, not an integer spelling. Use int(float("3.0")) only when truncation toward zero is actually the intended rule.

A complex value cannot be converted to int or float without an explicit decision about its imaginary component:

~~~python
# int(3 + 4j) raises TypeError
# float(3 + 4j) raises TypeError
print(complex(3, 4))  # (3+4j)
~~~

Never silently discard the imaginary part to force a conversion.

### 9.3 NaN, infinity, and comparisons

~~~python
import math

not_a_number = float("nan")
positive_infinity = float("inf")

print(math.isfinite(not_a_number))       # False
print(math.isfinite(positive_infinity))  # False
print(not_a_number == not_a_number)      # False
~~~

NaN is unusual: it is not equal to itself, and ordinary ordering comparisons with it do not behave like comparisons with ordinary finite numbers. When a measurement must be finite, check math.isfinite() explicitly before applying ordinary range logic.

### 9.4 Parse yes/no text deliberately

bool("False") is True because it tests whether the string is empty. If the user enters words, define the accepted vocabulary and compare text explicitly:

~~~python
answer = " YES ".strip().casefold()

if answer == "yes" or answer == "y":
    should_continue = True
elif answer == "no" or answer == "n":
    should_continue = False
else:
    should_continue = None

print(should_continue)
~~~

This previews if / elif / else, which are taught fully in Control Flow. The key idea here is that parsing words is an application rule; bool() is not a text parser.

## 10. Coding lab — Convert and assess measurements

### Lab requirements and acceptance criteria

Your script must:

- Keep raw text in clearly named variables.
- Parse decimal text to `float` and binary text to `int` using base 2.
- Preserve an identifier containing leading zeroes as `str`.
- Print each parsed value and its type.
- Compare truncation, rounding, and floor division for a negative value.
- Check that a measurement is finite before applying its example range rule.
- Distinguish an invalid representation from a validly parsed but out-of-range value.
- Explain at least one case where conversion would destroy information.

Test at least one ordinary value, one boundary value, one out-of-range value, one malformed string, and one non-finite value. Do not add exception handling yet; report which input would raise an exception and explain why.


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

The exercises progress from prediction to practical conversion and reasoning. Write your predictions before running code. For code-writing tasks, include the value and resulting type in your verification.


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

## Exercise solutions — open after attempting the exercises

Open only after attempting the lesson.

## Level 1
1. int("17") -> 17; float("17") -> 17.0; str(17) -> "17"; bool("0") -> True; int(-3.8) -> -3.
2. int("2.5") and float("two") raise ValueError; int(None) raises TypeError.
3. int(-6.8) truncates toward zero to -6; -6.8 // 1 floors to -7.0.
## Level 2
4. int("11110000", 2) is 240; hex(240) is "0xf0".
5. Normalize with strip().casefold(), then compare to explicit accepted yes/y/no/n values. Reject other text.
6. "900" parses as a number but may violate a maximum frequency of 694 MHz.
7. Convert both raw strings with float() before division; check that elapsed time is nonzero.
8. display = f"{value:.2f}"; the original float is unchanged.
## Level 3
9. "000731" is an identifier; int() discards leading zeroes.
10. NaN is a valid floating-point special value but not a finite ordinary measurement.
11. Truncating each reading before averaging discards fractional information and can change the answer.
12. Type is the kind of object; representation is how it is expressed; validity is whether it meets domain rules. "900" may parse as int but fail a frequency range.
## Lab review
Keep the identifier as str, parse binary text using base 2, compare truncation/rounding/floor for negatives, and distinguish parsing from domain validation.

## Knowledge check

1. Conversion versus parsing?
2. What does int() do to a float?
3. Why is round() not interchangeable with int()?
4. Why is bool("False") true?
5. ValueError versus TypeError?
6. Can a parsed value still be invalid?
7. Why can numeric conversion destroy an identifier?
8. Does formatting mutate a float?


### Knowledge check — Suggested answers

1. Conversion creates another type; parsing interprets a representation.
2. int() truncates toward zero.
3. round() applies rounding rules; int() truncates.
4. "False" is non-empty and truthy.
5. ValueError means unacceptable value; TypeError means inappropriate type.
6. Yes, it may violate a range, unit, or domain constraint.
7. Numeric conversion can remove leading zeroes and formatting.
8. No. Formatting creates a display string.
## Summary and completion criteria

Convert deliberately at clear boundaries. int() truncates floats toward zero. bool() tests truthiness, not textual meaning. Parsing, validation, and formatting solve different problems. Preserve information by choosing types according to meaning.

Complete the lab and solve unfamiliar exercises. Explain the difference between a representation error and a domain error before marking the lesson studied.

## Official references

- [Built-in Functions: int, float, str, bool](https://docs.python.org/3/library/functions.html)
- [Numeric Types](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)
- [Floating-Point Arithmetic](https://docs.python.org/3/tutorial/floatingpoint.html)
- [math.isfinite()](https://docs.python.org/3/library/math.html#math.isfinite)
