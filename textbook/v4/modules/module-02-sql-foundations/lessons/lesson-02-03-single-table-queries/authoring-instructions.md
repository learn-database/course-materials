# Lesson 2.3 Writing Instructions: Single-Table Queries

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file for this lesson.

## Assigned Lesson

- Lesson number: `2.3`
- Canonical title: `Single-Table Queries`
- Canonical slug: `single-table-queries`

## Output Paths

- Instruction file: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/lesson.md`
- Instructor draft: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/instructor.md`

## Summary

Draft Lesson 2.3, `Single-Table Queries`, as the first core SQL retrieval lesson in Module 2.

## Lesson Focus

Teach `SELECT`, `FROM`, `WHERE`, `ORDER BY`, aliases, and readable query structure for one-table reporting.

## Module Context

Lesson 2.3 follows:

- Lesson 2.1, where students learned the SQL Server environment and how to run code
- Lesson 2.2, an optional relational review that connects projection to column choice and selection to row filtering

Lesson 2.3 prepares students for:

- Lesson 2.4 on aggregates and grouping
- Lesson 2.5 on joins
- Lesson 2.6 on CTEs

The lesson must reflect Module 2's grading emphasis: students are judged on whether they can read, evaluate, verify, and explain query meaning, not only whether they can submit syntax that runs.

## Required Source Package

Read and apply these files:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/03-lesson-prompt.md`
3. `textbook/v4/05-lesson-writing-agent-index.md`
4. `textbook/v4/modules-plan/02-module-2-sql-foundations.md`
5. `textbook/christian_integration_guide.md`

Also use supporting v4 references as needed:

- `textbook/v4/01-module-content.md`
- `textbook/v4/02-instructional-strategies-for-lessons.md`
- `textbook/v4/06-design-object-naming-and-notation-conventions.md`

## Required Emphasis

- prioritize readable query structure and business-question alignment
- include examples where a valid query can still be misleading
- connect careless filtering to truthfulness and reporting risk
- remind students that AI can draft SQL, but students are still responsible for verifying whether a query answers the real question

## Lesson Design Notes

- Keep the lesson tightly within one-table scope.
- Use SQL Server and T-SQL defaults.
- Prefer one stable example table so students can focus on clause purpose rather than table-switching noise.
- Show clause-by-clause construction of a readable query.
- Include plain-language explanations of what each clause does.
- Include practice that asks students to interpret what a result set does and does not prove.
- Keep Christian integration embedded inside normal teaching elements such as why the lesson matters, common mistakes, reporting-risk warnings, and project checkpoints.

## Deliverables

Create all three files:

1. `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/authoring-instructions.md`
2. `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/lesson.md`
3. `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/instructor.md`

## Acceptance Criteria

- the lesson covers core single-table query clauses with plain-language explanation
- at least one example shows a technically valid query that does not answer the business question correctly
- practice elements ask students to interpret what a result set does and does not prove
- the lesson reflects Module 2's query-verification assessment model
- the lesson preserves the larger workflow connection to querying implemented data for business use
- Christian integration remains business-facing and subordinate to the technical lesson goal
- the student draft teaches directly enough for independent online use
- the instructor draft focuses on alignment, implementation, assessment, misconceptions, and risk notes rather than repeating the full lesson
