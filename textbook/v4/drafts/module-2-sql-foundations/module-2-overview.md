# Module 2 Overview: SQL Foundations

## Devotion

> *"Therefore each of you must put off falsehood and speak truthfully to your neighbor."*
> — Ephesians 4:25

A query is a question put to data. The organization asks: how many sessions went unpaid this month? which products are understocked? what does each employee earn? SQL is the language of that asking. And like any form of communication, it can answer honestly or it can mislead — not through intent, but through carelessness.

A query that filters out records it should include, aggregates data at the wrong level, or joins tables along the wrong path will return results that look authoritative while quietly distorting reality. A manager who trusts that result will make a decision based on something that is not true. Staff, customers, or students may be affected without knowing why.

This module treats SQL not only as syntax to learn but as a form of speaking truthfully to the organization and the people it serves. The skill it most wants to develop in you is not the ability to write queries fast. It is the habit of asking: does this result actually answer the question I was asked?

That is a form of faithful, careful work — and it is what this module is about.

## What This Module Is About

Module 2 teaches you to read, write, evaluate, and improve SQL queries against a running SQL Server database. The goal is not to generate queries quickly. The goal is to determine whether a query actually answers the business question it was supposed to answer.

This distinction matters more than it first appears. A query can execute without errors and still return the wrong answer. It can aggregate data at the wrong level, join tables in a way that duplicates rows, or filter records that should be included. If you cannot read and evaluate a query carefully, you cannot catch those failures.

## Why This Module Matters

In an environment where AI tools can write SQL on request, the scarce skill is not query generation. It is query judgment. Can you explain what a query does in business terms? Can you identify what it would miss, distort, or double-count? Can you verify that the result actually answers the question?

This module builds that judgment through six lessons that progressively expand the kinds of queries you can read and evaluate.

Poor SQL judgment also has human consequences. A miscounted staffing report, a miscalculated payroll total, a misdirected service query — these affect real decisions and the people those decisions touch.

## The Lessons At A Glance

| Lesson | Focus | What You Will Do |
|--------|-------|-----------------|
| 2.1: The SQL Server Environment | Navigate the tool | Verify database context, run scripts, read results and messages |
| 2.2: Set Operations (Optional) | Conceptual foundation | Review relations, tuples, selection, projection, and union as reading support |
| 2.3: Single-Table Queries | One-table SELECT | Write and evaluate queries that retrieve, filter, and sort from one table |
| 2.4: Aggregates and Grouping | Summarizing data | Use GROUP BY to summarize data; explain what one grouped row represents |
| 2.5: Joins | Connecting tables | Trace join paths; explain what a joined row represents; detect wrong or distorting joins |
| 2.6: Common Table Expressions | Multi-step clarity | Use CTEs to name intermediate results and make complex queries more readable |

Lesson 2.2 is optional. If you are already comfortable with relation, tuple, and set concepts, you can move directly to Lesson 2.3.

## How The Lessons Connect

Each lesson expands the scope of the queries you can handle:

- **2.1** gets you oriented in SQL Server before any SQL is written.
- **2.3** starts with the simplest meaningful query — one table, one business question.
- **2.4** adds the challenge of summarization, where grouping level determines meaning.
- **2.5** adds the challenge of connecting tables, where wrong paths produce wrong answers.
- **2.6** shows how to organize complex multi-step logic into named, checkable pieces.

The progression is deliberate. Each lesson builds a layer that the next lesson depends on.

## Where This Module Fits The Workflow

This module covers **stage 7** of the course workflow:

7. **Query and manipulate data** — retrieve and summarize data in ways that accurately answer business questions

You will use the tutoring center database and the database introduced in earlier lessons as your practice environment. Later, in Module 6, you will build your own database and write queries against it. The reading and evaluation skills you develop here apply throughout the course and beyond it.

## What The Assessment Will Ask

The module assessment is a **Query Verification Lab**. You will be given a set of candidate queries written against a provided database and asked to:

- explain in plain language what each query does and what it returns
- identify whether the query correctly answers the stated business question
- describe what is wrong with queries that fail or distort the answer
- revise at least one query to correct a specific failure

You will not be asked only to write new queries from scratch. You will be asked to evaluate and explain queries that already exist.

## Key Terms To Watch For

- `SELECT` — the clause that specifies which columns to return
- `FROM` — the clause that specifies which table or join to read from
- `WHERE` — the clause that filters rows before any grouping
- `GROUP BY` — groups rows so aggregate functions can summarize them
- `HAVING` — filters groups after aggregation
- `JOIN` — combines rows from two tables based on a matching condition
- `INNER JOIN` — returns only rows that match in both tables
- `LEFT JOIN` — returns all rows from the left table, matched or not
- `CTE` — Common Table Expression; a named intermediate result defined before the main query
- `aggregate function` — a function like `COUNT`, `SUM`, `AVG`, `MIN`, or `MAX` that computes a single value from a group of rows

## A Note On Verification

Running a query without errors is not the same as running a correct query. Throughout this module, you will practice asking: does this result actually answer the question? That habit — verifying against the business question, not just against the syntax — is the central skill this module develops.
