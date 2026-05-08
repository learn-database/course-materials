# Lesson 2.2 Instructions: Optional Review of Set Operations on Relations

## Canonical Lesson Identity

- Lesson number: `2.2`
- Canonical title: `Optional Review of Set Operations on Relations`
- Canonical slug: `optional-review-of-set-operations-on-relations`
- Module: `Module 2: SQL Foundations`

## Output Paths

- Instruction file: `textbook/v4/lesson-instructions/lesson-2.2-optional-review-of-set-operations-on-relations-instructions.md`
- Student draft: `textbook/v4/drafts/module-2-sql-foundations/lesson-2.2-optional-review-of-set-operations-on-relations.md`
- Instructor draft: `textbook/v4/drafts/module-2-sql-foundations/lesson-2.2-optional-review-of-set-operations-on-relations-instructor.md`

## Required Source Package

Read these files before drafting or revising the lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/02-module-2-sql-foundations.md`

## Lesson Role In Module 2

This lesson is an optional bridge between Lesson `2.1` and Lesson `2.3`.

- Lesson `2.1` gives students the SQL Server working environment.
- Lesson `2.2` gives a brief conceptual review of set and relation ideas that make SQL retrieval easier to read.
- Lesson `2.3` turns those ideas into actual `SELECT`, `FROM`, `WHERE`, and `ORDER BY` use.

The lesson should support the module's larger emphasis on query reading, verification, and honest result interpretation.

## Primary Strategy

- Primary learning type: `Concepts`
- Secondary learning type: `Principles`
- Strategy pattern:
  - definition and classification
  - set-based examples and non-examples
  - comparison of row thinking versus set thinking

## Drafting Priorities

- Keep the lesson brief, optional, and supportive.
- Teach only the set ideas that help students read and interpret SQL retrieval behavior.
- Connect each idea directly to later SQL clauses or result-set behavior.
- Use small concrete examples instead of symbolic notation or formal proofs.

## Content Scope

Include only the ideas students need for early SQL thinking:

- relation as a table-like structure
- tuple and attribute as row and column vocabulary
- relational schema as a compact structure description
- selection as keeping rows that meet a condition
- projection as keeping needed columns
- union as combining compatible result sets at a basic level

## Scope Boundaries

Do not turn this lesson into a full relational theory chapter.

Avoid or keep only passing mention of:

- formal relational algebra notation
- proof-style or notation-heavy treatment
- advanced set operations beyond what supports later SQL reading
- deep treatment of joins, normalization, keys, or database design theory

## Required Emphasis

- Keep reminding students that the payoff is later SQL understanding.
- Frame selection as the idea behind `WHERE`.
- Frame projection as the idea behind the `SELECT` column list.
- Frame union as the idea behind combining compatible result sets with `UNION`.
- Clarify the difference between `relational schema` and `SQL Server schema`.
- Explain that query logic changes the result set being viewed, not the stored rows themselves.

## Example Guidance

Use one small running relation such as:

```text
Student(StudentID PK, LastName, Program)
```

with a few sample rows that let the lesson show:

- a named relation
- one tuple
- one attribute
- a simple selection
- a simple projection
- a simple compatible union-style combination

Examples should connect directly to the kinds of result interpretation students will do in Lessons `2.3` to `2.5`.

## Christian Integration Guidance

Keep integration embedded and brief.

- Connect careful row filtering and result interpretation to truthful business reporting.
- Use at least one reminder that a technically valid query can still misstate reality if it keeps the wrong rows or presents the wrong columns.
- If the lesson includes a prompt about sensitive fields or people-affecting outputs, keep it tightly tied to the retrieval example.

## Deliverables

Create or revise:

- `textbook/v4/drafts/module-2-sql-foundations/lesson-2.2-optional-review-of-set-operations-on-relations.md`
- `textbook/v4/drafts/module-2-sql-foundations/lesson-2.2-optional-review-of-set-operations-on-relations-instructor.md`

## Acceptance Checklist

- The lesson stays optional-review in tone and scope.
- The lesson explains only the set ideas needed to support SQL thinking.
- Examples connect relation and set ideas directly to SQL retrieval behavior students will soon see.
- The student draft is LMS-ready and teaches directly.
- The instructor draft explains module fit, lesson boundaries, practice, and likely misconceptions.
- Shared v4 lesson expectations are met, including module context, workflow connection, and embedded Christian integration.
