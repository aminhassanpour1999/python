# Python Documentation

## Learning Objectives

By the end of this lesson, you should be able to:

- Navigate the official Python documentation and choose a suitable reference.
- Find a built-in function and interpret its signature, parameters, return value, exceptions, and version notes.
- Distinguish the Python Tutorial, Language Reference, Standard Library Reference, and third-party documentation.
- Check whether documentation matches the Python version you are using.
- Verify a claim by running a small, controlled experiment.

## 1. Why Documentation Matters

Documentation is the primary reference for how Python and its libraries are intended to work. It explains syntax, behavior, arguments, return values, exceptions, examples, and compatibility notes.

Search results, tutorials, and forum posts can be useful, but they may be outdated or omit important conditions. When a question concerns Python's behavior, consult official documentation and test your understanding with a small example.

You do not need to read documentation from beginning to end. The practical skill is finding the right page and extracting the details that answer your current question.

## 2. Choose the Right Reference

| Resource | Best used for |
| --- | --- |
| Python Tutorial | A guided introduction to language features, with examples in a learning sequence. |
| Language Reference | Precise, formal descriptions of Python syntax and language semantics. |
| Standard Library Reference | Built-in functions, types, and modules distributed with Python. |
| Glossary | Definitions of technical terms used throughout the documentation. |
| Python Packaging User Guide | Installing packages, managing dependencies, and packaging projects. |
| Third-party project documentation | APIs and behavior of packages that do not ship with Python itself. |

The Tutorial is usually the friendliest starting point for learning a topic. The Language Reference is more formal and useful when you need exact rules. You do not need to memorize it; learn that it exists and how to consult it.

A package being popular does not make it part of the standard library. NumPy and pandas, for example, are third-party packages with their own documentation and installation requirements.

## 3. Practical Example: Looking Up len()

Suppose you want to know what the built-in function len() does and what kinds of objects it accepts.

1. Open the [official built-in functions reference](https://docs.python.org/3/library/functions.html).
2. Find the entry for len.
3. Read its signature: len(object, /).
4. Read the description and version or implementation notes.
5. Predict what this code will print before running it.

    text = "Python"
    print(len(text))

Expected output:

    6

The documentation says len() returns the number of items in an object. For a string, those items are characters. The slash in the signature means the parameter before it is positional-only: call it as len(text), not len(object=text).

Now change the example to the string "signal processing". Predict the output, then run it. This checks that you understand the rule rather than merely recognizing a memorized result.

**Important distinction:** documentation describes the behavior a function promises; a small experiment checks your interpretation. Testing a few examples does not prove every possible case.

## 4. How to Read an API Entry

When you look up a function, method, or module, use this checklist:

1. **Purpose:** What problem does it solve?
2. **Signature:** What arguments can you pass, and which are optional?
3. **Parameters:** What kind of value is expected for each argument?
4. **Return value:** What comes back, and what does it represent?
5. **Exceptions:** Under what conditions can it fail?
6. **Side effects:** Does it change an object, write a file, access a network, or affect external state?
7. **Version notes:** Was the feature added, changed, or deprecated in a particular release?
8. **Examples:** Do they match the problem you are trying to solve?

Do not assume a function always returns a useful value just because it performs an operation. For example, print() displays text and returns None. A function may modify something or raise an exception rather than return the result you expected.

## 5. Version-Specific Documentation

Python evolves. A feature available in a newer release may not exist in an older one, and third-party packages may support only certain Python versions.

Check the version you are running:

    python --version

If your system distinguishes commands for Python 3, this may also work:

    python3 --version

The /3/ documentation URL generally points to the current Python 3 documentation, so read version notes carefully when working with an older interpreter.

When an example fails:

1. Check the Python version used to run the code.
2. Check whether the feature or argument exists in that version.
3. Read the full error message and inspect the relevant documentation entry.
4. Reduce the problem to the smallest example that still reproduces the issue.
5. Change one thing at a time and run it again.

Avoid assuming an old online answer applies unchanged to your environment.

## 6. Built-in Help and Introspection

Python provides tools that can help you investigate objects from an interactive interpreter.

- help(len) opens help for the built-in len() function.
- type("Python") tells you the type of the value.
- dir("Python") lists names available on that object; it is a discovery aid, not a complete specification.

Try help(len) in the Python REPL. It is useful as a quick local reference. For authoritative behavior and version notes, compare it with the online documentation.

## 7. A Repeatable Documentation Workflow

When you encounter an unfamiliar function or feature:

1. State the question precisely. For example: “What does len() return for a string?”
2. Search the official documentation or navigate to the relevant reference.
3. Read the description and signature instead of copying the first example you see.
4. Identify expected inputs, output, exceptions, side effects, and version constraints.
5. Predict what a minimal example will do.
6. Run it locally and compare the result with your prediction.
7. Modify one input or condition to test the rule.
8. Record the rule and source link in your notes if it will be useful again.

This process is useful beyond Python. It is a general way to learn APIs and technical tools without relying entirely on someone else's explanation.

## 8. Common Mistakes

- **Reading only the first search result:** it may refer to another Python version or a different package.
- **Confusing the tutorial with the full specification:** a tutorial teaches progressively; the Language Reference describes formal rules.
- **Confusing standard-library modules with third-party packages:** installation and support policies may differ.
- **Copying an example without predicting its result:** execution alone does not guarantee understanding.
- **Ignoring exceptions and side effects:** the normal return value is only part of an API's behavior.
- **Assuming one successful example proves every case:** test boundary conditions when they matter.

## Summary

Use the Python Tutorial for guided learning, the Language Reference for precise language rules, the Standard Library Reference for built-in functionality, the Glossary for terminology, and package-specific documentation for third-party tools. Check version notes, read the complete API entry, and test your interpretation with a small example.

## Exercises

1. Which resource would you start with for a guided introduction to Python's language features?
2. Which resource describes formal language syntax and semantics?
3. Explain the difference between the standard library and a third-party package.
4. In the signature len(object, /), what does the slash mean?
5. Look up round() in the official built-in functions reference. Record its purpose, signature, return behavior, and one detail that surprised you.
6. Run help(len) in the REPL. In your own words, describe one useful piece of information it shows.
7. Find a version note for a Python feature and explain why it might matter to someone running an older interpreter.
8. Choose one standard-library function, predict the output of a small example, run it, and explain whether the result matched your prediction.

## Knowledge Check

You are ready to move on when you can find an appropriate reference, interpret a function's signature and behavior, check version compatibility, and verify your understanding with a small experiment.

## References

- [Python documentation home](https://docs.python.org/3/)
- [The Python Tutorial](https://docs.python.org/3/tutorial/)
- [The Python Language Reference](https://docs.python.org/3/reference/)
- [The Python Standard Library](https://docs.python.org/3/library/)
- [Built-in functions, including len() and round()](https://docs.python.org/3/library/functions.html)
- [The Python Glossary](https://docs.python.org/3/glossary.html)
- [Python Packaging User Guide](https://packaging.python.org/en/latest/)
