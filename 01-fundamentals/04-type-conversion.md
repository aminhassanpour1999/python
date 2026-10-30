# Type Conversion

**Module:** Programming Fundamentals  
**Lesson:** 4 of 9 · **Level:** Beginner · **Study time:** 60–75 minutes  
**Prerequisites:** Variables and Data Types; Numbers and Operators; Strings

## Purpose and learning objectives

Type conversion creates a value of another type. Conversion can fail or lose information. By the end, you should be able to use int(), float(), str(), and bool(); explain implicit numeric promotion; parse numbers in different bases; recognize ValueError and TypeError; and distinguish conversion from validation.

## 1. Why conversion matters

    text_value = "25"
    integer_value = 25
    print(type(text_value))     # <class 'str'>
    print(type(integer_value))  # <class 'int'>

The values look similar when printed but have different types. Conversion is common at boundaries: user input, configuration, files, and external data.

## 2. Numeric conversions

### 2.1 int()

int() creates an integer from a compatible value:

    int("42")    # 42
    int(7.9)     # 7
    int(-7.9)    # -7
    int(True)    # 1
    int(False)   # 0

When converting a float, int() truncates toward zero. It does not round:

    int(4.9)     # 4
    int(-4.9)    # -4
    round(4.9)   # 5

Do not confuse int(-4.9) with -4.9 // 1, which is -5.0 because floor division rounds down toward negative infinity.

### 2.2 float()

    float("3.5")   # 3.5
    float("12")    # 12.0
    float(8)       # 8.0
    float("2.5e3") # 2500.0
    float("1e-3")  # 0.001

Python also recognizes strings such as "inf", "-inf", and "nan" as special floating-point values. These are edge cases, not ordinary finite measurements.

### 2.3 Parse an integer in another base

The second argument to int() specifies the base:

    int("1010", 2)  # 10
    int("17", 8)    # 15
    int("FF", 16)   # 255

The base must be from 2 through 36, and the text must be valid for that base.

## 3. Convert to text with str()

str(value) returns a human-readable string representation:

    count = 12
    text = str(count)
    print(text, type(text))  # 12 <class 'str'>

A representation is not necessarily a reversible data format. Formatting a float to two decimal places discards displayed precision even though the original float remains unchanged. For output that combines text and values, f-strings are often clearer.

## 4. Convert to bool()

bool(value) applies Python's truth-value rules:

    bool(1)        # True
    bool(0)        # False
    bool(-2)       # True
    bool("")       # False
    bool("False")  # True
    bool(None)     # False

A non-empty string is truthy even if its text says "False", "0", or "no". bool() does not interpret natural-language words. If you accept yes/no text, normalize it and compare against an explicitly allowed set. Truthiness is studied in depth in Lesson 6.

## 5. Implicit numeric conversion

Python sometimes promotes compatible numeric values during arithmetic:

    result = 3 + 2.5
    print(result, type(result))  # 5.5 <class 'float'>

This does not mean Python converts unrelated types automatically:

    # "3" + 2  # TypeError

The + operator supports numeric addition and string concatenation, but Python does not guess that the text "3" should become the integer 3. Complex arithmetic can also promote real numeric operands to complex values.

## 6. Conversion can lose information

| Conversion | Example | Consequence |
|---|---|---|
| float to int | int(3.9) | Fractional part discarded toward zero |
| int to float | float(3) | Becomes 3.0; huge integers may lose precision |
| float to text | str(3.14159) | Produces a textual representation |
| float to formatted text | f"{3.14159:.2f}" | Displays two decimals; original unchanged |
| number to bool | bool(0) | Tests truthiness, not meaning |

Never convert merely to silence an error. Decide what the value means and whether the conversion preserves the information you need.

## 7. Conversion errors

Two common exceptions:

- ValueError: the input's type is acceptable in principle, but its value cannot be converted as requested.
- TypeError: the constructor or operation received an inappropriate type.

Examples (run separately):

    int("hello")  # ValueError
    int("3.5")    # ValueError
    float(None)   # TypeError

Do not silently replace every invalid value with zero. That can turn bad input into a plausible but incorrect result. Exception handling is taught later; for now, recognize and explain the error.

## 8. Conversion is not validation

Conversion asks: can Python represent this input as the requested type? Validation asks: is the resulting value acceptable for this problem?

    frequency = float("0")  # Conversion succeeds

Zero may still be invalid for a task that requires a positive frequency. Likewise, a negative value may be syntactically valid but outside the application's allowed range.

A sound workflow:
1. Receive the original data.
2. Understand its expected format.
3. Convert it to the appropriate type.
4. Check domain constraints, range, and units.
5. Use it only after the checks pass.

## 9. Coding lab — Convert and validate measurements

Create conversion_lab.py.

    first_text = "18.5"
    second_text = "21.0"
    first = float(first_text)
    second = float(second_text)
    average = (first + second) / 2
    print(f"Average: {average:.2f}")

Tasks:
1. Predict values and types before running.
2. Compare int(8.9), round(8.9), int(-8.9), and -8.9 // 1. Explain the negative results.
3. Change the first value to "-5". Conversion succeeds; decide whether it is valid for your chosen quantity.
4. In a separate script, convert "not a number" to float and inspect the exception.
5. Convert binary text "1101" to an integer.

## 10. Independent exercises

1. Predict the value and type of int("17"), float("17"), str(17), bool("0"), and int(-3.8).
2. Which raise exceptions: int("25"), int("2.5"), float("2.5"), float("two"), int(None)? Name the exception types.
3. Predict int(6.8), int(-6.8), 6.8 // 1, and -6.8 // 1. Explain the difference.
4. Convert "11110000" from base 2 to an integer, then use hex().
5. Explain bool("False") and propose a safe yes/no text workflow.
6. Give a reason why a successfully converted negative value may still be invalid.
7. Repair this code: distance_text = "12.5"; time_text = "2"; speed = distance_text / time_text.
8. Format 3.14159265 to two decimal places and show that the original float is unchanged.

## Answer key

1. 17/int; 17.0/float; "17"/str; True/bool; -3/int.
2. int("2.5") and float("two") raise ValueError; int(None) raises TypeError. The others succeed.
3. 6, -6, 6.0, -7.0. int() truncates toward zero; // floors.
4. value = int("11110000", 2); hex(value) is "0xf0".
5. Every non-empty string is truthy. Strip whitespace, normalize case, accept only documented values, and reject all other input.
6. The domain may require non-negative, finite, in-range values or a particular unit.
7. Convert both strings to float before dividing.
8. display = f"{value:.2f}"; print(value) still displays the original value.

## Knowledge check

1. Why are "25" and 25 different?
2. What does int() do to negative floats?
3. What does bool("False") return?
4. How do ValueError and TypeError differ?
5. Why is conversion not validation?
6. When can conversion lose information?

## Summary and completion criteria

Conversion explicitly creates a value of another type. int() truncates floats toward zero; float() parses numeric text; str() creates text; bool() applies truthiness. Conversion can fail or lose information, and successful conversion does not establish domain validity.

- [ ] I can predict common conversions and resulting types.
- [ ] I can explain truncation versus rounding.
- [ ] I can parse numbers in a chosen base.
- [ ] I can identify common conversion exceptions.
- [ ] I can distinguish conversion from validation.
- [ ] I completed the lab and exercises independently.

## Official references

- [Built-in Functions](https://docs.python.org/3/library/functions.html)
- [Built-in Types — Numeric Types](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)
- [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)
