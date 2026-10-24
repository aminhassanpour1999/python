# How Python Runs

## Learning Objectives

- Distinguish source code, a Python implementation, and program execution.
- Describe the roles of interpreters, bytecode, and the Python virtual machine at a high level.
- Understand that Python has multiple implementations.
- Separate essential concepts from implementation details that can be learned later.

## 1. From Source Code to Execution

Python source code is the text a programmer writes in a `.py` file or enters interactively. To make that code do something, it must be processed by a **Python implementation**.

For example, a file named `hello.py` might contain:

```python
print("Hello, world!")
```

When you run the file with Python, the implementation processes the code and executes its instructions. The visible output is:

```text
Hello, world!
```

The source file is not the output: it is the program text from which execution begins.

## 2. What Is an Interpreter?

An **interpreter** is commonly described as software that executes a programming language's code. The word is useful, but real language implementations may involve several stages rather than simply reading one source line and executing it immediately.

Python is often called an interpreted language because developers typically run Python source through a Python runtime rather than manually compiling a standalone native executable. This description is useful for beginners, but it is not a complete account of every implementation detail.

## 3. Compilation, Bytecode, and the Python Virtual Machine

The default implementation, **CPython**, commonly compiles source code into an intermediate representation called **bytecode**. The CPython runtime then executes that bytecode using its evaluation machinery, often described at a high level as the Python virtual machine.

A simplified model is:

1. You write Python source code.
2. CPython parses and compiles it to bytecode.
3. The runtime executes the bytecode.
4. The program performs its work and produces effects such as output or file changes.

This is a conceptual model, not a promise that every implementation follows exactly the same internal steps. Python may also cache bytecode in `__pycache__` directories in circumstances where doing so is useful.

**Compilation and interpretation are not mutually exclusive categories.** A language implementation can compile source to an intermediate form and then execute that form in a runtime.

## 4. CPython and Other Implementations

**CPython** is the standard and most widely used implementation of Python; it is written primarily in C. Other implementations exist and may have different runtime strategies or goals. Examples include PyPy, which uses just-in-time compilation techniques, and Jython, which targets the Java platform (its support for Python language versions differs from CPython).

Most beginners should start with CPython unless a project specifically requires another implementation. Code portability and package compatibility can vary, so confirm support before choosing an alternative runtime.

## 5. Essential Versus Advanced Details

At this stage, remember the practical model:

- Python source code is written in files or entered interactively.
- A Python implementation runs that code.
- CPython commonly uses bytecode as an intermediate form.
- Runtime details differ among implementations and versions.
- You usually do not need to manipulate bytecode to write ordinary Python programs.

You will get more value early on from learning to read, write, test, and debug small programs than from memorizing virtual-machine internals. Return to implementation details when they help explain a real performance, compatibility, or debugging question.

## Summary

Running Python involves a language implementation and runtime. CPython usually compiles source to bytecode and executes it. Calling Python “interpreted” is a useful shorthand, but modern implementations can combine compilation and runtime execution in different ways.

## Exercises

1. What is the difference between a `.py` source file and the output it produces?
2. Why is “Python is interpreted” a useful but incomplete description?
3. Put these stages in a reasonable order for a simplified CPython model: source code, bytecode, execution.
4. Is compilation necessarily the same thing as producing a standalone native executable? Explain using this lesson.
5. Why might a beginner reasonably start with CPython rather than an alternative implementation?

## Knowledge Check

Be able to explain the simplified path from source code to execution and why implementation details should not be confused with the language's visible syntax.

## References

- [Python FAQ: General](https://docs.python.org/3/faq/general.html)
- [CPython internals documentation](https://devguide.python.org/internals/)
- [Python glossary](https://docs.python.org/3/glossary.html)