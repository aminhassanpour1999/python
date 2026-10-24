# First Python Program

## Learning Objectives

- Create and save a Python source file.
- Write and run a minimal Python program.
- Distinguish source code from program output.
- Edit and rerun a program.
- Recognize simple mistakes and build good file habits.

## 1. Create a Project Folder and File

Create a folder for your learning work, then create a file named `hello.py` inside it. The `.py` extension conventionally identifies a Python source file.

Use a clear project location and a simple filename. Avoid names that conflict with standard-library modules, such as `random.py`, `string.py`, or `statistics.py`, because such names can confuse imports later.

## 2. Write the First Program

Enter this code in `hello.py`:

```python
print("Hello, world!")
```

Save the file. The line is source code; it asks Python to display the text between the quotation marks.

Run the script from a terminal in the folder containing the file:

```bash
python3 hello.py
```

Use the equivalent command for your system if needed. Expected output:

```text
Hello, world!
```

The output is what the program displayed when it ran. It is not another line that you must put into the source file.

## 3. Change the Program

Replace the text with your own message:

```python
print("I am learning Python.")
```

Save and run the file again. Observe how changing the source code changes the output.

You can also print a calculation:

```python
print(2 + 3)
```

Output:

```text
5
```

Quotation marks make the content text. Without quotation marks, `2 + 3` is an arithmetic expression that Python evaluates before `print()` displays the result.

## 4. Run the Program in Visual Studio Code

If you use VS Code, open the project folder and open `hello.py`. Make sure the file is saved and select the intended Python interpreter using the Python extension's interpreter selector. Then use the **Run Python File** command or run the script from VS Code's integrated terminal.

The integrated terminal shows the program's output and error messages. If VS Code cannot find Python or runs a different version than expected, check the selected interpreter before reinstalling Python or packages. The editor, terminal, and interpreter are separate parts of the workflow.

## 5. Read Errors as Feedback

A missing quotation mark or closing parenthesis may cause a syntax error. For example:

```python
print("Hello, world!"
```

This code is incomplete because the function call's closing parenthesis is missing. Fix the source code, save it, and run it again.

When an error occurs, read the error message instead of randomly changing several things. Check the indicated line and nearby syntax, make one change, and rerun the program.

## 6. Good File and Project Habits

- Save changes before running the program.
- Use descriptive filenames and variable names as your projects grow.
- Keep related files in a project folder.
- Avoid naming your files after standard-library modules.
- Make small changes and run the program again.
- Keep a short record of what you tried and what you learned.

A tiny program is enough to practice the whole cycle: edit, save, run, observe, and revise.

## Summary

A Python program can be written in a `.py` file and executed with a Python command. `print()` displays values, but the code and its output are different. Changing one thing at a time and reading errors carefully are useful habits from the very beginning.

## Exercises

1. Create and run a file that prints `Hello, world!`.
2. Change the message to `I am learning Python.` and run it again.
3. Write a line that displays the result of `2 + 3`.
4. Predict the difference between `print("2 + 3")` and `print(2 + 3)`, then test your prediction.
5. Intentionally remove a closing parenthesis, run the file, and then fix the error.
6. Explain why naming a file `random.py` may cause problems in a future project.

## Knowledge Check

You should be able to create, save, run, edit, and troubleshoot a simple Python script without confusing the source code with its output.

## References

- [The Python Tutorial: An Informal Introduction to Python](https://docs.python.org/3/tutorial/introduction.html)
- [The Python Tutorial: Using the Python Interpreter](https://docs.python.org/3/tutorial/interpreter.html)