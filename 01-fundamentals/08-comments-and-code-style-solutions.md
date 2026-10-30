# Comments and Code Style — Exercise Solutions

Open only after attempting the lesson.

## Level 1
1. first_reading, second_reading, average_reading, elapsed_seconds.
2. str, list, type, sum, print, input, int.
3. A comment is ignored by Python; a string is a value; a docstring is a string literal in the documentation position.
4. Four spaces.
## Level 2
5. Use names that communicate quantity and unit, such as distance_km and elapsed_hours.
6. Split a long expression into meaningful intermediate values.
7. Repeating the next line adds little; explaining an external constraint or non-obvious assumption is useful.
8. CALIBRATION_FACTOR.
## Level 3
9. Improve names, units, spacing, grouping, and comments that explain intent.
10. No. Uppercase is a convention, not an immutability mechanism.
11. Determine the actual source unit and intended formula; correct code or comment to agree.
12. Run the same representative and boundary tests before and after and compare outputs.
13. A comment can explain why an unusual threshold is required by a standard or hardware constraint.
## Knowledge check
1. It communicates meaning or role.
2. It hides a built-in and can cause confusing errors.
3. Intent, assumptions, constraints, or non-obvious decisions.
4. A string literal in a designated documentation position.
5. Four spaces per level.
6. An unexplained literal whose meaning is unclear.
7. Improving internal structure without intentionally changing behavior.
8. Compare the same tests and outputs before and after.
## Lab review
The refactored code should preserve the formula, communicate units, and produce equivalent results for the same inputs.
