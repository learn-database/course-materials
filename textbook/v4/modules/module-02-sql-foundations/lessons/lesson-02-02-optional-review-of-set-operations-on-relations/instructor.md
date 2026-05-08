# Lesson 2.2: Optional Review of Set Operations on Relations

## Instructor-Facing Content

### Module

Module 2: SQL Foundations

### Lesson Purpose

Provide a brief optional review of relation and set ideas that make later SQL retrieval behavior easier to read and explain. The lesson should support SQL thinking without expanding into a formal relational theory chapter.

### Module Context

This lesson sits between Lesson `2.1`, which establishes the SQL Server environment, and Lesson `2.3`, which begins actual single-table query writing. Its role is to give students a lightweight conceptual bridge so `SELECT`, `WHERE`, and later result interpretation feel more intentional.

### Primary Learning Type(s)

Concepts

### Secondary Learning Type(s), If Any

Principles

### Estimated Time

20 to 30 minutes

### Lesson Outcomes

By the end of the lesson, students should be able to:

- explain why SQL retrieval is often discussed in set-style terms
- identify a relation, tuple, and attribute in a small example
- read a compact relational schema such as `Student(StudentID PK, LastName, Program)`
- distinguish `relational schema` from `SQL Server schema`
- explain selection, projection, and union in plain language
- connect those ideas to later SQL use of `SELECT`, `WHERE`, and `UNION`

### Module Alignment

- Supports the Module 2 purpose of building practical SQL fluency through reading, explanation, and verification rather than syntax production alone.
- Prepares students for Lesson `2.3` by giving them a mental model for result-set behavior.
- Reinforces the module emphasis on judging whether a query answers the business question honestly.

### Course Objective Alignment

- Objective `1`: know basic database terminology
- Objective `5`: create and use SQL statements for querying and data manipulation

### Lesson Sequence Role

- Follows environment setup in Lesson `2.1`
- Optionally refreshes row, column, and set language before query construction
- Prepares for Lesson `2.3` single-table queries and later lessons on grouping and joins

### Required Prior Knowledge

- Basic understanding that tables contain rows and columns
- Lesson `2.1` exposure to SQL Server schema as a namespace such as `dbo`
- No prior background in formal relational algebra is required

### Lesson Opening Guidance

- Tell students explicitly that this lesson is optional review, not a theory checkpoint.
- State the payoff early: later SQL clauses make more sense if students can ask "Which rows stay?" and "Which columns stay?"
- Remind students that Module 2 grades interpretation and query judgment, not just whether SQL executes.

### Teaching Notes

- Keep the lesson concrete and brief.
- Use one small running example instead of multiple abstract tables.
- Clarify the double meaning of `schema` early and visibly.
- Avoid notation-heavy treatment or detours into advanced relational theory.
- Keep bringing the ideas back to later SQL clause reading and result interpretation.

### Online Activities

- Optional low-stakes LMS concept check
- Short discussion or reflection prompt on why a technically valid query can still misstate the business situation

### Homework / Graded Assignments

- Prefer optional or very low-stakes work only
- If graded, use a brief explanation task rather than a larger artifact

### Deliverables

Possible deliverables for this optional lesson:

- guided practice responses
- short concept-check answers
- a brief explanation of how selection and projection support later SQL reading

### Assessment Plan

- Check whether students can explain the vocabulary in plain language.
- Check whether students can distinguish row filtering from column choice.
- Check whether students can map selection to `WHERE`, projection to the `SELECT` list, and union to compatible result-set combination.
- Use mistakes here as early indicators of who may struggle with query interpretation in Lesson `2.3`.

### Suggested Rubric Focus

- accurate use of relation, tuple, and attribute
- correct reading of simple relational schema notation
- clear distinction between `relational schema` and `SQL Server schema`
- correct explanation of selection, projection, and union
- direct connection to later SQL retrieval behavior

### Common Misconceptions

- Students may think `relational schema` means `dbo` or another SQL Server namespace.
- Students may confuse selection with choosing columns.
- Students may confuse projection with filtering rows.
- Students may assume this lesson requires formal relational algebra notation.
- Students may think a query that runs must also be answering the business question correctly.

### Christian Integration Notes

- Keep integration subordinate to the technical goal.
- Connect incorrect row filtering or careless column choice to truthful business reporting.
- A short reminder is enough: misleading output can affect people, decisions, and organizational trust even when the SQL is syntactically valid.

### Workflow Connection

This lesson supports the course workflow at the query-and-interpret stage. It helps students move from "I can run SQL" toward "I can explain what this result set means and whether it is trustworthy." That fits the v4 assessment shift toward verification, diagnosis, and business-question alignment.
