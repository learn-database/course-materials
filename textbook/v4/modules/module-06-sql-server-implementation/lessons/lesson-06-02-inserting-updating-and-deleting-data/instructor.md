# Lesson 6.2: Inserting, Updating, and Deleting Data

## Instructor-Facing Content

### Module

Module 6: SQL Server Implementation

### Lesson Purpose

Teach students to perform controlled data changes in SQL Server through dependency-aware inserts, condition-aware updates, careful deletes, and immediate verification of resulting data state. The lesson should make clear that successful execution is not enough. Students must decide whether a change is safe, meaningful, and aligned to the approved design.

### Module Context

Lesson 6.2 follows Lesson 6.1, where students built tables and constraints from the approved Database Design Diagram. It prepares students for Lesson 6.3, where they will build views for reporting. This position matters: the data changes made here determine whether later reporting is trustworthy. The lesson also supports Module 6's broader build-and-verify audit by treating DML as implementation work that still requires explanation, diagnosis, and verification.

### Primary Learning Type(s)

- Procedures

### Secondary Learning Type(s), If Any

- Problem solving / judgment

### Estimated Time

- 75 to 90 minutes

### Lesson Outcomes

By the end of the lesson, students should be able to:

- load sample data in dependency-aware order
- explain why selected child rows require matching parent rows
- write updates with conditions that fit the intended business action
- critique unsafe update or delete logic
- predict when a delete may fail because of dependencies or create business risk because of over-broad targeting
- verify that a completed change produced the intended database state
- justify sample data choices in terms of testing, reporting, privacy, and integrity

### Module Alignment

- Supports Module 6 Objective 2: load and change data in a dependency-aware and integrity-aware way.
- Extends the Lesson 6.1 emphasis that the approved design governs implementation choices.
- Prepares Lesson 6.3 by requiring representative, verified sample data for later view construction.
- Reinforces the module claim that output must be checked against the approved design, not trusted because SQL executed.

### Course Objective Alignment

- Course Objective 5: create and use SQL statements for querying and data manipulation
- Course Objective 6: administer introductory backup, recovery, security, and concurrency control work

### Lesson Sequence Role

This lesson is the transition from schema creation to data use. Students are no longer defining tables; they are proving they can operate within the rules those tables enforce. The lesson should repeatedly signal that DML is part of implementation verification, not a separate syntax island.

### Required Prior Knowledge

- Lesson 6.1 concepts: schema, table, `PK`, `FK`, entity integrity, referential integrity, and dependency-aware build order
- ability to read a small implementation-ready schema or Database Design Diagram
- basic `SELECT` use for preview and verification queries

### Lesson Opening Guidance

Begin by asking a structural question rather than a syntax question: "What must exist before a tutoring session can be inserted?" Use that prompt to reconnect students to parent-child reasoning from Lesson 6.1. Then shift to the broader lesson claim: a data change is only successful when it preserves structure and matches the business case.

### Teaching Notes

- Keep the lesson procedural. Show a full change cycle of preview, execute, and verify.
- Use one coherent case so students can see how inserts, updates, deletes, and later reporting fit together.
- Require students to preview target rows before non-trivial `UPDATE` or `DELETE` statements.
- Include at least one failed or near-failed change and explain it structurally in plain language.
- Treat verification as part of the procedure, not as optional cleanup.
- Keep the scope on controlled DML. Do not drift into transactions, triggers, or recovery workflow.
- Reinforce that AI-generated SQL is still subject to human verification and justification.
- Use SQL Server naming and T-SQL examples consistent with the course conventions.

### Online Activities

- parent-versus-child sequencing check
- guided DML lab with preview and verification queries
- short critique prompt where students identify why a proposed update or delete is unsafe
- discussion or annotation prompt asking what a failed delete reveals about relationship structure

### Homework / Graded Assignments

Assign a short DML script plus written explanation:

- insert representative sample data in dependency-aware order
- preview and perform one careful update with a narrow condition
- analyze or attempt one delete where dependencies or business meaning matter
- verify results after each major operation
- explain one unsafe change, failure, or over-broad condition in plain language
- justify why the sample data supports later querying or reporting

### Deliverables

- one SQL script containing `INSERT`, `UPDATE`, `DELETE`, preview queries, and verification queries
- one short explanation of one unsafe or failed data change
- one short note explaining why the sample data is useful and responsibly chosen

### Assessment Plan

Primary evidence item: controlled DML script

Checklist:

- inserts are sequenced in parent-before-child order
- inserted rows preserve intended foreign key relationships
- at least one update uses a clear and appropriately narrow condition
- preview and verification queries are present for risky changes
- delete behavior is predicted, explained, or handled with dependency awareness
- the final data state is checked against the intended business outcome

Secondary evidence item: short explanation and critique

Checklist:

- the explanation names the relevant schema rule, dependency, or targeting risk
- the explanation is written in plain business-facing language
- the critique explains why a proposed change is unsafe, not only that it is wrong
- the response connects sample data or change logic to integrity, privacy, stewardship, or truthful reporting when appropriate

### Suggested Rubric Focus

- quality of insert sequencing
- precision of update targeting
- quality of delete reasoning
- discipline of preview and verification
- ability to detect unsafe change logic
- clarity of explanation in structural and business terms
- quality and restraint of sample data choices

### Common Misconceptions

- "If the statement executes, the change must be correct."
- "A foreign key problem is just a SQL Server annoyance, not a relationship rule."
- "Any `WHERE` clause is good enough."
- "A delete is safe if it only affects one table."
- "Sample data is filler, so realism and restraint do not matter."
- "Verification means only checking that rows exist, not checking that the business meaning stayed correct."

### Christian Integration Notes

- Present careful data changes as stewardship of organizational information and operational trust.
- Connect unsafe updates and deletes to truthfulness: a technically successful statement can still create false reporting or hide real follow-up work.
- Connect sample data choices to privacy by discouraging unnecessary sensitive details in note text or test records.
- Keep the integration inside normal teaching moments such as common mistakes, critique prompts, and the project checkpoint rather than in a separate reflection block.

### Workflow Connection

In the course workflow, this lesson is where the approved design becomes active database use. Students have already interpreted the business process, built the ERD and DBDD, and created tables in SQL Server. Now they must change data in a way that preserves integrity and prepares for trustworthy reporting. The verification habits taught here carry directly into Lesson 6.3 and the broader Module 6 build-and-verify audit.
