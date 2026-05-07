# Lesson 2.2: Optional Review of Set Operations on Relations

## Lesson Overview

This optional lesson gives you a short conceptual bridge before SQL query writing begins. You do not need a full theory chapter here. You only need a few set and relation ideas that make later SQL clauses easier to read, explain, and verify.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain why SQL retrieval is often described in set-style terms
- identify a relation, tuple, and attribute in a small example
- read a compact relational schema such as `Student(StudentID PK, LastName, Program)`
- explain the difference between `relational schema` and `SQL Server schema`
- explain selection, projection, and union in plain language
- connect those ideas to later SQL use of `SELECT`, `WHERE`, and `UNION`

## Key Terms

- `relation`: a table-like structure discussed as a set of rows
- `tuple`: one row in a relation
- `attribute`: one column in a relation
- `relational schema`: a compact description of a relation's structure
- `selection`: keeping only rows that meet a condition
- `projection`: keeping only the needed columns
- `union`: combining compatible result sets

## Readings and Media

- Read this lesson from start to finish.
- Keep Lesson `2.1` in mind, especially the meaning of `SQL Server schema` as a namespace such as `dbo`.
- Use this page as a reference when you begin Lesson `2.3`.

## Core Content

### Start With a Small Relation

Use this simple relation throughout the lesson:

```text
Student(StudentID PK, LastName, Program)
```

and this small sample of rows:

```text
Student
+-----------+----------+---------+
| StudentID | LastName | Program |
+-----------+----------+---------+
| 1001      | Alvarez  | CIS     |
| 1002      | Brown    | DBM     |
| 1003      | Chen     | CIS     |
+-----------+----------+---------+
```

In this example:

- `Student` is the relation
- one tuple is the row for `1002 | Brown | DBM`
- `Program` is an attribute

The vocabulary is new, but the structure is not. Relation language is just a more precise way to talk about rows and columns when you start reading SQL behavior.

### Relation, Tuple, and Attribute

For this course, keep the terms simple:

- relation = the whole table-like structure
- tuple = one row
- attribute = one column

You do not need symbolic notation or formal proofs. You need enough vocabulary to understand how SQL returns and reshapes result sets.

### Relational Schema Versus SQL Server Schema

The word `schema` has two meanings in Module 2, and you need to keep them separate.

```text
Student(StudentID PK, LastName, Program)
```

This is a `relational schema`. It describes the structure of a relation: its name, attributes, and key marking.

```text
dbo.Student
```

This uses a `SQL Server schema`. Here, `dbo` is the namespace that contains the table.

Keep the difference clear:

- relational schema = structure description
- SQL Server schema = namespace or container

### Selection: Which Rows Stay?

Selection means keeping only the rows that meet a condition. Think of it as row filtering.

If you keep only students whose `Program = 'CIS'`, the remaining rows are:

```text
+-----------+----------+---------+
| StudentID | LastName | Program |
+-----------+----------+---------+
| 1001      | Alvarez  | CIS     |
| 1003      | Chen     | CIS     |
+-----------+----------+---------+
```

That is the same idea you will use later with a `WHERE` clause. A `WHERE` clause tells SQL which rows remain in the result.

This matters for business accuracy. If a report is supposed to show only active customers, scholarship-eligible students, or unpaid invoices, the main question is not "Did the query run?" The main question is "Did the query keep the correct rows?"

### Projection: Which Columns Stay?

Projection means keeping only the columns you need. Think of it as column choice.

If you keep only `StudentID` and `LastName`, the result is:

```text
+-----------+----------+
| StudentID | LastName |
+-----------+----------+
| 1001      | Alvarez  |
| 1002      | Brown    |
| 1003      | Chen     |
+-----------+----------+
```

That is the same idea you will use later with the `SELECT` list. The `SELECT` list tells SQL which columns to return.

Selection and projection answer different questions:

- selection asks, "Which rows stay?"
- projection asks, "Which columns stay?"

If you mix them up, query explanations get confusing fast.

### Union: Can Two Results Be Combined?

Union means combining compatible result sets. At this level, `compatible` means the results line up in structure and meaning.

Example:

```text
CISStudentNames
+----------+
| LastName |
+----------+
| Alvarez  |
| Chen     |
+----------+

DBMStudentNames
+----------+
| LastName |
+----------+
| Brown    |
+----------+
```

These two result sets are compatible because both return one column of student last names. A union-style combination would produce one result set of names.

Later, SQL uses `UNION` for this kind of combination. For now, the key idea is simple: SQL can combine compatible results, not just filter one table.

### How This Review Supports SQL Reading

When you begin writing and reading queries, keep translating the SQL back into these questions:

- `FROM`: what relation or table is the source?
- `WHERE`: which rows stay?
- `SELECT`: which columns stay?
- `UNION`: are two compatible results being combined?

That translation helps you interpret output instead of treating SQL as memorized syntax.

## Examples and Case

Suppose an advising office asks for a list of `CIS` students. A correct result must:

- keep only the rows for `CIS` students
- return the columns the office actually needs

If the query includes `DBM` students, the problem is not just technical. The result misstates the business reality. That is why careful row filtering is part of truthful reporting, not just syntax practice.

## Guided Practice

Answer these prompts before moving on:

1. In the `Student` example, what is the relation name?
2. Name one tuple in plain language.
3. Which items in `Student(StudentID PK, LastName, Program)` are attributes?
4. If you select rows where `Program = 'DBM'`, which row remains?
5. If you project only `LastName`, which columns remain?
6. In one sentence, how is `relational schema` different from `SQL Server schema`?
7. Why would the wrong selection be a business-reporting problem even if the query still runs?

## What To Do

- Read the lesson carefully.
- Work through the running `Student` example.
- Answer the guided practice prompts.
- Keep the two anchor questions in mind: "Which rows stay?" and "Which columns stay?"
- Return to this lesson if `WHERE`, `SELECT`, or `UNION` feels abstract in later lessons.

## Assignments

- Optional self-check or instructor-provided concept check
- Optional short written explanation connecting selection, projection, and union to later SQL use

## Deliverables

If your instructor assigns work for this optional lesson, submit:

- guided practice answers
- any short concept-check responses requested in the LMS

## Project Checkpoint or Module Connection

Module 2 is about more than producing runnable SQL. It is about deciding whether a query tells the truth about the business question. Use this lesson as a check on your own thinking: before trusting query output, ask whether you kept the right rows, returned the right columns, and combined results only when they were truly compatible.

## Wrap-Up

This lesson is a short review, not a full theory unit. If you can identify rows, columns, relation structure, selection, projection, and simple union ideas, you have enough background to move into Lesson `2.3`. The real payoff is not vocabulary for its own sake. The payoff is reading SQL results more clearly and catching misleading answers sooner.
