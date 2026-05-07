# Lesson 2.3: Single-Table Queries

## Lesson Overview

This lesson is your first full SQL retrieval lesson. You will learn how to turn a business question into a readable one-table query using `SELECT`, `FROM`, `WHERE`, `ORDER BY`, and simple aliases.

The goal is not to produce SQL that merely runs. The goal is to produce a result set that answers the question honestly and clearly.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- write readable one-table queries that use `SELECT`, `FROM`, `WHERE`, and `ORDER BY`
- choose columns that match a stated business question instead of defaulting to `SELECT *`
- use filters that keep the right rows and exclude the wrong rows
- use aliases when they make a result easier to understand
- identify a query that runs but still answers the business question incorrectly
- explain what a result set shows and what it does not prove

## Key Terms

- Query: a SQL statement that requests a result from the database.
- Clause: a named part of a SQL statement that has a specific job.
- Result set: the rows returned by a query.
- Predicate: a true-or-false condition used to filter rows.
- Alias: a temporary label used to improve readability in the query or the output.

## Readings And Media

- Read this lesson completely before starting the practice.
- Run the worked examples in SQL Server if your course environment is ready.
- If needed, review Lesson 2.2 for the idea that projection is column choice and selection is row filtering.

## Core Content

### Case Table

Use this one table throughout the lesson:

`dbo.Student`

Assume it includes columns such as:

- `StudentID`
- `FirstName`
- `LastName`
- `Major`
- `Classification`
- `EnrollmentStatus`
- `GPA`
- `StartDate`
- `AdvisorEmail`

Staying with one table helps you learn clause purpose without the extra complexity of joins.

### Start With The Business Question

Suppose the advising office asks:

"Show active CIS students and list them from highest GPA to lowest GPA."

Before you write SQL, identify the parts of the question:

- source table: `dbo.Student`
- needed columns: student identity plus the fields needed for the report
- needed rows: students whose `EnrollmentStatus` is `Active` and whose `Major` is `CIS`
- needed order: highest `GPA` first

This planning step matters. Many weak queries start with code instead of with the question.

### Readable Query Structure

Use a structure that makes each clause easy to inspect:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       Major,
       GPA
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
  AND Major = 'CIS'
ORDER BY GPA DESC,
         LastName,
         FirstName;
```

This structure helps in three ways:

- each clause has a clear visual role
- multiple filter conditions are easier to read
- later review is easier when you need to verify or repair the query

Readable structure is not cosmetic. It makes mistakes easier to catch.

### `SELECT`: Choose The Needed Columns

`SELECT` controls which columns appear in the result set.

```sql
SELECT StudentID,
       FirstName,
       LastName,
       GPA
FROM dbo.Student;
```

Plain-language reading:

- return the student ID, first name, last name, and GPA
- from the student table

At this point, the query returns all rows because no filter has been added yet.

Avoid treating `SELECT *` as your default reporting habit:

```sql
SELECT *
FROM dbo.Student;
```

That query may be useful for quick inspection while learning a table, but it is usually weak for business reporting because:

- it returns columns the question did not ask for
- it makes the result harder to review
- it can expose information that is unnecessary for the task

### `FROM`: Identify The Source Table

`FROM` identifies where the data comes from.

```sql
SELECT StudentID,
       FirstName,
       LastName,
       Major
FROM dbo.Student;
```

In this lesson, the source stays simple: one table. Even so, this clause still matters because every later choice depends on starting from the correct source.

### `WHERE`: Keep Only The Needed Rows

`WHERE` filters the rows in the result set. It does not change the stored table.

Start with an unfiltered query:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       EnrollmentStatus
FROM dbo.Student;
```

Now add a filter:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       EnrollmentStatus
FROM dbo.Student
WHERE EnrollmentStatus = 'Active';
```

What changed:

- the table did not change
- the query result changed
- only rows marked `Active` now appear

Now match the original business question more closely:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       Major,
       GPA
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
  AND Major = 'CIS';
```

This is where truthfulness starts to matter. If the business question is about active CIS students, then a query that leaves out the active-only condition does not just have a small technical flaw. It creates reporting risk because the result can be read as if it represents currently active students when it does not.

### `ORDER BY`: Present The Answer In A Useful Order

`ORDER BY` changes presentation, not row membership.

```sql
SELECT StudentID,
       FirstName,
       LastName,
       Major,
       GPA
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
  AND Major = 'CIS'
ORDER BY GPA DESC,
         LastName,
         FirstName;
```

Why this ordering helps:

- `GPA DESC` puts the strongest GPAs first
- `LastName` and `FirstName` make tie handling consistent and readable

Without `ORDER BY`, SQL Server does not promise a meaningful display order.

### Aliases: Improve Clarity Without Changing Stored Data

An alias gives a temporary label to a column in the result.

```sql
SELECT StudentID AS StudentNumber,
       FirstName,
       LastName,
       AdvisorEmail AS AdvisorContact
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
ORDER BY LastName,
         FirstName;
```

Use aliases when they improve meaning for the reader. Do not use them to disguise the meaning of a field.

Good use:

- `StudentID AS StudentNumber`
- `AdvisorEmail AS AdvisorContact`

Bad use:

- an alias that implies something different from what the field actually contains

### A Valid Query Can Still Be Misleading

Business question:

"Show active CIS students who should appear on the advisor outreach list."

