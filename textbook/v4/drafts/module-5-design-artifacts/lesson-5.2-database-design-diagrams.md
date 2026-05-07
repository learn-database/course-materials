# Lesson 5.2: Database Design Diagrams

## Lesson overview

In Lesson 5.1, you refined a conceptual ERD and protected it from implementation clutter. In this lesson, you build the next artifact in the workflow: the Database Design Diagram, or `DBDD`.

The `DBDD` has a different job from the conceptual ERD. The ERD explains business structure. The `DBDD` makes that structure build-ready by showing tables, columns, primary keys, foreign keys, data types, nullability, and other implementation-ready decisions.

## Lesson outcomes

By the end of this lesson, you should be able to:

- explain why the `DBDD` is a separate artifact from the conceptual ERD
- convert conceptual entities and relationships into tables and keys
- choose `PK` and `FK` structures that trace back to business meaning
- choose first-pass SQL Server data types from the kind of value each column stores
- decide `NULL` versus `NOT NULL` from optionality and required facts
- classify details as `ERD-only`, `DBDD-only`, `both`, or `neither`
- explain how design precision protects the organization from hidden operational errors

## Key terms

- `Database Design Diagram (DBDD)`: an implementation-ready design artifact that shows tables, columns, keys, data types, nullability, and other build-ready structural details
- `table`: the implementation structure that stores rows for one business subject or one resolved many-to-many relationship
- `column`: a named field within a table
- `primary key (PK)`: the column or column set that uniquely identifies each row
- `foreign key (FK)`: the column or column set that references a primary key in another table
- `data type`: the SQL Server definition that controls what kind of value a column may store
- `nullability`: the decision about whether a column may contain `NULL`
- `intersection table`: a table used to resolve a many-to-many relationship into buildable relational structure
- `entity integrity`: the rule that each row must be uniquely identifiable
- `referential integrity`: the rule that foreign-key values must match valid parent rows when the relationship requires them

## Readings and media

- Read this lesson page from start to finish before drafting your `DBDD`.
- Review your refined conceptual ERD from Lesson 5.1.
- Review `textbook/v4/06-design-object-naming-and-notation-conventions.md`, especially the sections on table names, column names, `PK`/`FK` naming, and ERD-versus-DBDD boundaries.
- Open your diagramming tool and prepare a clean workspace for a separate implementation-ready artifact.

## Core content

### 1. The `DBDD` is not the ERD with extra labels

Lesson 5.1 established the boundary: the conceptual ERD shows business meaning; the DBDD shows how to build it. This lesson focuses entirely on the DBDD side of that boundary.

The conceptual ERD answers business-facing questions:

- What does the organization track?
- How are those things related?
- Which attributes matter conceptually?
- What are the cardinality and optionality rules?

The `DBDD` answers build-ready questions:

- What tables must exist?
- What is the primary key of each table?
- Where do foreign keys belong?
- What data type fits each column?
- Which columns are `NULL` or `NOT NULL`?

That is why these are separate artifacts. The ERD remains conceptual. The `DBDD` becomes implementation-ready.

Use this boundary as a quick test:

| Detail | Conceptual ERD | DBDD |
| --- | --- | --- |
| Entities or tables being tracked | yes, as entities | yes, as tables |
| Relationships and business meaning | yes | yes, carried into table structure |
| Cardinality and optionality | yes | implied by keys and nullability decisions |
| `PK` labels | no | yes |
| `FK` labels | no | yes |
| SQL Server data types | no | yes |
| `NULL` or `NOT NULL` | no | yes |

The boundary matters because each artifact communicates with a different purpose. A clean ERD helps people reason about the business structure. A clean `DBDD` helps people build the database correctly.

### 2. Start with conceptual meaning, then convert it into tables

What Lesson 5.1 kept out of the conceptual ERD — primary keys, foreign keys, data types, and nullability — is exactly what the DBDD must include. The two artifacts are complementary: one shows business meaning, the other shows how to build it.

Do not start the `DBDD` by guessing table names out of nowhere. Start with a reviewed conceptual ERD.

A first-pass conversion usually follows this sequence:

1. convert each conceptual entity into a table
2. carry forward the relevant attributes as columns
3. assign a primary key to each table
4. place foreign keys where the conceptual relationships need them
5. resolve many-to-many relationships with intersection tables
6. assign data types and nullability from business meaning

You first saw intersection tables as a normalization repair in Lesson 4.3. Here they appear as fully specified DBDD tables — with their own primary key, foreign key columns, data types, and nullability decisions.

The `DBDD` adds implementation detail, but it should not change the underlying business meaning.

If the conceptual ERD says one `Patient` can have many `Appointment` records, the `DBDD` should preserve that rule. It should now preserve it through table structure and foreign keys rather than through a relationship line alone.

### 3. `PK` choices should reflect stable row identity

Every table in a `DBDD` needs a clear primary key because the database needs a reliable way to identify each row.

Choose a `PK` by asking what should distinguish one row from another in a stable way.

Examples:

- `Patient.PatientID` identifies one patient record
- `Provider.ProviderID` identifies one provider record
- `Invoice.InvoiceID` identifies one invoice
- `AppointmentService(AppointmentID, ServiceID)` can use a composite key when the pair is what must be unique

A good `PK` is not just a label you attach because every table needs one. It is the design decision that makes row identity explicit.

### 4. `FK` choices should carry relationships into implementation

A foreign key is how the `DBDD` carries a conceptual relationship into table structure.

In a one-to-many relationship, the foreign key usually belongs on the many side because those rows need a way to point back to the related parent row.

Example:

- one `Patient` can have many `Appointment` records
- each `Appointment` belongs to one `Patient`
- therefore `Appointment` needs `PatientID` as an `FK`

This is not mechanical decoration. The `FK` belongs there because the business meaning requires each appointment row to be tied to the correct patient row.

### 5. Data types come from the kind of fact being stored

Data types belong in the `DBDD` because implementation-ready design must say what kind of value each column may store.

Choose the data type by asking what the value means.

Examples:

- `DateOfBirth` should use `DATE` because it stores a date
- `StandardFee` should use `DECIMAL(10,2)` because it stores money-like amounts that require fixed precision
- `Phone` should usually use `VARCHAR(20)` because it is an identifier-like text value, not a number for arithmetic
- `IsActive` can use `BIT` because it records a yes-or-no status

Do not choose data types by appearance alone. A phone number may look numeric, but the business usually needs to store formatting characters, leading zeros, or extension notation. That makes it a text value in the design.

### 6. Nullability comes from business meaning, not habit

In Lesson 3.2 you classified participation as optional or required. Nullability is the implementation-level expression of that judgment — but the translation is not automatic. Optional participation tells you the business rule; nullability is how the DBDD enforces it, and the two do not always map one-to-one.

`NOT NULL` means every row must have a value in that column.

`NULL` means the design allows the value to be absent in a legitimate business condition.

Use the conceptual ERD and the business rules to make that decision.

Examples:

- if every `Appointment` must belong to one `Patient`, then `Appointment.PatientID` should be `NOT NULL`
- if an invoice may remain unpaid for a while, then `Invoice.PaidDate` may be `NULL`
- if a patient phone number is useful but not always known, then `Patient.Phone` may be `NULL`

Be careful with a common mistake: optional participation in the conceptual model does not always mean a nullable foreign key in the child table.

Example:

- a `Session` may have zero or one `SessionNote`
- this does not mean `SessionNote.SessionID` should be `NULL`
- it means some session rows will have no related note row yet
- if a `SessionNote` row exists, it must still belong to a session

So `SessionNote.SessionID` should still be `NOT NULL`.

That is why nullability decisions must be traced back to actual business meaning and actual table structure, not to a memorized shortcut.

### 7. Precision protects against hidden operational errors

Implementation-ready detail is not busywork. It is how the design prevents future confusion.

Consider these hidden error risks:

- a missing `FK` can allow records that refer to a patient, provider, or invoice that does not actually exist
- a weak data type can allow inconsistent values that break reports or sorting
- a careless `NULL` choice can make required data look optional
- a missing intersection table can force repeated values or duplicate combinations that create billing and scheduling confusion

Clear design helps coworkers, customers, staff, and decision-makers work with records they can understand and trust. Precision here is not diagram neatness — it is how the design prevents operational errors before they are built in.

### 8. A quick checklist for `DBDD` review

Before you submit a `DBDD`, ask:

- does every table trace back to a conceptual entity or a resolved many-to-many relationship?
- does every `PK` clearly identify rows?
- does every `FK` exist for a business reason I can explain?
- do the data types match the meaning of the values stored?
- do `NULL` and `NOT NULL` choices reflect real optionality and required facts?
- is this still a separate implementation-ready artifact rather than a cluttered conceptual ERD?

## Examples and case

### Cedar Valley Clinic conceptual summary

Assume the conceptual ERD has already been reviewed. It includes these business objects and relationships:

- `Patient`
- `Provider`
- `Appointment`
- `Service`
- `Invoice`
- one `Patient` can have many `Appointment` records
- one `Provider` can lead many `Appointment` records
- one `Appointment` can include many `Service` records
- one `Service` can appear in many `Appointment` records over time
- one `Appointment` produces one `Invoice`

### Worked `DBDD` conversion

