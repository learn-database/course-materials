# Lesson 2.6: Common Table Expressions

## Instructor-Facing Content

- **Module:** Module 2: SQL Foundations
- **Lesson purpose:** Teach students to use nonrecursive CTEs to organize intermediate result sets so multi-step queries are easier to read, explain, and verify.
- **Module context:** This lesson follows `Aggregates and Grouping` and `Joins`. Students should already know how grouped summaries and joined rows work. Lesson 2.6 does not add a new business-question type so much as a clearer structure for answering the same kinds of questions. It prepares students for the module's query-verification work by making intermediate logic easier to inspect and explain.
- **Primary learning type(s):** Procedures
- **Secondary learning type(s), if any:** Problem solving / judgment
- **Estimated time:** 75 to 90 minutes

### Lesson outcomes

By the end of this lesson, students should be able to:

- explain what problem a nonrecursive CTE solves in readable query design
- rewrite a longer working query using a nonrecursive CTE
- explain what rows the intermediate result contains before interpreting the final result
- compare an original query and a CTE rewrite and judge whether readability improved
- verify that a CTE rewrite still answers the original business question

### Module alignment

- Supports Module 2 objectives on using filtering, grouping, joins, and CTEs appropriately.
- Reinforces the module emphasis on reading and evaluating query logic rather than trusting execution alone.
- Extends Lesson 2.4 and Lesson 2.5 by reorganizing grouped and joined logic into named steps that are easier to verify.

### Course objective alignment

- Course Objective 5: create and use SQL statements for querying and data manipulation

### Lesson sequence role

- Deepens and applies prior Module 2 query knowledge by shifting from clause construction alone to readable multi-step query organization.

### Required prior knowledge

- `SELECT`, `FROM`, `WHERE`, and `ORDER BY`
- grouped queries with `COUNT`, `SUM`, `MIN`, `GROUP BY`, and `HAVING`
- relationship-based join reasoning from Lesson 2.5
- basic set and result-set thinking from Lesson 2.2, if completed

### Lesson opening guidance

- Begin with a working query that uses a derived table or otherwise compresses multiple logical steps into one dense statement.
- Ask students to identify the first meaningful result before you mention CTE syntax.
- Frame the lesson as query revision for clarity and verification, not as advanced SQL.
- Make students describe what one row in the intermediate result represents before discussing the outer query.

### Teaching notes

- Keep the lesson focused on nonrecursive CTEs used with `SELECT`.
- Use business-facing reports with a clear first step such as customer sales summaries or unpaid invoice summaries.
- Favor examples where the intermediate result has a stable business meaning, not arbitrary formatting.
- Repeatedly ask whether the CTE improved readability or merely added lines.
- Keep verification explicit: students should check the intermediate result, the outer filter, and the original business question.
- Avoid drifting into recursive CTEs, views, temporary tables, or performance claims unless they are only briefly named as out-of-scope boundaries.

### Online activities

- Query annotation task where students label the CTE definition and the consuming statement.
- Short comparison prompt asking which rewrite is easier to verify and why.
- Self-check on one-statement scope and on whether a given CTE name helps the reader.

### Homework / graded assignments

Assign one short submission that includes:

- the original working query
- a nonrecursive CTE rewrite
- an explanation of the intermediate result
- a verification note tied to the business question
- a readability comparison using specific reasons

### Deliverables

- one correct nonrecursive CTE rewrite
- one explanation of the intermediate result before the final result
- one verification note showing business-question alignment
- one readability comparison

### Assessment plan

- **Formative:** guided practice on intermediate-result explanation, naming quality, scope, and readability comparison
- **Graded:** one short query-revision submission with explanation and verification notes
- **Evidence of learning:** the student uses a CTE appropriately, explains the intermediate result accurately, and evaluates whether the rewrite improves the query
- **How this avoids over-relying on AI-generable artifacts:** the lesson asks students to explain row meaning, justify readability claims, and verify business-question alignment rather than submitting SQL alone
- **Stronger performance:** the student chooses a meaningful intermediate step, names it clearly, preserves the original logic, and gives a precise explanation of why the rewrite is easier to inspect

### Suggested rubric focus

- Accuracy of the CTE rewrite
- Accuracy of the intermediate-result explanation
- Quality of the verification note
- Specificity of the readability comparison
- Ability to connect structure to the business question

### Common misconceptions

- "A CTE is a permanent database object."
- "Using a CTE automatically makes a query better."
- "A CTE can be reused by later independent statements."
- "A CTE fixes weak join logic or incorrect grouping."
- "Readability is just appearance and has nothing to do with trustworthy reporting."

### Christian integration notes

- Keep the integration short and tied to reporting integrity.
- Use examples where unclear logic could misstate who qualifies for follow-up, review, or intervention.
- Emphasize that readable query structure supports honest representation of business reality and responsible handling of people-affecting information.

### Workflow connection

- This lesson remains in the retrieval and reporting part of the larger database workflow.
- It strengthens the quality-control side of querying by helping students separate intermediate logic from final presentation.
- That connection matters later when students must explain, verify, and revise SQL rather than merely submit a result.
