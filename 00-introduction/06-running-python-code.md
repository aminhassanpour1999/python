# Running Python Code

## Learning Objectives

- Distinguish the interactive interpreter (REPL) from a Python script.
- Understand the roles of the shell and the current working directory.
- Run a Python file from a terminal and an editor.
- Recognize common execution errors and basic troubleshooting steps.

## 1. Interactive Mode and the REPL

The **REPL** is an interactive environment whose name stands for Read–Eval–Print Loop: it reads an input, evaluates it, displays a result, and waits for more input.

Start it using a command available on your system, such as:

```bash
python3
```

Then enter a simple expression:

```python
2 + 3
```

The interactive interpreter displays the result:

```text
5
```

To leave the interpreter, use `exit()` or the platform's documented keyboard shortcut. A REPL is convenient for quick experiments, but work you want to preserve should generally be saved in a source file.

## 2. Python Scripts

A **script** is a source file, commonly ending in `.py`, that you run as a unit. Create a file named `hello.py`:

```python
print("Hello from a script!")
```

Run it from the terminal using the Python command available on your system:

```bash
python3 hello.py
```

On other systems, `python hello.py` or `py hello.py` may be the appropriate command. The command must point to the intended Python installation, and the file must be in the location the command expects.

Unlike the REPL, a script does not ordinarily display the value of every expression automatically. Use `print()` when you want to display a value.

## 3. The Shell and the Working Directory

The **shell** is the program that interprets terminal commands. It is not Python itself. For example, `python3 hello.py` is a shell command that launches Python and supplies a filename.

The **current working directory** is the directory from which a process runs. When you pass a relative filename such as `hello.py`, Python looks for it relative to the working directory (unless another path is supplied).

Useful shell commands differ by operating system. On many Linux and macOS shells, `pwd` prints the current directory and `ls` lists its contents. In Windows PowerShell, `Get-Location` and `Get-ChildItem` serve similar purposes.

If Python says it cannot open a file, check the filename and current directory before assuming the program itself is broken.

## 4. Running Code in an Editor

Editors such as VS Code can run Python files using their integrated terminal or Python-specific commands. The exact controls depend on installed extensions and editor configuration.

When running code in an editor:

1. Save the file.
2. Confirm the selected Python interpreter.
3. Check which file is being run.
4. Read the terminal output and any error message.
5. Re-run after making a deliberate change.

An editor may use a different interpreter from the one you invoke manually in a terminal. If results differ, compare the interpreter paths and environments.

## 5. Common Execution Problems

### Command not found

The command may be named differently or the executable may not be available through PATH. Check the installation and platform-specific command.

### File not found

Confirm the filename, extension, spelling, and working directory. Ensure the file was saved where you expect.

### Syntax error

Python could not parse the source code. Read the indicated line and nearby lines; the actual mistake can sometimes occur just before the reported location.

### Runtime error

The code started running but encountered a problem, such as attempting an invalid operation or opening a missing file. Read the error type and traceback from the bottom upward to locate the relevant part of your code.

### Unexpected output

Check the values used, the code path taken, and whether the file was saved before running. Predicting expected output before execution can help identify misunderstandings.

## Summary

Use the REPL for quick experiments and scripts for saved programs. The shell runs commands; Python executes Python code. The working directory affects how relative paths are resolved, and editor settings affect which interpreter is used.

## Exercises

1. When would you prefer the REPL, and when would you prefer a `.py` script?
2. What does the shell do when you enter `python3 hello.py`?
3. Why can a relative filename fail even when the file exists somewhere on your computer?
4. List three checks you would perform if a script works in a terminal but not in your editor.
5. Explain the difference between a syntax error and a runtime error.

## Knowledge Check

You should be able to start an interactive session, run a saved script, explain the role of the working directory, and troubleshoot a missing-file or interpreter problem.

## References

- [The Python Tutorial: Using the Python Interpreter](https://docs.python.org/3/tutorial/interpreter.html)
- [Python command-line and environment](https://docs.python.org/3/using/cmdline.html)
- [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python)