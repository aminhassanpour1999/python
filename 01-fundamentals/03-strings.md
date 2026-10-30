# Strings

**Prerequisites:** Variables and Data Types; Numbers and Operators  
**Study time:** 90–120 minutes plus independent practice


**Module:** Programming Fundamentals  
**Lesson:** 3 of 9  
**Level:** Beginner  
**Prerequisites:** Variables and Data Types; Numbers and Operators

## Lesson guide

This lesson develops the string type from its underlying model to practical text processing. Read one section at a time, predict outputs before running examples, and inspect invisible characters with `repr()`. Do not treat the method reference as a list to memorize: understand the behavior and choose an operation that matches the requirement.

**Recommended workflow**

1. Review the mental model and distinguish text from numeric values and bytes.
2. Type the examples and predict their outputs before execution.
3. Experiment with empty strings, whitespace, punctuation, Unicode, and missing search results.
4. Complete the lab and independent exercises without opening the model answers.
5. Use the knowledge check to identify concepts that need another pass.

## Learning objectives

By the end of this lesson, you should be able to:

- Explain that `str` is an immutable sequence of Unicode code points.
- Create ordinary, escaped, raw, and multiline string literals correctly.
- Use `len()`, positive and negative indexing, and slicing with start, stop, and step.
- Explain indexing errors, slice clipping, and exclusive stop boundaries.
- Combine, repeat, compare, and search strings, including membership and lexicographic ordering.
- Choose appropriate search, trimming, replacement, classification, splitting, partitioning, joining, and alignment methods.
- Explain why string methods return new values and avoid discarding their results.
- Format values with f-strings and common format specifications.
- Distinguish Unicode code points, grapheme clusters, normalization, and encoded bytes.
- Build and test a small text-processing program with explicit assumptions and edge cases.


## 1. The string mental model

### 1.1 Text is not a byte sequence

A Python `str` represents text as a sequence of Unicode code points. It is not a sequence of UTF-8 bytes. Encoding converts text to bytes for storage or transmission; decoding converts bytes back to text using a specified encoding.

This distinction matters whenever text crosses a file, network, or device boundary. The same visible text can have different byte representations under different encodings, and invalid byte sequences may fail to decode.


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

### 2.1 Quoting, adjacent literals, and literal boundaries

Single-quoted and double-quoted literals create the same type. Choose the quote style that avoids unnecessary escaping:

~~~python
apostrophe = "It's ready."
quotation = 'She said "ready".'
~~~

Python also joins adjacent string literals at compile time when they appear next to one another:

~~~python
message = (
    "The receiver is online "
    "and the measurement is valid."
)
print(message)
~~~

This is useful for long source-code lines. It is not the same as joining values stored in variables at runtime.

A string literal is different from a string expression. For example, `"RX-" + channel` performs concatenation at runtime. Adjacent literals are combined as part of parsing the source.

### 2.2 Escape details and Unicode literals

An escape sequence is interpreted when Python parses an ordinary string literal. If a backslash is followed by characters that do not form a recognized escape, Python may preserve it while issuing a warning depending on the version; do not rely on accidental escape behavior. Use a raw literal or double the backslash when that is the intended meaning.

~~~python
letter = "\u03A9"
code_point = "\u03A9"
print(letter)       # Ω
print(ord(letter))  # 937
~~~

The source spelling `"\\u03A9"` produces the Unicode character Ω. To store the six visible characters backslash-u-0-0-3-A-9, use a raw literal such as `r"\u03A9"` or escape the backslash.


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

### 3.1 Indexing precisely

For a string of length `n`, valid positive indexes are from `0` through `n - 1`; valid negative indexes are from `-n` through `-1`. Index `0` selects the first code point, and index `-1` selects the last.

~~~python
text = "RADIO"
# Valid: text[0], text[4], text[-1], text[-5]
# Invalid: text[5], text[-6]
~~~

Indexing an empty string always raises `IndexError`, because it has no valid position. Check the length or test for emptiness before indexing when the string may be empty.

### 3.2 Slicing precisely

