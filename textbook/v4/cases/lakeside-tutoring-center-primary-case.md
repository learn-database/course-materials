# Lakeside Tutoring Center Primary Case

## Role In The Course

Lakeside Tutoring Center is the primary running case for `ITM-2100 v4`.

Use this case first when a lesson needs a coherent example for:

- requirements discovery
- entities and attributes
- relationships and cardinality
- ERDs and DBDDs
- SQL queries
- SQL Server implementation
- permissions and operations
- late-course redesign

## Initial Case Narrative

Lakeside Tutoring Center offers tutoring sessions for students. Staff members track students, tutors, subjects, scheduled sessions, session notes, invoices, and payments.

Each student may attend many sessions. Each tutor may lead many sessions. Each session is for one subject. Tutors may be qualified for many subjects, and each subject may be taught by many tutors. Students may request help in many subjects, and each subject may be requested by many students.

After a completed session, staff may record one session note. Billing staff create invoices for completed sessions and record payments against invoices.

## Initial Design Goal

The initial design is intentionally simple. It uses separate tables for major business objects so students can follow the database workflow without abstraction overload.

## Initial Table Set

Use this as the simple early-course model:

- `Student`
- `Tutor`
- `Subject`
- `TutorSubject`
- `StudentSubjectRequest`
- `Session`
- `SessionNote`
- `Invoice`
- `Payment`
- `Staff`

## Relationship Patterns

| Pattern | Relationship |
|---|---|
| `1:M` | one `Student` may attend many `Session` records |
| `1:M` | one `Tutor` may lead many `Session` records |
| `1:M` | one `Subject` may appear in many `Session` records |
| `M:N` | `Tutor` and `Subject` through `TutorSubject` |
| `M:N` | `Student` and `Subject` through `StudentSubjectRequest` |
| optional dependent record | one `Session` may have zero or one `SessionNote` |
| `1:M` | one `Staff` member may create many `Invoice` records |
| `1:M` | one `Invoice` may have many `Payment` records |

## DBDD-Ready Table List

```text
Student(
    StudentID PK,
    FirstName,
    LastName,
    EmailAddress,
    GradeLevel,
    Active
)

Tutor(
    TutorID PK,
    FirstName,
    LastName,
    EmailAddress,
    HourlyRate,
    Active
)

Subject(
    SubjectCode PK,
    SubjectName
)

TutorSubject(
    TutorID PK/FK,
    SubjectCode PK/FK
)

StudentSubjectRequest(
    StudentID PK/FK,
    SubjectCode PK/FK,
    RequestedDate
)

Session(
    SessionID PK,
    StudentID FK,
    TutorID FK,
    SubjectCode FK,
    SessionDate,
    StartTime,
    Minutes,
    Status
)

SessionNote(
    SessionNoteID PK,
    SessionID FK,
    NoteText,
    FollowUpNeeded,
    CreatedAt
)

Staff(
    StaffID PK,
    FirstName,
    LastName,
    EmailAddress,
    StaffRole
)

Invoice(
    InvoiceID PK,
    StudentID FK,
    CreatedByStaffID FK,
    InvoiceDate,
    DueDate,
    TotalAmount,
    Status
)

Payment(
    PaymentID PK,
    InvoiceID FK,
    PaymentDate,
    PaymentAmount,
    PaymentMethod
)
```

## What This Case Teaches Well

- A clean business workflow from scheduling to billing.
- Required versus optional relationships.
- Many-to-many resolution through intersection tables.
- DBDD details such as PKs, FKs, nullability, and data types.
- SQL joins, grouping, views, controlled DML, and verification.
- Permission scenarios for tutors, staff, managers, and billing users.

## Later Redesign Opportunity

Later in the course, students can revisit this design and ask whether `Student`, `Tutor`, and `Staff` should remain separate person tables or move into a shared `User` and `Role` model.

The redesign should not be introduced early. It is more useful after students understand the simpler design and can judge what the redesign improves and what it complicates.
