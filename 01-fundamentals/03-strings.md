# Strings

**Prerequisites:** Variables and Data Types; Numbers and Operators  
**Study time:** 90–120 minutes plus independent practice

## Purpose and learning outcomes

Text is data: labels, names, identifiers, prompts, messages, and structured records. This lesson teaches a reliable mental model for Python strings, rather than a list of methods to memorize.

By the end, you can create and inspect string literals; explain immutability; use indexing, slicing, searching, splitting, joining, and formatting; recognize Unicode pitfalls; and test text-processing code with edge cases.

## 1. The string mental model

A Python string is an immutable sequence of Unicode code points. It is an object of type str. A string may be empty.

~~~python
empty = ""
message = "Hello, Python!"
symbol = "Ω"

print(type(message))  # <class 'str'>
print(len(empty))     # 0
print(len(message))   # 14
print(len(symbol))    # 1
~~~

The quote characters delimit a literal in source code; they are not part of its value. Single and double quotes create the same type. Choose the style that makes the text readable.

~~~python
first = 'Python'
second = "Python"
sentence = "It's Python."
escaped = 'It\'s Python.'
print(first == second)  # True
~~~

## 2. String literals and escapes

A backslash introduces an escape sequence in an ordinary string literal.

| Escape | Meaning |
|---|---|
| \\n | Newline |
| \\t | Tab |
| \\\\ | Backslash |
| \\' / \\" | Quote |
| \\r | Carriage return |
| \\b | Backspace |
| \\xhh | Hexadecimal code point |
| \\uXXXX | Four-digit Unicode escape |
| \\UXXXXXXXX | Eight-digit Unicode escape |

~~~python
message = "first line\nsecond line"
path = "folder\\file.txt"
print(message)
print(repr(path))
~~~

Expected output:

~~~text
first line
second line
'folder\\file.txt'
~~~

The built-in repr() gives a debugging representation that makes many invisible characters visible. It is not the same as user-facing output.

### Raw and multiline literals

A raw literal uses the r prefix. It is useful for patterns and path examples, but it is still an ordinary str object; raw describes literal parsing, not a special runtime type.

~~~python
ordinary = "A\nB"
raw = r"A\nB"
print(repr(ordinary))
print(repr(raw))
~~~

A raw literal cannot end with an odd number of backslashes because the final slash would escape the closing quote. Triple-quoted literals can span lines; the line breaks and indentation inside them become part of the value.

~~~python
message = """First line
Second line
Third line"""
print(message)
~~~

Triple quotes do not automatically make a comment. In a documented module, class, or function, a string in the docstring position has a special documentation role; that is covered in Code Style.

## 3. Length, indexing, and slicing

Indexing selects one code point. Positive indexes begin at zero; negative indexes count from the end.

~~~python
word = "PYTHON"
print(len(word))  # 6
print(word[0])    # P
print(word[-1])   # N
print(word[-2])   # O
~~~

The general slice form is sequence[start:stop:step]. The start is included and stop is excluded. Any of the three parts may be omitted. Step cannot be zero.

~~~python
word = "PYTHON"
print(word[1:4])   # YTH
print(word[:3])    # PYT
print(word[3:])    # HON
print(word[::2])   # PTO
print(word[::-1])  # NOHTYP
print(word[2:2])   # ''
print(word[:100])  # PYTHON
~~~

An out-of-range index raises IndexError; slice boundaries are clipped. This difference is intentional: indexing asks for one existing position, while slicing asks for a range.

~~~python
word = "cat"
# word[10] raises IndexError
print(word[0:10])  # cat
~~~

## 4. Immutability

A string cannot be changed in place. An expression such as text[0] = "J" raises TypeError. Build a new string and rebind the name instead.

~~~python
language = "Python"
language = "J" + language[1:]
print(language)  # Jython
~~~

String methods also return new strings. If the result is discarded, the original remains unchanged.

~~~python
label = "  receiver-01  "
label.strip()
print(repr(label))  # spaces remain

