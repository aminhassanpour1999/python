# Input and Output

**Prerequisites:** Variables and Data Types; Numbers and Operators; Strings; Type Conversion  
**Study time:** 60–90 minutes

## Purpose and learning outcomes

A useful program receives information, processes it, and communicates a result. This lesson covers basic terminal interaction with input() and print(). You will understand their return behavior, design clear prompts, separate raw input from computation, and test programs independently of an interactive terminal.

## 1. Output with print()

print() displays objects to a text stream. In ordinary beginner programs, that stream is usually standard output.

~~~python
print("Hello, Python!")
print(12)
print(3.5)
~~~

By default, print() separates multiple arguments with a space and ends with a newline.

~~~python
print("A", "B", "C")
print("A", "B", "C", sep="-")
print("Start", end=" ")
print("finish")
~~~

Output:

~~~text
A B C
A-B-C
Start finish
~~~

- sep controls the text between arguments.
- end controls the text after the final argument.
- file selects the output stream.
- flush controls whether the stream is forcibly flushed.

The defaults are sep=" " and end="\\n". At this stage, focus on sep and end.

### print() does not return the displayed text

~~~python
result = print("Displayed")
print(result)
~~~

Output:

~~~text
Displayed
None
~~~

print() performs an output action and returns None. Displaying something is not the same as returning a value.

### 1.1 Output streams and flushing

By default, print() writes to the standard output stream. Its file parameter can direct output to another text stream; flush requests that the stream be flushed immediately.

~~~python
import sys

print("Normal information")
print("Diagnostic message", file=sys.stderr)
print("Progress update", end=" ", flush=True)
print("done")
~~~

This is an introductory view of standard output and standard error. File and stream management are covered later. For ordinary beginner scripts, the default output stream is sufficient.

### 2.1 What input() does not do

input(prompt) displays the prompt without automatically adding a newline, reads one line, removes the trailing newline, and returns the remaining text. It does not automatically remove surrounding spaces or validate the text.

~~~python
raw_text = "  12.5  "
print(repr(raw_text))          # '  12.5  '
print(float(raw_text))         # 12.5
print(repr(raw_text.strip()))  # '12.5'
~~~

If the input stream reaches end-of-file before a line can be read, input() raises EOFError. This can happen when a program expects interactive input but is run in an environment with no input available. Handling EOFError is part of robust exception handling, taught later.

### 2.2 A complete example interaction

For this program:

~~~python
first_text = input("First voltage (V): ")
second_text = input("Second voltage (V): ")

first_v = float(first_text)
second_v = float(second_text)
average_v = (first_v + second_v) / 2

print(f"Average voltage: {average_v:.2f} V")
~~~

A sample interaction is:

~~~text
First voltage (V): 12.5
Second voltage (V): 13.5
Average voltage: 13.00 V
~~~

The text typed by the user appears after each prompt. The program's final line is printed output. This example assumes both inputs are valid numeric strings.

## 2. Input with input()

input() displays an optional prompt, reads one line from standard input, removes its trailing newline, and returns a string.

~~~python
name = input("Your name: ")
print(f"Hello, {name}!")
~~~

Even if the user types digits, the result is text.

~~~python
age_text = input("Age: ")
print(type(age_text).__name__)  # str
~~~

Convert explicitly before numeric operations.

~~~python
first_text = input("First number: ")
second_text = input("Second number: ")
first_number = float(first_text)
second_number = float(second_text)
total = first_number + second_number
print(f"Total: {total:.2f}")
~~~

Do not assume that input is valid just because the prompt asks for a number. Users can submit empty text, letters, unexpected units, or out-of-range values.

## 3. Separate the stages of a program

Use this mental model:

1. **Acquire:** read raw input as text.
2. **Interpret:** convert it to the intended type.
3. **Compute:** perform the calculation.
4. **Present:** format and display the result.

~~~python
distance_text = input("Distance (km): ")
time_text = input("Elapsed time (h): ")

distance_km = float(distance_text)
elapsed_hours = float(time_text)
average_speed_kmh = distance_km / elapsed_hours

print(f"Average speed: {average_speed_kmh:.2f} km/h")
~~~

This example assumes numeric text and nonzero time. It deliberately does not implement robust validation or exception handling; those belong later.

