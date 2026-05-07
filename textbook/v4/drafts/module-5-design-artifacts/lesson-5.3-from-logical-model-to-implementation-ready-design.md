# Lesson 5.3: From Logical Model to Implementation-Ready Design

## Lesson overview

This lesson is the bridge between two artifacts that students often blur together: the conceptual ERD and the implementation-ready Database Design Diagram, or DBDD. Your job in this lesson is not to redraw the ERD with extra labels. Your job is to preserve the ERD's meaning while making the design ready for later SQL Server implementation.

You will learn a repeatable way to move from conceptual relationships to tables, keys, foreign keys, intersection tables, data types, and nullability. You will also critique weak mapping decisions so that your design choices are explainable rather than mechanical.

## Lesson outcomes

By the end of this lesson, you should be able to:

- explain how a conceptual relationship becomes implementation-ready structure in a DBDD
- convert a reviewed conceptual ERD into first-pass tables without changing the business meaning
- justify primary key, foreign key, intersection-table, data-type, and nullability choices
- diagnose at least one weak or unjustified mapping decision
- explain where design precision protects users, customers, staff, or records from confusion or loss

## Key terms

- `logical model`: the conceptual representation of the business structure, typically shown in the ERD
- `Database Design Diagram (DBDD)`: the implementation-ready design artifact that shows tables, columns, keys, data types, and nullability
- `mapping decision`: a choice about how a conceptual element will be represented in the DBDD
- `intersection table`: a table that resolves a many-to-many relationship into two one-to-many relationships
- `nullability`: whether a column may hold `NULL`
- `artifact boundary`: the distinction between what belongs in the conceptual ERD and what belongs in the DBDD
- `design rationale`: a short explanation of why a mapping choice is structurally and conceptually correct

## Readings and media

- Read this lesson from start to finish before building or revising a DBDD.
- Review [Module 5: Design Artifacts](../../modules-plan/05-module-5-design-artifacts.md), especially the Lesson 5.3 role and assessment strategy.
- Review [Design Object Naming and Notation Conventions](../../06-design-object-naming-and-notation-conventions.md), especially the sections on table names, column names, foreign keys, intersection tables, and ERD-versus-DBDD boundaries.
- Reopen your reviewed conceptual ERD from Module 3 and Lesson 5.1 work before starting the conversion.

## Core content

## 1. The DBDD should add structure without changing meaning

The boundary between the ERD and the DBDD was established in Lessons 5.1 and 5.2. This lesson assumes that boundary is understood and focuses on the mapping decisions that cross it.

The conceptual ERD and the DBDD answer different questions.

The ERD answers:

- What business objects matter?
- How are those objects related?
- Which relationships are optional or required?

The DBDD answers:

- What tables must be built?
- Which columns identify rows?
- Where do foreign keys belong?
- Which data types fit the intended values?
- Which values are required and which may be missing?

That difference matters. If you add `PK`, `FK`, `INT`, `DATE`, or `NOT NULL` labels directly to the ERD, you blur the artifact boundary. If you build the DBDD without tracing back to the ERD, you risk inventing structure that no longer reflects the business meaning.

The bridge rule for this lesson is simple:

`Add implementation-ready detail, but do not rewrite the business meaning.`

## 2. Use a repeatable mapping method

Use this sequence whenever you move from a reviewed ERD to a first-pass DBDD:

1. Re-read the business rules and the reviewed conceptual ERD.
2. Convert each conceptual entity into a first-pass table.
3. Carry the conceptual identifier into the table as the primary key.
4. Add foreign keys that implement one-to-many or one-to-one relationships.
5. Resolve every many-to-many relationship with an intersection table.
6. Choose SQL Server data types that fit the meaning of each column.
7. Decide `NULL` or `NOT NULL` from required facts and legitimate business absence.
8. Review the DBDD against the ERD and ask whether any mapping choice changed the business meaning.
9. Write a short rationale for the most important design choices.

This sequence is useful because it forces you to explain decisions, not just place labels.

## 3. One conceptual relationship can become foreign-key structure

Suppose the reviewed conceptual ERD says:

- one `Student` can attend many `Session` instances
- each `Session` must belong to exactly one `Student`

That meaning becomes this DBDD structure:

```text
Student(StudentID PK, FirstName, LastName, Email)
Session(SessionID PK, StudentID FK, SessionDate, StartTime, Room)
```

The relationship is no longer shown only as a line between two conceptual entities. In the DBDD, it becomes a foreign key on the many side:

- `Session.StudentID` points back to `Student.StudentID`
- `Session.StudentID` should be `NOT NULL` because a session cannot exist without a student

This is the core reasoning pattern for one-to-many mapping:

- the conceptual meaning tells you what must stay true
- the DBDD structure shows how the database will enforce that truth later