For `text[start:stop:step]`, Python selects positions beginning at `start`, moving by `step`, and stopping before `stop`. The stop boundary is exclusive. A positive step moves left to right; a negative step moves right to left. A step of zero is invalid and raises `ValueError`.

~~~python
text = "0123456789"
print(text[2:8:2])   # 246
print(text[8:2:-2])  # 864
print(text[5:1:-1])  # 5432
print(text[5:1])     # ''
~~~

The last expression is empty because the default step is positive, while the start is greater than the stop. A negative step is required to move in the reverse direction.

Slicing is forgiving at the boundaries: indexes outside the string are clipped. This is why `text[:100]` is safe even when the string is shorter than 100 code points. Slicing does not raise `IndexError` merely because a boundary is outside the sequence.

### 3.3 Slices create strings; they do not edit the source

A slice returns a string value. Because strings are immutable, slicing and concatenation are common ways to construct a modified result:

~~~python
serial = "RX-2026-007"
short_serial = serial[:3] + serial[-3:]
print(short_serial)  # RX-007
print(serial)        # RX-2026-007
~~~


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

### 4.1 Why immutability matters

Immutability means that once a string object has been created, its sequence of code points cannot be changed in place. This makes strings predictable when they are passed to other parts of a program: one operation cannot silently edit the contents of an existing string object.

An operation that appears to modify a string actually creates a result:

~~~python
status = "offline"
updated_status = status.replace("off", "on")
print(status)          # offline
print(updated_status)  # online
~~~

If you want the name `status` to refer to the new value, rebind it explicitly:

~~~python
status = status.replace("off", "on")
~~~


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

### 5.1 Concatenation, repetition, and type boundaries

The `+` operator concatenates two strings, and `*` repeats a string by an integer count. These operations do not perform general conversion:

~~~python
prefix = "RX-"
channel = 7
# label = prefix + channel  # TypeError
label = prefix + str(channel)
print(label)  # RX-7
print("ha" * 3)  # hahaha
print("ha" * 0)  # ''
~~~

For output that combines text and numbers, an f-string is often clearer than manually converting and concatenating each part.

### 5.2 Lexicographic comparison is not numeric or linguistic sorting

String comparisons are lexicographic and case-sensitive. Python compares code-point values in sequence until a difference is found or one string ends. This explains why `"10" < "2"` is true: the first character `"1"` sorts before `"2"`.

This ordering is not a numeric comparison and is not necessarily the order a person expects in a language-specific dictionary. Parse numeric text when numeric ordering is intended. Locale-aware collation requires a separate, explicit approach.


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

#### Search details and empty substrings

Search methods operate on literal substrings; they do not interpret wildcards or regular expressions.

~~~python
text = "receiver receiver"
print(text.count("receiver"))  # 2
print(text.find(""))           # 0
print(text.startswith(("RX-", "TX-")))  # False
~~~

An empty substring is considered to occur at valid boundaries, so methods such as `find("")` have defined results. Be careful when the search term can be empty: a successful search may not mean that useful content was found.

The optional `start` and `end` arguments on search methods restrict the region being searched. Their boundaries follow Python's sequence indexing conventions.


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

### 6.1 Replacement and exact edge removal

`replace(old, new)` returns a new string with matching occurrences replaced. Its optional `count` argument limits how many replacements are made:

~~~python
text = "A-B-C-D"
print(text.replace("-", "_"))       # A_B_C_D
print(text.replace("-", "_", 2))    # A_B_C-D
~~~

Use `removeprefix()` and `removesuffix()` when the requirement is to remove one exact prefix or suffix. They leave the string unchanged if the exact text is not present.

~~~python
filename = "report.csv.backup"
print(filename.removesuffix(".csv"))  # report.csv.backup
print(filename.removesuffix(".backup"))  # report.csv
~~~

By contrast, `strip(chars)` treats its argument as a set of characters to remove repeatedly from both ends. It does not remove one exact multi-character token.

### 6.2 Classification is not full validation

Methods such as `isalpha()`, `isdecimal()`, `isdigit()`, `isnumeric()`, and `isalnum()` answer specific Unicode-based classification questions. They do not know the rules of your application, protocol, product code, or user account.

