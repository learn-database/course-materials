# Lesson 6.2 Writing Instructions

## Canonical Lesson Identity

- Lesson number: `6.2`
- Canonical title: `Inserting, Updating, and Deleting Data`
- Canonical slug: `inserting-updating-and-deleting-data`
- Instruction file: `textbook/v4/lesson-instructions/lesson-6.2-inserting-updating-and-deleting-data-instructions.md`
- Student draft: `textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.2-inserting-updating-and-deleting-data.md`
- Instructor draft: `textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.2-inserting-updating-and-deleting-data-instructor.md`

## Required Source Package

Read and follow these sources before revising or regenerating this lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/06-module-6-sql-server-implementation.md`

## Lesson Role In Module 6

Lesson 6.2 sits after table creation and before view construction. Students already built schema structure in Lesson 6.1. This lesson teaches them to use that structure through controlled data changes that are dependency-aware, integrity-aware, and verified against business intent. It prepares students for Lesson 6.3 by requiring sample data and change logic that will support meaningful reporting views.

## Learning Strategy

- Primary learning type: `Procedures`
- Secondary learning type: `Problem solving / judgment`
- Strategy pattern:
  - stepwise execution
  - controlled data-change practice
  - failure or near-failure diagnosis
  - verification after each change

## Core Scope

Keep the lesson tightly focused on controlled DML in SQL Server:

- `INSERT` in dependency-aware parent-before-child order
- `UPDATE` with safe and well-justified conditions
- `DELETE` with dependency awareness and careful business reasoning
- verification habits after each change
- sample data as a purposeful testing and reporting asset

Do not expand the lesson into transactions, rollback strategy, triggers, stored procedures, bulk import tooling, or advanced admin topics.

## Required Emphasis

The lesson must:

- emphasize data-change safety and verification
- show that successful execution is not enough
- teach students to judge whether a change is safe, meaningful, and aligned to the approved design
- include at least one unsafe `UPDATE` or `DELETE` example that students must critique
- connect data changes to stewardship, privacy, and integrity concerns
- frame verification as part of the procedure rather than optional cleanup

## Required Teaching Moves

- Reconnect directly to Lesson 6.1 by showing that DML operates under the schema and constraints already built.
- Use SQL Server and T-SQL examples.
- Keep a single running case so insert order, update targeting, delete behavior, and later reporting value remain connected.
- Include at least one failed or near-failed data change and explain it structurally in plain language.
- Teach students to preview target rows before risky `UPDATE` or `DELETE` statements.
- Require students to verify both row-level results and business meaning after each major change.
- Include sample data guidance that rejects low-value filler rows and unnecessary sensitive details.

## Recommended Running Case

Use the Lakeside Tutoring Center case already associated with Module 6:

- `Student(StudentID, FirstName, LastName, EmailAddress)`
- `Tutor(TutorID, FirstName, LastName, EmailAddress)`
- `Subject(SubjectID, SubjectName)`
- `Session(SessionID, StudentID, TutorID, SubjectID, SessionDate, StartTime, Room)`
- `SessionNote(SessionNoteID, SessionID, NoteText, FollowUpNeeded)`

The lesson should make these relationship rules visible:

- `Session` depends on valid `Student`, `Tutor`, and `Subject` rows
- `SessionNote` depends on a valid `Session` row

## Non-Negotiable Content Requirements

The student draft must include:

- direct teaching for independent online study
- explanation of parent rows, child rows, referential integrity, conditions, and verification
- at least one dependency-aware insert example
- at least one safe update example and one unsafe update example
- at least one delete example where dependency or business logic must be checked before execution
- at least one verification checklist or repeatable procedure
- guided practice that includes critique of unsafe change logic
- assignment guidance that requires explanation, not just working SQL

The instructor draft must include:

- module alignment and workflow connection
- lesson outcomes aligned to Module 6 objectives
- online activity and homework guidance
- rubric or checklist language for each evidence item
- misconceptions to watch for
- Christian integration notes tied to stewardship, privacy, integrity, and truthful reporting

## Assessment Expectations

Pair the DML artifact with second evidence. Acceptable evidence in this lesson includes:

- critique-and-repair of unsafe update or delete logic
- short explanation of why a data change is risky or safe
- verification of whether the resulting data state matches the business case

The lesson should make clear that AI can help draft DML, but students remain responsible for previewing targets, verifying results, and defending final change logic.

## Acceptance Checklist

Use this checklist before considering the lesson ready:

- the lesson teaches how inserts, updates, and deletes depend on structure and conditions
- at least one example or exercise asks students to detect unsafe change logic
- the lesson includes verification habits for checking that a data change did what the business case intended
- the lesson preserves the Module 6 focus on implementation verification rather than syntax alone
- the lesson supports the shared v4 expectation that artifact production is paired with explanation, diagnosis, or verification
- the lesson keeps Christian integration inside normal teaching elements rather than a stand-alone devotional section
