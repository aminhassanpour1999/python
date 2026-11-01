# Learning Charter

This file is the source of truth for how learning materials in this repository are planned, taught, reviewed, and maintained.

## Mission

Build deep, independent Python programming ability and the problem-solving skills needed to apply it—not merely collect notes or finish a book. The learner progresses one lesson at a time from fundamentals to advanced Python and, where useful, into language and implementation internals.

## Source hierarchy

1. **Python's official documentation is the primary technical authority.** Use the [Python Tutorial](https://docs.python.org/3/tutorial/) for guided learning, the [Language Reference](https://docs.python.org/3/reference/) for language syntax and semantics, and the [Standard Library reference](https://docs.python.org/3/library/) for built-ins and standard-library modules.
2. Use relevant official HOWTOs, PEPs, and Python project documentation for focused topics.
3. Use books, articles, courses, and other reliable material as supplementary explanations, exercises, and perspectives.
4. When sources disagree, prefer current official documentation for the relevant Python version. Record version-specific behavior and distinguish language guarantees from implementation details.

The curriculum is not controlled by any single book. Books may help explain a topic, but they do not replace official documentation as the source of truth.

## Language and scope

- Keep repository notes, topic outlines, code comments in examples, and project documentation in English unless a topic explicitly requires another language.
- Use Persian in conversational teaching when that helps explain concepts clearly.
- Organize the path from prerequisites to fundamentals, intermediate programming, advanced Python, and selected internals.
- This repository is Python-focused. Mathematics, scientific computing as a subject, signals and systems, communications, machine learning, and research content belong in separate subject-specific repositories.
- Avoid unnecessary fragmentation, duplicate explanations, and premature advanced details.
- Distinguish an outline, a working teaching draft, and an approved lesson. Existing files may contain full teaching notes; do not mislabel them as outlines.
- Develop or revise substantive lesson content when the learner is ready to study it or has explicitly authorized preparation. Do not fill the repository with material merely to make it look complete.
- Do not shorten a lesson simply to reduce its line count. Preserve useful depth; improve organization, explanations, examples, practice, and reference quality instead.

## Standard learning cycle

1. **Orient:** define the learning goal and prerequisites.
2. **Understand:** explain the concept clearly, including intuition and precise terminology.
3. **Read the source:** consult the relevant official documentation and identify what it specifies.
4. **Inspect:** study small examples and predict their behavior before running them.
5. **Experiment:** run, modify, and break examples to observe what changes.
6. **Practice independently:** solve exercises without seeing solutions first.
7. **Debug:** read errors, form hypotheses, test them, and explain the fix.
8. **Connect:** relate the concept to earlier knowledge and realistic uses.
9. **Build:** apply several concepts in a small, purposeful project when appropriate.
10. **Retrieve and review:** explain from memory, answer a knowledge check, and revisit weak areas.
11. **Document:** after the lesson is approved, add sufficiently deep English notes and verified references.

## Lesson content standard

For the nine Programming Fundamentals lessons, use [Lesson 2 — Numbers and Operators](./01-fundamentals/02-numbers-and-operators.md) as the canonical reference for instructional depth, organization, worked examples, practical application, exercise design, and model answers. The detailed mandatory standard and scoring gate live in the [Roadmap](./ROADMAP.md#canonical-lesson-standard--mandatory-for-all-nine-lessons). Do not mechanically copy its subject-specific content or force identical word counts; match its completeness and explanatory depth.

When a lesson is actually studied, its notes should account for every applicable item from this list:

- Learning objectives and prerequisites
- Clear concept explanations and mental models
- Syntax and semantics, including important distinctions
- Explanation grounded in the relevant official documentation
- Runnable examples with expected output and explanation
- Step-by-step worked examples where useful
- Common mistakes, edge cases, and debugging
- Best practices and when a feature is appropriate
- Approximately 10–12 independent exercises where the topic supports them, ordered from prediction and recall through application, debugging, and transfer
- Model answers placed after the exercise prompts in the same lesson file, so the learner can attempt problems first; do not create separate per-lesson solution files
- A knowledge check and concise summary
- Reliable references, primarily official Python documentation
- A meaningful coding lab with staged tasks, expected behavior, explicit acceptance criteria, and ordinary/boundary/invalid tests where applicable
- A small project or real-world connection when it adds learning value

Do not force every item into every lesson. Depth and format should fit the topic.

## Quality rules

- Accuracy and understanding matter more than speed or the number of files.
- Explain why something works, not only what to type.
- Distinguish what the Python documentation specifies from inference, implementation detail, or practical recommendation.
- Do not reveal exercise solutions before the learner attempts them unless requested.
- Never treat reading, copying, or generating notes as a substitute for writing code and solving new problems.
- Use sources responsibly; paraphrase rather than copying copyrighted material.
- Keep roadmap and progress tracking separate from lesson content.
- Do not mark a topic complete merely because its notes exist.

## Collaboration protocol

The learner and assistant work through one topic at a time. The assistant checks prerequisites and the roadmap, teaches and practices the concept interactively, then prepares or revises the English note. When the learner explicitly authorizes repository edits, make the requested changes and verify the resulting files. Otherwise, show substantive drafts for review before publishing. Keep lesson-material status separate from learner-progress status.

## Repository organization rule

Keep the learning path easy to navigate. Do not create separate answer-key or solutions files for individual lessons. Put exercise prompts first and model answers later in the same lesson file. Keep a cumulative assessment with its model answers at the end of that assessment file. The root `exercises/` directory is reserved for genuinely supplementary cross-module practice sets, not duplicate lesson exercises or separate answer keys. Add a new file only when it represents a genuinely distinct lesson, project, reference, or reusable tool.

## Additional lesson approval gate

Before a lesson is labeled an approved teaching reference, review it against these questions and the full mandatory checklist in the Roadmap:

1. **Coverage:** Are the essential concepts for this stage explicitly covered? Are deferred topics assigned to a later roadmap location?
2. **Depth:** Does the lesson explain why and how, not only list syntax or method names?
3. **Precision:** Are terminology, examples, edge cases, and expected outputs technically correct?
4. **Runnable practice:** Are there enough small examples to demonstrate each central idea? Are outputs shown where prediction matters?
5. **Transfer:** Does practice progress from recall to application, debugging, and unfamiliar reasoning?
6. **Independent attempt:** Do all exercise prompts appear before the explanatory model answers in the same lesson file, with no separate per-lesson solution file?
7. **Documentation:** Are relevant official documentation pages linked and accurately interpreted?
8. **Application:** Is there a lab or project when it adds real learning value?
9. **Boundaries:** Does the lesson avoid making later-stage features hidden prerequisites?
10. **Consistency:** Does the module README and roadmap accurately describe what the lesson teaches and what the learner has demonstrated?

A lesson should not receive a perfect score merely because it is long, has many headings, or contains many examples. A 100/100 rating requires evidence of accuracy, sufficient depth, complete stage-appropriate coverage, meaningful independent practice, relevant official references, and a verified review. If runtime behavior has not been tested, record that limitation rather than claiming full verification.