For example, a value may satisfy `isnumeric()` but still be invalid as a decimal number accepted by a particular interface. Define the allowed format first, then choose checks that implement that format. Detailed parsing and validation are covered in the Type Conversion lesson.


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

### 6.3 Additional text operations

`partition(separator)` splits at the first occurrence and always returns a three-item tuple: text before the separator, the separator itself, and text after it. If the separator is absent, the original string is returned as the first item and the other two items are empty.

~~~python
record = "RX-07:online:562"
print(record.partition(":"))
# ('RX-07', ':', 'online:562')
print("no separator".partition(":"))
# ('no separator', '', '')
~~~

`rpartition()` performs the corresponding operation at the last occurrence. `splitlines()` splits on recognized line boundaries and is often more suitable than splitting only on the literal newline character.


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
second = "e\u0301"
print(unicodedata.normalize("NFC", first) == unicodedata.normalize("NFC", second))
~~~

## 7. Splitting and joining

### 7.1 split() details

With no separator, `split()` treats runs of whitespace as one separator and discards leading/trailing empty fields. With an explicit separator, adjacent separators can produce empty fields. The optional `maxsplit` argument limits the number of splits.

~~~python
print("  red   green blue  ".split())
# ['red', 'green', 'blue']
print("red,,blue".split(","))
# ['red', '', 'blue']
print("key=value=extra".split("=", 1))
# ['key', 'value=extra']
~~~

Do not split a structured format by hand if its rules include quoting, escaping, nested values, or other grammar. Use the format's dedicated parser when the data is CSV, JSON, or another formal format.

### 7.2 join() details

The separator's `join()` method combines an iterable of strings. Every item must be a string; a non-string item raises `TypeError`. The separator appears only between items, not at the beginning or end.

~~~python
parts = ["RX", "07", "online"]
print(":".join(parts))  # RX:07:online
~~~


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

### 8.1 Format-specification anatomy

A format specification can control fill character, alignment, sign, width, grouping, precision, and presentation type. Not every option applies to every value type.

~~~python
value = 12345.678
print(f"{value:*>12,.2f}")  # ****12,345.68
print(f"{-7:+d}")           # -7
print(f"{42:06d}")          # 000042
~~~

For floating-point values, precision after a decimal point generally controls the number of digits displayed after the decimal separator for fixed-point formatting. It does not change the stored float and does not guarantee measurement accuracy.


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

### 9.1 Code points and grapheme clusters

A Python string index selects a Unicode code point, not necessarily one complete symbol as perceived by a user. A grapheme cluster is a sequence of one or more code points that a text-rendering system treats as one user-perceived character. Combining marks, emoji modifiers, and joined emoji sequences are common reasons these counts differ.

~~~python
import unicodedata

composed = "é"
decomposed = "e\u0301"

print(len(composed))       # 1
print(len(decomposed))     # 2
print(unicodedata.normalize("NFC", decomposed) == composed)  # True
~~~

The standard library's `unicodedata.normalize()` supports four normalization forms:

| Form | General purpose |
|---|---|
| NFC | Canonical decomposition followed by composition where possible |
| NFD | Canonical decomposition |
| NFKC | Compatibility decomposition followed by composition |
| NFKD | Compatibility decomposition |

Compatibility normalization may change distinctions that matter in identifiers or source text. Do not apply it blindly. Choose a normalization form only when the application's specification calls for it.

### 9.2 Inspecting code points

`ord()` returns the code point value of a one-character string, and `chr()` creates the character represented by a valid code point integer:

~~~python
symbol = "Ω"
print(ord(symbol))  # 937
print(chr(937))     # Ω
~~~

These functions work with one code point at a time. They do not count or extract user-perceived grapheme clusters.

### 9.3 Encoding and decoding

Encoding is an explicit boundary between text and bytes. UTF-8 is a common encoding, but the correct encoding must come from the file or protocol specification.

~~~python
text = "café"
data = text.encode("utf-8")
restored = data.decode("utf-8")

