# Strings — Exercise Solutions

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
## Knowledge check
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
## Lab review
Preserve the original, save transformations separately, use repr() to expose whitespace, test missing substrings, format units, and explain why len() is neither grapheme count nor byte count.
