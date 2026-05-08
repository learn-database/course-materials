# Lesson 6.3 Building Views

## Lesson overview

In Lesson 6.1, you built tables and constraints from the approved Database Design Diagram. In Lesson 6.2, you inserted, updated, and deleted data carefully enough that the database could be trusted. Now you are ready to package useful reporting logic into views.

This lesson is not about turning every `SELECT` into a database object. It is about recognizing when a business question comes up often enough to deserve a reusable reporting structure, testing the query before you package it, and verifying that the finished output serves the intended decision without exposing more information than necessary.

## Lesson outcomes

By the end of this lesson, you should be able to:

- explain what problem a view solves in SQL Server
- decide when a reporting question is appropriate for a view and when it should remain an ad hoc query
- write and test a `SELECT` statement before converting it into a view
- create a view in T-SQL from a tested query
- verify whether a view output answers the intended business question
- judge whether a view supports transparent decisions without exposing unnecessary details

## Key terms

- `view`: a named database object that stores a query definition for reuse
- `reusable reporting logic`: query logic worth packaging because the same question will be asked repeatedly
- `business question`: the real decision or reporting need the SQL should answer
- `verification`: checking whether output matches the intended rows, columns, and meaning
- `transparency`: making a report understandable enough to support honest decisions
- `oversharing`: exposing columns or details that are not needed for the reporting purpose

## Readings and media

- Read this lesson from beginning to end before writing your own view.
- Keep the approved DBDD and the sample data from Lessons 6.1 and 6.2 available while you work.
- Review `textbook/v4/modules-plan/06-module-6-sql-server-implementation.md` if you want to see how this lesson fits the module blueprint.
- No separate video is required for this lesson.

## Core content

### 1. What problem does a view solve?

A view solves a repeated reporting problem.

Suppose a staff member needs the same joined report every day or every week. Rewriting that query each time wastes effort and increases the chance that different people will produce slightly different versions of the report. A view packages that logic under one name so the database can answer the repeated question more consistently.

That means a view is useful when all of these are true:

- the question is asked repeatedly
- the query logic is worth reusing
- the output has a clear audience and purpose

A view is not appropriate just because a query exists. One-time troubleshooting, cleanup, and narrow technical checks usually do not need a named database object.

### 2. What a view does and does not do

What a view does:

- stores query logic under a reusable name
- makes repeated reporting easier to read and rerun
- supports consistency when the same report is needed often

What a view does not do:

- guarantee that the logic is correct
- replace understanding of joins, filters, or columns
- turn a weak query into a strong report
- justify exposing every available column

The important distinction is this: a view can save effort, but it cannot replace judgment.

### 3. When is a view appropriate?

Ask these questions before you build one:

1. Who needs this information?
2. What decision or recurring task does the output support?
3. Will the same question be asked again?
4. Which columns are necessary for that purpose?
5. Which columns would be unnecessary or inappropriate to expose?

If the answer points to repeated, business-facing reporting, a view is a strong candidate.

If the answer points to a one-time import error, one suspicious row, or temporary cleanup work, keep the query ad hoc.

### 4. Procedure: test first, package second, verify third

Use this repeatable procedure in Module 6:

1. state the business question in one sentence
2. identify the tables and joins needed from the approved design
3. write the base `SELECT`
4. run the query and inspect the rows and columns
5. revise the logic until it answers the intended question
6. convert the tested query into `CREATE VIEW`
7. query the view
8. verify that the output matches the business question
9. remove unnecessary details if the view exposes more than the audience needs

Do not reverse this order. If `CREATE VIEW` succeeds before the logic has been tested, you may end up with a working object that still answers the wrong question.

### 5. Worked case: upcoming tutoring sessions

Assume the approved design includes these tables:

- `Student(StudentID, FirstName, LastName, Email, Phone)`
- `Tutor(TutorID, FirstName, LastName)`
- `Subject(SubjectID, SubjectName)`
- `Session(SessionID, StudentID, TutorID, SubjectID, SessionDate, StartTime, Room, Status)`