cleaned = label.strip()
print(repr(cleaned))  # 'receiver-01'
~~~

This is one of the most common string bugs: calling a method without using its return value.

## 5. Combining, comparing, and searching

The + operator concatenates strings; * repeats a string. Neither automatically converts arbitrary values to text.

~~~python
name = "radio" + " " + "signal"
rule = "-" * 12
print(name)
print(rule)
print(f"Count: {12}")
~~~

For many pieces, str.join() is usually clearer and more efficient than repeated concatenation. The separator is the string on which join() is called, and every item must itself be a string.

Membership checks for a substring and is case-sensitive.

~~~python
filename = "report_final.csv"
print(".csv" in filename)       # True
print("draft" not in filename)  # True
~~~

Strings compare lexicographically by Unicode code point values, not as numbers or necessarily as human dictionary order.

~~~python
print("python" == "Python")  # False
print("A" < "B")             # True
print("10" < "2")            # True
~~~

If numeric ordering is required, parse numeric text first. Locale-aware sorting and linguistic collation are separate topics.

### Search operations

| Operation | Behavior when absent |
|---|---|
| find(sub) | Returns -1 |
| index(sub) | Raises ValueError |
| count(sub) | Returns zero |
| sub in text | Returns False |
| startswith(prefix) | Returns False |
| endswith(suffix) | Returns False |

~~~python
message = "Python is practical"
print(message.find("is"))        # 7
print(message.find("Java"))      # -1
print(message.startswith("Py")) # True
print(message.endswith("cal"))  # True
~~~

Choose find() when absence is an ordinary result to handle. Choose index() when absence should be exceptional.

## 6. Cleaning and classifying text

strip() removes leading and trailing whitespace, not whitespace inside the text. lstrip() and rstrip() target one side.

~~~python
raw = "  sensor A\t\n"
print(repr(raw.strip()))   # 'sensor A'
print(repr(raw.lstrip()))
print(repr(raw.rstrip()))
~~~

The optional argument to strip() is a set of characters, not a literal prefix or substring. Use removeprefix() or removesuffix() when exact prefix/suffix removal is intended.

Case methods include lower(), upper(), title(), and casefold(). casefold() is intended for caseless matching and handles some Unicode case distinctions more aggressively than lower().

~~~python
print("Straße".lower())     # straße
print("Straße".casefold())  # strasse
~~~

For simple caseless comparison, normalize both sides consistently. Unicode normalization is a distinct operation and may also be necessary.

Classification methods include isalpha(), isdigit(), isdecimal(), isnumeric(), isalnum(), isspace(), islower(), and isupper().

~~~python
print("204".isdecimal())  # True
print("²".isdigit())      # True
print("²".isdecimal())    # False
~~~

These methods follow Unicode definitions. They do not automatically enforce an ASCII-only identifier policy. State the allowed alphabet explicitly when a protocol or specification requires it.

## String-method reference

| Task | Useful methods | Important distinction |
|---|---|---|
| Trim whitespace | strip(), lstrip(), rstrip() | Does not remove internal whitespace |
| Replace substrings | replace() | Literal substring replacement |
| Remove exact edge text | removeprefix(), removesuffix() | Exact match, unlike strip(chars) |
| Split | split(), rsplit(), splitlines() | splitlines() recognizes line boundaries |
| Divide once | partition(), rpartition() | Returns a three-item tuple |
| Search | find(), rfind(), index(), rindex(), count() | Choose missing-substring behavior deliberately |
| Change case | lower(), upper(), title(), capitalize(), swapcase(), casefold() | Case conversion is not normalization |
| Classify | isalpha(), isdecimal(), isdigit(), isnumeric(), isalnum(), isspace(), isidentifier() | Unicode-aware; not a complete application validator |
| Align and pad | center(), ljust(), rjust(), zfill() | Useful for terminal output |

Examples:

