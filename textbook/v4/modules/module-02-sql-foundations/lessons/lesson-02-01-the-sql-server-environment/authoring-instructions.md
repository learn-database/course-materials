# Lesson 2.1 Instructions: The SQL Server Environment

## Lesson Identity

- Lesson number: `2.1`
- Canonical title: `The SQL Server Environment`
- Canonical slug: `the-sql-server-environment`
- Module: `Module 2: SQL Foundations`

## Objective

Draft Lesson 2.1 as the SQL Server orientation lesson for v4. The lesson should prepare students to work inside the course SQL environment before they begin deeper query-reading and query-evaluation work.

## Required Source Package

Read and apply these files:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/03-lesson-prompt.md`
3. `textbook/v4/05-lesson-writing-agent-index.md`
4. `textbook/v4/modules-plan/02-module-2-sql-foundations.md`
5. `textbook/christian_integration_guide.md`

Use `textbook/v4/02-instructional-strategies-for-lessons.md` and `textbook/v4/06-design-object-naming-and-notation-conventions.md` as supporting references for learning-type alignment and the schema-term distinction.

## Deliverables

Create these files:

- `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-01-the-sql-server-environment/authoring-instructions.md`
- `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-01-the-sql-server-environment/lesson.md`
- `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-01-the-sql-server-environment/instructor.md`

## Lesson Focus

Cover these ideas directly:

- client and server roles
- SSMS workspace basics, including Object Explorer, query window, results, and messages
- database context and why it must be checked before execution
- running provided starter scripts or starter statements carefully
- checking results and messages instead of assuming success
- optional alternate-client awareness for VS Code with the `mssql` extension or `sqlcmd`

## Required Emphasis

The lesson must:

- frame careful environment setup and script execution as accountable work
- teach result checking, not just button-clicking
- make classroom environment assumptions explicit when needed
- prepare students for Module 2's verification-oriented assessment pattern
- connect operational care to trustworthy reporting or responsible system stewardship at least once

## Scope Rules

- Keep the lesson tool-oriented and procedural, not a full query-writing lesson.
- Treat SQL Server and T-SQL as the defaults.
- Treat SSMS as the main classroom path unless the lesson explicitly marks an alternate-client note as optional.
- Introduce SQL Server schema only as a named container or namespace such as `dbo`.
- Do not drift into administration topics such as security design, server installation, or deep object management.

## Module Context To Preserve

Module 2 shifts assessment away from query generation alone and toward query reading, verification, and business-question alignment. Lesson 2.1 should therefore establish early habits of:

- checking execution context
- verifying whether results match the intended task
- explaining what the tool did and what the output means
- refusing to trust a script just because it ran

This lesson should prepare students for later lessons on single-table queries, aggregates, joins, and CTEs, and for the module's query-verification lab.

## Recommended Student-Facing Moves

- State the classroom assumptions plainly:
  - the course provides connection details
  - the course provides a target database
  - the course may provide starter scripts
  - screenshots or buttons may vary by tool version
- Show the basic execution path:
  - client sends request
  - SQL Server executes request
  - client displays results and messages
- Give students at least one repeatable verification routine before execution and one after execution.
- Include common beginner mistakes such as wrong server, wrong database context, partial selection, ignored messages, and rerunning setup scripts without checking prior results.

## Acceptance Checklist

The lesson is complete when:

- the student draft explains how to recognize context, run starter scripts, and verify results
- common setup mistakes and verification habits are included
- at least one touchpoint connects operational care to trustworthy business reporting or system stewardship
- the instructor draft aligns the lesson to Module 2's verification-centered assessment strategy
- the lesson remains asynchronous, AI-aware, and strong enough for independent study
