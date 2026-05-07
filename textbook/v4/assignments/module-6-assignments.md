# Module 6 Assignments

## Lesson 6.1: DDL Build Order Check

### DBDD Slice

- `Student(StudentID PK, FirstName, LastName, Email)`
- `Tutor(TutorID PK, FirstName, LastName)`
- `Session(SessionID PK, StudentID FK REFERENCES Student, TutorID FK REFERENCES Tutor, SessionDate, Minutes)`

### Flawed Build Order

```sql
CREATE TABLE Session (
    SessionID int NOT NULL PRIMARY KEY,
    StudentID int NOT NULL,
    TutorID int NOT NULL,
    SessionDate date NOT NULL,
    Minutes int NOT NULL,
    CONSTRAINT FK_Session_Student FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    CONSTRAINT FK_Session_Tutor FOREIGN KEY (TutorID) REFERENCES Tutor(TutorID)
);

CREATE TABLE Student (
    StudentID int NOT NULL PRIMARY KEY,
    FirstName varchar(50) NOT NULL,
    LastName varchar(50) NOT NULL,
    Email varchar(100) NOT NULL
);

CREATE TABLE Tutor (
    TutorID int NOT NULL PRIMARY KEY,
    FirstName varchar(50) NOT NULL,
    LastName varchar(50) NOT NULL
);
```

### Tasks

1. Correct the build order.
2. Explain why the original order can fail.
3. Add one verification query or command you would run after creating the tables.

### Submission

Submit corrected SQL or ordered table names plus explanation and verification check.

### Grading Criteria

- dependency-aware build order
- accurate FK explanation
- reasonable verification habit

## Lesson 6.2: Safe Data Change Review

### DML Statements

```sql
-- A
INSERT INTO Session (SessionID, StudentID, TutorID, SessionDate, Minutes)
VALUES (9001, 999, 12, '2026-09-15', 60);

-- B
UPDATE Student
SET Active = 0;

-- C
DELETE FROM Tutor
WHERE TutorID = 12;
```

Assume `StudentID = 999` does not exist and tutor `12` has existing sessions.

### Tasks

1. Diagnose the risk in each statement.
2. Rewrite statement `B` safely for only `StudentID = 104`.
3. Explain what should be checked before statement `C`.
4. Provide one verification query for your corrected update.

### Submission

Submit diagnosis, corrected SQL, and verification query.

### Grading Criteria

- DML risk identification
- safe condition use
- referential-integrity reasoning
- verification query quality

## Lesson 6.3: View Output Verification

### Business Question

Which active tutors have completed sessions, and how many completed minutes have they taught?

### Proposed View

```sql
CREATE VIEW TutorSessionSummary AS
SELECT
    t.TutorID,
    t.FirstName,
    t.LastName,
    COUNT(*) AS SessionCount,
    SUM(s.Minutes) AS TotalMinutes
FROM Tutor AS t
JOIN Session AS s ON t.TutorID = s.TutorID
GROUP BY t.TutorID, t.FirstName, t.LastName;
```

### Tasks

1. Decide whether the view fully answers the business question.
2. Identify what is missing or misleading.
3. Revise the view.
4. Explain what the output does and does not prove.

### Submission

Submit your judgment, revised SQL, and explanation.

### Grading Criteria

- correct view diagnosis
- business-question alignment
- valid revised SQL
- careful output interpretation