Separate names help reveal where data changes representation. Avoid reusing one name for raw text and converted numeric data when that makes the program harder to reason about.

## 4. Design good prompts and output

A prompt should state what is expected. A result should explain what the number means.

~~~python
voltage_v = float(input("Enter voltage in volts (V): "))
doubled_voltage_v = voltage_v * 2
print(f"Twice the voltage: {doubled_voltage_v:.2f} V")
~~~

Useful output includes a descriptive label, unit, appropriate precision, and a sign when direction matters. Formatting does not create measurement accuracy: six displayed decimal places do not mean the instrument measured six decimal places reliably.

## 5. Fixed data versus interactive input

Interactive input is convenient for people but awkward for repeatable automated tests. Test a calculation with fixed values before adding prompts.

~~~python
distance_km = 12.5
elapsed_hours = 0.5
average_speed_kmh = distance_km / elapsed_hours
print(f"{average_speed_kmh:.2f} km/h")
~~~

Try different values and predict results first. This separates calculation correctness from terminal interaction. Later, functions will make this separation cleaner.

## 6. Basic checks and current limitations

At this stage, you can perform simple checks such as testing whether text is empty or matches an allowed word.

~~~python
raw_name = input("Name: ")
clean_name = raw_name.strip()

if clean_name:
    print(f"Hello, {clean_name}")
else:
    print("A name is required.")
~~~

This previews if, which is taught in Control Flow. Do not build complex validation before learning the relevant tools.

float(raw_text) may raise ValueError. A robust interactive program should explain the problem and allow a retry. Exception handling and loops are taught later.

## 7. Common mistakes

1. Assuming input is numeric: input() always returns str.
2. Adding numeric-looking strings: "3" + "4" produces "34".
3. Ignoring units: a value of 5 is ambiguous without a unit.
4. Dividing by zero: a value may be numeric but invalid for a calculation.
5. Overstating precision: display precision is not measurement accuracy.
6. Mixing interface and calculation: hard-coded prompts make logic harder to test.
7. Confusing print and return: print displays and returns None.
8. Assuming every environment is interactive: IDE consoles, notebooks, automated tests, and online runners may handle standard input differently.

## 8. Coding lab — Interactive average calculator

Create input_output_lab.py.

1. Ask for two voltage readings and include V in each prompt.
2. Store raw input in variables ending in _text.
3. Convert both explicitly to float.
4. Calculate the average.
5. Display both readings and the average with labels and units.
6. Use sep in one output statement and end in another.
7. Test the calculation separately with fixed values.
8. Record what happens with empty input, non-numeric text, zero, and negative values. Do not claim robust handling if it is not implemented.

## 9. Independent exercises

### Level 1

1. What does input() return?
2. What are print()'s default sep and end values?
3. Predict the exact output of calls using default and custom sep/end.
4. What does print() return?

### Level 2

5. Display voltage with two decimal places and its unit.
6. Rewrite a vague prompt so it names the expected unit.
7. Separate raw text, converted values, calculation, and output in a speed calculator.
8. Why does "3" + "4" not perform numeric addition?
9. List four useful test inputs for a numeric command-line program.

### Level 3

10. Why should a serial number not be converted to int?
11. What happens when numeric input contains surrounding spaces?
12. Why can displaying many decimal places be misleading?
13. A script waits in an automated environment. Give a plausible explanation.
14. Distinguish invalid format, invalid range, and incorrect unit.

## Exercise solutions — open after attempting the exercises

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

## Knowledge check

1. What is print() for?
2. What do sep and end control?
3. Why must input often be converted?
4. Why keep raw and converted values separately?
5. What is gained by separating calculation from input/output?
6. Conversion versus validation?
7. Why should output include units?
8. Why are fixed values useful for testing?

## Summary and completion criteria

input() returns text; conversion is explicit. print() displays objects and returns None. Separate acquisition, conversion, computation, and presentation. Label values and units, and choose display precision responsibly. Complete the lab, predict output, and explain what the current version does not yet handle before marking this lesson studied.

## Official references

- [input()](https://docs.python.org/3/library/functions.html#input)
- [print()](https://docs.python.org/3/library/functions.html#print)
- [Formatted String Literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)
