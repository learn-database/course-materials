# Lesson 6.1 Writing Instructions: Creating Tables and Constraints

## Lesson Identity

- Lesson number: `6.1`
- Canonical title: `Creating Tables and Constraints`
- Canonical slug: `creating-tables-and-constraints`
- Module: `Module 6: SQL Server Implementation`

## Output Paths

- Instruction file: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-01-creating-tables-and-constraints/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-01-creating-tables-and-constraints/lesson.md`
- Instructor draft: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-01-creating-tables-and-constraints/instructor.md`

## Required Source Package

Read and follow these files before drafting:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/06-module-6-sql-server-implementation.md`

## Lesson Role Inside Module 6

Lesson 6.1 is the implementation handoff from Module 5 design artifacts to Module 6 SQL Server execution.

- Prior lesson context:
  - Module 5 established the approved Database Design Diagram as the implementation-ready artifact.
  - Students should already understand that the ER Diagram and DBDD are different artifacts.
- Current lesson role:
  - teach DDL basics
  - teach `CREATE TABLE`
  - teach PK and FK constraints
  - teach dependency-aware build order
  - teach verification that the built schema matches the approved DBDD
- Forward link:
  - Lesson 6.2 depends on these tables and constraints for safe `INSERT`, `UPDATE`, and `DELETE` work.

## Learning Strategy

Use the Lesson 6.1 strategy from `textbook/v4/02-instructional-strategies-for-lessons.md`.

- Primary learning type: `Procedures`
- Secondary learning type: `Principles`
- Required strategy pattern:
  - modeled DDL build
  - dependency-order demonstration
  - execution with verification
  - failure diagnosis
- Required assessment evidence:
  - students build tables and constraints in a dependency-aware order
  - students explain why order and constraints matter
  - students verify the built schema against the DBDD

## Non-Negotiable Scope

The lesson must stay tightly focused on the approved DBDD becoming executable SQL Server structure.

Include:

- DDL basics in SQL Server
- `CREATE TABLE` syntax as implementation work, not redesign
- primary key and foreign key constraints
- at least brief treatment of `NOT NULL`, `UNIQUE`, `CHECK`, and `DEFAULT` where the case requires them
- dependency-aware build order
- verification against the approved DBDD

Do not expand into:

- data loading as the main focus
- broader query instruction
- advanced SQL Server storage or indexing topics
- a catalog of every possible SQL Server constraint option

## Required Emphasis

The lesson must explicitly do all of the following:

- tie DDL choices back to the approved design rather than treating SQL writing as free-form invention
- explain why dependency order matters operationally, not just syntactically
- explain why integrity constraints matter operationally, not just syntactically
- connect constraints to accountability and business-rule fidelity in the case
- treat successful execution as necessary but insufficient without verification
- preserve the ERD versus DBDD boundary

## Required Case And Teaching Moves

Use one coherent case that includes parent and child tables. The lesson should support all of these instructional moves:

- model how to read a DBDD and convert it into `CREATE TABLE` statements
- show how to determine parent-first build order from FK dependencies
- demonstrate at least one build-order failure or constraint omission and diagnose it
- provide at least one verification or audit item in which students detect where the built schema drifts from the DBDD
- include at least one touchpoint asking which constraint matters most for trustworthy operations in the case and why

## Student-Facing Requirements

The student lesson must be LMS-ready and teach directly for independent study.

Required sections:

- Lesson overview
- Why this lesson matters
- Lesson outcomes
- How this lesson fits the module
- How this lesson fits the larger workflow
- Key terms
- Readings and media
- Core content
- Examples and case
- Guided practice
- What to do
- Assignments
- Deliverables
- Project checkpoint or module connection
- Wrap-up

The student-facing content must include:

- at least one full `CREATE TABLE` example set
- a dependency-aware table-creation sequence
- a schema-verification checklist or audit routine tied to the DBDD
- one prompt that asks students to detect schema drift from the approved design
- one prompt that asks students which constraint matters most for trustworthy operations in the case

## Instructor-Facing Requirements

The instructor draft should focus on implementation, alignment, and assessment rather than restating the whole lesson.

Required sections:

- Module
- Lesson purpose
- Module context
- Primary learning type
- Secondary learning type
- Estimated time
- Lesson outcomes
- Module alignment
- Course objective alignment
- Lesson sequence role
- Required prior knowledge
- Lesson opening guidance
- Teaching notes
- Online activities
- Homework / graded assignments
- Deliverables
- Assessment plan
- Suggested rubric focus
- Common misconceptions
- Christian integration notes
- Workflow connection

The instructor draft must explicitly reinforce:

- verification against the approved DBDD
- diagnosis of build-order and constraint failures
- the module's build-and-verify audit assessment pattern

## Christian Integration Guidance

Use the module 6 and chapter 11 integration direction from the course documents.

- Keep integration subordinate to the technical goal.
- Connect constraints to trustworthy operations, accountability, and business-rule fidelity.
- Use business-facing language such as stewardship, trust, transparency, integrity, and responsible data use only where it fits naturally.
- Do not add a stand-alone devotional section.

## Acceptance Checklist

The lesson package is acceptable only if all of the following are true:

- the lesson explains how to build tables and constraints in dependency-aware order
- at least one example or audit item asks students to detect where a schema build drifts from the DBDD
- at least one touchpoint asks which constraint matters most for trustworthy operations in the case
- the lesson reflects Module 6's emphasis on implementation verification
- the lesson meets the shared v4 lesson rules for async direct teaching, AI-aware verification, and module-context alignment
