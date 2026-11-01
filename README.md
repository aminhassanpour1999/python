# Python Learning Path

A structured, lesson-by-lesson path for developing deep, independent Python programming ability—from first principles to advanced language features, professional development practices, and selected implementation internals.

**Python's official documentation is the primary source of truth for this curriculum.** The [Python Tutorial](https://docs.python.org/3/tutorial/) provides a guided learning path; the [Language Reference](https://docs.python.org/3/reference/) defines language syntax and semantics; and the [Standard Library reference](https://docs.python.org/3/library/) documents built-in and standard-library facilities. Lessons interpret, organize, explain, and supplement those sources with examples, experiments, exercises, labs, and projects. Books and other resources are supplementary.

**The [curriculum roadmap](./ROADMAP.md) is the source of truth for topic coverage, prerequisites, planned depth, deferred topics, and learning status.** A topic appearing in a lesson or roadmap is not automatically learned or mastered.

## How to use this repository

1. Follow the curriculum in order and respect prerequisites.
2. Study one lesson at a time; do not treat the repository as a book to skim.
3. Read the relevant official documentation alongside the lesson. Follow its links, inspect signatures, and check version notes.
4. Predict example output before running code; then type, run, modify, and test the examples yourself.
5. Attempt exercises before reading the model answers later in the **same lesson file**.
6. Debug deliberately and explain why a fix works.
7. Complete labs and cumulative projects rather than collecting notes.
8. Keep repository notes, code comments, and project documentation in English; use Persian explanations in study conversations when useful.
9. Mark learner progress only after actual study, independent practice, and review.
10. Revisit and improve earlier notes when later learning reveals a gap or a more accurate explanation.

## Curriculum

| Stage | Section | Purpose |
|---:|---|---|
| 0 | [Introduction](./00-introduction/README.md) | Programming concepts, Python, setup, first program, and documentation literacy |
| 1 | [Programming Fundamentals](./01-fundamentals/README.md) | Values, numbers, strings, conversion, I/O, logic, style, and debugging |
| 2 | [Control Flow](./02-control-flow/README.md) | Decisions, loops, iteration, and repetition |
| 3 | [Data Structures](./04-data-structures/README.md) | Collections, iteration, data representation, and mutability |
| 4 | [Functions](./03-functions/README.md) | Decomposition, parameters, return values, scope, and reusable behavior |
| 5 | [Object-Oriented Programming](./05-oop/README.md) | Classes, composition, inheritance, and Python's data model |
| 6 | [Files and Errors](./06-files-and-errors/README.md) | Exceptions, paths, files, and reliable programs |
| 7 | [Modules and Packages](./07-modules-and-packages/README.md) | Imports, environments, dependencies, and project workflow |
| 8 | [Advanced Python](./08-advanced-python/README.md) | Iterators, generators, decorators, typing, async, concurrency, and performance |
| 9 | [Testing and Software Quality](./09-testing-and-quality/README.md) | Systematic testing, debugging, logging, and maintainable code |
| 10 | [Python Internals](./10-python-internals/README.md) | Execution model, objects, memory, bytecode, and CPython internals |

[Supplementary exercises](./exercises/README.md) provide cumulative practice across modules. [Projects](./projects/README.md) provide independent, progressively larger applications.

## Learning standard

The [Learning Charter](./LEARNING-CHARTER.md) defines the teaching method and quality rules. Lessons use the relevant parts of this cycle:

**Orient → Understand → Inspect → Experiment → Practice → Debug → Connect → Build → Review → Document**

Lesson-material status and learner mastery are separate. A complete draft is not automatically an approved lesson, and an approved lesson is not proof that the learner has mastered it.

## Primary technical references

- [Python Documentation](https://docs.python.org/3/) — primary source of truth
- [The Python Tutorial](https://docs.python.org/3/tutorial/) — guided introduction to the language
- [The Python Language Reference](https://docs.python.org/3/reference/) — authoritative language syntax and semantics
- [The Python Standard Library](https://docs.python.org/3/library/) — built-ins and standard-library modules
- [Python HOWTOs](https://docs.python.org/3/howto/) — focused technical guides
- [Python Packaging User Guide](https://packaging.python.org/) — packaging and distribution guidance
- [PEP 8](https://peps.python.org/pep-0008/) — style guidance

Books such as *Python Crash Course* and *Python Tricks* may provide alternative explanations, exercises, and useful perspectives. They supplement the official documentation; they do not override it or determine the curriculum.

## Scope

This repository teaches Python itself: the language, built-in types, standard library, programming practices, testing, packaging, and relevant implementation details. Mathematics, scientific computing as a subject, signals and systems, communications engineering, machine learning, and research content belong in separate focused repositories. Python skills learned here will support those subjects later.

Follow the [Learning Charter](./LEARNING-CHARTER.md) and [Roadmap](./ROADMAP.md) when deciding what belongs here.
