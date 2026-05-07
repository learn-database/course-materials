# Lesson 2.4: Aggregates and Grouping

## Instructor-Facing Content

### Module

- Module 2: SQL Foundations

### Lesson purpose

- Teach students how aggregate functions and `GROUP BY` change a result from detail rows into summary rows.
- Make reporting level explicit so students can explain what one grouped row represents and detect when a valid SQL query still misstates the business question.
- Connect summarized-query accuracy to honest business reporting and the module's emphasis on verification rather than query production alone.

### Module context

- Lesson 2.1 established the SQL Server execution environment.
- Lesson 2.2 optionally refreshed set-based thinking that supports summarization.
- Lesson 2.3 taught one-table clause structure with `SELECT`, `FROM`, `WHERE`, and `ORDER BY`.
- Lesson 2.4 builds directly on that foundation by shifting from detail retrieval to summary interpretation.
- Lesson 2.5 will extend this work into joins, where row meaning becomes more complex before grouping is applied.
- This lesson supports the Module 2 `Query Verification Lab` by training students to verify whether a grouped query actually answers the stated business question.

### Primary learning type(s)

- Principles

### Secondary learning type(s), if any

- Procedures

### Estimated time

- 90 to 120 minutes

### Lesson outcomes

- Distinguish detail-level questions from summary-level questions.
- Choose aggregate functions that match the reporting question.
- Explain how grouping changes the meaning of one output row.
- Use `GROUP BY` to create the intended reporting level.
- Decide whether a condition belongs in `WHERE` or `HAVING`.
- Diagnose and repair a misleading grouped query in business-facing terms.

### Module alignment

- Supports Module 2 objectives to use aggregates and grouping appropriately.
- Reinforces the module's human-must-know emphasis on interpreting output against a business prompt.
- Advances the primary graded assessment by requiring explanation, diagnosis, and revision of plausible but flawed SQL.

### Course objective alignment

- Course objective 5: create and use SQL statements for querying and data manipulation.
- Supports the workflow stage `query and manipulate data`.

### Lesson sequence role

- Deepens Module 2 query work by moving from clause-level retrieval into summarized reporting and report-meaning judgment.

### Required prior knowledge

- Students can open SQL Server tools and execute starter code from Lesson 2.1.
- Students can read one-table `SELECT`, `FROM`, `WHERE`, and `ORDER BY` structure from Lesson 2.3.
- Students may benefit from recalling Lesson 2.2 set-based thinking when they struggle to interpret grouped rows.

### Lesson opening guidance

- Open with a contrast between one detail query and one aggregate query from the same table.
- Ask students two questions before discussing syntax:
  - What does one row mean in the detail result?
  - What does one row mean in the summary result?
- State early that grouping is a meaning problem before it is a clause problem.

### Teaching notes

- Keep examples on one table so grouping logic stays visible.
- Use a recurring `sales.[Order]` case with `OrderID`, `CustomerID`, `SalesRepID`, `OrderDate`, `OrderStatus`, and `OrderTotal`.
- Repeatedly require students to read one row aloud in plain language.
- Include at least one valid SQL query whose grouping level answers the wrong question.
- Treat misleading summaries as business-integrity problems, not only technical defects.
- Avoid joins, window functions, optimization talk, and advanced reporting features.
- If students ask why this matters morally, keep the answer business-facing: distorted summaries can mislead managers about customers, employees, or operations.
- Remind students that AI can draft working grouped SQL, so the assessed skill is explanation, diagnosis, and verification of report meaning.

### Online activities

- Short LMS checkpoint where students classify questions as detail-level or summary-level.
- Query comparison activity where students choose between two valid grouped queries and justify which one matches the business report.
- Brief discussion or annotation task: explain what one row means in a grouped result and why that matters for honest reporting.

### Homework / graded assignments

- A short worksheet with:
  - one aggregate-only query
  - one grouped query
  - one grouped query using both `WHERE` and `HAVING`
  - one misleading grouped query to diagnose and repair
  - one short explanation of grouped row meaning

### Deliverables

- one SQL worksheet or text submission containing the required queries
- one short written explanation of reporting level and filter placement

### Assessment plan

- Formative:
  - classify detail versus summary questions
  - state what one grouped row represents
  - place candidate filters in `WHERE` or `HAVING`
- Graded:
  - a lesson worksheet that includes query writing, diagnosis, revision, and explanation
- Evidence of learning:
  - the student selects an appropriate aggregate
  - the student groups at the correct reporting level
  - the student explains why a misleading grouped query is misleading
  - the student justifies filter placement in business-facing terms
- AI-resilient design:
  - the assignment does not rely on query production alone
  - students must explain row meaning, reject a plausible wrong query, and repair it
- Stronger performance:
  - the student identifies not only the broken clause but also the business consequence of the distorted summary

### Suggested rubric focus

- Aggregate choice matches the reporting question.
- Grouping columns match the intended reporting level.
- `WHERE` and `HAVING` are used at the correct stage of query logic.
- Explanation makes row meaning and group meaning explicit.
- Diagnosis identifies why a plausible grouped query would mislead a business audience.

### Common misconceptions

- Thinking grouped queries still return original table rows.
- Adding extra grouped columns without realizing they change report meaning.
- Treating any valid SQL report as trustworthy.
- Using `HAVING` for row-level filters that belong in `WHERE`.
- Explaining only clause syntax instead of the business interpretation of the output.

### Christian integration notes

- Keep integration brief and inside normal instruction.
- Name summary distortion as a truthfulness problem when it could mislead staffing, evaluation, compensation, or operational decisions.
- Use course language such as stewardship, integrity, and honest reporting only where it supports the technical point.
- Avoid stand-alone reflection sections. Embed the point inside the misleading-grouping example, common mistakes, or assessment rationale.

### Workflow connection

- This lesson teaches how stored rows become summarized reports during the querying stage of the database workflow.
- It prepares students for later query work by establishing that result meaning must be verified before a report can be trusted.
