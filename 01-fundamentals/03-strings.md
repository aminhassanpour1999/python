# Strings

**Module:** Programming Fundamentals  
**Lesson:** 3 of 9 · **Level:** Beginner · **Study time:** 75–90 minutes  
**Prerequisites:** Variables and Data Types; basic expressions

## Purpose and learning objectives

Strings (type str) represent text. They are used for labels, messages, user input, identifiers, and text data. By the end of this lesson, you should be able to create string literals; explain quoting and escape sequences; use length, indexing, and slicing; explain immutability; combine and compare strings; use common methods; format values with f-strings; and recognize basic Unicode issues.

## 1. String literals

A string literal is text enclosed in quotes. Single and double quotes have the same meaning:

    language = 'Python'
    message = "It's a useful language."
    quotation = 'She said, "Hello!"'

Choose the quote style that makes the text easiest to read. A quote can also be escaped with a backslash:

    message = 'It\'s Python.'

Common escape sequences:

| Sequence | Meaning |
|---|---|
| \\n | Newline |
| \\t | Horizontal tab |
| \\r | Carriage return |
| \\\\ | Literal backslash |
| \\' or \\" | Quote character |
| \\uXXXX | Unicode code point |

    report = "Name:\tReceiver\nStatus:\tOnline"
    print(report)

Triple single or double quotes allow multiline strings. Newlines and indentation inside the literal are part of the string. Triple-quoted strings are also used for docstrings later; they are not comments.

A raw string literal has an r prefix. It is useful for text containing many backslashes, such as regular-expression patterns and Windows-style paths:

    path = r"C:\Users\Amin\Documents"
    pattern = r"\d+"

Raw strings are still str objects. A raw string cannot end with an odd number of backslashes because the final backslash would escape the closing quote.

## 2. Length, indexing, and slicing

Use len(text) to get the number of Unicode code points:

    word = "Python"
    print(len(word))  # 6

Indexes start at zero. Negative indexes count from the end:

    print(word[0])   # P
    print(word[1])   # y
    print(word[-1])  # n
    print(word[-2])  # o

An index outside the valid range raises IndexError. For a string of length n, valid positive indexes are 0 through n-1 and valid negative indexes are -n through -1.

A slice extracts a range:

    text = "0123456789"
    print(text[1:5])   # 1234
    print(text[:3])    # 012
    print(text[6:])    # 6789
    print(text[::2])   # 02468
    print(text[::-1])  # 9876543210

The general form is sequence[start:stop:step]. The start is included; the stop is excluded. Omitted values use defaults. A slice extending beyond the string boundaries is clipped rather than raising IndexError. This differs from indexing a single position.

## 3. Immutability

Strings are immutable: their contents cannot be changed in place.

    word = "Python"
    # word[0] = "J"  # TypeError
    new_word = "J" + word[1:]
    print(word)      # Python
    print(new_word)  # Jython

String methods also return new strings rather than modifying the original:

    label = "  SIGNAL  "
    cleaned = label.strip().lower()
    print(label)    #   SIGNAL
    print(cleaned)  # signal

If you want the transformed result under the original name, reassign it explicitly: label = label.strip().

## 4. Combining, repeating, and comparing strings

The + operator concatenates strings. Both operands must be strings:

    first = "Ada"
    last = "Lovelace"
    full_name = first + " " + last

The * operator repeats a string when multiplied by an integer:

    print("ha" * 3)  # hahaha
    print("-" * 20)

Use in and not in to test substring membership. These checks are case-sensitive:

    print("Python" in "Python is readable")  # True
    print("python" in "Python is readable")  # False

Strings support equality and ordering comparisons. Ordering is based on Unicode code points, not language-aware dictionary order. For ordinary labels, equality is usually what you need.

## 5. Useful string methods

| Method | Purpose |
|---|---|
| lower(), upper(), casefold() | Change letter case; casefold is intended for caseless matching |
| capitalize(), title() | Apply simple capitalization conventions |
| strip(), lstrip(), rstrip() | Remove whitespace or specified characters from the ends |
| replace(old, new) | Return a string with occurrences replaced |
| find(sub) | Return first position, or -1 if absent |
| index(sub) | Return first position, or raise ValueError if absent |
| count(sub) | Count non-overlapping occurrences |
| startswith(), endswith() | Test a prefix or suffix |
| split(sep) | Split text into a list of strings |
| isalpha(), isdigit(), isdecimal(), isalnum(), isspace() | Test character categories; do not confuse Unicode digit categories |\n| removeprefix(), removesuffix() | Remove an exact prefix or suffix when present |\n| partition(sep) | Split once into a three-part tuple |\n| center(), ljust(), rjust(), zfill() | Align or pad text for simple display |\n| join(iterable) | Join strings using the receiver as separator |

    raw = "  QPSK Receiver  "
    label = raw.strip().upper()
    print(label)  # QPSK RECEIVER

    csv_line = "red,green,blue"
    colors = csv_line.split(",")
    print(colors)
    print(" | ".join(colors))

Important distinctions:
- strip() removes from the ends, not from the middle.
- split() without an argument groups whitespace; split(",") uses the exact comma separator.
- join() is called on the separator, and every item must be a string.
- find() returns -1 when absent; index() raises ValueError.
- Methods return results. Assign the result if you need to keep it.

