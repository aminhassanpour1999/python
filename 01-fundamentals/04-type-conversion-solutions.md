# Type Conversion — Exercise Solutions

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
## Knowledge check
1. Conversion creates another type; parsing interprets a representation.
2. int() truncates toward zero.
3. round() applies rounding rules; int() truncates.
4. "False" is non-empty and truthy.
5. ValueError means unacceptable value; TypeError means inappropriate type.
6. Yes, it may violate a range, unit, or domain constraint.
7. Numeric conversion can remove leading zeroes and formatting.
8. No. Formatting creates a display string.
## Lab review
Keep the identifier as str, parse binary text using base 2, compare truncation/rounding/floor for negatives, and distinguish parsing from domain validation.