| Table | Key structure | Selected columns | Why the choice fits the business meaning |
| --- | --- | --- | --- |
| `Patient` | `PatientID` `PK` | `FirstName VARCHAR(50) NOT NULL`, `LastName VARCHAR(50) NOT NULL`, `DateOfBirth DATE NOT NULL`, `Phone VARCHAR(20) NULL` | Names and birth date are required to identify the patient correctly. Phone may be missing when intake is incomplete. |
| `Provider` | `ProviderID` `PK` | `ProviderName VARCHAR(100) NOT NULL`, `LicenseNumber VARCHAR(30) NOT NULL` | The row needs a stable key. License number is a meaningful fact that should likely be unique. |
| `Appointment` | `AppointmentID` `PK`, `PatientID` `FK`, `ProviderID` `FK` | `ScheduledStart DATETIME2 NOT NULL`, `CheckInTime DATETIME2 NULL`, `AppointmentStatus VARCHAR(20) NOT NULL` | An appointment must belong to a patient and provider, so both foreign keys are required. Check-in time may be unknown until arrival. |
| `Service` | `ServiceID` `PK` | `ServiceName VARCHAR(100) NOT NULL`, `StandardFee DECIMAL(10,2) NOT NULL`, `IsActive BIT NOT NULL` | Fee needs exact numeric precision. Active status is naturally yes-or-no. |
| `AppointmentService` | `AppointmentID` `PK/FK`, `ServiceID` `PK/FK` | `Quantity INT NOT NULL`, `LineCharge DECIMAL(10,2) NOT NULL` | The table resolves the many-to-many relationship and makes each appointment-service pairing explicit. |
| `Invoice` | `InvoiceID` `PK`, `AppointmentID` `FK` | `InvoiceDate DATE NOT NULL`, `TotalAmount DECIMAL(10,2) NOT NULL`, `PaidDate DATE NULL` | The invoice must point to its appointment. `PaidDate` can be empty until payment happens. |

### What this example shows

- the `DBDD` keeps the same business meaning as the conceptual ERD
- `AppointmentService` exists because the many-to-many relationship must become buildable table structure
- each `PK`, `FK`, data type, and nullability choice has a business reason
- implementation detail is added in the `DBDD` without pushing that detail backward into the conceptual ERD

## Guided practice

### Guided practice 1: convert the structure

Use the Cedar Valley Clinic case and answer these questions.

1. Which conceptual entities become first-pass tables?
2. Which relationship requires an intersection table?
3. Which table should receive `PatientID` as a foreign key, and why?
4. Why is `Phone` better as `VARCHAR(20)` than as `INT`?
5. Why can `PaidDate` be `NULL` while `InvoiceDate` should be `NOT NULL`?

### Guided practice 2: classify the detail

Classify each item as `ERD-only`, `DBDD-only`, `both`, or `neither`. Try it yourself before checking the model answer.

| Detail | Your classification |
| --- | --- |
| `Patient` as a tracked business object |  |
| one `Patient` can have many `Appointment` records |  |
| `Appointment.PatientID` marked as an `FK` |  |
| `StandardFee DECIMAL(10,2)` |  |
| `PaidDate` may be unknown until payment occurs |  |
| `Invoice.PaidDate NULL` |  |
| the color of the appointment screen button |  |

Model answer:

| Detail | Classification | Why |
| --- | --- | --- |
| `Patient` as a tracked business object | `both` | The business object appears conceptually in the ERD and as a table in the `DBDD`. |
| one `Patient` can have many `Appointment` records | `both` | The relationship is stated conceptually in the ERD and carried into the `DBDD` through `FK` structure. |
| `Appointment.PatientID` marked as an `FK` | `DBDD-only` | Foreign-key notation is implementation-ready detail. |
| `StandardFee DECIMAL(10,2)` | `DBDD-only` | SQL Server data types belong only in the `DBDD`. |
| `PaidDate` may be unknown until payment occurs | `both` | The business meaning can be discussed conceptually and then implemented through nullability. |
| `Invoice.PaidDate NULL` | `DBDD-only` | `NULL` versus `NOT NULL` is implementation-ready detail. |
| the color of the appointment screen button | `neither` | Interface styling is outside both the conceptual ERD and the `DBDD`. |

## What to do

1. Reopen your reviewed conceptual ERD from Lesson 5.1.
2. Convert each entity into a first-pass table.
3. Resolve any many-to-many relationships with intersection tables.
4. Assign a `PK` to each table.
5. Add `FK` columns that carry the conceptual relationships into the design.
6. Choose first-pass SQL Server data types for each column.
7. Mark columns `NULL` or `NOT NULL` using business meaning and requiredness.
8. Review your draft with the `DBDD` checklist in this lesson.

## Assignments

- Build a `DBDD` for the reviewed case used in your course work.
- Write a short rationale that explains:
  - one detail that belongs in the `DBDD` but not in the conceptual ERD
  - one `PK` choice
  - one `FK` choice
  - one data type choice
  - one `NULL` or `NOT NULL` choice
- Complete a short artifact-boundary classification check using `ERD-only`, `DBDD-only`, `both`, and `neither`.

## Deliverables

- one Database Design Diagram
- one short written design rationale
- one completed artifact-boundary classification activity or check

## Project checkpoint or module connection

Before you submit, answer this question in one or two sentences:

Where does design precision in your `DBDD` most directly protect people, staff, customers, or records from confusion, loss, or inaccurate reporting?

That question matters because Module 5 is not only about drawing the artifact. It is about knowing whether the right information is in the right artifact and whether the design is precise enough to deserve trust.

## Wrap-up

The `DBDD` is the first implementation-ready artifact in the database workflow. Its job is to turn conceptual meaning into tables, keys, data types, and requiredness decisions that a database builder can actually use. If you keep the boundary clear, both artifacts improve: the ERD remains conceptually clean, and the `DBDD` becomes specific enough to prevent hidden design mistakes before implementation starts.
