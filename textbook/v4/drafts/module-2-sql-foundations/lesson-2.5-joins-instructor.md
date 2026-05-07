# Lesson 2.5: Joins

## Instructor-Facing Content

- **Module:** Module 2: SQL Foundations
- **Lesson purpose:** Teach students why joins are needed for multi-table business questions, how join paths determine result meaning, and how to verify that joined output answers the intended question instead of a plausible but wrong one.
- **Module context:** Lesson 2.3 established one-table query reading and writing. Lesson 2.4 taught that grouping changes result meaning. Lesson 2.5 adds the next major risk area: combining related tables can still return believable but incorrect output. Lesson 2.6 will then show students how to organize joined logic into clearer stages with CTEs. This lesson directly supports the Module 2 `Query Verification Lab` by emphasizing join judgment over query production alone.
- **Primary learning type(s):** Principles
- **Secondary learning type(s), if any:** Procedures
- **Estimated time:** 90 to 120 minutes

### Lesson outcomes

By the end of this lesson, students should be able to:

- explain why a join is needed for a given business question
- identify the correct join path between related tables
- write readable beginner joins using `INNER JOIN` and basic `LEFT JOIN`
- explain what one joined row represents
- diagnose a believable wrong join that uses the wrong relationship path
- detect row duplication caused by joining to a detail table
- verify that a joined query answers the intended business question

### Module alignment

- Supports Module 2 objectives to read and explain multi-table queries.
- Reinforces the module's human-must-know emphasis on detecting incorrect logic even when a query runs.
- Advances the primary graded assessment by asking students to reject plausible-but-wrong join logic and explain the business consequence.

### Course objective alignment

- Course Objective 5: create and use SQL statements for querying and data manipulation

### Lesson sequence role

- Moves students from one-table retrieval and grouped interpretation into relationship-based query reasoning across tables.
- Prepares students for CTE-based query organization in Lesson 2.6.

### Required prior knowledge

- Students can read `SELECT`, `FROM`, `WHERE`, and `ORDER BY` from Lesson 2.3.
- Students understand grouped row meaning and duplicate-risk thinking from Lesson 2.4.
- Students can benefit from optional Lesson 2.2 set-based review if they struggle to interpret what a result row represents.

### Lesson opening guidance

- Open with a business question that one table cannot answer, such as "List each order with the customer name."
- Ask students to identify the needed tables and the path between them before showing SQL.
- After the first correct join, immediately ask what one row represents.
- Introduce the idea early that a wrong join can still return polished and believable output.

### Teaching notes

- Keep the lesson centered on relationship path and row meaning, not on a survey of join syntax.
- Use `INNER JOIN` as the default pattern and introduce `LEFT JOIN` only when unmatched left-side rows matter to the question.
- Use one recurring sales case for most examples so students can focus on path logic instead of constantly relearning the scenario.
- Add one short service-ticket case to show a wrong join that still looks believable because both join columns point to real employees.
- Repeatedly require plain-language reading of one joined row.
- Surface row duplication explicitly by joining `sales.[Order]` to `sales.OrderLine` and asking what `COUNT(*)` now counts.
- Treat bad joins as business-integrity problems when they distort conclusions about people, inventory, service responsibility, or operations.
- Remind students that AI can draft syntactically correct joins quickly, so the assessed skill is verification and explanation, not mere production.

### Online activities

- Short LMS prompt where students identify whether one table or multiple tables are needed for a business question.
- Join-path activity where students choose the correct relationship route and reject wrong paths.
- Diagnosis exercise featuring a believable wrong join on service-ticket employee roles.
- Row-meaning annotation task where students explain what one joined row represents before interpreting counts or summaries.

### Homework / graded assignments

Assign one short worksheet or Markdown response that includes:

- one correct `INNER JOIN` query
- one plain-language explanation of joined row meaning
- one join-path explanation for a multi-table question
- one critique of a believable wrong join
- one row-duplication diagnosis and repair
- one short `LEFT JOIN` justification

### Deliverables

- one correct join query
- one plain-language row-meaning explanation
- one join-path explanation
- one critique of a wrong-but-believable join
- one repair of a row-duplication problem
- one verification note tied to the business question

### Assessment plan

- **Formative:** identify when a join is needed, choose a path, explain row meaning, and spot duplication risk
- **Graded:** short query-verification worksheet with both query construction and diagnosis tasks
- **Evidence of learning:** the student chooses the correct path, explains what the joined rows represent, and identifies why a plausible wrong join is wrong
- **How this avoids over-relying on AI-generable artifacts:** the work requires explanation, diagnosis, and verification of meaning instead of accepting runnable SQL as sufficient evidence
- **Stronger performance:** the student names the exact relationship error, explains the business consequence, and distinguishes row duplication from legitimate repeated business facts

### Suggested rubric focus

- Join path matches the business question
- Joined row meaning is stated accurately
- `INNER JOIN` versus `LEFT JOIN` choice matches the reporting need
- Diagnosis clearly explains why a believable wrong join is wrong
- Verification note shows awareness of duplication, missing rows, or wrong-row matching

### Common misconceptions

- "If the query runs, the join must be correct."
- "Any matching ID columns can be joined as long as the data type fits."
- "Joining to more tables only adds columns and does not change row meaning."
- "If duplicate rows appear after a join, SQL Server must be malfunctioning."
- "`LEFT JOIN` and `INNER JOIN` are interchangeable if the output looks close enough."

### Christian integration notes

- Keep integration subordinate to the technical lesson and embedded inside normal examples.
- Connect careless joins to truthful reporting and neighbor-serving information systems.
- Name the real harm: a bad join can misstate employee workload, customer activity, inventory demand, or service responsibility.
- Use business-facing language such as integrity, stewardship, accountability, and honest reporting only where it sharpens the query judgment point.

### Workflow connection

- This lesson remains in the retrieval and reporting stage of the course workflow.
- It teaches students to combine stored facts responsibly so reporting reflects real business relationships instead of accidental matches.
- That verification habit supports later lessons, the Module 2 `Query Verification Lab`, and any future project work that depends on multi-table reports.
