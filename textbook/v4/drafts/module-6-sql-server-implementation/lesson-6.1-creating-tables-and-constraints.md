# Lesson 6.1: Creating Tables and Constraints

## Lesson Overview

In Module 5, you turned business requirements into an approved Database Design Diagram, or DBDD. In this lesson, you use that approved design to build real SQL Server tables and constraints.

This lesson is about implementation, not redesign. The DBDD already tells you which tables, columns, keys, data types, nullability rules, and relationships the database should have. Your job now is to express those approved decisions in SQL Server with `CREATE TABLE` and constraint definitions, then verify that the built schema still matches the design.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain DDL as the part of SQL used to build database structure
- translate an approved DBDD into dependency-aware `CREATE TABLE` statements
- implement `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`, and `DEFAULT` constraints where the design requires them
- explain why dependency order matters when building a schema
- detect where a built schema drifts from the approved DBDD
- verify that a completed schema matches the intended design before moving on to data work

## Key Terms

- `DDL`: Data Definition Language, the SQL used to create or change database structure
- `CREATE TABLE`: the SQL Server statement used to create a new table
- `constraint`: a rule SQL Server enforces on a column or table
- `primary key`: the constraint that identifies each row uniquely and does not allow `NULL`
- `foreign key`: the constraint that enforces a valid reference to a parent table
- `entity integrity`: the rule that each row must have a valid primary key
- `referential integrity`: the rule that child rows must reference valid parent rows when the design requires it
- `dependency-aware build order`: creating parent tables before child tables that reference them
- `schema drift`: a mismatch between the approved DBDD and the schema that was actually built

## Readings and Media

- Read this lesson from start to finish before writing the full build script.
- Keep your approved DBDD from Module 5 open while you work.
- Review [06-module-6-sql-server-implementation.md](../../modules-plan/06-module-6-sql-server-implementation.md) for the module blueprint.
- Review [06-design-object-naming-and-notation-conventions.md](../../06-design-object-naming-and-notation-conventions.md) for table and column naming expectations.
- Use your SQL Server environment so you can execute and verify the script as you go.

## Core Content

## 1. DDL Builds the Approved Structure

DDL is the part of SQL that defines database objects. In this lesson, the central DDL statement is `CREATE TABLE`.

That matters because Module 6 is not a fresh design exercise. You are implementing decisions that were already made in the DBDD:

- table names come from the DBDD
- column names come from the DBDD
- data types come from the DBDD
- `NULL` or `NOT NULL` comes from the DBDD
- PK, FK, and other constraint needs come from the DBDD

This is why the ER Diagram and the DBDD must stay distinct. The ER Diagram is conceptual. The DBDD is implementation-ready. When you write SQL Server DDL, the DBDD is your immediate authority.

## 2. Read the DBDD Before You Write SQL

Before you start typing, list the design decisions you must implement. A good pre-build checklist includes:

- each table name
- each column name
- each data type
- whether each column is required or optional
- the primary key for each table
- every foreign-key relationship
- any additional `UNIQUE`, `CHECK`, or `DEFAULT` requirements

This step reduces careless drift. Many schema mistakes do not come from complicated SQL. They come from skipping the design review and relying on memory.

## 3. Determine Build Order from Dependencies

A foreign key creates a dependency. If table `Section` references `Course`, then `Course` must exist before `Section` can be created with that foreign key.

Think in parent-child terms:

- a parent table is referenced by another table
- a child table holds the foreign key that points to the parent

That means build order is not a cosmetic preference. It is part of the procedure.

Use this rule:

1. create parent tables with no dependencies first
2. create child tables after the parent tables they reference
3. verify that every FK in the child points to an already created parent

## 4. Case Setup: Advising-Center Registration DBDD

Use this approved DBDD for the lesson case.

**Approved tables**