This query is technically valid:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       GPA
FROM dbo.Student
WHERE Major = 'CIS'
ORDER BY GPA DESC;
```

Why it is still wrong for the question:

- it does not filter for `EnrollmentStatus = 'Active'`
- it leaves out `AdvisorEmail`, which the outreach task likely needs
- it can be read as if all returned students are active when the query never checked that condition

This is the kind of mistake Module 2 wants you to catch. Query correctness is not just syntax correctness.

A stronger version is:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       GPA,
       AdvisorEmail AS AdvisorContact
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
  AND Major = 'CIS'
ORDER BY GPA DESC,
         LastName,
         FirstName;
```

### Read The Result Set Carefully

Suppose the stronger query returns 12 rows.

What the result set does support:

- these 12 rows met the filter conditions in the query
- each listed student is both `Active` and in the `CIS` major, assuming the stored data is accurate
- the rows are ordered from highest GPA to lowest GPA

What the result set does not prove by itself:

- that these are the only students the college should contact for every advising purpose
- that the data in `EnrollmentStatus`, `Major`, or `AdvisorEmail` is complete and error-free
- that GPA alone is enough to decide advisor outreach priority

This distinction matters in business reporting. A query result is evidence about a defined question, not proof of every related claim.

### Clause-By-Clause Reading Example

Read this query in plain language:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       GPA
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
  AND GPA >= 3.50
ORDER BY GPA DESC,
         LastName,
         FirstName;
```

Plain-language explanation:

- `FROM dbo.Student`: start from the student table
- `WHERE EnrollmentStatus = 'Active'`: keep only active students
- `AND GPA >= 3.50`: keep only students whose GPA is 3.50 or higher
- `SELECT ...`: display student ID, name, and GPA
- `ORDER BY ...`: show the highest GPA first, then sort ties by name

If you can read a query this way, you are better prepared to verify whether it answers the right question.

## Examples And Case

### Example 1: Contact List For Active Students

```sql
SELECT StudentID,
       FirstName,
       LastName,
       AdvisorEmail AS AdvisorContact
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
ORDER BY LastName,
         FirstName;
```

This result is useful for a general active-student contact list.

### Example 2: High-GPA CIS Students

```sql
SELECT StudentID,
       FirstName,
       LastName,
       Major,
       GPA
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
  AND Major = 'CIS'
  AND GPA >= 3.50
ORDER BY GPA DESC,
         LastName,
         FirstName;
```

This result supports a more specific business question: active CIS students at or above a stated GPA threshold.

### Example 3: Recently Started Active Students

```sql
SELECT StudentID,
       FirstName,
       LastName,
       StartDate
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
ORDER BY StartDate DESC,
         LastName,
         FirstName;
```

This result can help identify newer active students for a welcome or advising follow-up.

## Guided Practice

### Guided Practice 1: Choose The Right Columns

Business question:

"Create an active student contact list for advisors."

Write a query that returns only the columns needed for that task.

Check your work:

- did you avoid `SELECT *`
- did you include a field that actually supports contact or identification
- did you leave out fields that would only add noise

### Guided Practice 2: Add The Missing Filter

Start with this query:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       Major,
       GPA
FROM dbo.Student;
```

Business question:

"Show only active CIS students."

Add the `WHERE` clause, then explain in one or two sentences which rows disappear from the result and why.

### Guided Practice 3: Repair A Misleading Query

Business question:

"Show active CIS students and their advisor contact information."

Weak query:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       AdvisorEmail
FROM dbo.Student
WHERE Major = 'CIS';
```

Tasks:

- revise the query so it answers the question
- explain why the original query is misleading even though it runs
- state one business risk if a reader assumes the original result shows only active students

### Guided Practice 4: What Does The Result Prove

Suppose this query returns 8 rows:

```sql
SELECT StudentID,
       FirstName,
       LastName,
       GPA
FROM dbo.Student
WHERE EnrollmentStatus = 'Active'
  AND GPA < 2.00
ORDER BY GPA,
         LastName,
         FirstName;
```

Answer these questions:

1. What does this result set show?
2. What does it not prove?
3. What follow-up question would you ask before using this result for a high-stakes decision?

### Guided Practice 5: Use An Alias Carefully

Write a query for active students that uses one alias that improves clarity. Then explain why your alias is clearer than the stored column name.

## What To Do

1. Read each business question before reading the SQL.
2. For each worked example, identify the job of `SELECT`, `FROM`, `WHERE`, and `ORDER BY`.
3. Run the examples if your SQL environment is available.
4. Complete the guided practice tasks.
5. For every answer, check whether the query runs.
6. For every answer, check whether the result actually answers the question.

## Assignments

Complete a short Lesson 2.3 query verification worksheet or LMS submission that includes:

- three one-table queries written from business prompts
- two query diagnoses where you explain why a technically valid query is still wrong
- one result-interpretation response that explains what a query result does and does not prove
- one short note on which output fields in this lesson require extra care because they affect people, privacy, fairness, or sensitive decisions

## Deliverables

Submit:

- your three completed queries
- your two query repairs or diagnoses
- your result-interpretation response
- your short responsible-data-use note

## Project Checkpoint Or Module Connection

Module 2 is preparing you for a query verification lab. That means you should expect to evaluate candidate queries, reject misleading ones, and explain why a result set is or is not trustworthy.

As a project checkpoint, ask yourself:

- which fields in your case database would require extra care because they affect people directly
- how could a careless filter or careless column choice distort the truth of a business report

## Wrap-Up

Single-table queries are simple enough to learn clause by clause, but they already require judgment. A query can run successfully and still give a misleading answer. In this course, that difference matters.

The next lessons will build from this foundation. Before moving on, make sure you can do three things reliably: choose the right columns, filter the right rows, and explain what your result does and does not mean.
