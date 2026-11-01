# Python Internals

> Status: Planned syllabus only. This is an advanced optional deep dive after strong practical Python foundations. It distinguishes language-level guarantees from CPython-specific implementation details.

## Lesson map

1. Python's execution model
2. Names, namespaces, scopes, and frames
3. Objects, identity, references, and lifetime
4. Memory management and garbage collection
5. Code objects and bytecode inspection with `dis`
6. CPython architecture and implementation overview
7. Import system and module loading internals
8. Attribute access, descriptors, and method resolution order
9. Final assessment and reproducible investigation

## Learning goal

Investigate Python behavior with authoritative documentation and appropriate inspection tools, explain the evidence, and distinguish portable language semantics from implementation-specific observations.

## Primary references

- [Python Data Model](https://docs.python.org/3/reference/datamodel.html)
- [Python Execution Model](https://docs.python.org/3/reference/executionmodel.html)
- [`dis` — Disassembler for Python bytecode](https://docs.python.org/3/library/dis.html)
- [`gc` — Garbage Collector interface](https://docs.python.org/3/library/gc.html)
- [CPython Developer Guide](https://devguide.python.org/)