~~~python
filename = "report.final.csv"
print(filename.removesuffix(".csv"))  # report.final
record = "RX-07:online:562"
print(record.partition(":"))  # ('RX-07', ':', 'online:562')
print("42".zfill(5))  # 00042
print("RX".center(8, "-"))  # ---RX---
~~~

Use unicodedata.normalize() when the specification requires consistent Unicode normalization. Normalization is separate from lower() and casefold(); do not normalize opaque identifiers unless their rules allow it.

~~~python
import unicodedata
first = "é"
second = "e\\u0301"
print(unicodedata.normalize("NFC", first) == unicodedata.normalize("NFC", second))
~~~

## 7. Splitting and joining

split() divides text into pieces; join() combines strings with a separator.

~~~python
raw = "red, green, blue"
parts = raw.split(",")
first = parts[0].strip()
second = parts[1].strip()
third = parts[2].strip()
result = " | ".join([first, second, third])
print(result)  # red | green | blue
~~~

With no separator, split() groups runs of whitespace. With an explicit separator, empty fields can be preserved.

~~~python
print("a  b".split())      # ['a', 'b']
print("a,,b,".split(","))  # ['a', '', 'b', '']
~~~

A list comprehension is a compact alternative for cleaning each part; it is previewed here and taught systematically in Data Structures.

Do not use split() as a universal parser. CSV quoting, escaping, nested structures, and formal formats require their dedicated parsers.

## 8. Formatting with f-strings

F-strings embed expressions in braces. A format specification follows a colon.

~~~python
name = "Receiver A"
frequency_mhz = 562.34567
print(f"{name}: {frequency_mhz:.2f} MHz")
~~~

Output: Receiver A: 562.35 MHz.

| Format | Purpose |
|---|---|
| :.2f | Two decimal places |
| :,.2f | Thousands separator and two decimals |
| :>10 / :<10 / :^10 | Right / left / center alignment |
| :+.2f | Always show sign |
| :08d | Zero-pad an integer to width 8 |
| :.3e | Scientific notation |
| :.1% | Percentage with one decimal |

~~~python
voltage = 12.5
change = 0.075
identifier = 42
print(f"Voltage: {voltage:8.2f} V")
print(f"Change:  {change:+.1%}")
print(f"ID:      {identifier:06d}")
~~~

Formatting creates a display representation; it does not mutate or improve the precision of the stored value. Keep f-string expressions simple and calculate complicated values beforehand.

## 9. Unicode: code points, visible characters, and bytes

Python str values are sequences of Unicode code points. A visible character may consist of more than one code point. For example, an accented letter may be represented as one precomposed code point or as a base letter followed by a combining mark.

~~~python
precomposed = "é"
combined = "e\u0301"
print(precomposed == combined)  # False
print(len(precomposed))         # 1
print(len(combined))            # 2
~~~

They may look the same while having different code-point sequences. Unicode normalization, such as NFC, can standardize canonically equivalent text. The standard library module unicodedata provides normalization tools.

Distinguish:

- Code point: one Unicode value in the Python string.
- Grapheme cluster: a sequence users perceive as one character.
- Encoded bytes: a representation used for storage or transmission.

len(text) counts code points, not grapheme clusters and not UTF-8 bytes.

~~~python
text = "café"
encoded = text.encode("utf-8")
decoded = encoded.decode("utf-8")
print(type(text).__name__)      # str
print(type(encoded).__name__)  # bytes
print(len(text))                # 4
print(len(encoded))             # 5
print(decoded == text)           # True
~~~

This is an introduction only. Detailed bytes, files, and encoding behavior are covered later. Never infer transmitted byte length from len(text).

## 10. Common mistakes and debugging

1. Calling strip() or upper() and discarding the returned string.
2. Confusing indexing with slicing.
3. Concatenating a string and a number without conversion or formatting.
4. Assuming equality is case-insensitive.
5. Treating strip(chars) as exact substring removal.
6. Converting identifiers to numbers and losing leading zeroes.
7. Assuming one visible symbol always equals one code point.
8. Treating split() as a parser for every data format.
9. Believing formatting changes the underlying numeric value.
10. Ignoring empty strings and whitespace-only input.

