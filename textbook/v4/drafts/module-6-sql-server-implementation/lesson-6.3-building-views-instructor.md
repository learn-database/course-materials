# Lesson 6.3 Building Views

## Instructor-Facing Content

### Module

Module 6: SQL Server Implementation

### Lesson purpose

Teach students how to identify a repeatable reporting need, build a view from a tested query, and verify that the resulting output answers the intended business question without exposing unnecessary details. The lesson should frame views as reusable reporting structures, not as shortcuts that replace judgment.

### Module context

This lesson closes the core implementation sequence in Module 6.

- Lesson `6.1` focused on building tables and constraints from the approved DBDD.
- Lesson `6.2` focused on careful data changes and output verification.
- Lesson `6.3` uses that existing structure and data to package reusable reporting logic.

The lesson also prepares students for the module's build-and-verify audit by reinforcing that technically successful SQL may still be wrong if it does not align with the business question or if it exposes the wrong information.

### Primary learning type(s)

Procedures

### Secondary learning type(s), if any

Problem solving / judgment

### Estimated time

75 to 90 minutes

### Lesson outcomes

By the end of this lesson, students should be able to:

- explain what problem a view solves and when one is appropriate
- distinguish a reusable reporting need from a one-time ad hoc query
- write and test a base `SELECT` before creating a view
- create a view in SQL Server from tested query logic
- verify whether a view output answers the intended business question
- judge whether a view supports transparent decisions without oversharing

### Module alignment

- Supports Module 6 Objective 3: create views that package reusable query logic for reporting.
- Reinforces Module 6's broader emphasis on verification that implementation aligns with intended design and use.
- Contributes directly to the module assessment task that asks students to verify whether a view output answers the intended business question.

### Course objective alignment

- Objective 1: know basic database terminology
- Objective 5: create and use SQL statements for querying and data manipulation

### Lesson sequence role

This lesson sits after the schema-building and DML lessons because a useful view depends on approved structure and meaningful data. It prepares students for Module 7 by giving them reporting objects that later operational topics can reference, but its most direct sequencing role is inside Module 6's implementation-and-verification arc.

### Required prior knowledge

- Lesson `6.1`: tables, PKs, FKs, and dependency-aware implementation from the approved DBDD
- Lesson `6.2`: inserts, updates, deletes, and verification after data changes
- Module 2 query basics, especially `SELECT`, joins, filtering, aliases, and result interpretation
- v4 naming conventions for implementation objects

### Lesson opening guidance

Open with two prompts:

1. "Find the one row from today's import where the tutor reference is missing."
2. "Show tomorrow's tutoring schedule with student, tutor, room, and subject."

Ask which one deserves a view and why. Use that comparison to frame the central rule: views should be justified by repeated reporting value, not by the fact that a query exists.

### Teaching notes

- Keep the lesson tied to approved design and loaded sample data. Do not teach views as isolated syntax.
- Insist on the sequence `test -> package -> verify -> revise`.
- Emphasize that `CREATE VIEW` success only proves that SQL Server accepted the definition.
- Use one coherent case so students spend their effort on view judgment, not on reloading context.
- Include one technically valid but misleading view and one oversharing view. Students need practice diagnosing output quality, not just syntax.
- Avoid drifting into advanced optimization or security administration. The lesson focus is reusable reporting logic and output verification.

### Online activities

- quick classification check: view-worthy or ad hoc
- short response: explain why a view stores query logic rather than copied report rows
- output-review check: determine whether a provided view answers the intended business question
- short judgment prompt: identify whether a view is transparent, oversharing, or both

### Homework / graded assignments

#### Assignment 1: choose and justify

Students compare one view-worthy question with one ad hoc query and justify both choices in business terms.

#### Assignment 2: build and verify a reporting view

Students submit a tested `SELECT`, a `CREATE VIEW` statement, a verification query, and a short explanation of whether the output answers the intended question without exposing unnecessary details.

### Deliverables

- one short rationale comparing a reusable reporting question with an ad hoc query
- one tested `SELECT` statement
- one `CREATE VIEW` statement
- one query against the created view
- one short verification note on business-question fit and data visibility

### Assessment plan

Formative evidence:

- classify view-worthy versus ad hoc questions
- identify missing or unnecessary columns in sample view outputs
- revise one technically valid but misleading view

Summative evidence:

- a view-creation submission built from a tested query
- a written verification note that evaluates fit to the intended business question
- a short explanation of whether the view is transparent without oversharing

Success should depend on judgment as well as syntax. A student who writes valid SQL but cannot explain why the output is right, wrong, incomplete, or oversharing has not met the main learning goal.

### Suggested rubric focus

- Reporting purpose is clear, repeatable, and appropriate for a view.
- Base query logic matches the stated business question before packaging.
- View definition is readable and uses a clear purpose-based name.
- Verification explains whether the output answers the intended question.
- Student identifies unnecessary exposure when a view includes details that do not serve the report purpose.

### Common misconceptions

- "Every useful query should become a view."
- "If `CREATE VIEW` runs successfully, the view must be correct."
- "A view stores report data like a new table."
- "More columns always make a view more transparent."
- "If data exists in a table, it should be shown in the report."

### Christian integration notes

Keep integration short and practical.

- Connect reporting quality to truthfulness and accountable business decisions.
- Connect column choice to stewardship of data visibility.
- Remind students that transparency is not the same as exposing every personal detail.
- Frame good view design as neighbor-serving information work: reports should be understandable, useful, and appropriately limited.

### Workflow connection

This lesson occupies the reporting-logic step of the larger workflow. Students move from design and implementation into reusable information use. The same verification habit developed here should carry into later modules, especially when they evaluate permissions, procedural logic, and final-project revisions. A view is therefore both a SQL object and an interpretation checkpoint: it reveals whether the database is helping the organization ask and answer the right question.
