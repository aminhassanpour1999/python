# Learning Charter

This file is the source of truth for how learning materials in this repository are planned and developed.

## Mission

Build deep, independent Python programming ability and the problem-solving skills needed to apply it—not merely collect notes or finish a book. Python's official documentation is a primary reference, but learning may draw on high-quality books, official documentation, exercises, projects, and other reliable resources. No single book controls the curriculum.

## Language and scope

- Keep repository notes, topic outlines, code comments in examples, and project documentation in English unless a topic explicitly requires another language.
- Use Persian in conversational teaching when that helps explain concepts clearly.
- Organize the path from prerequisites to fundamentals, then applications and specialization.
- Avoid unnecessary fragmentation, duplicate explanations, and premature advanced details.
- Distinguish an outline, a working teaching draft, and an approved lesson. Existing files may contain full teaching notes; do not mislabel them as outlines.
- Develop or revise substantive lesson content when the learner is ready to study it or has explicitly authorized preparation. Do not fill the repository with material merely to make it look complete.
- Do not shorten a lesson simply to reduce its line count. Preserve useful depth; improve organization, explanations, examples, practice, and reference quality instead.

## Standard learning cycle

1. **Orient:** define the learning goal and prerequisites.
2. **Understand:** explain the concept clearly, including intuition and precise terminology.
3. **Inspect:** study small examples and predict their behavior before running them.
4. **Experiment:** run, modify, and break examples to observe what changes.
5. **Practice independently:** solve exercises without seeing solutions first.
6. **Debug:** read errors, form hypotheses, test them, and explain the fix.
7. **Connect:** relate the concept to earlier knowledge and realistic uses.
8. **Build:** apply several concepts in a small, purposeful project when appropriate.
9. **Retrieve and review:** explain from memory, answer a knowledge check, and revisit weak areas.
10. **Document:** only after the lesson is approved, add concise but sufficiently deep English notes and verified references.

## Lesson content standard

For the nine Programming Fundamentals lessons, use [Lesson 2 — Numbers and Operators](./01-fundamentals/02-numbers-and-operators.md) as the canonical reference for instructional depth, organization, worked examples, practical application, exercise design, and model answers. The detailed mandatory standard and scoring gate live in the [Roadmap](./ROADMAP.md#canonical-lesson-standard--mandatory-for-all-nine-lessons). Do not mechanically copy its subject-specific content or force identical word counts; match its completeness and explanatory depth.

When a lesson is actually studied, its notes should account for every applicable item from this list:

- Learning objectives and prerequisites
- Clear concept explanations and mental models
- Syntax and semantics, including important distinctions
- Runnable examples with expected output and explanation
- Step-by-step worked examples where useful
- Common mistakes, edge cases, and debugging
- Best practices and when a feature is appropriate
- Approximately 10–12 independent exercises where the topic supports them, ordered from prediction and recall through application, debugging, and transfer
- Model answers placed after the exercise prompts in the same lesson file, so the learner can attempt problems first; do not create separate solution files
- A knowledge check and concise summary
- Reliable references, preferring official documentation when suitable
- A meaningful coding lab with staged tasks, expected behavior, explicit acceptance criteria, and ordinary/boundary/invalid tests where applicable
- A small project or real-world connection when it adds learning value

Do not force every item into every lesson. Depth and format should fit the topic.

## Quality rules

- Accuracy and understanding matter more than speed or the number of files.
- Distinguish essential knowledge from optional deeper material.
- Explain why something works, not only what to type.
- Do not reveal exercise solutions before the learner attempts them unless requested.
- Never treat reading, copying, or generating notes as a substitute for writing code and solving new problems.
- Use sources responsibly; paraphrase rather than copying copyrighted material.
- Keep roadmap and progress tracking separate from lesson content.
- Do not mark a topic complete merely because its notes exist.

## Collaboration protocol

The learner and assistant work through one topic at a time. The assistant checks prerequisites and the roadmap, teaches and practices the concept interactively, then prepares or revises the English note. When the learner explicitly authorizes repository edits, make the requested changes and verify the resulting files. Otherwise, show substantive drafts for review before publishing. Keep lesson-material status separate from learner-progress status.

## Long-term direction

Build a strong foundation in Python and programming, then progress into mathematics, scientific computing, signals and systems, communications, machine learning, and research workflows. Respect prerequisite order and connect these areas through projects when appropriate.


## Repository organization rule

Keep the learning path easy to navigate. Do not create separate answer-key or solutions files for individual lessons. Put exercise prompts first and model answers later in the same lesson file. Keep a single cumulative assessment with its model answers at the end of that assessment file. Add a new file only when it represents a genuinely distinct lesson, project, reference, or reusable tool.

## Additional lesson approval gate

Before a lesson is labeled an approved teaching reference, review it against these questions and the full mandatory checklist in the Roadmap:

1. **Coverage:** Are the essential concepts for this stage explicitly covered? Are deferred topics assigned to a later roadmap location?
2. **Depth:** Does the lesson explain why and how, not only list syntax or method names?
3. **Precision:** Are terminology, examples, edge cases, and expected outputs technically correct?
4. **Runnable practice:** Are there enough small examples to demonstrate each central idea? Are outputs shown where prediction matters?
5. **Transfer:** Does practice progress from recall to application, debugging, and unfamiliar reasoning?
6. **Independent attempt:** Do all exercise prompts appear before the explanatory model answers in the same lesson file, with no separate per-lesson solution file?
7. **Application:** Is there a lab or project when it adds real learning value?
8. **Boundaries:** Does the lesson avoid making later-stage features hidden prerequisites?
9. **References:** Are authoritative sources linked for version-sensitive or nuanced behavior?
10. **Consistency:** Does the module README and roadmap accurately describe what the lesson teaches and what the learner has demonstrated?

A lesson should not receive a perfect score merely because it is long, has many headings, or contains many examples. A 100/100 rating requires evidence of accuracy, sufficient depth, complete stage-appropriate coverage, meaningful independent practice, and a verified review. If runtime behavior has not been tested, record that limitation rather than claiming full verification.
