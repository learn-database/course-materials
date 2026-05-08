# Lesson 4.3: Normalization and Design Repair

## Lesson Overview

This lesson treats normalization as design repair. The goal is not to memorize
labels and then split a relation by habit. The goal is to diagnose what is weak
in a design, connect that weakness to business consequences, compare competing
decompositions, and defend the one that preserves the real meaning of the data.

You will use the functional dependency and key reasoning from Lessons 4.1 and
4.2 to identify anomalies, explain why they matter, and repair a weak relation
without losing the business story it is supposed to represent.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- identify insert, update, and delete anomalies in a weak relation
- explain the business consequences of those anomalies
- distinguish partial dependency, transitive dependency, and BCNF determinant
  problems
- compare a sound decomposition with a weak one and explain which is more
  defensible
- explain when a tidy-looking answer still breaks the intended business meaning
- decompose a weak relation into stronger relations and justify each repair step
- distinguish normalized operational design from justified denormalization for
  read-only or read-mostly reporting scenarios
- connect design repair to stewardship of time, resources, and trust in a
  project scenario

## Key Terms

- `anomaly`: a data problem caused by weak structure rather than a single typing
  mistake
- `insert anomaly`: difficulty adding one fact without inventing or repeating
  another fact
- `update anomaly`: repeated storage of the same fact, which creates
  contradiction risk
- `delete anomaly`: loss of one fact when deleting another
- `decomposition`: splitting a weak relation into clearer relations
- `partial dependency`: a non-key attribute depending on only part of a
  composite key
- `transitive dependency`: a non-key attribute depending on another non-key
  attribute
- `normal form`: a checkpoint that describes what kind of structural weakness
  has been removed
- `BCNF`: a checkpoint that asks whether every determinant is a superkey
- `intersection table`: a relation that resolves a many-to-many relationship
  and stores any relationship-level facts
- `denormalization`: intentionally storing repeated or derived data in a less
  normalized structure for a justified purpose, usually reporting or analytics
- `data warehouse`: a reporting-oriented database built from operational
  sources and commonly used for read-only or read-mostly analysis

## Readings And Media

- Read this lesson carefully from start to finish.
- Keep
  [06-design-object-naming-and-notation-conventions.md](../../06-design-object-naming-and-notation-conventions.md)
  available if you want a quick reminder about relation-schema naming and
  notation.
- Review the Module 4 plan in
  [04-module-4-design-logic.md](../../modules-plan/04-module-4-design-logic.md)
  if you want to see how this lesson supports the module judgment task.
- No separate video or external media is required.

## Core Content

### 1. Start With The Business Meaning Before The Labels

Normalization begins with a question: what does one row mean?

Lessons 4.1 and 4.2 used this question to ground dependency and key reasoning. Normalization uses it the same way: a decomposition is only valid if every resulting table still has a clear, recoverable answer to what one row represents.

Use this weak relation:

`EnrollmentRecord(StudentID, SectionID, StudentName, CourseID, InstructorID, InstructorOffice, Term, FinalGrade)`

Business meaning:

One row records one student's enrollment in one section.

That one row is carrying several different levels of fact:

- student fact: `StudentName`
- section facts: `CourseID`, `InstructorID`, `Term`
- instructor fact: `InstructorOffice`
- enrollment fact: `FinalGrade`

The design is weak because different kinds of facts are being stored together.
That is what creates anomaly risk.

### 2. Use A Working FD Set That Makes The Repair Clear

For this lesson, use this smaller working set of functional dependencies:

- `StudentID -> StudentName`
- `SectionID -> CourseID, InstructorID, Term`
- `InstructorID -> InstructorOffice`
- `StudentID, SectionID -> FinalGrade`

The candidate key for the original relation is `StudentID, SectionID`.

This working set is useful because each dependency points to one fact owner:

- student-level determinant
- section-level determinant
- instructor-level determinant
- enrollment-level determinant

You are not changing the meaning of the design by writing a smaller working set.
You are making the reasoning easier to defend.

