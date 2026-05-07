# Lesson 1.2: From Business Process to Database

## Lesson Overview

Lesson 1.1 asked whether a business situation calls for a database. Lesson 1.2 answers the next question: if a database is the right tool, what happens between the business need and a working system?

This lesson gives you the map for the rest of the course. You will see the full workflow, the purpose of each stage, and the boundary between the two design artifacts students most often confuse: the ER Diagram and the Database Design Diagram.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain the full workflow from business process to working database use
- identify which artifacts belong to which workflow stages
- explain what the ER Diagram shows
- explain what the Database Design Diagram adds
- describe why workflow discipline supports truthful, accountable organizational reporting

## The Workflow Map

Use this course workflow spine as your reference:

1. understand the business process
2. identify data requirements and business rules
3. identify entities, attributes, and relationships
4. create the conceptual ER Diagram
5. convert the logical model into an implementation-ready Database Design Diagram
6. implement the design in SQL Server
7. query and manipulate data
8. manage introductory operational concerns
9. revise the solution when requirements or constraints change

You should think of this as a chain, not a pile. Each stage answers a different question.

| Workflow stage | Main question | Typical output |
| --- | --- | --- |
| Business process | What work is the organization trying to perform? | Case description, process notes, purpose statement |
| Data requirements and rules | What information must be tracked, and what rules govern it? | Requirement list, business rules |
| Entities, attributes, relationships | What are the main things to track, and how are they connected? | Early model notes, candidate entities and relationships |
| ER Diagram | What does the business structure look like conceptually? | Conceptual ERD |
| Database Design Diagram | What structural detail is needed to build the database? | Implementation-ready DBDD |
| SQL Server implementation | How do we create the database objects? | Tables, constraints, scripts |
| Query and manipulation | How will users retrieve and update data? | Queries, views, data changes |
| Operational control | How will the database stay usable, controlled, and recoverable? | Access decisions, backup thinking, concurrency controls |
| Revision | What must change when the business changes? | Updated artifacts and revised implementation |

## Running Case: Campus Tutoring Center

To make the workflow concrete, use this case throughout the lesson.

The campus tutoring center wants to:

- schedule tutoring sessions
- assign tutors to students
- record whether sessions were completed
- review tutoring activity by student, tutor, and course

That is the business process. The database work begins there, not with tables or SQL syntax.

## Stage 1: Understand The Business Process

Start with the real work the organization needs to perform. In this case, the tutoring center is trying to coordinate tutoring services and later report on what happened.

If you misunderstand the business process, later design work will be wrong even if the diagrams look polished. A neat artifact cannot rescue a bad understanding of the actual work.

Ask questions such as:

- Who uses the system?
- What recurring work must the system support?
- What decisions depend on the stored data?
- What would go wrong if the records were incomplete or inaccurate?

## Stage 2: Identify Data Requirements And Business Rules

Next, identify what information the system must store and what rules shape that information.

For the tutoring center, likely data requirements include:

- student identity
- tutor identity
- course being supported
- session date and time
- session status

Likely business rules include:

- a tutoring session must be tied to one student
- a tutoring session must be assigned to one tutor
- tutoring activity may need to be reported by course

This stage is where you separate must-track data from background detail. The color of the tutoring center walls might appear in a case description, but it does not belong in the database for this purpose.

## Stage 3: Identify Entities, Attributes, And Relationships

Now turn the requirements into a simple model of the business structure.

From the tutoring case, you can likely identify these entities:

- `Student`
- `Tutor`
- `Course`
- `TutoringSession`

You can also identify likely attributes:

- `StudentID`
- `TutorID`
- `CourseID`
- `SessionDate`
- `SessionStatus`

And you can identify relationships:

- a `Student` can have many `TutoringSession` records over time
- a `Tutor` can lead many `TutoringSession` records
- a `Course` can be associated with many `TutoringSession` records

This is still not implementation. You are clarifying the business structure before deciding how SQL Server will store it.

## Stage 4: Create The ER Diagram

The ER Diagram answers this question:

What does the business structure look like conceptually?

In this course, the ERD is a conceptual or logical artifact. It shows:

- entities
- identifiers
- significant attributes
- relationships
- cardinality
- optionality

For the tutoring case, the ERD might show that one `Tutor` can lead many `TutoringSession` instances, or that each `TutoringSession` is related to one `Student`.

### What The ERD Does Not Show

The ERD does not show:

- SQL Server data types
- nullability choices
- implementation-level foreign key notation
- other build-ready table details

Those details matter later, but they do not belong in the ERD. If you add them too early, you blur the artifact boundary and make it harder to see the business meaning clearly.

## Stage 5: Create The Database Design Diagram

The Database Design Diagram answers a different question:

What structural detail is needed to build this database?

The DBDD is an implementation-ready artifact. It shows:

- tables
- columns
- primary keys
- foreign keys
- data types
- nullability