When debugging text, inspect both repr(value) and type(value).__name__. They reveal invisible whitespace and unexpected types.

## 11. Worked example: receiver label

The requirement is a label consisting of RX- followed by exactly two decimal digits. This example checks that shape; it is not a universal validation framework.

~~~python
label = " RX-07 "
cleaned = label.strip().upper()
has_prefix = cleaned.startswith("RX-")
channel_text = cleaned[3:]
has_two_digits = len(channel_text) == 2 and channel_text.isdecimal()
is_valid_shape = has_prefix and has_two_digits

print(f"Original: {label!r}")
print(f"Cleaned: {cleaned!r}")
print(f"Valid shape: {is_valid_shape}")
~~~

Test RX-7, rx-07, RX-AB, RX-007, empty text, and non-ASCII numerals. A correct implementation follows an explicit specification rather than assumptions.

## 12. Coding lab — Text label and report

Create string_lab.py.

1. Define a raw label with leading/trailing spaces and a hyphen.
2. Preserve the original and create a cleaned uppercase label with underscores.
3. Display both with repr().
4. Extract a substring with slicing.
5. Check a required prefix and suffix.
6. Split three comma-separated color names, clean them, and join with |.
7. Format a floating-point measurement with a unit and two decimal places.
8. Test empty text, missing substrings, out-of-range slices, and non-ASCII text.
9. Explain why the original strings remain unchanged.

Do not use loops, functions, classes, or exception handling; those are later topics.

## 13. Independent exercises

### Level 1 — Recall and predict

1. State the type and length of "42", 42, and "é".
2. For word = "PYTHON", predict word[0], word[-1], word[1:4], word[:3], word[::2], and word[::-1].
3. Explain "one\n two" versus r"one\n two".
4. Explain word[100] versus word[:100].

### Level 2 — Apply

5. Clean "  receiver-01  " by trimming, replacing hyphen with underscore, and uppercasing. Preserve the original.
6. Split "red, green, blue" into clean values and join with " | ".
7. Format 12345.6789 with thousands separator and two decimals.
8. When should find() be preferred to index()?
9. Check whether a label starts with RX- and ends with -01.

### Level 3 — Reason and debug

10. Repair code that discards strip() output and concatenates text with an integer.
11. Explain why visible symbols and len() counts can differ.
12. Explain why "000731" should remain a product-code string.
13. Compare lower() and casefold().
14. Propose a basic 3–12 character label rule that begins with a letter and contains no spaces. State its limitations.

## Exercise solutions

Attempt the exercises and knowledge check before opening the separate [strings — Exercise Solutions](./003-strings-solutions.md).

## Knowledge check

1. What does string immutability mean?
2. What does len() count?
3. Indexing versus slicing?
4. Why do string methods return new values?
5. find() versus index()?
6. split() versus join()?
7. What does :.2f do and not do?
8. Why can visually identical strings compare unequal?
9. str versus bytes?
10. Why is a serial number usually text?

## Summary and completion criteria

A str is an immutable sequence of Unicode code points. Indexing selects one code point; slicing extracts a range. Methods return new strings. Search, split, join, and formatting tools should be selected according to their precise behavior. Code points, grapheme clusters, and encoded bytes are different.

Study this lesson only after you can explain these distinctions, complete the lab independently, solve at least one exercise from each level, and debug a text-processing error using repr() and type inspection.

## Official references

- [Text Sequence Type — str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)
- [String Methods](https://docs.python.org/3/library/stdtypes.html#string-methods)
- [Format String Syntax](https://docs.python.org/3/library/string.html#format-string-syntax)
- [Formatted String Literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)
- [Unicode HOWTO](https://docs.python.org/3/howto/unicode.html)
- [unicodedata](https://docs.python.org/3/library/unicodedata.html)