Business question:

"Which upcoming tutoring sessions are scheduled, and who is involved in each one?"

This is a strong view candidate because the question is repeatable, staff-facing, and built from several related tables.

Start with the tested query:

```sql
SELECT s.SessionID,
       s.SessionDate,
       s.StartTime,
       s.Room,
       s.Status,
       st.FirstName + ' ' + st.LastName AS StudentName,
       t.FirstName + ' ' + t.LastName AS TutorName,
       sub.SubjectName
FROM dbo.[Session] AS s
INNER JOIN dbo.Student AS st
    ON s.StudentID = st.StudentID
INNER JOIN dbo.Tutor AS t
    ON s.TutorID = t.TutorID
INNER JOIN dbo.Subject AS sub
    ON s.SubjectID = sub.SubjectID
WHERE s.SessionDate >= CAST(GETDATE() AS date)
  AND s.Status = 'Scheduled';
```

Check the test output before building the view:

- Are the joins correct?
- Do the rows show only scheduled upcoming sessions?
- Do the columns actually help the tutoring coordinator?
- Is anything important missing?
- Is anything unnecessary exposed?

If the test output answers the question well, package it:

```sql
CREATE VIEW dbo.vScheduledSessionReport
AS
SELECT s.SessionID,
       s.SessionDate,
       s.StartTime,
       s.Room,
       s.Status,
       st.FirstName + ' ' + st.LastName AS StudentName,
       t.FirstName + ' ' + t.LastName AS TutorName,
       sub.SubjectName
FROM dbo.[Session] AS s
INNER JOIN dbo.Student AS st
    ON s.StudentID = st.StudentID
INNER JOIN dbo.Tutor AS t
    ON s.TutorID = t.TutorID
INNER JOIN dbo.Subject AS sub
    ON s.SubjectID = sub.SubjectID
WHERE s.SessionDate >= CAST(GETDATE() AS date)
  AND s.Status = 'Scheduled';
```

Then query the view:

```sql
SELECT SessionDate,
       StartTime,
       Room,
       StudentName,
       TutorName,
       SubjectName
FROM dbo.vScheduledSessionReport
ORDER BY SessionDate, StartTime;
```

That final query is not the end of the thinking. You still need to decide whether the output answers the original business question clearly.

### 6. Transparent reporting without oversharing

Suppose a classmate builds this version instead:

```sql
CREATE VIEW dbo.vScheduledSessionContactReport
AS
SELECT s.SessionDate,
       s.StartTime,
       s.Room,
       st.FirstName + ' ' + st.LastName AS StudentName,
       st.Email,
       st.Phone,
       t.FirstName + ' ' + t.LastName AS TutorName,
       sub.SubjectName
FROM dbo.[Session] AS s
INNER JOIN dbo.Student AS st
    ON s.StudentID = st.StudentID
INNER JOIN dbo.Tutor AS t
    ON s.TutorID = t.TutorID
INNER JOIN dbo.Subject AS sub
    ON s.SubjectID = sub.SubjectID
WHERE s.SessionDate >= CAST(GETDATE() AS date)
  AND s.Status = 'Scheduled';
```

This view might execute correctly, but that does not automatically make it a good reporting structure.

Ask the business question again:

"Which upcoming tutoring sessions are scheduled, and who is involved in each one?"

For that question, student email and phone may be unnecessary. Including them can turn a useful scheduling view into an oversharing view. Transparency does not mean showing every column. It means showing enough information for an honest, understandable decision without exposing details that do not serve the purpose.

In many business settings, careful reporting is part of stewardship and trust. People should be able to understand decisions, but they should not see personal details just because those details are available in the table.

### 7. Technically valid can still be wrong

A view can fail in more than one way.

Example 1: wrong question

If the view returns all sessions, including cancelled ones, it may not answer the coordinator's scheduling question.

Example 2: weak output

If the view returns only `SessionID`, `StudentID`, and `TutorID`, the output is too technical for a coordinator-facing report.

