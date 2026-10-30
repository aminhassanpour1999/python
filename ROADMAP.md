# Python Curriculum Roadmap

**Purpose:** Maintain one auditable map of the Python learning path, including foundational language skills, intermediate and advanced Python, engineering/scientific computing, and applied projects.

**Primary reference:** [Python documentation](https://docs.python.org/3/). The curriculum is not limited to one book or tutorial.

**Scope:** This is a comprehensive, staged learning path for practical Python and the user's scientific/engineering direction—not an attempt to teach every third-party library or every CPython implementation detail. Required core language features have an explicit home; specialized topics are labeled for later study.

> **Important:** A topic appearing in this roadmap means it is planned, not that it has already been taught or mastered. Progress must reflect demonstrated understanding and practice—not the existence of notes.

## How to read this roadmap

Each topic has a planned home. Some topics are introduced in one place and revisited at greater depth later. That is deliberate: first learn enough to use a feature safely, then return to its internals when the prerequisites are in place.

### Status definitions

- **Planned** — assigned a place in the curriculum but not yet taught in a complete lesson.
- **In progress** — currently being studied; not yet signed off.
- **Studied** — explained, practiced, and reviewed in a learning session.
- **Demonstrated** — the learner can solve unfamiliar exercises and explain the reasoning without copying a worked example.
- **Needs review** — a gap or recurring mistake has been identified and needs targeted practice.

A file being present, a lesson being read, or code being copied is not sufficient evidence for **Demonstrated**.

## Curriculum principles

1. Teach prerequisites before relying on them.
2. Keep foundational lessons focused, but do not silently omit important features from the overall curriculum.
3. Mark the difference between **introduce**, **use fluently**, and **understand deeply**.
4. Include syntax, semantics, edge cases, common mistakes, runnable examples, independent practice, and suitable references.
5. Place exercise prompts before their model answers in the same lesson file; clearly label the answer section so learners can attempt the work first, and do not create separate per-lesson solution files.
6. Revisit topics through cumulative exercises and projects.
7. Use official documentation as a primary reference and verify version-sensitive details.
8. Keep repository notes in English; use Persian for conversational explanations when useful.
9. Update this roadmap when the course changes. If a topic is deferred, record its destination instead of leaving it as an untracked promise.
10. Do not mark a topic complete until the learner has demonstrated it.

11. Use **[02 — Numbers and Operators](./01-fundamentals/02-numbers-and-operators.md)** as the canonical structural and depth reference for all nine Fundamentals lessons. Preserve its quality and teaching approach; do not mechanically copy numeric-specific content into unrelated lessons.
12. A lesson's length must follow the depth of its subject. Do not force equal word counts, but do not shorten a lesson by omitting an essential explanation, example, edge case, exercise, or assessment component.
13. Keep the repository curriculum self-contained: a learner should be able to study a lesson, perform its lab, attempt its exercises, check model answers, and review official references without needing an unlisted companion solution file.
14. Distinguish language guarantees from implementation details, beginner-level essentials from optional depth, and source-backed facts from practical recommendations.
15. Every code example and answer must be technically accurate for the stated Python version, internally consistent, and checked at an appropriate level before the lesson is approved.

---

## Stage 0 — Introduction

**Repository section:** [00-introduction](./00-introduction/README.md)  
**Status:** Partially studied based on the latest verifiable project history; Lessons 1–3 have study/review evidence. Lessons 4–8 and the formal assessment require confirmation before Stage 0 can be marked complete.

- What Python is, its strengths, limitations, and common application areas
- Basic programming vocabulary: algorithm, program, input, processing, output
- At a high level, how Python code is executed; distinguish general Python concepts from CPython-specific implementation details
- Installation, interpreter selection, and development setup
- Running code in the terminal and from a source file
- First program, reading tracebacks at an introductory level, and using official documentation
- Basic problem decomposition and output prediction

**Completion evidence:** explain the concepts in your own words, run and modify a small script, predict its output, and complete the Introduction assessment.

## Stage 1 — Programming Fundamentals

### Canonical lesson standard — mandatory for all nine lessons

**Reference lesson:** [02 — Numbers and Operators](./01-fundamentals/02-numbers-and-operators.md). This file is the benchmark for instructional depth, organization, worked examples, practical application, exercises, model answers, and reference quality. It is the standard to meet, not a ceiling and not a word-count template. Keep the reference lesson stable unless a factual correction or a deliberate improvement is necessary; any such change must preserve or raise the benchmark.

Every Fundamentals lesson must be a complete, coherent teaching chapter. Adapt the sections to the subject, but account for every requirement below. If a requirement genuinely does not apply, state why in the lesson review rather than silently omitting it.

#### A. Orientation and learning contract

- Exact lesson title, module, lesson number, stage/level, realistic study-time estimate, prerequisites, and recommended study method.
- A short lesson guide explaining the purpose, the mental model, how the lesson connects to prior learning, and where the topic will be developed later.
- Specific, observable learning objectives using actions such as identify, explain, predict, compare, choose, implement, test, and debug.
- A scope boundary: what this lesson teaches now, what it previews, and what is deliberately deferred to a named later lesson/stage.

#### B. Conceptual teaching and technical precision

- Begin with the learner's mental model before introducing syntax details.
- Explain terminology, rules, syntax, semantics, evaluation behavior, and relevant object/type behavior—not just definitions or lists.
- Explain why a feature behaves as it does at the level appropriate to this stage.
- Compare easily confused concepts explicitly (for example, equality vs identity, parsing vs validation, or display formatting vs stored value).
- Include the important variants, boundaries, exceptions, edge cases, limitations, and version-sensitive details within the lesson's scope.
- Distinguish Python language guarantees from CPython-specific behavior and implementation details.
- Explain trade-offs and selection criteria: when to use a feature, when not to use it, and what a safer or clearer alternative is.
- Avoid unexplained jargon, hidden prerequisites, hand-waving phrases, and claims that a beginner cannot verify.

#### C. Worked examples and reference material

- Provide progressive examples: minimal syntax, ordinary use, combined use, practical use, and edge-case behavior where relevant.
- Every non-trivial example must be runnable or clearly labeled as a fragment, intentional error, pseudocode, or expected exception.
- Show expected output when output is deterministic; explain important lines and the reasoning behind the result.
- Include comparison/reference tables where they genuinely improve precision or scanning; do not add decorative tables.
- Use meaningful names, explicit units where relevant, consistent formatting, and comments that explain intent rather than repeat syntax.
- Include at least one worked example that demonstrates a complete reasoning process from problem to code to verification.
- Include practical examples that fit the topic. Engineering examples may appear when they genuinely clarify a concept, but the Python repository must remain Python-focused; do not turn Fundamentals into a communications, mathematics, or signals course.
- Link directly to relevant official Python documentation and any applicable PEP. Explain what each reference is useful for when a bare link would be ambiguous.

#### D. Pitfalls, boundaries, and debugging

- A dedicated common-mistakes section covering realistic beginner errors and misconceptions.
- For each important mistake: show the problematic pattern, explain the reason or resulting behavior, and provide a corrected approach.
- Include relevant exception types, failure modes, boundary values, and diagnostic techniques.
- Explain how to inspect or test unexpected behavior using appropriate tools and evidence.
- Do not teach advanced exception handling, loops, functions, collections, or other later-stage topics as if they were prerequisites; mark previews clearly.

#### E. Coding lab

- A meaningful, topic-specific lab with a clear goal and a realistic scenario.
- State the starting point, required inputs/data, expected behavior, and constraints.
- Break the lab into ordered, achievable steps; explain the purpose of each step.
- Include a complete expected result or representative output where appropriate.
- Define explicit acceptance criteria: correctness, edge cases, readability, naming, units, and required explanations.
- Include a test checklist with ordinary, boundary, and invalid cases wherever applicable.
- Require the learner to explain at least one design choice or observed behavior, not merely submit code.
- Keep the lab within the concepts already taught or clearly identify any preview syntax.

#### F. Independent practice and model answers

- Provide approximately 10–12 independent exercises when the topic supports that amount; fewer are acceptable only when justified by the topic's scope and depth.
- Arrange exercises progressively: recall/prediction, direct application, combination, debugging, and reasoning/transfer.
- Cover every major learning objective across the exercise set; do not let a large exercise count hide missing objectives.
- State inputs, expected outputs, constraints, and edge cases precisely enough to make answers assessable.
- Include at least one unfamiliar transfer or debugging problem, not just variations of worked examples.
- Put all model answers in the **same lesson file**, after all exercise prompts. Never create separate per-lesson solution files.
- Give explanatory answers: explain why, show working code where code is requested, state expected output where useful, and accept valid alternatives for open-ended tasks.
- Keep answers aligned with the exercise wording and with the Python behavior taught in the lesson. Do not reveal answers before the exercise section.

#### G. Retrieval, review, and completion

- Include a knowledge check that tests understanding rather than only memorized definitions.
- Put suggested answers after the questions, clearly separated so the learner can self-test first.
- Include a concise but substantive summary of the chapter's core mental models and rules.
- Include explicit completion criteria that can be demonstrated without copying the examples.
- Identify what the learner should be able to explain, predict, write, test, and debug independently.
- Make clear that reading or ticking a checkbox alone does not prove mastery.

#### H. Technical and editorial quality gate

Before a lesson is marked aligned, verify all of the following:

- All objectives are taught, practiced, and assessed.
- No important topic promised by the objectives is missing from the body, lab, exercises, or assessment.
- Code blocks have valid syntax unless intentionally demonstrating an error; expected outputs are correct.
- Examples and answer keys agree with one another and use concepts introduced at the appropriate point.
- Headings, numbering, terminology, capitalization, punctuation, Markdown fences, tables, and internal links are consistent.
- No duplicate sections, orphan headings, empty answer sections, stale references, broken paths, or contradictory instructions remain.
- Official references resolve to the relevant authoritative documentation and support the claims made.
- At least representative examples and all newly introduced or corrected code have been executed when practical; record the limits of verification honestly.
- The lesson is self-contained and does not depend on a deleted solution file or undocumented external explanation.

#### I. Review rubric

Score each lesson against these dimensions before calling it complete: (1) scope and objectives, (2) conceptual depth, (3) technical accuracy, (4) coverage and edge cases, (5) worked examples and outputs, (6) practical application/lab, (7) exercise coverage and progression, (8) explanatory answer key, (9) review/completion criteria, and (10) references and editorial integrity.

A score of 100/100 is permitted only when every applicable requirement above is met and the verification evidence is recorded. If any essential item is missing, the lesson is not 100/100; list the gap and revise it. Written-material quality is never the same as learner mastery. Do not update learner progress as a side effect of editing teaching material.

**Implementation order:** keep Lesson 2 as the benchmark; audit and align Lessons 1 and 3–9 one by one; then re-audit the cumulative assessment, module README, Quality Review, Learning Charter, and this roadmap for consistency. Do not mark the stage's teaching materials fully aligned until every item has passed the gate.


**Repository section:** [01-fundamentals](./01-fundamentals/README.md)  
**Teaching-material status:** Alignment against the reference lesson is in progress. Do not describe the module as 100/100 or fully audited until every lesson has passed the common standard and its examples, exercises, answer key, and links have been checked. Learner mastery is tracked separately.  
**Learner status:** Lesson 1 is complete and Lesson 2 is in progress, based on the learner's confirmed study position. Lessons 3–9 and the cumulative assessment remain pending. Do not mark a lesson demonstrated without independent study and practice.

This stage teaches a complete stage-appropriate foundation for writing, reading, reasoning about, and debugging small straight-line Python programs. Completeness here means mastery of the listed beginner-level concepts, not mastery of all Python or professional senior-level ability. It deliberately stops before branching and loops, which belong to Stage 2.

### Lesson sequence and required coverage

1. **Variables and Data Types** — names, objects, values, assignment and rebinding; identifiers and keywords; naming; built-in scalar types `int`, `float`, `complex`, `str`, `bool`, and `NoneType`; dynamic typing; `type()`; equality versus identity; common mistakes.
2. **Numbers and Operators** — integer, floating-point, and complex literals; arithmetic; true division, floor division and modulo; unary operators; precedence and associativity; chained comparisons; Boolean operators and short-circuiting; augmented assignment; all six bitwise operators and masks; negative-integer inversion and shifts; floating-point representation, tolerance, rounding and formatting; `math`, `cmath`, `Decimal`, `Fraction`; numeric built-ins; units and readable formulas.
3. **Strings** — literals, quoting, escapes, raw and multiline strings; length, indexing, slicing; immutability; concatenation and repetition; membership and lexicographic comparisons; search and classification methods; trimming, exact prefix/suffix removal, replacement, splitting, partitioning, joining, alignment and padding; f-strings and format specifications; Unicode code points, normalization, grapheme clusters, and the distinction between str and encoded bytes.
4. **Type Conversion** — `int()`, `float()`, `str()`, `bool()`; numeric promotion; base conversion; truncation versus rounding; information loss; `ValueError` and `TypeError`; conversion versus validation.
5. **Input and Output** — `print()`, multiple arguments, `sep`, `end`; `input()` and its string return value; prompt design; input → conversion → calculation → output; labels, units, formatting, reproducible fixed-data tests, and basic validation awareness.
6. **Booleans and None** — Boolean values; comparisons; truthiness and common falsy values; distinction between falsey values and `None`; `and`, `or`, `not`; truth tables; short-circuit evaluation; operand-return behavior; `is None`.
7. **Expressions and Statements** — expressions and values; statements and actions; assignment evaluation; multiple and chained assignment previews; precedence; side effects; tracing; syntax, runtime, and logic errors; readable calculations.
8. **Comments and Code Style** — useful comments; strings versus docstrings; naming; constants; whitespace and indentation; PEP 8 basics; units in names; introductory refactoring and behavior verification.
9. **Basic Debugging** — error categories; tracebacks; common exceptions; inspecting values and types; `repr()`; minimal reproducible examples; hypothesis-driven debugging; debugger concepts; appropriate and inappropriate uses of `assert`.

### Teaching assets and coverage levels

Exercise prompts appear before model answers in the same lesson file; no separate per-lesson solutions files are used. The module also includes a cumulative 50-point assessment and a stage-appropriate measurement-report project brief. See the [module guide](./01-fundamentals/README.md).

- **Introduce and use:** syntax and everyday semantics for every item above.
- **Use safely:** common mistakes, boundaries, conversion failures, and numeric precision decisions.
- **Understand conceptually:** object identity, Unicode code points, short-circuiting, side effects, and debugger workflow.
- **Deferred deliberately:** loops and branching, collections in depth, functions, robust exception handling, file I/O, modules, classes, testing frameworks, and advanced internals. Each has a later curriculum home.

### Assessment and exit criteria

Complete the [Programming Fundamentals final assessment](./01-fundamentals/10-final-assessment.md) and score at least 40/50. Review every missed topic and retry it without notes. Then complete the unscored transfer task at the end of the assessment, using new values and explaining the reasoning independently. The learner may be marked **Demonstrated** only after independently explaining and completing that work.

**Scope note:** Fundamentals is comprehensive for its intended stage, not a claim to teach all of Python. Python is too broad for one beginner module. The roadmap preserves every important later topic in its proper stage rather than forcing advanced features into the foundation.

## Stage 2 — Control Flow

**Repository section:** [02-control-flow](./02-control-flow/README.md)

- Conditional execution: `if`, `elif`, `else`, nested conditions, and truthiness
- `for` loops, iterable basics, and `range()`
- `while` loops, termination conditions, and avoiding accidental infinite loops
- `break`, `continue`, and loop `else`
- Nested loops, tracing, counters, accumulators, and sentinel patterns
- Comprehensions: list, set, and dictionary; readability and when not to use them
- Structural pattern matching (`match` / `case`), guards, and supported pattern forms
- Off-by-one errors, loop invariants at an introductory level, and edge-case testing

**Assessment:** solve unfamiliar problems involving branching, repetition, validation, and small simulations without copying a template.

## Stage 3 — Functions

**Repository section:** [03-functions](./03-functions/README.md)

- Defining and calling functions; parameters, arguments, return values, and `None`
- Positional and keyword arguments; defaults and the mutable-default-argument pitfall
- Scope, local/global names, lifetime, and name resolution
- Returning multiple values through tuples and unpacking
- Docstrings, type hints, and function contracts
- Pure functions, side effects, decomposition, and reuse
- Lambda expressions and selected functional tools when they improve clarity
- Recursion, base cases, recursion limits, and iterative alternatives
- Testing functions, test cases, boundary conditions, and simple assertions
- Basic higher-order functions and closures; deeper decorator use is deferred to Stage 8

**Assessment:** decompose a moderately sized problem into testable functions and justify the interface of each function.

## Stage 4 — Data Structures and Object Behavior

**Repository section:** [04-data-structures](./04-data-structures/README.md)

- Lists: creation, indexing, slicing, mutation, methods, and copying
- Tuples and sequence unpacking
- Dictionaries: keys, values, lookup, mutation, iteration, and key constraints
- Sets, uniqueness, membership, and set operations
- Bytes and bytearray: binary data, indexing behavior, and encoding/decoding text; memoryview is a later efficiency topic
- Nested structures and choosing a suitable representation
- Iteration protocols at a practical level; iterable versus iterator
- Mutability, aliasing, shallow copy, deep copy, and identity
- Sorting, key functions, searching, and common collection patterns
- Complexity intuition (time/space growth) and choosing data structures deliberately

**Assessment:** select, implement, and test a data representation for a realistic small task.

## Stage 5 — Object-Oriented Programming and the Python Data Model

**Repository section:** [05-oop](./05-oop/README.md)

- Objects, classes, instances, attributes, methods, and `self`
- Instance attributes versus class attributes
- Encapsulation conventions, properties, and controlled interfaces
- Inheritance versus composition; method overriding and `super()`
- Polymorphism and duck typing
- Dataclasses and practical class design
- Special methods and the data model: `__init__`, `__repr__`, `__str__`, equality, ordering, hashing, and container behavior
- **Numeric protocols and operator overloading:** `__add__`, `__sub__`, `__mul__`, `__truediv__`, `__floordiv__`, `__mod__`, `__pow__`, reflected operations, in-place operations, and comparison methods where appropriate
- Related protocols such as `__abs__`, `__bool__`, `__int__`, `__float__`, and `__complex__`
- Consistency rules, return types, unsupported operations, and when not to overload operators

**Depth requirement:** do not merely memorize special-method names. Explain how syntax such as `a + b` is dispatched at a high level, how custom types should preserve intuitive behavior, and how to test edge cases. Implementation-level details can be deferred unless they materially affect correct use.

**Assessment:** design a small class with a clear purpose and tests, and explain why a class is more suitable than simpler functions or data structures.

## Stage 6 — Exceptions, Files, and Reliable Programs

**Repository section:** [06-files-and-errors](./06-files-and-errors/README.md)

- Exceptions and tracebacks; common built-in exception types
- `try`, `except`, `else`, and `finally`; catching specific exceptions
- Raising exceptions, designing useful error messages, and exception chaining at a practical level
- Input validation and failure handling
- File paths, `pathlib`, reading and writing text files, and explicit encodings
- Binary file I/O, bytes-like objects, and distinguishing text from raw bytes
- Context managers and `with`
- Structured data files such as CSV and JSON
- Resource cleanup, robust file operations, and testing failure paths

**Assessment:** build a small program that validates input, handles expected failures, and safely reads or writes data.

## Stage 7 — Modules, Packages, Environments, and Project Workflow

**Repository section:** [07-modules-and-packages](./07-modules-and-packages/README.md)

- Imports, module namespaces, and the import system at a practical level
- Packages and a maintainable project layout
- Main-module guard: `if __name__ == "__main__":`
- Standard library versus third-party dependencies; learn to discover relevant standard-library modules instead of reinventing common tools
- Practical standard-library toolkit: `pathlib`, `datetime`, `re`, `collections`, `itertools`, `functools`, `statistics`, `logging`, `argparse`, `subprocess`, and `sqlite3` as appropriate to projects
- Virtual environments and reproducible dependency setup
- Installing packages, package versions, and basic dependency management
- Configuration, environment variables, and separating configuration from code
- Command-line programs and argument parsing where appropriate
- Git-based workflow, README writing, and reproducible run instructions

**Assessment:** create a small, multi-file project that another person can install, run, and understand from its documentation.

## Stage 8 — Advanced Python

**Repository section:** [08-advanced-python](./08-advanced-python/README.md)

- Iterables, iterators, generators, `yield`, generator expressions, and asynchronous iteration/generators at an appropriate level
- Decorators, closures, and preserving wrapped-function metadata
- Context-manager protocol and custom context managers
- Comprehension and generator-expression trade-offs
- Type annotations beyond the basics: unions, generics, protocols, and static checking as appropriate
- Python's object model and attribute lookup at a practical depth
- Descriptors, `__new__`, method resolution order, `__slots__`, and metaprogramming only after the data model is understood; teach these as advanced/optional depth rather than prerequisites for ordinary Python work
- Concurrency overview: threads, processes, asynchronous I/O, `async` / `await`, and choosing the right model
- Performance measurement, profiling, algorithmic complexity, and avoiding premature optimization
- Testing with a test framework, test organization, mocks only when useful, and code-quality tooling
- Packaging and distribution, project configuration, and documentation quality
- Practical use of regular expressions, dates/times, logging, command-line interfaces, databases, and subprocesses; apply only after the relevant fundamentals and discuss security/portability pitfalls
- Memory behavior, references, garbage collection, and implementation-specific behavior where relevant
- The distinction between language guarantees and CPython implementation details

**Assessment:** explain trade-offs, test edge cases, and build a maintainable project that combines several advanced concepts. Advanced topics are studied after core programming is strong; they are not silently considered covered by the foundational course.

---

## Stage 9 — Scientific Python and Numerical Computing

**Related future study areas:** scientific computing and mathematics. These will be maintained in separate, subject-specific repositories; this roadmap tracks only the Python skills needed for later work.

This is a dedicated application track, not a replacement for core Python.

### Numerical foundations

- Floating-point limits, significant digits, conditioning, numerical error, and tolerances
- Absolute versus relative error; rounding and stable comparisons
- Overflow/underflow and the limits of finite precision
- Algorithmic complexity and numerical stability
- Reproducibility, random-number generators, seeds, and experimental methodology

### NumPy

- `ndarray`, shape, dimensions, `dtype`, indexing, slicing, and views versus copies
- Vectorization, broadcasting, Boolean masks, and avoiding unnecessary Python loops
- Aggregation, axes, reshaping, stacking, and array manipulation
- Random sampling and reproducible simulation
- Linear algebra basics, matrix operations, and solving systems appropriately
- Performance trade-offs and memory layout at a suitable level

### Data analysis and visualization

- pandas Series and DataFrames, importing data, cleaning, filtering, grouping, and missing values
- Matplotlib figures, axes, labels, legends, units, and honest visualization
- Reproducible analysis notebooks and scripts
- Choosing a library based on the problem rather than habit

### Numerical algorithms

- Root finding and solving equations
- Interpolation and approximation
- Numerical differentiation and integration
- Linear systems and least-squares methods
- Optimization basics
- Randomized methods and Monte Carlo simulation
- Stability, convergence, error estimates, and limits of each method

Use NumPy, SciPy, pandas, and Matplotlib where appropriate. Implement small algorithms from first principles when it teaches the underlying idea; use well-tested library implementations for real work when appropriate.

## Stage 10 — Engineering, Signals, Communications, and Applied AI

**Related future study areas:** signals and systems, communications, machine learning, and research. Their subject-specific notes belong in separate repositories; this roadmap covers Python prerequisites and applications only.

The order of these topics depends on the supporting mathematics and signal-processing prerequisites.

- Representing sampled signals, arrays, units, sampling rates, and time/frequency axes
- Reading and writing common data formats; validating measurement data
- Plotting time-domain and frequency-domain signals
- Sinusoids, complex exponentials, phasors, and complex-valued arrays
- Fourier analysis and FFT use, including sampling and interpretation pitfalls
- Filtering, convolution, correlation, and noise experiments
- Modulation and demodulation simulations; comparing modulation schemes
- Feature extraction and basic signal classification
- Machine-learning workflow: train/validation/test splits, baselines, metrics, leakage, and reproducibility
- Introductory model training with suitable libraries; deeper ML and deep learning only after foundations
- Engineering projects with clear problem statements, tests, plots, and documented limitations

**Project quality bar:** each project should state the problem, assumptions, units, method, verification strategy, results, and limitations. A visually impressive plot or a working demo alone does not establish correctness.

---

## Cross-cutting skills — revisit throughout the course

These are not one-off lessons; they should be practiced repeatedly.

- Reading documentation and signatures, checking version notes, and finding authoritative answers
- Writing small reproducible examples to investigate uncertain behavior
- Debugging from evidence instead of guessing
- Testing normal cases, boundary cases, and invalid inputs
- Code readability, naming, decomposition, and maintainability
- Git commits, meaningful change summaries, and project documentation
- Basic security and privacy hygiene when handling files, credentials, and user data
- Explaining the reasoning behind a solution and reviewing one's own work

## Explicit gap register

These are known coverage requirements to check during lesson development. A row is not complete until its lesson actually teaches the listed material and the learner has practiced it.

| Topic | Planned home | Required coverage | Current status |
|---|---|---|---|
| Complex numbers (`complex`) | Stage 1: Numbers and Operators; revisit Stage 9–10 | Literals, real/imaginary parts, arithmetic, magnitude with `abs()`, conjugation, unsupported ordering comparisons, and later engineering applications | **Teaching material present; learner practice/sign-off pending** |
| Bitwise operators | Stage 1: Numbers and Operators; revisit in practical computing | All six operators, binary examples, shifts, masks, negative-integer behavior, and practice | **Teaching material present; learner practice/sign-off pending** |
| Operator precedence and associativity | Stage 1, then revisit when new syntax appears | Teach arithmetic, shifts, bitwise, comparisons, identity/membership, Boolean, conditional, lambda, and assignment-expression precedence at the appropriate point; include the official full table as a reference and work through edge cases | **Core operator coverage present in Lesson 2; later syntax revisited in its lessons; learner practice pending** |
| Numeric data model and protocols | Stage 5: OOP and Python Data Model | Special methods, dispatch model, reflected/in-place operations, comparisons, conversion protocols, consistency and tests | **Planned** |
| Floating-point and numerical error | Stage 1 introduction; Stage 9 depth | Representation, rounding, tolerances, error, conditioning, stability, and practical decision-making | **Introductory coverage present in Lesson 2; advanced numerical coverage planned for Stage 9** |
| Numerical algorithms | Stage 9: Scientific Python | Root finding, interpolation, differentiation/integration, linear systems, optimization, convergence and error | **Planned** |
| NumPy and scientific tools | Stage 9 | Arrays, dtypes, broadcasting, vectorization, linear algebra, data analysis and visualization | **Planned** |
| Engineering applications | Stage 10 | Signals, complex-valued data, FFT, filtering, modulation, reproducible experiments and evaluation | **Planned** |

## Lesson sign-off checklist

Before a lesson is marked **Demonstrated**, check the relevant items:

- [ ] I can explain the core concepts in my own words.
- [ ] I can predict and explain example outputs without running the code first.
- [ ] I can write a solution to a new problem without copying the worked example.
- [ ] I have tested at least one boundary case or likely failure mode.
- [ ] I can explain a common mistake and how to debug it.
- [ ] I have reviewed my errors and can solve the missed questions again.
- [ ] The lesson's references are relevant and the technical claims have been checked.
- [ ] The roadmap's status and any remaining gaps have been updated.

## Maintenance rule

At the beginning of a new lesson, check its place and prerequisites in this roadmap. At the end, update the status based on what was actually studied and demonstrated. If a topic is deferred, add or preserve its explicit destination in the gap register. Never silently drop a planned topic.

## Official references

- [Python Tutorial](https://docs.python.org/3/tutorial/)
- [Python Language Reference](https://docs.python.org/3/reference/)
- [Built-in Types](https://docs.python.org/3/library/stdtypes.html)
- [Built-in Functions](https://docs.python.org/3/library/functions.html)
- [Numeric Types — `int`, `float`, `complex`](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)
- [Expressions and the complete operator-precedence table](https://docs.python.org/3/reference/expressions.html#operator-precedence)
- [Complex number operations](https://docs.python.org/3/library/cmath.html)
- [Decimal arithmetic](https://docs.python.org/3/library/decimal.html)
- [Rational numbers](https://docs.python.org/3/library/fractions.html)
- [Emulating numeric types](https://docs.python.org/3/reference/datamodel.html#emulating-numeric-types)
- [PEP 8 — Style Guide for Python Code](https://peps.python.org/pep-0008/)
- [NumPy documentation](https://numpy.org/doc/)
- [SciPy documentation](https://docs.scipy.org/doc/scipy/)
- [pandas documentation](https://pandas.pydata.org/docs/)
- [Matplotlib documentation](https://matplotlib.org/stable/)