For the same tutoring case, the DBDD might show a `TutoringSession` table with columns such as `TutoringSessionID`, `StudentID`, `TutorID`, `CourseID`, `SessionDate`, and `SessionStatus`, along with data types and required-versus-optional decisions.

## ERD Versus DBDD: Boundary Rule

Keep this distinction exact:

| If the statement says... | It belongs to... | Why |
| --- | --- | --- |
| "`Tutor` is related to many `TutoringSession` records." | ERD | It describes conceptual structure and cardinality. |
| "`TutoringSession` needs a `TutorID` foreign key column." | DBDD | It describes implementation-ready table detail. |
| "`SessionDate` should be stored as a date or datetime value." | DBDD | Data type decisions belong to the build-ready artifact. |
| "`Course` is an entity the business must track." | ERD-stage thinking | It identifies a tracked thing in the conceptual model. |

The DBDD does not replace the ERD. It builds on the ERD. The ERD preserves the business structure; the DBDD prepares that structure for construction.

## Stages 6 Through 9: Build, Use, Control, Revise

After the design artifacts are ready, the workflow continues.

### Stage 6: Implement The Design In SQL Server

This is where you create tables, keys, constraints, and other objects in SQL Server. The DBDD should guide this work.

### Stage 7: Query And Manipulate Data

Now users need the database to answer questions and support work. For the tutoring center, examples include:

- Which sessions were completed this week?
- How many sessions were held for each course?
- Which tutor handled the most sessions this month?

### Stage 8: Manage Introductory Operational Concerns

A working database must remain usable and controlled. That includes topics such as:

- appropriate access
- reliable backup and recovery habits
- safe handling of concurrent use

### Stage 9: Revise When Requirements Change

Business work changes. New reporting needs appear. Policies change. A good database team returns to the workflow, updates the model, and revises the implementation without pretending the first version was final forever.

## AI Use: What You Still Must Verify

AI can help summarize a case, suggest entities, or draft an early diagram explanation. That does not remove your responsibility to verify the result.

When using AI at this stage, always check:

- whether the workflow stages are in the correct order
- whether the suggested data actually supports the business process
- whether the ERD content stays conceptual
- whether the DBDD content adds implementation-ready detail without changing the business meaning

A polished AI answer is not proof that the reasoning is correct.

## Quick Check

Answer these without looking back first.

1. Put these in order: `DBDD`, `business process`, `ERD`, `SQL Server implementation`, `data requirements`.
2. Which artifact should show cardinality and optionality?
3. Which artifact should show data types and nullability?
4. Why is it risky to jump straight from a case description to table creation?
5. Which workflow stage is mainly responsible for helping the organization decide what information must be tracked?

### Quick Check Answers

1. `business process` -> `data requirements` -> `ERD` -> `DBDD` -> `SQL Server implementation`
2. The ERD
3. The DBDD
4. You can build structures that do not match the real business need or reporting requirement.
5. The data requirements and business rules stage

## Guided Practice

### Practice 1: Place The Artifact In The Workflow

Match each artifact or output to the workflow stage where it primarily belongs.

| Artifact or output | Your answer |
| --- | --- |
| list of business rules |  |
| conceptual ER Diagram |  |
| foreign key columns with data types |  |
| SQL `CREATE TABLE` statements |  |
| revised design after a policy change |  |

### Check Your Work

| Artifact or output | Correct workflow stage |
| --- | --- |
| list of business rules | identify data requirements and business rules |
| conceptual ER Diagram | create the conceptual ER Diagram |
| foreign key columns with data types | create the Database Design Diagram |
| SQL `CREATE TABLE` statements | implement the design in SQL Server |
| revised design after a policy change | revise the solution when requirements or constraints change |

### Practice 2: ERD Or DBDD?

Classify each statement.

1. "`Enrollment` connects `Student` and `Course`."
2. "`EnrollmentDate` in the `Enrollment` table should not allow nulls."
3. "One `Course` can have many `Enrollment` records."
4. "The `Enrollment` table needs `StudentID` and `CourseID` foreign keys."

### Check Your Work

1. ERD
2. DBDD
3. ERD
4. DBDD

## Independent Practice

Use this short scenario.

A small clinic wants to schedule appointments, track which provider sees each patient, and report no-show rates by month.

Write a short response that does all three tasks:

1. name the first five workflow stages for this case in order
2. identify two likely ERD-level statements
3. identify two likely DBDD-level statements

If you can do that clearly, you are ready for the Module 1 assessment style.

## Lesson Wrap-Up

This lesson gives you the course map. The workflow begins with the business process, moves through requirements and design artifacts, continues through implementation and use, and returns to revision when the organization changes.

Keep one rule in mind as you move forward: the ERD and DBDD are connected, but they are not the same artifact. The ERD explains the business structure. The DBDD prepares that structure for building. Later modules will keep returning to that boundary.
