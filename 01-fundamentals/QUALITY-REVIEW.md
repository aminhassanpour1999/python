# Programming Fundamentals — Quality Review

**Review state:** Revision 3 — alignment in progress  
**Canonical reference:** [02 — Numbers and Operators](./02-numbers-and-operators.md)  
**Mandatory standard:** [Canonical lesson standard in the main Roadmap](../ROADMAP.md#canonical-lesson-standard--mandatory-for-all-nine-lessons)

## Purpose and scope

This file records the actual state of the teaching materials. It must not award perfect scores merely because a file exists, has many words, or contains the expected headings.

Lesson 2 is the agreed benchmark for the depth, explanatory approach, organization, worked examples, practical application, independent practice, and model answers expected from the other Fundamentals lessons. It is a subject-specific reference, not a requirement to copy its exact headings or word count.

The current task is to bring Lessons 1 and 3–9 up to that standard, verify them, and then re-audit the cumulative assessment and supporting documents. The learner's study progress is separate and must not be changed by editorial work.

## Review rubric

Each lesson will be reviewed against all ten dimensions below. A perfect score requires evidence for every applicable requirement in the Roadmap's canonical standard.

| Dimension | What must be demonstrated |
|---|---|
| 1. Scope and objectives | Accurate prerequisites, explicit scope, observable objectives, and complete coverage of the lesson's promised outcomes |
| 2. Conceptual depth | Clear mental models, precise terminology, explanations of why and how, and distinctions between easily confused concepts |
| 3. Technical accuracy | Correct Python syntax, semantics, outputs, terminology, examples, and version-sensitive claims |
| 4. Coverage and boundaries | Relevant variants, edge cases, limitations, failure modes, and clearly deferred later-stage material |
| 5. Worked examples | Progressive, understandable, runnable examples with expected output and reasoning where appropriate |
| 6. Practical application | A meaningful lab with staged tasks, explicit acceptance criteria, and suitable tests |
| 7. Independent practice | Approximately 10–12 progressively challenging exercises where appropriate, covering all major objectives and including debugging or transfer |
| 8. Model answers | Explanatory answers after all prompts in the same lesson file; no separate per-lesson solution files |
| 9. Retrieval and completion | Knowledge check with later answers, substantive summary, and demonstrable completion criteria |
| 10. References and editorial integrity | Relevant official references, consistent structure, working links, no duplicate/orphan sections, and honest verification notes |

A lesson with an essential gap is not 100/100. If an item genuinely does not apply to a topic, the reviewer must explain why rather than silently ignore it.

## Lesson-by-lesson status

| Lesson | Current state | Audit result |
|---|---|---|
| 01 — Variables and Data Types | Expanded revision committed (~5,940 words); includes a deeper names/objects model, identity/type/value distinctions, assignment evaluation, chained assignment, dynamic/strong typing distinction, mutability preview, and 12 exercises; full audit still pending | **Pending full technical, structural, and example verification** |
| 02 — Numbers and Operators | Canonical reference lesson selected by agreement | **Benchmark; do not infer that the other lessons meet this standard** |
| 03 — Strings | Expanded revision committed (~4,940 words); includes deeper literal, slicing, method, formatting, Unicode, encoding, lab, and exercise coverage | **Full technical and structural audit pending** |
| 04 — Type Conversion | Expanded revision committed (~3,450 words); adds a conversion pipeline, constructor boundaries, base parsing, truncation/rounding/floor distinctions, truthiness, finite checks, information-loss guidance, lab criteria, and explanatory examples | **Full technical and structural audit pending** |
| 05 — Input and Output | Existing material retained pending alignment | **Not yet audited against the canonical standard** |
| 06 — Booleans and None | Existing material retained pending alignment | **Not yet audited against the canonical standard** |
| 07 — Expressions and Statements | Existing material retained pending alignment | **Not yet audited against the canonical standard** |
| 08 — Comments and Code Style | Existing material retained pending alignment | **Not yet audited against the canonical standard** |
| 09 — Basic Debugging | Existing material retained pending alignment | **Not yet audited against the canonical standard** |

No numerical lesson scores are assigned in this revision. Scores will be recorded only after the corresponding audit is complete.

## Supporting material status

| Component | Current state |
|---|---|
| Module README | Updated to identify Lesson 2 as the benchmark and state that alignment is in progress |
| Learning Charter | Updated to point to the canonical lesson and the mandatory Roadmap standard |
| Main Roadmap | Updated with the complete Fundamentals lesson standard, review rubric, implementation order, and honest teaching-material status |
| Final assessment | Requires a consistency review after all nine lessons are aligned |
| Measurement Report project brief | Requires a consistency review against the final lesson scope and prerequisites |

## Verification progress

- Selected newly added examples from Variables and Data Types were executed successfully, including reassignment, right-hand-side evaluation, tuple assignment, chained assignment, and string rebinding.
- Selected newly added Strings examples were executed successfully. A format-width example initially had an incorrect expected padding count; execution exposed it, the expected output was corrected, and the selected examples then passed.
- Selected newly added Type Conversion examples were executed successfully, including base parsing, negative truncation/rounding/floor behavior, Boolean text truthiness, and finite-number checks.
- These are representative checks, not a claim that every code block in the three revised lessons has been executed. Full lesson audits remain pending.

## Verification policy

For each lesson, record what was actually checked:

- Review every objective against the teaching sections, lab, exercises, and answers.
- Check code fences, syntax, outputs, formulas, examples, and answer-key consistency.
- Execute all newly introduced or materially changed examples when practical; execute the lab's core solution and representative boundary cases.
- Check internal links and relevant official documentation references.
- Inspect heading order, numbering, repeated sections, orphan headings, tables, and Markdown structure.
- State clearly which examples were executed and which were only inspected. Never claim that all code was run if it was not.
- Keep the answer key after the exercise prompts in the same file.
- Do not update the learner's progress tracker as a side effect of editing lessons.

## Overall status

**Not yet approved as a fully aligned module.** Lesson 2 is the agreed reference. Lesson 1 has been expanded and is awaiting a complete audit; Lessons 3–9 still require alignment. The overall 100/100 approval from the previous review is withdrawn because the lessons were not, in fact, at a consistent depth.

This is a review of teaching-material quality only. It says nothing about the learner's mastery, which must be established through independent practice, assessment, and transfer work.