- `Student(StudentID, FirstName, LastName, Email, StartTerm)`
- `Course(CourseID, CourseCode, CourseTitle, Credits)`
- `Section(SectionID, CourseID, TermCode, SectionNumber, DeliveryMode, SeatsAvailable)`
- `Enrollment(EnrollmentID, StudentID, SectionID, EnrolledOn, StatusCode)`

**Approved implementation details**

- `StudentID`, `CourseID`, `SectionID`, and `EnrollmentID` are primary keys
- `Student.Email` must be unique
- `Course.CourseCode` must be unique
- `Course.Credits` must stay between `1` and `6`
- `Section.CourseID` references `Course.CourseID`
- `Section.SeatsAvailable` must be `0` or greater and defaults to `25`
- `Enrollment.StudentID` references `Student.StudentID`
- `Enrollment.SectionID` references `Section.SectionID`
- `Enrollment.EnrolledOn` defaults to the current date
- `Enrollment.StatusCode` must be `Enrolled`, `Waitlisted`, or `Dropped`

From that DBDD, the dependencies are:

- `Student`: no FK dependency in this case
- `Course`: no FK dependency in this case
- `Section`: depends on `Course`
- `Enrollment`: depends on `Student` and `Section`

So a valid build order is:

1. `Student`
2. `Course`
3. `Section`
4. `Enrollment`

`Student` and `Course` can switch places because neither depends on the other. What cannot change is that `Section` must come after `Course`, and `Enrollment` must come after both of its parent tables.

## 5. Translate One Table from DBDD to SQL

Suppose the DBDD shows this approved design for `Course`:

- `CourseID` integer, required, PK
- `CourseCode` `varchar(12)`, required, unique
- `CourseTitle` `varchar(100)`, required
- `Credits` tiny integer, required, must stay between `1` and `6`

That becomes:

```sql
CREATE TABLE dbo.Course
(
    CourseID int NOT NULL,
    CourseCode varchar(12) NOT NULL,
    CourseTitle varchar(100) NOT NULL,
    Credits tinyint NOT NULL,
    CONSTRAINT PK_Course PRIMARY KEY (CourseID),
    CONSTRAINT UQ_Course_CourseCode UNIQUE (CourseCode),
    CONSTRAINT CHK_Course_Credits CHECK (Credits BETWEEN 1 AND 6)
);
```

You should be able to trace each line back to the design:

- the table name comes from the DBDD
- the columns and data types come from the DBDD
- `NOT NULL` comes from the requiredness decision
- the primary key implements row identity
- the unique constraint enforces the approved business rule for `CourseCode`
- the check constraint enforces the approved value range for `Credits`

## 6. Full Build Example for the Case

```sql
CREATE TABLE dbo.Student
(
    StudentID int NOT NULL,
    FirstName varchar(40) NOT NULL,
    LastName varchar(40) NOT NULL,
    Email varchar(120) NOT NULL,
    StartTerm char(6) NOT NULL,
    CONSTRAINT PK_Student PRIMARY KEY (StudentID),
    CONSTRAINT UQ_Student_Email UNIQUE (Email)
);

CREATE TABLE dbo.Course
(
    CourseID int NOT NULL,
    CourseCode varchar(12) NOT NULL,
    CourseTitle varchar(100) NOT NULL,
    Credits tinyint NOT NULL,
    CONSTRAINT PK_Course PRIMARY KEY (CourseID),
    CONSTRAINT UQ_Course_CourseCode UNIQUE (CourseCode),
    CONSTRAINT CHK_Course_Credits CHECK (Credits BETWEEN 1 AND 6)
);

CREATE TABLE dbo.Section
(
    SectionID int NOT NULL,
    CourseID int NOT NULL,
    TermCode char(6) NOT NULL,
    SectionNumber varchar(10) NOT NULL,
    DeliveryMode varchar(20) NOT NULL,
    SeatsAvailable int NOT NULL
        CONSTRAINT DF_Section_SeatsAvailable DEFAULT (25),
    CONSTRAINT PK_Section PRIMARY KEY (SectionID),
    CONSTRAINT FK_Section_Course FOREIGN KEY (CourseID)
        REFERENCES dbo.Course (CourseID),
    CONSTRAINT CHK_Section_SeatsAvailable CHECK (SeatsAvailable >= 0)
);

CREATE TABLE dbo.Enrollment
(
    EnrollmentID int NOT NULL,
    StudentID int NOT NULL,
    SectionID int NOT NULL,
    EnrolledOn date NOT NULL
        CONSTRAINT DF_Enrollment_EnrolledOn DEFAULT (CAST(GETDATE() AS date)),
    StatusCode varchar(12) NOT NULL,
    CONSTRAINT PK_Enrollment PRIMARY KEY (EnrollmentID),
    CONSTRAINT FK_Enrollment_Student FOREIGN KEY (StudentID)
        REFERENCES dbo.Student (StudentID),
    CONSTRAINT FK_Enrollment_Section FOREIGN KEY (SectionID)
        REFERENCES dbo.Section (SectionID),
    CONSTRAINT CHK_Enrollment_StatusCode
        CHECK (StatusCode IN ('Enrolled', 'Waitlisted', 'Dropped'))
);
```