### 3. Anomalies Are Business Problems, Not Just Vocabulary

Before naming a normal form, identify what can go wrong.

#### Insert Anomaly

Suppose a new instructor is hired and assigned an office before being assigned
to any section with current enrollments. In the weak relation, there is no
clean way to store the office fact by itself. The business must either invent a
fake enrollment row or wait until unrelated data exists.

Business consequence:

Scheduling or staffing records may stay incomplete because the design has no
honest place to store the instructor fact.

#### Update Anomaly

Suppose `InstructorOffice` changes. Because the same office value may appear in
many enrollment rows, one change may require many edits. If even one row is
missed, advising or scheduling staff may see conflicting office assignments.

Business consequence:

The database stops telling one consistent story, which damages trust in reports
and wastes time on rework.

#### Delete Anomaly

Suppose the last student drops a section. If the final enrollment row is
deleted, the organization may also lose the section's `CourseID`, `InstructorID`,
or `Term` facts if those facts existed only inside enrollment rows.

Business consequence:

Deleting an enrollment may accidentally erase information the registrar or
department still needs.

Anomalies matter because they expose how weak design turns routine work into
contradiction, waste, or data loss.

### 4. What 1NF, 2NF, 3NF, And BCNF Each Address

Keep the checkpoints separate. Each one answers a different question.

#### 1NF

`1NF` asks whether values are atomic and whether repeating groups have been
removed.

Weak example:

`EnrollmentDraft(StudentID, StudentName, SectionList)`

If `SectionList` stores several section values in one column, the design is not
yet ready for clean relational reasoning.

1NF addresses this problem:

- repeating groups
- packed lists
- non-atomic values

#### 2NF

`2NF` matters when the key is composite.

In `EnrollmentRecord`, the key is `StudentID, SectionID`. A 2NF problem exists
when a non-key attribute depends on only part of that key.

Examples:

- `StudentID -> StudentName`
- `SectionID -> CourseID, InstructorID, Term`

2NF addresses this problem:

- non-key facts depending on only part of a composite key

#### 3NF

`3NF` asks whether a non-key attribute depends on another non-key attribute.

After a 2NF repair, imagine this remaining relation:

`Section(SectionID, CourseID, InstructorID, InstructorOffice, Term)`

Here:

- `SectionID -> InstructorID`
- `InstructorID -> InstructorOffice`

That means `InstructorOffice` depends on `SectionID` through another non-key
attribute.

3NF addresses this problem:

- non-key facts depending on other non-key facts

#### BCNF

`BCNF` asks whether every determinant is a superkey.

A relation can pass 3NF and still fail BCNF. Use this contrast case:

`AdvisingAssignment(StudentID, InstructorID, ProgramCode)`

Dependencies:

- `StudentID, InstructorID -> ProgramCode`
- `InstructorID -> ProgramCode`

Candidate keys:

- `StudentID, InstructorID`
- `StudentID, ProgramCode`

This can pass 3NF because `ProgramCode` is a prime attribute. It still fails
BCNF because `InstructorID` is a determinant but not a superkey.

BCNF addresses this problem:

- a non-superkey determinant still controlling attributes

### 5. Repair The Main Relation Step By Step

Start with:

`EnrollmentRecord(StudentID, SectionID, StudentName, CourseID, InstructorID, InstructorOffice, Term, FinalGrade)`

#### Step 1: Remove Partial Dependencies

Move the student fact to a student relation:

- `Student(StudentID, StudentName)`

Move the section facts together:

- `Section(SectionID, CourseID, InstructorID, InstructorOffice, Term)`

Keep the enrollment fact with the whole key:

- `Enrollment(StudentID, SectionID, FinalGrade)`

This repair addresses the 2NF problem because `StudentName` and the section
facts no longer repeat across the many combinations of `StudentID` and
`SectionID`.

#### Step 2: Remove The Transitive Dependency

Inside `Section`, the office fact still belongs to the instructor determinant.
Move it to its own relation:

- `Instructor(InstructorID, InstructorOffice)`
- `Section(SectionID, CourseID, InstructorID, Term)`

Now the main repaired set is:

- `Student(StudentID, StudentName)`
- `Instructor(InstructorID, InstructorOffice)`
- `Section(SectionID, CourseID, InstructorID, Term)`
- `Enrollment(StudentID, SectionID, FinalGrade)`

#### Step 3: Recheck The Meaning

Ask whether each relation now stores one coherent kind of fact:

- `Student` stores student identity facts
- `Instructor` stores instructor facts
- `Section` stores section facts
- `Enrollment` stores relationship facts about one student in one section

That is a defensible repair because the design is cleaner and the original row
meaning is still recoverable.

### 6. Compare Better And Worse Decompositions

Do not assume that every decomposition is good just because it produces more
tables.

#### Sound Decomposition

- `Student(StudentID, StudentName)`
- `Instructor(InstructorID, InstructorOffice)`
- `Section(SectionID, CourseID, InstructorID, Term)`
- `Enrollment(StudentID, SectionID, FinalGrade)`

Why it is sound:

- facts move to the determinant that owns them
- update risk is reduced
- the meaning "one student enrolled in one section" is preserved in
  `Enrollment`

#### Weak But Tidy-Looking Decomposition

- `Student(StudentID, StudentName)`
- `Section(SectionID, CourseID, InstructorID, Term, InstructorOffice)`
- `CourseEnrollment(StudentID, CourseID, FinalGrade)`

Why it looks tidy:

- each table appears shorter
- `FinalGrade` appears to stay in an enrollment-style table

Why it is weak:

- `InstructorOffice` still repeats inside `Section`, so the office update
  anomaly remains
- `CourseEnrollment(StudentID, CourseID, FinalGrade)` changes the business
  meaning from section enrollment to course enrollment
- if a course has two sections in the same term, the design no longer tells you
  which section the student actually took

This is the kind of answer you must reject. It looks organized, but it breaks
the intended meaning of the original relation.

### 7. Decomposition Must Preserve Meaning, Not Just Reduce Redundancy

A stronger design does more than reduce repetition. It also preserves the facts
the business actually cares about.

That means every proposed repair should answer two questions:

1. What anomaly or dependency problem does this split remove?
2. What row-level business meaning must still be recoverable afterward?

In an AI-available workflow, this matters even more. An AI tool may generate a
tidy decomposition quickly, but you still have to verify that it keeps the
correct business meaning. A polished answer is not enough.

### 8. When Denormalization Is A Deliberate Reporting Choice

Normalization is the usual goal for an operational database. Operational
databases support daily work: scheduling, enrollment, billing, tutoring records,
case notes, inventory changes, and other transactions that must be inserted,
updated, and deleted accurately.

Denormalization is different. `Denormalization` means intentionally storing some
repeated or derived data in a design that is less normalized than the
transactional source. That can be legitimate, but only when the purpose changes.

The most common legitimate setting is a reporting or data warehousing scenario.
A data warehouse is often built from operational systems so managers can run
reports, dashboards, historical comparisons, and trend analysis without
disrupting daily transaction work. These reporting databases are usually
read-only or read-mostly for the people using them. Data is loaded, refreshed,
or rebuilt through controlled processes rather than edited one transaction at a
time by normal users.

That difference matters. In an operational database, repeated facts increase
update-anomaly risk because users keep changing live data. In a reporting
database, repeated facts may be accepted because the design is optimized for
fast, understandable reports, and the refresh process controls how repeated
values are produced.

For example, a normalized operational design might store:

- `Student(StudentID, StudentName)`
- `Section(SectionID, CourseID, InstructorID, Term)`
- `Instructor(InstructorID, InstructorOffice)`
- `Enrollment(StudentID, SectionID, FinalGrade)`

A reporting table might intentionally flatten some of those facts:

`EnrollmentReport(StudentID, StudentName, SectionID, CourseID, Term, InstructorID, InstructorOffice, FinalGrade)`

That reporting table repeats `StudentName` and `InstructorOffice`. In the
operational system, that repetition would be a warning sign. In a controlled
reporting copy, it may be acceptable because the table is designed for reading,
filtering, grouping, and summarizing, not for recording daily changes.

Use this judgment rule:

- normalize the operational source of truth
- denormalize only for a clearly justified reporting, analytics, or warehouse
  need
- make the denormalized copy read-only or read-mostly for report users
- document which normalized source tables feed the reporting table
- control refresh logic so repeated values do not drift into conflicting stories

Denormalization is not a beginner escape hatch from hard design work. It is a
later design decision made after you understand the normalized source and the
reporting workload.

### 9. Many-To-Many Repair Uses An Intersection Table

In Lesson 3.2 you identified many-to-many relationships at the conceptual level and noted they could not be directly implemented. This lesson shows what to do about them: resolve the relationship through an intersection table that holds the foreign keys of both sides.

Many-to-many cases create another structural problem. Suppose one `Order` can
contain many `Product` values, and one `Product` can appear on many orders.

Do not pack multiple products into one order row.

Use an intersection table:

- `Order(OrderID, CustomerID, OrderDate)`
- `Product(ProductID, ProductName)`
- `OrderLine(OrderID, ProductID, Quantity)`

What does `OrderLine` preserve?

- one order can include many products
- one product can appear on many orders
- `Quantity` belongs to the relationship, not to `Order` alone or `Product`
  alone

This lesson introduces intersection tables as repair logic. You will represent
them more formally in later design-artifact work.

## Examples And Case

### Main Worked Case: Enrollment Repair

Original relation:

`EnrollmentRecord(StudentID, SectionID, StudentName, CourseID, InstructorID, InstructorOffice, Term, FinalGrade)`

Working FD set:

- `StudentID -> StudentName`
- `SectionID -> CourseID, InstructorID, Term`
- `InstructorID -> InstructorOffice`
- `StudentID, SectionID -> FinalGrade`

Reasoning summary:

- the relation is in 1NF if all values are atomic
- it fails 2NF because some non-key attributes depend on only part of the
  composite key
- after the 2NF repair, section-level data still fails 3NF because
  `InstructorOffice` depends on `InstructorID`
- the stronger decomposition preserves the meaning of one student in one section

Final repaired set:

- `Student(StudentID, StudentName)`
- `Instructor(InstructorID, InstructorOffice)`
- `Section(SectionID, CourseID, InstructorID, Term)`
- `Enrollment(StudentID, SectionID, FinalGrade)`

### BCNF Contrast Case

Relation:

`AdvisingAssignment(StudentID, InstructorID, ProgramCode)`

Dependencies:

- `StudentID, InstructorID -> ProgramCode`
- `InstructorID -> ProgramCode`

Reasoning summary:

- 3NF can pass because `ProgramCode` is prime
- BCNF fails because `InstructorID` is not a superkey
- the BCNF repair aligns determinants with keys more defensibly

### Meaning-Preservation Contrast

Compare these two proposals for the enrollment case:

- `Enrollment(StudentID, SectionID, FinalGrade)`
- `CourseEnrollment(StudentID, CourseID, FinalGrade)`

The first preserves section-level meaning. The second collapses section meaning
into course meaning. That may seem harmless until the business needs to know
which section, instructor, or term the student actually had.

### Denormalized Reporting Contrast

A denormalized reporting table such as
`EnrollmentReport(StudentID, StudentName, SectionID, CourseID, Term, InstructorName, FinalGrade)`
may be appropriate if it is a read-only report table refreshed from normalized
source tables. It would be inappropriate as the main operational table where
staff edit students, sections, instructors, and grades directly.

## Guided Practice

### Practice 1: Connect Anomaly To Consequence

For the weak `EnrollmentRecord` design, write one sentence each for:

- an insert anomaly and the business work it delays
- an update anomaly and the contradiction it could create
- a delete anomaly and the information it could erase

### Practice 2: Name The Dependency Problem

Classify each example as a 1NF, 2NF, 3NF, or BCNF problem:

- `SectionList` stored in one column
- `StudentID -> StudentName`
- `InstructorID -> InstructorOffice` inside a section relation
- `InstructorID -> ProgramCode` in the advising case

### Practice 3: Compare Two Decompositions

Compare these alternatives:

Option A:

- `Student(StudentID, StudentName)`
- `Instructor(InstructorID, InstructorOffice)`
- `Section(SectionID, CourseID, InstructorID, Term)`
- `Enrollment(StudentID, SectionID, FinalGrade)`

Option B:

- `Student(StudentID, StudentName)`
- `Section(SectionID, CourseID, InstructorID, Term, InstructorOffice)`
- `CourseEnrollment(StudentID, CourseID, FinalGrade)`

Answer these questions:

1. Which option removes more anomaly risk?
2. Which option preserves the intended meaning better?
3. Which specific fact is misplaced or lost in the weaker option?

### Practice 4: Defend The Repair

Using the main worked case, list the final repaired relations and give one short
reason for each relation. Your reason should name the determinant that owns the
fact set.

### Practice 5: Decide Whether Denormalization Is Justified

For the enrollment case, explain whether each design should be normalized or
denormalized:

- the operational database used by staff to enter students, sections, and grades
- a read-only dashboard table refreshed nightly for enrollment trend reports

Your answer should name the risk of denormalizing the operational database and
the reason denormalization may be acceptable for the reporting copy.

## What To Do

1. Read the lesson carefully.
2. Work through the main repair case in order.
3. Complete the guided practice and compare the alternative decompositions.
4. Check that your answers connect structural weakness to business consequences.
5. Verify that your proposed decomposition preserves the intended meaning of the
   original relation.
6. Distinguish operational source-of-truth design from read-only reporting or
   data-warehouse design.

## Assignments

### Normalization And Design-Repair Analysis

Given a weak relation and its business rules:

- identify likely insert, update, and delete anomalies
- explain why those anomalies matter to the organization
- identify the relevant key or keys
- rewrite the dependencies into a smaller working set when that improves
  clarity
- explain whether the design fails 1NF, 2NF, 3NF, or BCNF and why
- compare at least two decomposition options
- defend the stronger option in plain language
- explain whether the weaker option leaves a dependency problem behind or
  breaks the intended meaning
- explain whether a denormalized reporting copy would be justified, and why it
  should not replace the normalized operational source of truth

### Intersection-Table Repair Prompt

For one many-to-many case supplied by your instructor, propose an intersection
table and explain what relationship-level fact that table preserves.

## Deliverables

- one normalization and design-repair analysis with anomaly diagnosis,
  comparison of alternatives, and justification
- one short many-to-many repair explanation using an intersection table
- one short denormalization judgment for a read-only reporting or data-warehouse
  scenario

## Project Checkpoint Or Module Connection

Choose one relation from your semester project and ask:

1. What facts are being repeated, and why?
2. What update, insert, or delete anomaly could that repetition create?
3. Does your current design preserve the real business meaning of one row?
4. Where would a better decomposition improve stewardship of time, resources,
   or trust?
5. If you later create a reporting table or data warehouse, what repeated facts
   might be acceptable there because the copy is read-only or read-mostly?

Write a short paragraph that explains one repair you would make and how that
repair serves both technical quality and responsible organizational practice.

## Wrap-Up

Normalization is not a contest to create the most tables. It is a way to defend
better design.

The key questions are:

- what anomaly or dependency problem exists here?
- what business consequence does that weakness create?
- which decomposition actually fixes the problem?
- does the repair preserve the intended meaning of the original relation?

If you can answer those questions clearly, you are doing more than following a
procedure. You are making and defending a design judgment that will support
cleaner artifacts in Module 5 and more trustworthy database work later.
