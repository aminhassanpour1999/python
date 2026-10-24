# Strings

> **Status:** Syllabus outline. We will expand this lesson into teaching notes, a coding lab, exercises, and a small project when we study it.

## Learning objectives

- Create string literals with single, double, and triple quotes.
- Explain indexing, slicing, and the fact that strings are immutable.
- Use common string methods without confusing a returned string with an in-place change.
- Format values clearly with f-strings.
- Recognize whitespace and basic text-normalization issues.

## Sections

1. **String literals** — quoting, escape sequences, and multiline strings.
2. **Combining and repeating text** — concatenation, repetition, and readable alternatives.
3. **Indexing** — positive and negative indexes and the meaning of an index error.
4. **Slicing** — start, stop, and step; why the stop index is excluded.
5. **String immutability** — methods return results rather than modifying the original string in place.
6. **Useful methods** — `lower()`, `upper()`, `strip()`, `replace()`, `split()`, and `join()`.
7. **f-strings and formatting** — embedding values and formatting numeric output.
8. **Whitespace and normalization** — leading/trailing spaces, case, and cautious handling of user-provided text.
9. **Common mistakes** — mixing strings and numbers, incorrect indexes, and assuming methods mutate a string.

## Coding lab

Build a small report that formats a measurement with a label and unit. Clean a user-provided label with suitable string methods and show the original and normalized versions.

## Exercises

- Predict indexing and slicing results.
- Repair string-concatenation mistakes.
- Format numbers inside f-strings.
- Explain why calling a string method does not necessarily change the original variable.

## Knowledge check

Explain indexing versus slicing, string immutability, and when an f-string is useful.

## References

- [Python Tutorial: Text](https://docs.python.org/3/tutorial/introduction.html#text)
- [String Methods](https://docs.python.org/3/library/stdtypes.html#string-methods)
- [Formatted String Literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)