## 4. A many-to-many relationship needs an intersection table, not a shortcut

By now you have seen many-to-many resolution three times: as a conceptual pattern in Lesson 3.2, as a normalization repair in Lesson 4.3, and as a DBDD element in Lesson 5.2. This lesson practices the mapping decision — translating the conceptual relationship into a correctly specified intersection table.

Now suppose the reviewed conceptual ERD says:

- one `Tutor` may teach many `Subject` instances
- one `Subject` may be taught by many `Tutor` instances

That relationship cannot stay as a direct many-to-many line in a buildable relational design. The DBDD needs a table that can store pairings without repeating columns or hiding the relationship inside free text.

One clean mapping is:

```text
Tutor(TutorID PK, FirstName, LastName)
Subject(SubjectCode PK, SubjectName)
TutorSubject(TutorID PK/FK, SubjectCode PK/FK)
```

This table is not technical clutter. It preserves a real business fact:

- tutors are qualified to teach subjects

If the relationship needs its own descriptive fact, such as certification date, that fact belongs in the intersection table because it describes the pairing.

## 5. Optionality informs nullability, but it does not mechanically equal nullability

As Lesson 5.2 established, optional participation does not equal nullable. Apply that distinction here when assigning nullability to each column during the mapping process.

Students often over-simplify this step.

Suppose the ERD says:

- a `Session` may have zero or one `SessionNote`
- each `SessionNote` belongs to exactly one `Session`

One weak mapping would be:

```text
SessionNote(SessionNoteID PK, SessionID FK NULL, NoteText, SubmittedAt)
```

That choice is weak because it misreads optionality. The optional rule means a session might have no note row yet. It does not mean a note row may exist without a session.

The stronger mapping is:

```text
SessionNote(SessionNoteID PK, SessionID FK NOT NULL, NoteText, SubmittedAt)
```

Why?

- The absence of a `SessionNote` row represents the optional side of the relationship.
- If a `SessionNote` row exists, it must belong to one session.

Nullability should follow the meaning of the specific column, not a memorized shortcut.

## 6. Weak mapping decisions usually sound plausible at first

A design can look tidy and still be unjustified. Review these examples.

| Weak mapping decision | Why it is weak | Better mapping logic |
| --- | --- | --- |
| Rename a tutoring request relationship table as `StudentEnrollment` | The new table name changes the business meaning from requesting tutoring to enrolling in a course | Name the table `StudentSubjectRequest` if it stores student requests for subjects |
| Make `Session.StudentID` nullable | It allows a session record with no student, which breaks the required business rule | Keep `Session.StudentID` as `NOT NULL` because every session belongs to a student |
| Store multiple subject codes in one `Tutor.Subjects` text column | The design hides a many-to-many relationship inside one field and prevents reliable relational structure | Use `TutorSubject(TutorID, SubjectCode)` as an intersection table |
| Add data types and `PK` labels to the conceptual ERD itself | The artifact no longer stays conceptual, so the ERD and DBDD lose their distinct roles | Keep implementation-ready details in the DBDD only |

Weak mapping decisions matter because later implementation work will inherit them. A poor bridge decision here can become a broken table, a confusing query, or a hidden data-quality problem in Module 6.

## 7. Review every DBDD for accountability before calling it finished

Before you accept a mapping choice, ask:

- Which conceptual meaning is this table or foreign key implementing?
- Did I add structure, or did I accidentally change the business story?
- If another analyst reads this DBDD, could they explain the original relationship without guesswork?
- If this design were implemented as written, where could users, customers, staff, or records be harmed by ambiguity, duplication, or missing relationships?

Design precision protects real work. A nullable foreign key that should be required can create orphan records. A misleading intersection-table name can cause staff to misread what the system is tracking. A hidden many-to-many relationship can lead to duplicated facts and inconsistent reporting.

Faithful professional follow-through means making mapping choices that are understandable, defensible, and safe to implement.

## Examples and case

## Lakeside Tutoring Center bridge example

Assume the reviewed conceptual ERD includes these entities:

- `Student`
- `Tutor`
- `Subject`
- `Session`
- `SessionNote`

Assume the reviewed conceptual relationships include these rules:

- one `Student` can attend many `Session` instances, and each `Session` belongs to one `Student`
- one `Tutor` can lead many `Session` instances, and each `Session` belongs to one `Tutor`
- one `Subject` can appear in many `Session` instances, and each `Session` is for one `Subject`
- one `Session` may have zero or one `SessionNote`
- one `Student` may request many `Subject` instances, and one `Subject` may be requested by many `Student` instances
- one `Tutor` may teach many `Subject` instances, and one `Subject` may be taught by many `Tutor` instances

One implementation-ready DBDD could be:

