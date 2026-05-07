# Module 2 Assignments

Use the sample schema below for Lessons 2.3 through 2.6 unless the LMS provides a live database.

## Sample Tables

`Student(StudentID, FirstName, LastName, GradeLevel, Active)`

`Tutor(TutorID, FirstName, LastName, HourlyRate, Active)`

`Session(SessionID, StudentID, TutorID, SessionDate, Subject, Minutes, Status)`

Sample row meanings:

- `Active` is `1` for current students or tutors and `0` for inactive records.
- `Status` may be `Completed`, `Cancelled`, or `NoShow`.
- `Minutes` stores the scheduled or completed session length.

## Lesson 2.1: Environment Verification Check

### Purpose

Verify that you can work in the SQL Server environment used for the course.

### Tasks

1. Open the course SQL Server tool.
2. Select the assigned course database.
3. Run this query:

```sql
SELECT DB_NAME() AS CurrentDatabase;
SELECT 'ITM2100 setup check' AS Message;
```

4. Explain the role of the client, the server, and the selected database context.

### Submission

Submit:

- screenshot or copied output
- database name shown by `DB_NAME()`
- 3-4 sentence explanation of why database context matters

### Grading Criteria

- successful query execution
- correct database context
- accurate explanation of client, server, and context

## Lesson 2.2: Set Thinking Mini-Sort

### Purpose

Connect relation and set ideas to SQL query behavior.

### Items To Classify

Classify each item as `relation`, `row`, `attribute`, `selection`, `projection`, or `not relational`.

1. The `Student` table.
2. One student record for `StudentID = 104`.
3. The `LastName` field.
4. Keeping only active tutors.
5. Showing only `FirstName`, `LastName`, and `GradeLevel`.
6. Changing a student's last name.
7. The set of all completed tutoring sessions.
8. Sorting students alphabetically.

### Tasks

1. Complete the classification.
2. Correct two misunderstandings from this list.
3. Explain in one paragraph how set thinking helps you read SQL.

### Submission

Submit the completed classification table and paragraph.

### Grading Criteria

- accurate classification
- clear distinction between row thinking and set thinking
- useful connection to SQL

## Lesson 2.3: One Table, Three Queries

### Business Question

Which active students are in grade 10, listed alphabetically by last name?

### Candidate Queries

```sql
-- Query A
SELECT StudentID, FirstName, LastName, GradeLevel
FROM Student
WHERE GradeLevel = 10 AND Active = 1
ORDER BY LastName, FirstName;

-- Query B
SELECT StudentID, FirstName, LastName, GradeLevel
FROM Student
WHERE GradeLevel = 10 OR Active = 1
ORDER BY LastName, FirstName;

-- Query C
SELECT StudentID, FirstName, LastName
FROM Student
WHERE GradeLevel = 10 AND Active = 1;
```

### Tasks

1. Choose the query that best answers the business question.
2. Explain why each rejected query is weaker or wrong.
3. Revise one rejected query so it answers the question correctly.

### Submission

Submit your answers in short numbered responses.

### Grading Criteria

- correct query choice
- accurate explanation of filter and output problems
- corrected SQL is readable and aligned to the business question

## Lesson 2.4: Summary Result Check

### Business Question

How many completed tutoring sessions occurred for each subject?

### Candidate Queries

```sql
-- Query A
SELECT Subject, COUNT(*) AS CompletedSessionCount
FROM Session
WHERE Status = 'Completed'
GROUP BY Subject
ORDER BY Subject;

-- Query B
SELECT Subject, Status, COUNT(*) AS SessionCount
FROM Session
GROUP BY Subject, Status
ORDER BY Subject, Status;
```

### Tasks

1. Choose the query that best answers the business question.
2. Explain what each row in the result means.
3. Explain one misleading conclusion someone might draw from the weaker query.

### Submission

Submit:

- selected query
- row-meaning explanation
- misleading-interpretation warning

### Grading Criteria

- correct grouping logic
- accurate output interpretation
- recognition of reporting risk

## Lesson 2.5: Join Path Diagnosis

### Business Question

List each completed session with the student's name, tutor's name, subject, date, and minutes.

### Candidate Queries

```sql
-- Query A
SELECT
    s.SessionID,
    st.FirstName AS StudentFirstName,
    st.LastName AS StudentLastName,
    t.FirstName AS TutorFirstName,
    t.LastName AS TutorLastName,
    s.Subject,
    s.SessionDate,
    s.Minutes
FROM Session AS s
JOIN Student AS st ON s.StudentID = st.StudentID
JOIN Tutor AS t ON s.TutorID = t.TutorID
WHERE s.Status = 'Completed';

-- Query B
SELECT
    s.SessionID,
    st.FirstName AS StudentFirstName,
    st.LastName AS StudentLastName,
    t.FirstName AS TutorFirstName,
    t.LastName AS TutorLastName,
    s.Subject,
    s.SessionDate,
    s.Minutes
FROM Session AS s
JOIN Student AS st ON s.TutorID = st.StudentID
JOIN Tutor AS t ON s.StudentID = t.TutorID
WHERE s.Status = 'Completed';
```

### Tasks

1. Choose the correct join.
2. Explain what each row in the correct result represents.
3. Diagnose the join error in the weaker query.
4. Explain one business risk of trusting the weaker query.

### Submission

Submit your answers in 4 short sections.

### Grading Criteria

- correct join path
- clear joined-row meaning
- accurate diagnosis of mismatched keys
- realistic business risk

## Lesson 2.6: Name the Intermediate Result

### Starting Query

```sql
SELECT TutorID, Subject, COUNT(*) AS CompletedSessionCount
FROM Session
WHERE Status = 'Completed'
GROUP BY TutorID, Subject
HAVING COUNT(*) >= 3
ORDER BY TutorID, Subject;
```

### Tasks

1. Rewrite the query using one CTE named `CompletedSessions`.
2. Explain what rows appear inside the CTE before the final grouping.
3. Explain whether the CTE improves readability and why.

### Submission

Submit:

- rewritten SQL
- CTE explanation
- readability judgment

### Grading Criteria

- valid CTE structure
- accurate intermediate-result explanation
- defensible readability judgment
