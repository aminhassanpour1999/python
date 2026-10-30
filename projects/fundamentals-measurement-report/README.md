# Fundamentals Measurement Report — Project Brief

**Stage:** Programming Fundamentals  
**Type:** Small command-line program  
**Prerequisites:** All nine Fundamentals lessons  
**Status:** Planned; complete after the module assessment

## Goal

Build a small, readable program that receives a set of measurement values, checks the assumptions that can be checked with Fundamentals concepts, calculates a summary, and presents a clear report.

This project is deliberately constrained to the language features taught in Fundamentals. Do not use loops, functions, classes, collections, file I/O, or exception handling. Those features belong to later stages.

## Scenario

A technician records two voltage readings from a test point and wants a compact report. The program should preserve the original text inputs, convert them to numeric values, calculate an average and signed difference, and display values with units and sensible precision.

## Requirements

1. Ask for two voltage readings; prompts must state volts (V).
2. Keep the raw input strings separate from converted numeric values.
3. Convert both values explicitly to float.
4. Calculate the arithmetic mean and signed difference (second minus first).
5. Display both original readings, the average, and the signed difference.
6. Label every measurement and include units.
7. Use f-string formatting consistently.
8. Use meaningful names and readable expressions.
9. State the program's assumptions and limitations.
10. Test ordinary values, decimal values, zero, negative values, and values that are syntactically numeric but outside any domain range you choose to define.

## Suggested test matrix

| First input | Second input | Average (V) | Difference (V) |
|---:|---:|---:|---:|
| 10 | 20 | 15 | +10 |
| 1.5 | 2.5 | 2 | +1 |
| 0 | 8 | 4 | +8 |
| 5 | 5 | 5 | +0 |
| -2 | 2 | 0 | +4 |

The table checks arithmetic behavior only. A real instrument or application may forbid negative voltages or impose other constraints; write down the domain rule rather than assuming one.

## Required deliverables

- A Python source file named fundamentals_measurement_report.py.
- A short README describing the program, assumptions, and how to run it.
- A test log containing inputs, predicted outputs, actual outputs, and any defects found.
- A brief explanation of how the program uses concepts from all nine lessons.

## Acceptance criteria

The project is ready for review when:

- It runs for valid numeric input.
- The formulas are correct and independently explained.
- Raw text and numeric values are not confused.
- Output labels and units are unambiguous.
- Tests include ordinary, boundary, and invalid cases.
- The learner can explain every line without copying a worked solution.
- Limitations are stated honestly. Non-numeric input may raise ValueError because robust exception handling is outside this stage.

## Review rubric (100 points)

| Area | Points |
|---|---:|
| Correct conversion and data representation | 15 |
| Correct calculations and formulas | 20 |
| Clear output, units, and formatting | 15 |
| Naming, readability, and style | 15 |
| Test design and evidence | 20 |
| Explanation of assumptions and limitations | 15 |
| **Total** | **100** |

A score of 80/100 is a review threshold, not a mastery guarantee. The learner must explain the solution and complete a small unfamiliar modification independently.
