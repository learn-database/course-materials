# Lesson 6.2: Inserting, Updating, and Deleting Data

## Lesson Overview

In Lesson 6.1, you built tables and constraints from an approved Database Design Diagram. In this lesson, you start using that structure through controlled data changes. The goal is not just to make `INSERT`, `UPDATE`, and `DELETE` run. The goal is to make changes that respect dependencies, limit risk, and leave the database in the state the business case actually intended.

This matters in an AI-available course. AI can draft DML quickly, but a generated statement is not trustworthy just because it executes. You still have to judge whether the change logic is safe, whether it touches the right rows, and whether the final data state matches the approved design.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- insert sample data in dependency-aware order
- explain why a child row depends on an existing parent row
- write updates with conditions that match the intended business action
- critique unsafe update or delete logic
- predict when a delete may fail or cause business risk
- verify that a data change produced the intended result
- choose sample data that supports later querying and reporting without oversharing unnecessary details

## Key Terms

- `data manipulation`: changing stored data with statements such as `INSERT`, `UPDATE`, and `DELETE`
- `parent row`: a row another table depends on through a foreign key
- `child row`: a row that depends on a parent row through a foreign key
- `referential integrity`: the rule that related rows must remain valid across tables
- `condition`: the `WHERE` logic that limits which rows an `UPDATE` or `DELETE` affects
- `verification`: checking that the data change affected the intended rows and preserved the intended meaning
- `sample data`: representative rows used to test structure, support queries, and prepare for later reporting

## Readings And Media

- Read this lesson completely before writing your DML script.
- Reopen your Lesson 6.1 schema or table-creation script so you can see the existing constraints.
- Keep the approved Database Design Diagram nearby while you work.
- Review the module plan if you need to reconnect this lesson to Module 6's build-and-verify emphasis.

## Core Content

### Data Changes Work Under The Schema

`INSERT`, `UPDATE`, and `DELETE` are data manipulation statements, but they do not bypass the schema you already built. The schema still controls what is allowed.

That means:

- a child row cannot safely reference a parent row that does not exist
- an update must identify the correct target rows
- a delete must account for dependent rows and for the business value of the data being removed

When DML goes wrong, the problem is often structural, not mysterious. Your job is to read the structure before you change the data.

### Running Case: Lakeside Tutoring Center

Use this implementation-ready schema throughout the lesson:

- `Student(StudentID, FirstName, LastName, EmailAddress)`
- `Tutor(TutorID, FirstName, LastName, EmailAddress)`
- `Subject(SubjectID, SubjectName)`
- `Session(SessionID, StudentID, TutorID, SubjectID, SessionDate, StartTime, Room)`
- `SessionNote(SessionNoteID, SessionID, NoteText, FollowUpNeeded)`

Important relationships:

- each `Session` row must reference an existing `Student`
- each `Session` row must reference an existing `Tutor`
- each `Session` row must reference an existing `Subject`
- each `SessionNote` row must reference an existing `Session`

From those rules, you can already infer a safe insert order:

1. `Student`
2. `Tutor`
3. `Subject`
4. `Session`
5. `SessionNote`

That is not a memorized trick. It comes from the parent-child structure.

### `INSERT`: Load Parent Rows Before Child Rows

Start with parent tables:

```sql
INSERT INTO Student (StudentID, FirstName, LastName, EmailAddress)
VALUES
    (1001, 'Ava', 'Lopez', 'ava.lopez@rtc.edu'),
    (1002, 'Marcus', 'Hill', 'marcus.hill@rtc.edu');

INSERT INTO Tutor (TutorID, FirstName, LastName, EmailAddress)
VALUES
    (2001, 'Priya', 'Shah', 'priya.shah@rtc.edu'),
    (2002, 'Daniel', 'Kim', 'daniel.kim@rtc.edu');

INSERT INTO Subject (SubjectID, SubjectName)
VALUES
    (3001, 'Database Design'),
    (3002, 'Statistics');
```

Then add child rows that depend on those parents:

```sql
INSERT INTO Session (SessionID, StudentID, TutorID, SubjectID, SessionDate, StartTime, Room)
VALUES
    (4001, 1001, 2001, 3001, '2026-09-15', '15:00', 'B201'),
    (4002, 1002, 2002, 3002, '2026-09-16', '10:00', 'B105');

INSERT INTO SessionNote (SessionNoteID, SessionID, NoteText, FollowUpNeeded)
VALUES
    (5001, 4001, 'Reviewed normalization examples and primary key choices.', 1);
```

Why this order works:

- `Session` needs valid `StudentID`, `TutorID`, and `SubjectID` values
- `SessionNote` needs a valid `SessionID`

Now look at an unsafe insert:

