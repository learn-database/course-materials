# Lesson 8.3: Final Project Integration and Revision

## Lesson Overview

This lesson completes the course by treating your database project as one connected package instead of a stack of separate assignments. A final project is not trustworthy just because each file looks reasonable on its own. It is trustworthy when the requirements, ER Diagram, Database Design Diagram, SQL objects, procedural logic, permissions, and tests tell the same business story.

In Lessons 8.1 and 8.2, you learned how to justify and test stored procedures and triggers. In Lesson 8.3, you will review the whole system, respond to a late change request, and explain your revisions honestly.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- review a full project package for cross-artifact consistency
- trace one business-rule change across the artifacts that should be affected
- explain which artifacts must change, which can stay the same, and why
- revise a project in a defensible order from earliest artifact to latest implementation
- judge whether views, procedures, triggers, permissions, and tests still match the revised design
- evaluate whether the final package is coherent, honest about limitations, and trustworthy for the stated business purpose

## Key Terms

- `cross-artifact consistency`: agreement across the project package so names, rules, structures, and behaviors align
- `change request`: a late adjustment to business requirements, access rules, or expected outputs
- `revision path`: the order in which you update artifacts after finding a problem or receiving a new rule
- `trustworthy package`: a complete, reviewable submission that matches its stated scope and does not hide known limits
- `limitation statement`: a short explanation of what the package does not do, or what remains simplified, so the reviewer is not misled

## Readings And Media

- Read this lesson carefully before revising your final project.
- Keep `textbook/v4/06-design-object-naming-and-notation-conventions.md` available while you review names and artifact boundaries.
- Revisit your Module 8 work on stored procedures and triggers if your project uses them.
- Gather your own current project artifacts before starting the guided and independent work.

## Core Content

## 1. Treat The Final Project As One System

Your final project usually includes several artifact types:

- requirements summary or business-rule list
- ER Diagram
- Database Design Diagram
- SQL table and constraint scripts
- views
- stored procedures
- triggers
- permissions or user-role notes
- tests or verification evidence

Do not review these one at a time as if they were unrelated homework files. Review them as one system. If the requirements say one thing, the ERD shows another, the DBDD shows a third, and the SQL scripts implement a fourth, the package is not ready.

## 2. Start With The Change, Then Trace Its Reach

When a late change arrives, do not jump straight into SQL. Start by asking three questions:

1. What exactly changed in the business rule?
2. Which artifacts express that rule?
3. What evidence would show the revised package is still coherent?

This helps you avoid surface-only edits. A late change often reaches farther than one script.

## 3. Keep Artifact Boundaries Clear

Reviewing the whole package does not erase the differences between artifacts.

Keep these boundaries explicit:

- the ER Diagram is conceptual and shows entities, identifiers, relationships, cardinality, and optionality
- the Database Design Diagram is implementation-ready and shows tables, columns, PKs, FKs, data types, and nullability
- SQL scripts build and enforce the design
- views shape outputs for specific business questions
- procedures and triggers automate selected behavior
- permissions define who may see or change what
- tests show whether the revised package actually behaves as intended

Do not fix an ERD problem by adding SQL data types to the ERD. Do not fix a permission problem only by changing a view name. Each artifact has its own job.

## 4. Revise From Earliest Artifact To Latest Artifact

When you find a mismatch, look for the earliest place where the problem begins.

Use this revision order:

1. confirm the requirement or business rule
2. update the ER Diagram if the conceptual structure changed
3. update the Database Design Diagram if the implementation-ready structure changed
4. update SQL tables, constraints, and other database objects
5. update views, procedures, triggers, and permissions if the change affects behavior or access
6. update tests and verification notes
7. update any limitation statement or submission memo

This sequence matters because downstream artifacts should implement upstream decisions, not invent them.

## 5. Worked Case: Harbor Community Tutoring Late Change

Assume a tutoring-center project already tracks `Student`, `Tutor`, `Session`, `Subject`, and `SessionNote`.

Late change request:

`Every completed tutoring session must have exactly one approved session note. The note must record ApprovedByTutorID and ApprovedAt. Families may see whether a note exists, but only LeadTutor and ProgramDirector roles may read the note text.`

This one change can touch many artifacts.

### Requirements / Business Rules

The package now needs a rule that links note approval to completed sessions and a rule that limits note-text visibility.

### ER Diagram

The ERD may need revision if it previously showed `SessionNote` as optional without the new completed-session rule, or if it did not distinguish the relationship needed to support note approval clearly.

### Database Design Diagram

The DBDD may need:

- `ApprovedByTutorID`
- `ApprovedAt`
- revised nullability rules
- clearer relationship detail between `Session` and `SessionNote`

### SQL Tables And Constraints

The SQL implementation may need:

- new columns in `SessionNote`
- foreign-key support for `ApprovedByTutorID`
- constraints that fit the revised completion rule where possible

### Views

If the project includes a family-facing progress view, that view should not expose note text. It may need to expose only a flag such as `HasApprovedSessionNote`.

### Procedures

If a procedure marks a session as completed, that procedure may need revision so it checks for the required approved note or coordinates the completion workflow differently.

### Triggers

A trigger might be justified if the project chooses event-driven enforcement for a rule that must be checked automatically on update. A trigger might also be unnecessary if the project already enforces the rule cleanly inside a completion procedure. The point is not to add a trigger automatically. The point is to justify the choice.

### Permissions

Roles such as `LeadTutor`, `ProgramDirector`, `FamilyPortalReader`, or similar access definitions may need revision so note text is restricted while summary status remains visible.

### Tests

The project now needs tests for:

