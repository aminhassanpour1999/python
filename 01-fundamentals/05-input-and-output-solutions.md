# Input and Output — Exercise Solutions

Open only after attempting the lesson.

## Level 1
1. input() returns str.
2. sep defaults to one space; end defaults to a newline.
3. Track sep between arguments and end after each call.
4. print() returns None.
## Level 2
5. print(f"Voltage: {voltage:.2f} V").
6. Example: "Enter elapsed time in seconds (s): ".
7. Keep raw strings in *_text names, convert to numbers, calculate, then format labelled output.
8. input() returns strings, so "3" + "4" becomes "34".
9. Test ordinary values, decimals, zero, negatives, empty input, and non-numeric text.
## Level 3
10. A serial number is an identifier; converting to int loses leading zeroes.
11. input() returns the typed characters except the trailing newline. float() accepts surrounding whitespace in numeric text.
12. Display precision does not create measurement accuracy.
13. The program may be waiting for interactive standard input unavailable in the runner.
14. Invalid format cannot be parsed; invalid range parses but violates a domain rule; incorrect unit uses an unexpected unit.
## Knowledge check
1. print() displays objects to a text stream.
2. sep separates arguments; end follows the final argument.
3. input() returns str.
4. Separate names make representation changes explicit.
5. Calculations can be tested with fixed values independently of terminal interaction.
6. Conversion changes/creates a type; validation checks requirements.
7. Units make measurements interpretable.
8. Fixed data makes tests repeatable.
## Lab review
Separate raw strings, numeric values, calculation, and output. State clearly that invalid input is not yet handled robustly.