```sql
INSERT INTO Session (SessionID, StudentID, TutorID, SubjectID, SessionDate, StartTime, Room)
VALUES
    (4003, 1099, 2001, 3001, '2026-09-18', '11:00', 'B210');
```

This should fail because `StudentID = 1099` does not exist. The lesson is not "SQL Server rejected my work." The lesson is "the schema protected the database from a false relationship."

### Verify After Every Insert Group

Execution alone is not proof. Verify the data state after each major insert.

```sql
SELECT StudentID, FirstName, LastName
FROM Student;

SELECT SessionID, StudentID, TutorID, SubjectID, SessionDate, Room
FROM Session;

SELECT s.SessionID,
       st.FirstName AS StudentFirstName,
       t.FirstName AS TutorFirstName,
       sub.SubjectName
FROM Session AS s
JOIN Student AS st
    ON s.StudentID = st.StudentID
JOIN Tutor AS t
    ON s.TutorID = t.TutorID
JOIN Subject AS sub
    ON s.SubjectID = sub.SubjectID;
```

The join matters because it checks whether the relationship you intended is the relationship you actually created.

### `UPDATE`: Preview, Target, Then Verify

A safe update starts before the `UPDATE` statement. First preview the target rows.

```sql
SELECT SessionID, SubjectID, Room
FROM Session
WHERE SessionID = 4002;
```

Then write the update:

```sql
UPDATE Session
SET Room = 'B207'
WHERE SessionID = 4002;
```

Then verify:

```sql
SELECT SessionID, Room
FROM Session
WHERE SessionID = 4002;
```

This is safe because the condition matches the intended business action: move one specific session.

Now critique this version:

```sql
UPDATE Session
SET Room = 'B207'
WHERE SubjectID = 3002;
```

Why is it risky?

- it may affect more than one session
- it matches a subject, not a single scheduled event
- it could silently change valid rows that were not meant to move

The rule is not "SubjectID is always wrong." The rule is "your condition must match your real intention."

Here is an even worse example:

```sql
UPDATE SessionNote
SET FollowUpNeeded = 0;
```

This statement has no `WHERE` clause, so it changes every note row. If those flags are used to track students who still need help, this is not only technically careless. It also distorts operational truth and could cause staff to miss students who still need follow-up.

### `DELETE`: Check Dependencies And Business Meaning First

A delete requires two kinds of judgment:

1. structural judgment: do dependent child rows exist?
2. business judgment: should this history be removed at all?

Suppose you try this:

```sql
DELETE FROM Session
WHERE SessionID = 4001;
```

If `SessionNote` still contains a row for `SessionID = 4001`, the delete should fail because the child row still depends on the parent row.

That failure is meaningful:

- `Session` is the parent row
- `SessionNote` is the child row
- the foreign key prevents an orphaned note

Now critique this delete:

```sql
DELETE FROM SessionNote
WHERE SessionID = 4001;
```

This might be correct if the business decision is "remove every note tied to the cancelled session." It is unsafe if the true goal is "remove one duplicate note," because the condition may delete several notes at once. Again, the question is not only "Will it run?" but also "Does it match the intended business action?"

If the approved action really is to remove the session and its note, a dependency-aware sequence is:

```sql
DELETE FROM SessionNote
WHERE SessionID = 4001;

DELETE FROM Session
WHERE SessionID = 4001;
```

Then verify:

```sql
SELECT SessionID
FROM Session
WHERE SessionID = 4001;

SELECT SessionID
FROM SessionNote
WHERE SessionID = 4001;
```

Both queries should return no rows if the deletion sequence matched the intended action.

### Verification Is A Procedure, Not An Afterthought

Use this checklist for every meaningful data change:

1. read the schema and identify dependencies
2. preview the rows you think will change
3. write the `INSERT`, `UPDATE`, or `DELETE`
4. run a verification query immediately after execution
5. decide whether the result matches the business case, not just the SQL syntax

For updates and deletes, a preview query is often the difference between safe work and accidental damage:

```sql
SELECT SessionID, SubjectID, Room
FROM Session
WHERE SubjectID = 3002;
```

If this preview returns three rows and you meant to change one, stop and rewrite the condition.

### Good Sample Data Supports Testing And Reporting

Useful sample data is not random filler. It should help you test structure and support later reporting work.

Useful choices in this case include:

- more than one student
- more than one tutor
- more than one subject
- sessions on different dates
- one session with a note and one without a note
- rows that later support reporting by tutor, subject, or follow-up status

Weak choices include:

- ten nearly identical rows that do not test any new relationship or condition
- fake note text that includes unnecessary sensitive details
- rows that make later reporting impossible because everything is the same

You want data that is realistic enough to test the system, but not reckless, exaggerated, or needlessly invasive.

## Examples And Case

### Worked Sequence

