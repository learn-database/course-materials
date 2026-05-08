# Lesson 2.4 Writing Instructions

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file for this lesson.

## Lesson Identity

- Lesson number: `2.4`
- Canonical title: `Aggregates and Grouping`
- Canonical slug: `aggregates-and-grouping`
- Module: `Module 2: SQL Foundations`

## Canonical Output Paths

- Instruction file: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/lesson.md`
- Instructor draft: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/instructor.md`

## Required Source Package

Read these files before drafting:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/02-module-2-sql-foundations.md`

## Lesson Purpose

Draft the lesson on summarized query results. Teach aggregate functions, grouping logic, and interpretation of summarized results in business reporting. The lesson should help students understand not only how summarized results are produced, but how grouping choices change what a result actually means.

## Module Context To Preserve

- This lesson follows Lesson `2.3`, where students learned one-table `SELECT`, `FROM`, `WHERE`, and `ORDER BY` work.
- This lesson prepares students for Lesson `2.5`, where row meaning becomes more complex because joins can duplicate, remove, or reshape rows before grouping.
- This lesson supports the Module 2 `Query Verification Lab` by helping students explain whether a summarized query actually answers the business question.
- This lesson sits in the course workflow stage `query and manipulate data`.

## Primary Strategy Requirements

From `textbook/v4/02-instructional-strategies-for-lessons.md`:

- Primary learning type: `Principles`
- Secondary learning type: `Procedures`
- Strategy pattern:
  - rule explanation for grouped versus ungrouped work
  - contrasting examples
  - output interpretation
  - diagnosis of grouping mistakes

## Scope Boundaries

- Keep the lesson focused on one-table aggregate and grouped reporting before joins are introduced.
- Do not drift into advanced analytic SQL, optimization, window functions, or join-heavy reporting.
- Use SQL Server and T-SQL defaults.
- Keep examples small enough that reporting level stays easy to inspect.
- Treat grouped-query interpretation as part of the lesson, not as an optional add-on.

## Required Emphasis

- Make row meaning and group meaning explicit.
- Include examples where grouping choices distort business interpretation.
- Connect summary accuracy to honest reporting.
- Include at least one example or practice item that asks students to diagnose a misleading grouping choice.
- Include at least one touchpoint that names why distorted summaries create a business-integrity problem.
- Keep Christian integration embedded, business-facing, and subordinate to the technical goal.

## Required Coverage

The student-facing draft should clearly teach:

- the difference between detail questions and summary questions
- what common aggregate functions do in business-facing terms
- how `GROUP BY` determines what one output row represents
- how to test grouped-query meaning by reading one row in plain language
- how a valid SQL query can still answer the wrong business question when grouped at the wrong level
- when a condition belongs in `WHERE` and when it belongs in `HAVING`
- how grouped reporting connects to the module's focus on explanation, diagnosis, and verification

## Required Practice And Assessment Shape

- Include guided practice with support.
- Include independent work with reduced support.
- Include at least one critique-and-repair or diagnosis task, not only query writing.
- Keep the lesson aligned to the v4 AI-available model: students may use AI to draft SQL, but they must verify reporting level, explain row meaning, and detect misleading summaries themselves.

## Suggested Case Shape

Use one small recurring reporting case such as `sales.[Order]` so students can focus on summary logic without join complexity. Suitable columns include:

- `OrderID`
- `CustomerID`
- `SalesRepID`
- `OrderDate`
- `OrderStatus`
- `OrderTotal`

## Deliverables

Create:

- `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/lesson.md`
- `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/instructor.md`

Split the final lesson into student-facing and instructor-facing draft files while keeping the section requirements from `textbook/v4/03-lesson-prompt.md`.

## Acceptance Check

Before finishing, confirm that the lesson:

- explains aggregate and grouping behavior in business-facing terms
- makes row meaning and group meaning explicit more than once
- includes a misleading grouping example or practice item
- names summary distortion as a truthfulness or business-integrity problem
- connects back to Lesson `2.3`, forward to Lesson `2.5`, and to the Module 2 `Query Verification Lab`
- works as primary instructional material for independent online study
