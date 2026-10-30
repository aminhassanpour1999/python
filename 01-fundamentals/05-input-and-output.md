# Input and Output

**Module:** Programming Fundamentals  
**Lesson:** 5 of 9 · **Level:** Beginner · **Study time:** 60–75 minutes  
**Prerequisites:** Variables and Data Types; Strings; Type Conversion

## Purpose and learning objectives

A program becomes interactive when it receives information and communicates results. By the end, you should be able to use print() with sep and end; explain that input() returns a string; build an input → conversion → calculation → output workflow; design clear prompts; format results with f-strings and units; and identify basic validation requirements.

## 1. Output with print()

print() displays objects and, by default, writes a newline afterward:

    print("Hello, Python!")
    print(42)
    print(3.14)

You can pass multiple arguments. By default, one space separates them:

    name = "Receiver"
    frequency = 99.5
    print("Device:", name, "Frequency:", frequency)

The sep parameter controls the separator:

    print("2026", "10", "30", sep="-")
    print("red", "green", "blue", sep=" | ")

The end parameter controls what is written after the final argument. It defaults to a newline:

    print("Loading", end="...")
    print("done")

Use sep and end when they improve the output; do not use them merely to make code clever.

## 2. Input with input()

input(prompt) displays an optional prompt, reads one line of text, removes the trailing newline, and returns a string:

    name = input("What is your name? ")
    print(f"Hello, {name}!")

Even if the user types digits, input() does not automatically return a number:

    age = input("Enter your age: ")
    print(type(age))  # <class 'str'>

The input is text and must be converted before numeric arithmetic.

## 3. Input-to-computation workflow

A common beginner program follows four steps:

1. Ask for information.
2. Convert it to the required type.
3. Perform the calculation.
4. Display a labelled result.

    first_text = input("First measurement in volts: ")
    second_text = input("Second measurement in volts: ")

    first = float(first_text)
    second = float(second_text)
    average = (first + second) / 2

    print(f"Average: {average:.2f} V")

This version assumes both inputs are valid numeric strings. If a user enters "unknown", conversion raises ValueError. Robust handling is taught in the later Exceptions lesson. Understand this limitation and test it deliberately.

## 4. Design good prompts and output

A good prompt states what information is required and, when relevant, the unit and accepted format.

Weak: "Value: "  
Better: "Enter temperature in degrees Celsius: "

Output should explain what a value means:

    distance_km = 12.5
    time_hours = 0.5
    speed_kmh = distance_km / time_hours

    print(f"Distance: {distance_km:.1f} km")
    print(f"Time: {time_hours:.2f} h")
    print(f"Average speed: {speed_kmh:.1f} km/h")

Do not imply precision that the measurement does not support. Printing many decimal places does not make a measurement more accurate.

## 5. Interactive versus fixed data

Fixed values are often easier to reproduce and test:

    first = 10.0
    second = 20.0
    average = (first + second) / 2
    print(f"Average: {average:.1f}")

An interactive version uses input(), but the calculation can remain the same. Notice which lines receive input, which calculate, and which display results. Keeping these responsibilities distinct makes later testing easier.

## 6. Basic input checks

Before using input, consider:
- Is it empty or only whitespace?
- Is it in the expected format?
- Can it be converted?
- Is it within the allowed range?
- Does it use the expected unit?

Conversion is not validation. float("-10") succeeds, but a negative value may be invalid for a particular quantity. Branching and robust exception handling are taught later.

## 7. Common mistakes

1. Assuming input() returns a number.
2. Concatenating a number and text with + instead of using an f-string.
3. Omitting units or labels.
4. Writing vague prompts.
5. Displaying unjustified decimal precision.
6. Assuming conversion proves that the value is meaningful.
7. Ignoring invalid input or silently replacing it with zero.
8. Mixing input, calculation, and presentation into one unreadable expression.

## 8. Coding lab — Interactive average calculator

Create average_calculator.py.

Tasks:
1. Ask for two measurements using prompts that specify the unit.
2. Store the returned strings in names ending with _text.
3. Convert both to floats and inspect their types.
4. Calculate the average in a separate variable.
5. Print the inputs and average with labels, two decimal places, and units.
6. Test whole numbers, decimals, zero, a negative value, and invalid text.
7. Write a note explaining what the current program does not handle.

Checklist:
- [ ] Clear prompts.
- [ ] Explicit conversion.
- [ ] Separate calculation and presentation.
- [ ] Labels and units in output.
- [ ] Normal and invalid input tested.
- [ ] Limitation documented.

## 9. Independent exercises

1. Predict the exact output and line breaks:
   
       print("A", "B", "C")
       print("A", "B", "C", sep="-")
       print("Start", end=" ")
       print("finish")

2. Why does adding inputs "3" and "4" produce text "34" rather than numeric 7? Rewrite it for numeric addition.
3. Given voltage = 12.3456, print "Voltage: 12.35 V".
4. Improve the prompts "Value: " and "Time: " by stating the expected quantity and unit.
5. Rewrite a long input/calculation/output expression using meaningful intermediate variables.
6. List four test inputs for a calculator and explain what each checks.
7. Why is displaying ten decimal places not proof of ten-decimal-place accuracy?

## Answer key

1. Three lines: "A B C", "A-B-C", and "Start finish".
2. input() returns strings, and + concatenates them. Convert both to float or int before addition.
3. print(f"Voltage: {voltage:.2f} V")
4. Example: "Enter temperature in degrees Celsius: " and "Enter elapsed time in seconds: ".
5. Use separate input, conversion, calculation, and print statements.
6. Useful cases include ordinary integers, decimals, zero, a boundary value, negative input, empty input, and non-numeric text.
7. Formatting controls display; it cannot add precision absent from the source measurement.

## Knowledge check

1. What do sep and end control?
2. What does input() return?
3. Why must numeric input be converted?
4. How is validation different from conversion?
5. Why should output include units?
6. Why are fixed values useful for repeatable tests?

## Summary and completion criteria

print() displays values; sep and end customize separators and endings. input() reads one line and returns a string. A clear beginner script separates input, conversion, calculation, and output. Prompts and results should include context and units.

- [ ] I can use print() with sep and end.
- [ ] I can explain input()'s return type.
- [ ] I can build an input-to-calculation workflow.
- [ ] I can format readable output with units.
- [ ] I tested normal and invalid input and documented limitations.
- [ ] I completed the lab and exercises independently.

## Official references

- [Built-in Functions — print()](https://docs.python.org/3/library/functions.html#print)
- [Built-in Functions — input()](https://docs.python.org/3/library/functions.html#input)
- [Formatted String Literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)