```text
Student(
    StudentID INT PK,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Email VARCHAR(100) NOT NULL
)

Tutor(
    TutorID INT PK,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    HireDate DATE NOT NULL
)

Subject(
    SubjectCode VARCHAR(20) PK,
    SubjectName VARCHAR(100) NOT NULL
)

Session(
    SessionID INT PK,
    StudentID INT FK NOT NULL,
    TutorID INT FK NOT NULL,
    SubjectCode VARCHAR(20) FK NOT NULL,
    SessionDate DATE NOT NULL,
    StartTime TIME NOT NULL,
    Room VARCHAR(20) NOT NULL
)

SessionNote(
    SessionNoteID INT PK,
    SessionID INT FK NOT NULL,
    NoteText VARCHAR(1000) NOT NULL,
    FollowUpRecommendation VARCHAR(500) NULL,
    SubmittedAt DATETIME2 NOT NULL
)

StudentSubjectRequest(
    StudentID INT PK/FK NOT NULL,
    SubjectCode VARCHAR(20) PK/FK NOT NULL,
    RequestedOn DATE NOT NULL
)

TutorSubject(
    TutorID INT PK/FK NOT NULL,
    SubjectCode VARCHAR(20) PK/FK NOT NULL
)
```

## What this example shows

- `Session.StudentID`, `Session.TutorID`, and `Session.SubjectCode` implement required one-to-many relationships.
- `StudentSubjectRequest` resolves a conceptual many-to-many relationship without changing what the relationship means.
- `TutorSubject` resolves subject qualification as a separate many-to-many relationship instead of hiding it in a text field.
- `SessionNote.SessionID` remains `NOT NULL` even though a session may have no note yet.
- Data types appear in the DBDD because the design is now implementation-ready.
- The ERD stays conceptual because implementation labels were not pushed backward into the conceptual artifact.

## Critique item

A teammate proposes this table instead:

```text
StudentEnrollment(
    StudentID INT PK/FK,
    SubjectCode VARCHAR(20) PK/FK
)
```

Critique it:

- The structure could hold pairings, but the table name is unjustified.
- The conceptual relationship is about tutoring requests, not course enrollment.
- The table may be technically valid while still misrepresenting the business process.

This is why DBDD review is not only procedural. You must judge whether the structure still tells the truth about the case.

## Guided practice

Work through these prompts in order:

1. List the conceptual entities from your reviewed ERD and write the first-pass tables they become.
2. Choose one one-to-many relationship and explain exactly which table gets the foreign key and why.
3. Choose one many-to-many relationship and draft the intersection table that resolves it.
4. Identify one optional relationship and explain how its meaning affects nullability in the DBDD.
5. Diagnose one weak mapping decision from the table above and rewrite it with stronger logic.
6. Write one sentence answering this question: `What business meaning would be lost if this mapping were implemented badly?`

## What to do

Create or revise a DBDD from a reviewed conceptual ERD.

Your DBDD should:

- include the full table set needed to represent the reviewed conceptual model
- use clear primary key and foreign key structure
- resolve many-to-many relationships with intersection tables
- use reasonable SQL Server data types
- mark `NULL` and `NOT NULL`
- preserve the meaning of the original conceptual relationships

Your process should also include a short explanation of why your key mapping decisions are correct.

If you use AI:

- you may ask it to propose table structures, key placement, or candidate data types
- you must still verify that the proposal matches the reviewed ERD
- you must still explain one good mapping decision and one weak mapping decision in your own words

## Assignments

## Assignment 1: Mapping critique

Review a flawed ERD-to-DBDD conversion and identify:

- one unjustified table name, foreign key, or nullability choice
- why that choice weakens the design
- how you would repair it

## Assignment 2: Implementation-ready conversion

Submit a revised DBDD for your case and attach a short design rationale that explains:

- how one conceptual relationship became implementation-ready structure
- why one foreign key is required
- why one nullability choice is correct
- where precision in your design protects people, work, or records from confusion or loss

## Deliverables

- one implementation-ready DBDD
- one short written design rationale
- one critique-and-repair response for a weak mapping decision

## Project checkpoint or module connection

Before you submit, answer this checkpoint prompt:

`Where in your design does precision protect users, customers, staff, or records from confusion or loss, and what specific mapping choice provides that protection?`

Then answer this second checkpoint:

`If someone implemented your DBDD exactly as written, which relationship or constraint would matter most for trustworthy operation later?`

These questions connect Module 5 to Module 6. The design you justify here becomes the structure someone will implement in SQL Server next.

## Wrap-up

This lesson completes Module 5 by making the mapping logic visible. A good DBDD is not just a more detailed picture. It is a defensible translation from conceptual meaning to implementation-ready structure.

If you can explain how one relationship became a foreign key or an intersection table, diagnose a weak mapping choice, and show where precision protects later work, then you are ready for the next module. Module 6 will take this implementation-ready design and turn it into SQL Server tables and constraints.