print(data)                 # b'caf\xc3\xa9'
print(len(text), len(data)) # 4 5
print(restored == text)     # True
~~~

Decoding bytes with the wrong encoding can produce incorrect text or raise `UnicodeDecodeError`. Encoding text with a restrictive encoding can raise `UnicodeEncodeError` if a character cannot be represented. Do not silently ignore or replace errors unless the data-loss policy is intentional and documented.


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

### Debugging checklist for text

When a string behaves unexpectedly, ask:

1. Is the value actually a `str`, or is it bytes, a number, or `None`?
2. Does `repr(value)` reveal leading/trailing whitespace, tabs, newlines, or backslashes?
3. Is the operation case-sensitive?
4. Is the search substring absent or empty?
5. Is the code using a character index while assuming a byte offset or visible-character position?
6. Was the return value of an immutable string method saved?
7. Does the input follow the expected encoding and normalization policy?

Use a minimal example with the exact text that caused the issue. For Unicode problems, include the code points or `repr()` output rather than relying only on how the text looks on screen.


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

### Lab goal and acceptance criteria

**Goal:** Build a short, deterministic text report from a device label, a list of text fields, and a numeric measurement.

Your finished script must:

- Preserve the raw input string and store cleaned text in a separate name.
- Use `repr()` to make whitespace visible during inspection.
- Extract the intended section using a correct slice boundary.
- Check a prefix and suffix without confusing absence with an empty search term.
- Split and clean the supplied comma-separated values, then join them with the requested separator.
- Format the numeric measurement with a unit and the specified precision.
- Include tests for empty input, missing delimiters, repeated delimiters, non-ASCII text, and an out-of-range slice.
- Explain why the original string is unchanged after transformations.

**Constraints:** do not use loops, user-defined functions, classes, regular expressions, or exception handling. Those features belong to later stages. If the lab uses a list literal for a few known parts, treat it as provided data; collection behavior is not the learning target.


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

Attempt every exercise before reading the model answers. For prediction tasks, write the output first; for code-writing tasks, run your solution and test at least one edge case.


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

## Exercise solutions — open after attempting the exercises

Open only after attempting the lesson. Equivalent correct reasoning is acceptable.

## Level 1
1. "42" is str with length 2; 42 is int; precomposed "é" has length 1.
2. For PYTHON: P, N, YTH, PYT, PTO, NOHTYP.
3. The ordinary literal interprets backslash-n as a newline; the raw literal preserves backslash plus n.
4. Indexing requests one position and raises IndexError if absent; slicing clips boundaries.
## Level 2
5. cleaned = raw.strip().replace("-", "_").upper(). The original remains unchanged.
6. Split on comma, strip each part, then join with " | ".
7. f"{12345.6789:,.2f}" displays 12,345.68.
8. find() returns -1 when absent; index() raises ValueError.
9. text.startswith("RX-") and text.endswith("-01").
## Level 3
10. Save the return value of strip(); use an f-string to combine text and an integer.
11. len() counts Unicode code points. A visible symbol can contain multiple code points.
12. A product code is an identifier. int() removes leading zeroes.
13. lower() lowercases; casefold() is designed for caseless matching and handles more Unicode distinctions. Normalization may still be needed.
14. A basic guarded rule is non-empty, length 3–12, first character isalpha(), and no spaces. This still allows many Unicode letters and does not define all permitted punctuation.
## Lab review
Preserve the original, save transformations separately, use repr() to expose whitespace, test missing substrings, format units, and explain why len() is neither grapheme count nor byte count.

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


### Knowledge check — Suggested answers

1. String contents cannot be changed in place.
2. Unicode code points.
3. Indexing selects one position; slicing selects a range with exclusive stop.
4. str is immutable, so methods return new strings.
5. find() returns -1; index() raises ValueError.
6. split() divides text; join() combines strings with a separator.
7. :.2f controls displayed decimal places, not stored value or accuracy.
8. They may use different code-point sequences, such as precomposed and combining forms.
9. str is text; bytes is a sequence of byte values.
10. Identifiers may need leading zeroes and exact formatting.

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
