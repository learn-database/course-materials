# Module 2: SQL Foundations

### Purpose

- Build practical SQL fluency for retrieving and organizing data.
- Shift assessment from writing queries alone to reading, evaluating, testing, and revising them.

### Objectives

- navigate the SQL Server environment and run provided code
- read and explain single-table and multi-table queries
- use filtering, sorting, aggregates, grouping, joins, and CTEs appropriately
- determine whether a query actually answers the business question

### Human Must Know

- what question a query is trying to answer
- how to read query structure
- how to detect incorrect logic even when a query runs
- how to interpret output against a business prompt

### AI May Assist With

- generating query drafts
- fixing syntax
- executing and revising queries
- producing sample data and test cases

### Christian Integration Focus

- connect query work to honest reporting and careful representation of business reality
- treat careless filtering, grouping, or joins as truthfulness problems when they distort decisions about people or operations

### Integration Touchpoints

- include one query-review example where a technically valid query still misstates the business situation
- include one prompt asking which fields or outputs require extra care because they affect people, privacy, fairness, or sensitive decisions

### Lessons

#### Lesson 2.1: The SQL Server Environment
- client and server roles
- workspace, query window, and database context
- running starter scripts and checking results

#### Lesson 2.2: Optional Review of Set Operations on Relations
- sets, rows, columns, and projection or selection ideas that support SQL thinking

#### Lesson 2.3: Single-Table Queries
- `SELECT`, `FROM`, `WHERE`, `ORDER BY`, aliases, and readable query structure

#### Lesson 2.4: Aggregates and Grouping
- aggregate functions, grouping logic, and interpretation of summarized results

#### Lesson 2.5: Joins
- join purpose, join paths, and row meaning across related tables

#### Lesson 2.6: Common Table Expressions
- using CTEs to organize intermediate result sets and improve readable query logic

### Assessment Strategy

This module should not treat a submitted query alone as strong evidence, because AI can generate and test working SQL. The module should instead ask students to compare alternatives, detect subtle errors, and explain why one query is correct.

### Primary Graded Assessment

#### Query Verification Lab

- Format: students receive multiple candidate queries and one business question
- Students choose the best query, reject the others, explain the failure mode in each wrong query, and interpret the result set

### Secondary Evidence

- timed quiz on query reading and result interpretation
- short annotation of one query with clause-by-clause explanation

### What To Grade

- business-question alignment
- recognition of incorrect filters, grouping, joins, or row duplication
- quality of result interpretation
- ability to explain query behavior in plain language
- ability to explain why a misleading result would be a business-integrity problem, not just a syntax problem

### Module Assessment Tasks

- identify which query correctly answers a business question
- diagnose why a wrong query still returns plausible but incorrect output
- interpret a result set and explain what it does and does not prove
- revise a flawed query and explain the correction

### Why This Assessment Holds Up Better

- it grades query judgment, not just query production
- it makes students verify meaning rather than trust execution
- it uses AI-generated SQL as the prompt rather than the answer