- attempting to complete a session without an approved note
- completing a session with a valid approved note
- confirming family-facing outputs hide note text
- confirming authorized roles can still access the right data

## 6. Ask Which Artifacts Must Change And Why

A good revision response does not say, "Everything changed." It also does not say, "I only updated the SQL script."

A better response sounds like this:

`The change affects requirements, the ERD, the DBDD, the SessionNote table script, the completion procedure, the family-facing progress view, permission grants, and the test set. I did not add a trigger because the completion procedure already controls the unit of work, and adding a trigger would duplicate the rule without improving clarity.`

That answer is strong because it identifies both changed and unchanged artifacts with reasons.

## 7. Review Coherence, Honesty, And Trust

Before submitting a final package, ask:

- Do the artifacts still describe the same business purpose?
- Are the names consistent across requirements, ERD, DBDD, SQL, views, procedures, triggers, permissions, and tests?
- Does each artifact still do the job it is supposed to do?
- Are known limitations stated honestly instead of hidden?
- Could another reviewer follow the revision path without guessing?

This matters technically and ethically. Trustworthy work does not hide drift, missing pieces, or unsupported claims.

## 8. Use AI Carefully In Final Revision

AI can help compare scripts, propose revised SQL, list possibly affected artifacts, or generate test ideas. That can save time. It does not remove your responsibility to verify:

- whether the proposed change belongs in the ERD or only in the DBDD
- whether a trigger is justified or duplicated unnecessarily
- whether permissions actually match the business rule
- whether tests prove the revised behavior
- whether your final explanation is truthful about what the project does and does not do

In this lesson, human judgment matters most in deciding scope, coherence, and trustworthiness.

## Examples And Case

## Quick Contrast Example

Weak revision note:

`Updated final project for new note rule.`

Stronger revision note:

`The change request affected the SessionNote relationship and note-approval fields, so I revised the requirement summary, ERD, DBDD, SessionNote table script, completion procedure, family progress view, permission grants, and tests. I did not add a trigger because the completion procedure already enforces the rule as one unit of work.`

The stronger note helps a reviewer trust the package because it names the affected artifacts and explains one deliberate non-change.

## Case Question

For the tutoring-center change request, which artifacts must change and why?

Use this list and write one reason beside each item:

- requirements or business-rule summary
- ER Diagram
- Database Design Diagram
- SQL tables and constraints
- family-facing view
- completion procedure
- trigger, if any
- permissions
- tests

Then identify one artifact that may not need to change and justify that decision.

## Guided Practice

## Practice 1: Artifact Reach Check

Read the tutoring-center change request again. For each artifact below, mark `must change`, `might change`, or `no change`, then write one sentence of justification.

| Artifact | Decision | Why |
| --- | --- | --- |
| Requirements / business rules |  |  |
| ER Diagram |  |  |
| Database Design Diagram |  |  |
| SQL tables / constraints |  |  |
| Views |  |  |
| Procedures |  |  |
| Triggers |  |  |
| Permissions |  |  |
| Tests |  |  |

## Practice 2: Earliest-Artifact Diagnosis

Suppose a student updated the `SessionNote` table script and family-facing view, but the ER Diagram and Database Design Diagram still show the old structure.

Answer:

1. Where does the revision path need to restart?
2. Why is the current package still incoherent?
3. Which downstream artifacts should be checked again after the earlier artifacts are fixed?

## Practice 3: Honest Limitation Statement

Write a 2 to 4 sentence limitation statement for this situation:

`Your project now enforces note approval for session completion, but you did not build a separate audit table for note revision history.`

The statement should be honest without pretending the package does more than it does.

## Practice 4: Trustworthiness Check

Answer these questions:

1. What part of this revision most directly supports truthful and trustworthy reporting?
2. What part most directly protects sensitive information?
3. What would make the package less trustworthy even if the SQL compiles?

## What To Do

1. Gather your current project package.
2. Identify one late change request or one known inconsistency in the package.
3. Trace which artifacts are affected.
4. Revise from the earliest affected artifact to the latest.
5. Check whether views, procedures, triggers, permissions, and tests still fit the revised rule.
6. Write a short explanation of what changed, what did not change, and why.
7. Add an honest limitation statement if the package still simplifies part of the business situation.

## Assignments

## Assignment 1: Change-Request Revision Matrix

Create a revision matrix for one business-rule change in your project.

Your matrix must include:

- the change request in one or two sentences
- each relevant artifact type
- whether it changed, might need review, or did not change
- a brief why statement for each row

## Assignment 2: Final Integration Memo

Write a 400 to 700 word memo that:

- explains the change request
- describes the revision path you followed
- names at least one artifact that changed and one artifact that stayed unchanged
- justifies any view, procedure, trigger, permission, or test changes
- states whether the final package is coherent, honest about limitations, and trustworthy for the stated business purpose

## Deliverables

- one completed change-request revision matrix
- one revised final project package or revised project sample
- one final integration memo

## Project Checkpoint Or Module Connection

Before you finish Module 8, use this checkpoint:

`Does my final package still tell one coherent story across the requirements, ERD, DBDD, SQL objects, outputs, access rules, and tests? If it has limitations, did I state them honestly? Would a reviewer trust this package for the business purpose I claim it serves?`

This checkpoint is part of faithful professional follow-through. Coherence and honesty are not extra polish. They are part of database quality.

## Wrap-Up

Lesson 8.3 completes the course by shifting attention from isolated artifacts to integrated revision. A database solution is not fully defensible until it can absorb change without becoming inconsistent or misleading. Your strongest final evidence is not that you built a package once. It is that you can review it, revise it, justify it, and state its limits truthfully.