This script does more than create objects. It enforces design decisions.

- `PRIMARY KEY` protects identity
- `FOREIGN KEY` protects valid relationships
- `UNIQUE` protects fields that should not be duplicated
- `CHECK` protects allowed values and ranges
- `DEFAULT` provides approved fallback values

## 7. Why Dependency Order and Constraints Matter Operationally

Dependency order matters because implementation is cumulative. If you create a child table before the parent table it references, SQL Server cannot enforce the relationship correctly at build time.

Constraints matter because operations depend on them later:

- without a PK, duplicate rows can make matching and updates unreliable
- without an FK, child rows can point to records that do not exist
- without `NOT NULL`, required data can be left missing
- without `CHECK`, invalid status codes or impossible quantities can enter the system
- without `UNIQUE`, supposedly distinct business identifiers can collide

In the advising-center case, missing constraints could affect registration, seat availability, advising reports, and follow-up work. A technically running schema can still misrepresent the real operation if the design rules are not enforced.

That is why constraints are practical expressions of accountability. They help the database remain faithful to the approved business rules instead of silently accepting inaccurate structure.

## 8. Build Failure Example

Suppose you try to create `Enrollment` before `Student` and `Section`:

```sql
CREATE TABLE dbo.Enrollment
(
    EnrollmentID int NOT NULL,
    StudentID int NOT NULL,
    SectionID int NOT NULL,
    CONSTRAINT PK_Enrollment PRIMARY KEY (EnrollmentID),
    CONSTRAINT FK_Enrollment_Student FOREIGN KEY (StudentID)
        REFERENCES dbo.Student (StudentID),
    CONSTRAINT FK_Enrollment_Section FOREIGN KEY (SectionID)
        REFERENCES dbo.Section (SectionID)
);
```

The problem is not just that the script is "out of order." The problem is structural:

- `Enrollment` is a child table
- `Student` and `Section` are parent tables for its foreign keys
- those parent tables must exist first

The fix is to reorder the build so that the referenced parent tables are created before the dependent child table.

## 9. Verification Is Part of the Procedure

A schema is not verified just because SQL Server accepted the script. You still need to compare the built result to the approved DBDD.

Use a post-build verification checklist:

1. confirm that every required table exists
2. confirm that each table has the required columns
3. confirm that each column uses the intended data type
4. confirm which columns are `NOT NULL`
5. confirm the primary key on each table
6. confirm every foreign key and its parent table reference
7. confirm any `UNIQUE`, `CHECK`, and `DEFAULT` rules from the DBDD
8. note any drift before moving to data loading

In SQL Server, you can use Object Explorer, script inspection, or system metadata queries to perform this audit. What matters for this lesson is the reasoning: compare the built schema to the approved design explicitly.

## 10. Schema Drift Audit Example

Read this version of `Section` and compare it to the approved DBDD:

```sql
CREATE TABLE dbo.Section
(
    SectionID int NOT NULL,
    CourseID int NULL,
    TermCode char(6) NOT NULL,
    SectionNumber varchar(10) NOT NULL,
    DeliveryMode varchar(20) NOT NULL,
    SeatsAvailable int NULL,
    CONSTRAINT PK_Section PRIMARY KEY (SectionID)
);
```

This script may execute, but it drifts from the approved design in several ways:

- `CourseID` is nullable even though the section must belong to a course
- the foreign key from `Section.CourseID` to `Course.CourseID` is missing
- `SeatsAvailable` is nullable instead of required
- the default of `25` is missing
- the check that prevents negative seat counts is missing

This is the kind of audit work Module 6 expects. Running is not the same as matching the design.

## Examples and Case

Use the advising-center registration case to practice three connected habits:

- trace each SQL choice back to the approved DBDD
- order the build script by parent-child dependency
- verify the built schema instead of trusting execution alone

Operationally, this case is about accurate registration and trustworthy reporting. If the schema allows impossible enrollments or unbounded status values, the database can distort what staff think is happening.

## Guided Practice

## Practice 1: Mark the DBDD Decisions

For the advising-center case, label each item as one of these:

- table definition
- requiredness rule
- primary key
- foreign key
- other constraint

Then explain which of those items must be visible in the final SQL script.

## Practice 2: Rebuild the Order

A teammate proposes this sequence:

1. `Enrollment`
2. `Section`
3. `Course`
4. `Student`

Rewrite the order so it matches the dependencies, then explain why your order is safer.

## Practice 3: Detect the Drift

Use the flawed `Section` table shown earlier. Identify every place where the built schema has drifted from the approved DBDD, and name one likely operational risk created by that drift.

## Practice 4: Constraint Judgment

In the advising-center case, which single constraint do you think matters most for trustworthy operations:

- a primary key
- a foreign key
- a unique constraint
- a check constraint
- a default constraint

Choose one and explain your answer in both technical and business terms.

## What to Do

Complete the lesson in this order:

1. review the approved DBDD from Module 5
2. list the tables, columns, keys, and additional constraints
3. determine the dependency-aware build order
4. write the `CREATE TABLE` statements
5. execute the build script in SQL Server
6. diagnose and fix any failures
7. verify the final schema against the DBDD
8. write a short note explaining any corrected drift you found

## Assignments

## Assignment 1: DBDD-to-DDL Build

Write the full table-creation script for the advising-center registration case.

Your script must:

- create the tables in a dependency-aware order
- implement the required primary keys and foreign keys
- implement the required `UNIQUE`, `CHECK`, and `DEFAULT` constraints
- use naming consistent with course conventions

## Assignment 2: Drift Audit

Review a provided flawed build snippet and identify where the schema does not match the approved DBDD. Explain why each mismatch matters.

## Assignment 3: Constraint Reflection

Answer this prompt in a short paragraph:

Which constraint in this case matters most for trustworthy operations, and how does it protect accountability or business-rule fidelity?

## Deliverables

- one SQL script containing the full dependency-aware table build
- one short verification checklist or audit note comparing the built schema to the DBDD
- one short response to the trustworthy-operations constraint prompt

## Project Checkpoint or Module Connection

This lesson connects directly to Module 6's build-and-verify audit pattern. Before moving to Lesson 6.2, you should be able to answer two questions:

- Does the built schema match the approved DBDD?
- Which enforced rule is most important for trustworthy operation in this case, and why?

If you cannot answer those questions clearly, the implementation is not ready for data loading.

## Wrap-Up

Lesson 6.1 turns the approved DBDD into executable SQL Server structure. The key habits are straightforward but non-negotiable:

- build from the approved design
- create tables in dependency-aware order
- enforce business rules with constraints
- verify the built schema before trusting it

Those habits carry directly into Lesson 6.2, where the data changes must respect the structure you created here.
