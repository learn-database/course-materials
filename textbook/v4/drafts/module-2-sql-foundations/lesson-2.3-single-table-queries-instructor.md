# Lesson 2.3: Single-Table Queries

## Instructor-Facing Content

### Module

- Module 2: SQL Foundations

### Lesson Purpose

- Introduce the first core SQL retrieval lesson and teach students to build, read, evaluate, and revise one-table queries using `SELECT`, `FROM`, `WHERE`, `ORDER BY`, aliases, and readable query structure.

### Module Context

- Lesson 2.1 gave students the environment setup and execution workflow needed to run SQL in SQL Server.
- Lesson 2.2 optionally supplied the conceptual background of projection and selection.
- Lesson 2.3 is where those ideas become practical query work.
- The lesson prepares students for Lesson 2.4 on grouped results, Lesson 2.5 on joins, and Lesson 2.6 on CTEs.
- It also supports the module's query verification lab by establishing that a query must be interpreted against the business question, not only checked for valid execution.

### Primary Learning Type(s)

- Procedures

### Secondary Learning Type(s), If Any

- Problem solving / judgment

### Estimated Time

- 90 to 120 minutes

### Lesson Outcomes

- Students write readable one-table queries that use `SELECT`, `FROM`, `WHERE`, and `ORDER BY`.
- Students choose columns and filters that match a business question.
- Students use aliases when they improve output clarity.
- Students distinguish a technically valid query from a business-correct query.
- Students explain what a result set does and does not prove.

### Module Alignment

- Supports the Module 2 objective to read and explain single-table and multi-table queries.
- Supports the module emphasis on business-question alignment and query verification.
- Establishes the judgment habit that later lessons need for grouping, joins, and CTE-based structure.

### Course Objective Alignment

- Course Objective 5: create and use SQL statements for querying and data manipulation.
- Also supports the course-wide priority of verification and explanation in an AI-available environment.

### Lesson Sequence Role

- Introduces and deepens the first practical SQL retrieval pattern in Module 2.

### Required Prior Knowledge

- Students can open the SQL environment, choose the correct database context, run code, and inspect results from Lesson 2.1.
- Students understand the idea that tables have rows and columns.
- Students may have completed the optional Lesson 2.2 review of projection and selection.

### Lesson Opening Guidance

- Begin with a business prompt before showing SQL.
- Ask students what rows belong in the answer, what columns belong in the answer, and what sort order would make the result useful.
- Keep the opening focused on the idea that a valid query can still be the wrong report.

### Teaching Notes

- Keep all examples inside one table. Do not preview joins, aggregates, grouping, or CTEs.
- Use one stable case table such as `dbo.Student` so students focus on clause purpose rather than schema navigation.
- Model readable formatting explicitly. Students should see that layout supports verification.
- Treat `SELECT *` as an inspection shortcut, not a reporting norm.
- Emphasize that `WHERE` changes returned rows, not stored data.
- Emphasize that `ORDER BY` changes presentation, not truth conditions.
- Include at least one query that runs correctly but misstates the business question because of a missing or careless filter.
- When students interpret a result, press them to state both what the result shows and what it does not prove.

### Online Activities

- Clause-labeling activity: students mark the role of `SELECT`, `FROM`, `WHERE`, and `ORDER BY` in a sample query.
- Query comparison activity: students choose which of two valid queries better answers a business prompt.
- Short written interpretation: students explain one result set's limits in plain language.

### Homework / Graded Assignments

A short query verification worksheet or LMS submission should include:

- three one-table query responses to business prompts
- two diagnoses or repairs of flawed queries
- one explanation of what a result set does and does not prove
- one short responsible-data-use note tied to fields that affect people or sensitive decisions

### Deliverables

- Three readable one-table queries
- Two diagnosis or repair responses
- One result-interpretation explanation
- One short note on responsible handling of sensitive or people-affecting fields

### Assessment Plan

Formative evidence should come from:

- students identifying clause purpose during guided practice
- students explaining why a weak query is weak even when it runs
- students interpreting the limits of a result set

Graded evidence should come from:

- students submitting one-table queries tied to business prompts
- students diagnosing misleading but valid queries
- students explaining result-set meaning and limits in plain language

AI-available safeguard:

- grading should not rely on query production alone
- stronger evidence comes from the diagnosis, explanation, and verification portions of the submission

### Suggested Rubric Focus

- Business-question alignment: selected columns, filters, and sort order fit the stated need.
- Query readability: clause structure is readable and easy to inspect.
- Verification quality: the student identifies why a valid query may still be wrong.
- Result interpretation: the student states both what the result supports and what it does not establish.
- Responsible reporting: the student recognizes when careless filtering or output choice would distort a report about people or operations.

### Common Misconceptions

- If the SQL runs, the answer must be correct.
- `SELECT *` is an acceptable default for business reporting.
- `WHERE` changes the stored table.
- `ORDER BY` is optional even when the business task depends on a meaningful order.
- An alias changes the stored column instead of only the displayed label.
- A result set proves more than the specific query conditions justify.

### Christian Integration Notes

- Keep the integration inside normal lesson elements, not in a separate devotional section.
- Use truthful reporting as the main integration thread.
- Name careless filtering as both a technical problem and an integrity problem when it misstates the business situation.
- When discussing fields such as `AdvisorEmail` or other people-related attributes, prompt students to consider appropriate use, privacy, and whether the output includes more data than the task requires.
- Keep the language business-facing: trustworthy reporting, accountable work, careful representation, and responsible data use.

### Workflow Connection

- This lesson sits at the workflow stage where implemented data is retrieved for business use.
- It connects the earlier environment lesson to the later query-analysis lessons by giving students their first repeatable retrieval pattern.
- It also establishes the habit of verifying result meaning before trusting a report, which aligns with the course-wide shift from artifact production alone to explanation, diagnosis, and judgment.
