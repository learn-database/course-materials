# Lesson 2.6 Writing Instructions

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file for this lesson.

## Assigned lesson

- Lesson number: `2.6`
- Canonical title: `Common Table Expressions`
- Canonical slug: `common-table-expressions`
- Module: `Module 2: SQL Foundations`

## Output paths

- Instruction file: `textbook/v4/lesson-instructions/lesson-2.6-common-table-expressions-instructions.md`
- Student draft: `textbook/v4/drafts/module-2-sql-foundations/lesson-2.6-common-table-expressions.md`
- Instructor draft: `textbook/v4/drafts/module-2-sql-foundations/lesson-2.6-common-table-expressions-instructor.md`

## Summary

Draft Lesson 2.6, `Common Table Expressions`, as the readability and intermediate-result lesson for SQL Foundations.

## Required source package

Read these files before drafting:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/02-module-2-sql-foundations.md`

## Lesson focus

Teach how nonrecursive CTEs organize intermediate result sets, support readable query logic, and help students reason about multi-step retrieval.

## Module context to preserve

- This lesson follows `Aggregates and Grouping` and `Joins`.
- It should show students how to reorganize already-working grouped and joined queries into clearer stages.
- It should prepare students for the module's query-verification emphasis by making intermediate logic easier to inspect and explain.
- It should reinforce that readable SQL supports trustworthy business reporting, not just cleaner formatting.

## Lesson-specific requirements

- Keep the lesson focused on nonrecursive CTEs used with `SELECT`.
- Present CTEs as a readability, reasoning, and verification tool rather than as advanced syntax.
- Use business-facing reporting examples with meaningful intermediate result sets.
- Make students explain what the intermediate result contains before they interpret the final result.
- Keep the lesson aligned to the v4 AI-available model by including explanation, comparison, and verification work in addition to query writing.

## Required emphasis

- present CTEs as a readability and reasoning tool
- use business-facing examples with intermediate logic students can inspect
- explain what problem a CTE solves in readable query design
- keep the focus on clarity, verification, and business-question alignment

## Boundaries and non-goals

- Avoid recursive CTE coverage except for a brief boundary note that it is outside this lesson.
- Do not turn the lesson into a performance-tuning discussion.
- Do not treat CTEs as permanent objects, replacements for views, or shortcuts around weak join or grouping logic.
- Do not frame the lesson as "advanced SQL for its own sake."

## Suggested teaching moves

- Start with a working query that is dense enough to be hard to explain in one pass.
- Identify the natural intermediate result and name it clearly.
- Compare the original query to a CTE rewrite and ask whether readability actually improved.
- Include at least one prompt where students must describe the rows in the CTE before discussing the final report.
- Add a verification habit such as checking the intermediate result independently or comparing the rewrite to the original business question.

## Christian integration guidance

- Keep integration brief and business-facing.
- Connect readable query structure to truthful reporting and responsible decision support.
- Note that unclear query logic can hide distortions that affect people, privacy, fairness, or operational accountability.

## Acceptance criteria

- the lesson explains what problem a CTE solves in readable query design
- at least one example or practice item asks students to explain an intermediate result before the final result
- the lesson keeps the focus on clarity, verification, and business-question alignment
- the lesson stays within one-statement, nonrecursive beginner coverage
- the lesson also meets the shared v4 lesson acceptance criteria

## Invocation note

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file, then write only Lesson `2.6` using the canonical title, slug, and output paths above.
