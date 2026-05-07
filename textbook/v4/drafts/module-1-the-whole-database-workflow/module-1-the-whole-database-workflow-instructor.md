# Module 1: The Whole Database Workflow

## Instructor-Facing Overview

### Module Purpose

Module 1 is the orientation module for the whole course. Its job is to give students a reusable end-to-end map of the database workflow, establish the `ERD` versus `DBDD` boundary early, and set the expectation that AI-generated artifacts still require human verification and judgment.

### Alignment And Implementation Priorities

- keep the module broad, clear, and business-readable rather than notation-heavy
- teach the workflow as one connected sequence, not as isolated topics
- reinforce that the `ERD` is conceptual and the `DBDD` is implementation-ready
- keep normalization, SQL execution, and operational control at preview level only
- embed at least one normal-course prompt tying data structure to truthful reporting, stewardship, or neighbor-serving business practice

### Lesson Fit

- Lesson `1.1` establishes why databases matter and when a database is or is not warranted
- Lesson `1.2` traces the workflow from business process to working database and clarifies artifact-stage handoffs

Together, the lessons should prepare students for case framing, workflow ordering, and artifact-boundary judgment without requiring a full technical deliverable.

### What To Grade

- correct workflow sequence
- accurate distinction between `ERD` and `DBDD`
- sound judgment about when a database is appropriate
- explanation of what information a case must track
- ability to explain why workflow discipline supports trustworthy business reporting

### Assessment And Evidence Notes

- prefer timed or classification-based checks over polished artifact-only submissions
- use short case prompts, artifact-to-stage matching, and `ERD`-versus-`DBDD` classification
- if students produce a draft artifact or workflow summary with AI help, pair it with explanation or verification work that reveals whether they understand the choice

### Common Misconceptions

- "A database is always better than a spreadsheet."
- "The `ERD` and `DBDD` are basically the same diagram."
- "If AI can produce a clean artifact, the reasoning is probably correct."
- "Query writing is where database work really begins."
- "Any detail in a case description belongs in the database."

### Scope Boundaries And Risk Notes

- do not turn this module into a full modeling, normalization, or SQL lesson
- do not require a complete `ERD` or `DBDD` as the main evidence of learning here
- do not blur artifact boundaries by introducing data types, nullability, or implementation `PK`/`FK` notation as part of `ERD` instruction
- watch for students who can recite the workflow but cannot explain the purpose of each stage
- watch for overreliance on AI summaries that sound polished but misclassify business fit or artifact boundaries

### Grading Focus

This module should reward framing and judgment more than production polish. Students should leave with a stable mental model of the whole-system workflow and a clear understanding that correct database work depends on verifying why a choice is appropriate, not only on producing an artifact that looks finished.
