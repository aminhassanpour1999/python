# Booleans and None

**Module:** Programming Fundamentals  
**Lesson:** 6 of 9 · **Level:** Beginner · **Study time:** 60–75 minutes  
**Prerequisites:** Variables and Data Types; Numbers and Operators; Type Conversion

## Purpose and learning objectives

Boolean values represent truth. They are central to comparisons, decisions, validation, and program logic. None represents the absence of a value. By the end, you should be able to use comparisons; explain truthiness; distinguish falsy values from None; use and, or, and not; explain short-circuiting and operand-return behavior; and check None correctly.

## 1. Boolean values

Python's Boolean type is bool and its two values are True and False:

    is_ready = True
    has_error = False
    print(type(is_ready))  # <class 'bool'>

Names are case-sensitive: write True and False, not true and false.

## 2. Comparisons

| Operator | Meaning |
|---|---|
| == | Equal |
| != | Not equal |
| < | Less than |
| <= | Less than or equal |
| > | Greater than |
| >= | Greater than or equal |

    temperature = 24
    print(temperature > 20)   # True
    print(temperature == 24)  # True
    print(temperature != 24)  # False

Comparisons can be chained:

    print(10 <= temperature < 30)  # True

This checks both bounds; the middle expression is evaluated only once.

Equality and identity are different:
- == compares values.
- is checks whether references point to the same object.
Use == for ordinary values and is None for the None singleton.

## 3. Truth-value testing (truthiness)

Many objects can be tested in a Boolean context. This is called truthiness.

Common falsy values:
- False and None
- Numeric zero: 0, 0.0, 0j
- Empty text: ""
- Empty containers such as [], (), {}, and set()

Most other values are truthy. In particular, non-empty strings are truthy even if their text is "False", "0", or "no".

    print(bool(0))        # False
    print(bool(-1))       # True
    print(bool(""))       # False
    print(bool("False"))  # True
    print(bool("0"))      # True
    print(bool(None))     # False

The collection examples are previews; lists, tuples, dictionaries, and sets are taught in the Data Structures module.

### Truthiness is not equality

    print(0 == False)     # True
    print("" == False)    # False
    print(None == False)  # False
    print(0 is None)      # False

bool is a subtype of int, so False behaves numerically like zero and True like one in some operations. This is a language fact, not a reason to use Booleans as counters.

Test the condition you mean. Do not call bool() unnecessarily.

## 4. Boolean operators

| Operator | Meaning |
|---|---|
| and | Both operands must be truthy |
| or | At least one operand must be truthy |
| not | Inverts truth value |

    voltage = 3.3
    signal_present = True
    within_range = voltage >= 0 and voltage <= 5
    can_process = within_range and signal_present
    needs_attention = not can_process

Truth tables:

| A | B | A and B | A or B |
|---|---|---|---|
| False | False | False | False |
| False | True | False | True |
| True | False | False | True |
| True | True | True | True |

| A | not A |
|---|---|
| False | True |
| True | False |

Use parentheses when a compound condition is difficult to read.

## 5. Short-circuit evaluation

Python evaluates and and or from left to right and stops when the result is already known:
- A and B does not evaluate B if A is falsy.
- A or B does not evaluate B if A is truthy.

    denominator = 0
    safe = denominator != 0 and 10 / denominator > 1
    print(safe)  # False

The division is skipped because the first condition is false. Short-circuiting can guard operations, but avoid obscure expressions with side effects.

## 6. and and or return operands

In Python, and and or do not necessarily return True or False. They return one of their operands:
- x and y returns x if x is falsy; otherwise y.
- x or y returns x if x is truthy; otherwise y.

    print(0 and "hello")       # 0
    print("ready" and 42)      # 42
    print("" or "default")     # default
    print("active" or "idle")  # active

This can provide defaults, but explicit logic is often clearer for beginners. Do not assume the result type is bool.

## 7. The meaning of None

None is a special singleton object representing absence of a value, an unavailable result, or an intentionally empty result:

    measurement = None
    print(type(measurement))  # <class 'NoneType'>

| Value | Typical meaning | Type |
|---|---|---|
| 0 | Numeric zero | int |
| 0.0 | Floating-point zero | float |
| False | Boolean false | bool |
| "" | Empty text | str |
| None | No value / no result | NoneType |

These values may all be falsy, but they mean different things.

Check None with identity:

    if measurement is None:
        print("No measurement is available.")

Use is not None for the inverse. This is the conventional and correct way to test for None.

A name assigned to None exists and refers to the None object. A name never assigned in the current scope is undefined there and can raise NameError when accessed.

## 8. Common mistakes

1. Using = instead of ==.
2. Using is for ordinary value equality.
3. Treating every falsy value as None.
4. Assuming bool("False") is False.
5. Assuming and/or always return bool.
6. Ignoring evaluation order and short-circuiting.
7. Writing long, tangled conditions instead of named intermediate Boolean values.

## 9. Coding lab — Measurement status checker

Create status_checker.py.

    measurement = 3.7
    minimum = 0.0
    maximum = 5.0
    is_connected = True

Tasks:
1. Create a Boolean for whether measurement is within the inclusive range.
2. Create a Boolean for whether the device is connected.
3. Combine them into an acceptance condition.
4. Set measurement to None. Check for None before numeric comparisons.
5. Test the lower and upper boundaries, values just outside them, zero, and None.
6. Guard a division with a nonzero check and explain short-circuiting.

## 10. Independent exercises

1. Predict bool() for 0, 1, -1, 0.0, "", " ", "False", and None.
2. Given temperature = 18, write expressions for equal to 18; not equal to 20; between 10 inclusive and 25 exclusive; outside that range.
3. Explain why reading is None differs from not reading.
4. Why is denominator != 0 and 100 / denominator > 5 safe when denominator is zero?
5. Predict values and types of: a = "" or "unknown"; b = "online" and 1; c = 0 and 100.
6. Repair if status is "ready": use value equality, not identity.
7. Simplify not (is_connected == False).

## Answer key

1. False, True, True, False, False, True, True, False.
2. temperature == 18; temperature != 20; 10 <= temperature < 25; not (10 <= temperature < 25).
3. None means no value. not reading tests truthiness and is also true for zero, False, and empty text.
4. The left operand is false, so Python skips the division.
5. a is "unknown" (str); b is 1 (int); c is 0 (int).
6. if status == "ready": ...
7. is_connected. A Boolean name already expresses the condition.

## Knowledge check

1. What are the two Boolean values?
2. What does truthiness mean?
3. Name common falsy values.
4. Why is "False" truthy?
5. How do and/or differ from bitwise &/|?
6. What is short-circuit evaluation?
7. Can and/or return non-Boolean values?
8. Why use is None?
9. Why is not value not a substitute for value is None?

## Summary and completion criteria

Comparisons produce Boolean results. Truthiness tests many kinds of values. Falsy does not mean None. and/or short-circuit and return operands. None represents absence; check it with is None.

- [ ] I can interpret comparisons.
- [ ] I can classify common values as truthy or falsy.
- [ ] I can distinguish None from zero, False, and empty text.
- [ ] I can explain short-circuiting and operand-return behavior.
- [ ] I can test a compound condition at its boundaries.
- [ ] I completed the lab and exercises independently.

## Official references

- [Truth Value Testing](https://docs.python.org/3/library/stdtypes.html#truth-value-testing)
- [Built-in Constants](https://docs.python.org/3/library/constants.html)
- [Boolean Operations](https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not)
- [Comparisons](https://docs.python.org/3/reference/expressions.html#comparisons)