## 6. Formatting with f-strings

An f-string begins with f before its opening quote. Expressions inside braces are evaluated:

    name = "Amin"
    count = 3
    print(f"{name} recorded {count} measurements.")

A format specification follows a colon:

    voltage = 3.14159265
    print(f"{voltage:.2f}")     # 3.14
    print(f"{voltage:10.2f}")   # width 10
    print(f"{voltage:>10.2f}")  # right-aligned
    print(f"{voltage:^10.2f}")  # centered

Other useful formats:

    count = 1234567
    ratio = 0.875
    print(f"{count:,}")    # 1,234,567
    print(f"{ratio:.1%}")  # 87.5%
    print(f"{count:08d}")  # 01234567

Formatting controls presentation; it does not change the original value. A formatted result is a string. The debug form f"{variable=}" can display a name and its value. Use f-strings for readable output; do not use eval() to format data.

## 7. Unicode: a necessary distinction

Python strings represent Unicode text. They can contain characters from many writing systems. A string is a sequence of Unicode code points, but a visible symbol is not always one code point. Accented letters can use combining marks, and emoji can be sequences joined together. Therefore len() is not always the number of user-perceived characters.

Practical rules:
- Do not assume all text is ASCII.
- Do not slice international user-visible text by guessed positions unless the format guarantees them.
- Normalize text only when the task requires it.
- When reading or writing files, choose an explicit encoding such as UTF-8; file handling comes later.

## 8. Common mistakes

1. Concatenating a string and a number with +. Use an f-string or deliberate str() conversion.
2. Expecting a string method to mutate the original.
3. Confusing indexing with slicing; indexing can raise IndexError, while slices are clipped.
4. Using strip() to remove internal whitespace.
5. Assuming membership checks ignore case.
6. Calling join() on the list instead of on the separator.
7. Assuming len() counts visible emoji or grapheme clusters.

## 9. Coding lab — Clean and format a measurement label

Create string_report.py.

    raw_device = "  qpsk receiver  "
    frequency_mhz = 99.51234
    status = "online"

Tasks:
1. Predict len(raw_device) and raw_device[2:6] before running the code.
2. Create a cleaned uppercase label without changing raw_device.
3. Print a report using an f-string, two decimal places, and the MHz unit.
4. Check whether the cleaned label contains "QPSK". Test a lowercase search and explain the difference.
5. Split "red, green, blue", remove surrounding spaces from each item, and join them with " | ".
6. Add a tab and newline to a test string and observe strip().

Checklist:
- [ ] Predicted length and slice output.
- [ ] Preserved the original string.
- [ ] Used f-string formatting and units.
- [ ] Tested case-sensitive membership.
- [ ] Explained one limitation of len() for Unicode.

## 10. Independent exercises

Attempt before reading the answer key.

1. Explain the difference between "one\\ntwo", r"one\\ntwo", and a triple-quoted string spanning two lines.
2. For text = "PYTHON", predict text[0], text[-1], text[1:4], text[:3], text[::2], and text[::-1].
3. Explain why replacing word[0] is invalid and rewrite it to produce "Jython".
4. Transform "  receiver-01   " into "RECEIVER_01" without changing the original.
5. Convert "red, green, blue" into "red | green | blue".
6. Given name = "Sensor A" and value = 12.34567, print "Sensor A: 12.35 units" with an f-string.
7. Explain the different missing-substring behavior of find() and index().
8. Why can len("👩‍💻") be greater than one?
9. Repair: count = 5; message = "Samples: " + count.

## Answer key

1. The ordinary literal contains a newline; the raw literal contains a backslash followed by n; the triple-quoted literal contains the source newline.
2. P, N, YTH, PYT, PTO, NOHTYP.
3. Strings are immutable. One solution: word = "J" + word[1:].
4. cleaned = raw.strip().replace("-", "_").upper().
5. Split on comma, strip each item, then join with " | ". A readable solution:
   
       items = [item.strip() for item in "red, green, blue".split(",")]
       result = " | ".join(items)

6. print(f"{name}: {value:.2f} units")
7. find() returns -1; index() raises ValueError.
8. The displayed emoji is a sequence of Unicode code points joined as one grapheme.
9. message = f"Samples: {count}"

## Knowledge check

1. What is the difference between indexing and slicing?
2. Why is the slice stop position excluded?
3. What does immutability mean?
4. What do split() and join() do?
5. What does .2f control?
6. Why is len() not always the count of visible characters?

## Summary and completion criteria

Strings are immutable sequences of Unicode code points. Indexing selects one position; slicing extracts a range with an exclusive stop. Methods return results, and f-strings provide readable interpolation and formatting.

- [ ] I can create ordinary, escaped, raw, and multiline strings.
- [ ] I can predict indexing and slicing.
- [ ] I can explain immutability.
- [ ] I can use common string methods and f-strings.
- [ ] I can explain the code-point versus visible-character distinction.
- [ ] I completed the lab and attempted the exercises independently.

## Official references

- [Python Tutorial — Text](https://docs.python.org/3/tutorial/introduction.html#text)
- [Built-in Types — str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)
- [String Methods](https://docs.python.org/3/library/stdtypes.html#string-methods)
- [Formatted String Literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)
- [Unicode HOWTO](https://docs.python.org/3/howto/unicode.html)