Example 3: oversharing

If the view includes personal columns that are not needed for the report, the output may reveal too much information even though the joins and syntax are correct.

The core rule is simple: successful execution proves that SQL Server accepted the object. It does not prove that the view supports the right business decision.

## Examples and case

### Strong view candidate

Business question:

"Show all scheduled tutoring sessions for the next seven days with date, time, room, student name, tutor name, and subject."

Why it is strong:

- repeatable need
- clear audience
- stable output
- business-facing purpose

### Weak candidate for a view

Business question:

"Find the one row from today's import where the tutor reference is missing."

Why it should remain ad hoc:

- one-time troubleshooting task
- narrow technical purpose
- unlikely to be reused as a stable report

### Verification example

If a coordinator says the report should help assign rooms, but the view output does not include `Room`, the view is incomplete even if it runs successfully.

## Guided practice

### Practice 1: view-worthy or ad hoc?

Decide whether each question should become a view. Write one sentence explaining why.

1. "List all scheduled tutoring sessions for front-desk staff each morning."
2. "Find the one subject row with a misspelled course code from today's cleanup."
3. "Show active tutors and the subjects they currently cover for weekly planning."

### Practice 2: does the output answer the question?

A classmate says this view answers the question "Which upcoming sessions are scheduled, and who is involved?"

```sql
CREATE VIEW dbo.vScheduledSessionIDs
AS
SELECT s.SessionID,
       s.StudentID,
       s.TutorID,
       s.SubjectID
FROM dbo.[Session] AS s
WHERE s.SessionDate >= CAST(GETDATE() AS date)
  AND s.Status = 'Scheduled';
```

Answer these questions:

1. Does the output answer the intended business question fully? Why or why not?
2. Which columns are missing for a readable report?
3. What would you revise before keeping this view?

### Practice 3: transparent but not oversharing

The tutoring coordinator wants a repeatable schedule view. Should the view include student email and phone? Explain your answer in terms of:

- the reporting purpose
- transparency for decision-making
- unnecessary exposure of details

## What to do

1. Review the approved DBDD and the sample data you already loaded.
2. Choose one repeated reporting question from the case or your project tables.
3. Write the underlying `SELECT`.
4. Test it and revise the joins, filters, and columns until it answers the intended question.
5. Convert the tested query into a `CREATE VIEW` statement.
6. Query the view.
7. Write a short verification note explaining whether the output answers the business question and whether it exposes any unnecessary details.

## Assignments

### Assignment 1: choose and justify

Choose one business question that deserves a view and one that should remain an ad hoc query.

For each choice, explain:

- who would use the output
- whether the question is repeatable
- why a view is or is not appropriate

### Assignment 2: build and verify a view

Submit:

- the tested `SELECT`
- the `CREATE VIEW` statement
- one `SELECT` against the new view
- a short verification note explaining whether the output answers the intended business question
- one short note explaining whether the view supports transparent decisions without oversharing

## Deliverables

- one short rationale comparing a view-worthy question to an ad hoc query
- one tested `SELECT` statement
- one `CREATE VIEW` statement
- one verification query against the view
- one short output-review note

## Project checkpoint or module connection

For your semester project, identify one recurring reporting question that should be answered with a view. Keep the view tied to the approved design and ask whether the output is both useful and appropriately limited. A stronger project view is not the one with the most columns. It is the one that best supports a real business question.

This checkpoint also prepares you for Module 6's build-and-verify audit, where you may need to judge whether a technically successful view still fails the intended reporting purpose.

## Wrap-up

Views are reusable reporting structures, not magic shortcuts. Their value comes from packaging tested logic so repeated questions can be answered more consistently.

The lasting skill from this lesson is not memorizing `CREATE VIEW`. It is learning to ask better questions about fit: Is this question repeated? Does the output answer it clearly? Does the view support truthful, transparent decisions without revealing unnecessary information? If you can answer those questions well, you are doing more than writing SQL. You are building reporting logic the organization can trust.