Use the Lakeside Tutoring Center schema and complete this sequence:

```sql
INSERT INTO Student (StudentID, FirstName, LastName, EmailAddress)
VALUES
    (1001, 'Ava', 'Lopez', 'ava.lopez@rtc.edu'),
    (1002, 'Marcus', 'Hill', 'marcus.hill@rtc.edu');

INSERT INTO Tutor (TutorID, FirstName, LastName, EmailAddress)
VALUES
    (2001, 'Priya', 'Shah', 'priya.shah@rtc.edu'),
    (2002, 'Daniel', 'Kim', 'daniel.kim@rtc.edu');

INSERT INTO Subject (SubjectID, SubjectName)
VALUES
    (3001, 'Database Design'),
    (3002, 'Statistics');

INSERT INTO Session (SessionID, StudentID, TutorID, SubjectID, SessionDate, StartTime, Room)
VALUES
    (4001, 1001, 2001, 3001, '2026-09-15', '15:00', 'B201'),
    (4002, 1002, 2002, 3002, '2026-09-16', '10:00', 'B105');

INSERT INTO SessionNote (SessionNoteID, SessionID, NoteText, FollowUpNeeded)
VALUES
    (5001, 4001, 'Reviewed normalization examples and primary key choices.', 1);
```

### Unsafe Change Logic To Critique

Suppose the business request is: "Move session `4002` to room `B207` and keep all other sessions unchanged."

Which statement fits the request, and why?

```sql
UPDATE Session
SET Room = 'B207'
WHERE SessionID = 4002;
```

```sql
UPDATE Session
SET Room = 'B207'
WHERE SubjectID = 3002;
```

Now suppose the business request is: "Remove one duplicate note while keeping the real tutoring history."

Why is this statement unsafe without more information?

```sql
DELETE FROM SessionNote
WHERE SessionID = 4001;
```

Your explanation should name the risk, not just say "it might delete too much."

## Guided Practice

### Practice 1: Identify Safe Insert Order

Write the safest insert order for these tables and explain one dependency:

- `Student`
- `Tutor`
- `Subject`
- `Session`
- `SessionNote`

### Practice 2: Explain The Failed Insert

Explain why this statement should fail and identify the parent table that must be checked first:

```sql
INSERT INTO Session (SessionID, StudentID, TutorID, SubjectID, SessionDate, StartTime, Room)
VALUES
    (4010, 1099, 2001, 3001, '2026-09-20', '13:00', 'B210');
```

### Practice 3: Critique Unsafe Update Logic

The business request is "clear the follow-up flag only for notes attached to cancelled sessions that were already reviewed by staff."

Why is this statement unsafe?

```sql
UPDATE SessionNote
SET FollowUpNeeded = 0;
```

What would you preview before writing a safer update?

### Practice 4: Predict Delete Behavior

If `SessionNote` contains rows for `SessionID = 4001`, explain whether this delete should succeed:

```sql
DELETE FROM Session
WHERE SessionID = 4001;
```

Then explain what you would verify after the delete attempt.

## What To Do

1. Reopen or rebuild your Lesson 6.1 schema in SQL Server.
2. Insert representative sample data in dependency-aware order.
3. Run verification queries after each major insert group.
4. Preview the rows for one planned update.
5. Run one precise update with a clear condition and verify the result.
6. Analyze or attempt one delete where dependency or business logic matters.
7. Verify the final data state after the delete or corrected delete sequence.
8. Write a short explanation of one unsafe change and why it is unsafe.

## Assignments

Submit one SQL script and one short written explanation that show the following:

- dependency-aware inserts
- one careful update with preview and verification
- one dependency-aware delete or delete critique
- verification queries after each major operation
- explanation of one integrity-related failure or unsafe condition
- explanation of why your sample data supports later querying or reporting

## Deliverables

- one SQL script containing `INSERT`, `UPDATE`, `DELETE`, preview queries, and verification queries
- one short explanation of an unsafe or failed data change
- one short note explaining how your sample data supports testing, reporting, and responsible data use

## Project Checkpoint Or Module Connection

Load sample data into your semester project tables in dependency-aware order. Before each update or delete, preview the affected rows. After each major change, verify that the resulting data state still reflects the approved design and the business case you are modeling.

This checkpoint supports the Module 6 build-and-verify audit. You are not just proving that a statement runs. You are proving that the database still tells the truth after the change.

## Wrap-Up

This lesson moves the database from built structure to controlled use. The central habit is simple: read the structure, make the change carefully, and verify the outcome immediately.

Carry three ideas into Lesson 6.3. First, sample data should be useful, not random. Second, successful execution is not enough. Third, data changes are part of stewardship: they should protect integrity, limit unnecessary exposure, and support truthful reporting.
