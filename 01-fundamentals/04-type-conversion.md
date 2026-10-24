# Type Conversion

> **Status:** Syllabus outline. We will expand this lesson into teaching notes, a coding lab, exercises, and a small project when we study it.

## Learning objectives

- Explain the difference between a value's type and its displayed text.
- Convert common values using `int()`, `float()`, `str()`, and `bool()`.
- Understand that `input()` returns a string, even when the user types digits.
- Predict common conversion results and recognize invalid conversions.
- Avoid assuming that every conversion preserves the original meaning.

## Sections

1. **Why conversion matters** — values from text input, files, and external sources.
2. **Numeric conversions** — `int()` and `float()`, including truncation versus rounding.
3. **Text conversion** — `str()` and readable output.
4. **Boolean conversion** — truth-value testing with `bool()` and common truthy/falsy examples.
5. **Conversion errors** — why strings such as `"hello"` cannot be converted to a number with `float()`.
6. **Conversion versus validation** — successful conversion does not guarantee a value is sensible for the problem.
7. **Safe beginner workflow** — inspect, convert, and test representative inputs; detailed exception handling comes later.

## Coding lab

Convert two text-form measurements into numbers, calculate a result, and display it with a clear label. Test valid numeric text and at least one invalid example; explain what happens rather than hiding the error.

## Exercises

- Predict the type and result of conversions.
- Identify why a conversion fails.
- Distinguish truncation from rounding.
- Explain why `input()` needs conversion before numeric arithmetic.

## Knowledge check

Explain why `"12"` is not the same as `12`, and name one limitation of converting user input directly.

## References

- [Built-in Functions](https://docs.python.org/3/library/functions.html)
- [Built-in Types](https://docs.python.org/3/library/stdtypes.html)
