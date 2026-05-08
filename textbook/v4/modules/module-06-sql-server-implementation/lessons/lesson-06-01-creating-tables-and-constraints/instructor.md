# Lesson 6.1: Creating Tables and Constraints

## Instructor-Facing Content

### Module

Module 6: SQL Server Implementation

### Lesson Purpose

Teach students to convert an approved Database Design Diagram into executable SQL Server structure with `CREATE TABLE`, primary keys, foreign keys, and supporting constraints. The lesson should reinforce that implementation choices are accountable to the approved design, not invented during script writing.

### Module Context

Lesson 6.1 begins Module 6's implementation work. Module 5 established the DBDD as the implementation-ready artifact. Lesson 6.1 uses that artifact to build the schema, Lesson 6.2 depends on the finished structure for controlled data changes, and Lesson 6.3 depends on both structure and data for reusable reporting views.

Module 6's distinct emphasis is verification. Students should therefore treat successful execution as one checkpoint, not the final standard of correctness.

### Primary Learning Type

Procedures

### Secondary Learning Type

Principles

### Estimated Time

90 to 120 minutes

### Lesson Outcomes

By the end of the lesson, students should be able to:

- explain DDL as structure-building work in SQL Server
- translate an approved DBDD into dependency-aware `CREATE TABLE` statements
- implement required `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`, and `DEFAULT` constraints
- explain why dependency order matters for schema creation
- detect where a built schema drifts from the DBDD
- verify that the final schema matches the approved design before moving to DML work

### Module Alignment

- supports the module objective to create tables and constraints in SQL Server from the approved DBDD
- supports the module objective to verify that implementation aligns with the intended design
- feeds the module's primary build-and-verify audit by giving students a concrete schema to inspect, critique, and defend

### Course Objective Alignment

- Course Objective 3: create ER Diagrams and Database Design Diagrams that reflect a given business process
- Course Objective 5: create and use SQL statements for querying and data manipulation

### Lesson Sequence Role

This lesson is the implementation handoff from design artifacts to executable SQL Server structure. It assumes students can read a DBDD and now requires them to express that approved design faithfully in SQL. It prepares students for dependency-aware data loading and change work in Lesson 6.2.

### Required Prior Knowledge

- the difference between the ER Diagram and the DBDD
- Module 5 understanding of tables, columns, data types, PKs, FKs, and nullability
- basic SQL Server environment use from Module 2
- awareness that Module 6 emphasizes verification, not just script production

### Lesson Opening Guidance

Start with a compact DBDD and ask students to identify:

- which parts become column definitions
- which parts become PK or FK clauses
- which tables must be created first

Then show a short failure case where a child table is created before its parent table. Use that failure to establish that dependency order is part of the build procedure, not a cosmetic preference.

### Teaching Notes

- Keep the approved DBDD visible throughout the lesson. Students should trace each SQL choice back to a design choice.
- Preserve the ERD versus DBDD boundary explicitly. The ERD is not enough detail for full table creation.
- Keep the SQL Server schema name visible in examples, such as `dbo.Student`.
- Treat `CHECK`, `DEFAULT`, and `UNIQUE` as implementation of approved business rules, not as optional advanced extras.
- Use one coherent case with both independent parent tables and dependent child tables so build order is meaningful.
- Include at least one schema-drift example that executes successfully but still fails verification against the DBDD.
- Reconnect the lesson to the module assessment pattern: build, diagnose, verify.

### Online Activities

- short concept check distinguishing DDL from DML
- mapping activity that matches DBDD decisions to SQL clauses
- dependency-order reordering exercise
- drift audit prompt that asks students to identify missing or altered constraints
- short judgment prompt asking which single constraint matters most for trustworthy operations in the case

### Homework / Graded Assignments

Assign a DBDD-to-DDL build submission that includes:

- a full dependency-aware `CREATE TABLE` script
- required PK, FK, `UNIQUE`, `CHECK`, and `DEFAULT` clauses
- a short verification checklist or audit note showing whether the final schema matches the DBDD
- a short explanation of one corrected mismatch or one especially important constraint choice

### Deliverables

- one SQL script for the full table build
- one short schema verification note tied directly to the approved DBDD
- one short response to the trustworthy-operations constraint prompt

### Assessment Plan

Formative checks:

- identify DDL versus DML
- classify DBDD decisions by SQL implementation type
- reorder a flawed build sequence
- detect schema drift in a flawed table definition

Graded evidence:

- completed DDL build in dependency-aware order
- explanation of why order and constraints matter
- verification that the final schema matches the DBDD

The lesson should produce evidence that students can do more than generate SQL. They should be able to diagnose and verify whether the generated result deserves trust.

### Suggested Rubric Focus

- fidelity to the approved DBDD
- correct dependency-aware build order
- correct use of PK and FK constraints
- correct use of supporting `UNIQUE`, `CHECK`, and `DEFAULT` constraints where required
- quality of schema-verification reasoning
- clarity of explanation about why one key constraint matters for trustworthy operations

### Common Misconceptions

- if the script runs, the schema must be correct
- `CREATE TABLE` is a chance to improve or rewrite the design informally
- foreign keys matter only when data is inserted later
- build order is optional if the syntax is otherwise correct
- only PK and FK constraints matter for design fidelity
- the ERD alone provides enough detail for implementation

### Christian Integration Notes

Keep integration inside normal technical teaching. Suitable touchpoints in this lesson include:

- explaining that constraints are practical forms of accountability and business-rule fidelity
- showing how missing constraints can distort reports, seat counts, or follow-up actions
- asking which constraint most directly protects trustworthy operations in the case

Use business-facing language such as stewardship, trust, integrity, accountability, and truthful reporting only where it clarifies the operational consequence of weak implementation.

### Workflow Connection

This lesson corresponds to the course workflow stage where the approved design becomes executable SQL Server structure. The habits taught here carry directly into later Module 6 work:

- Lesson 6.2 assumes the structure and constraints are present before data changes begin
- Lesson 6.3 assumes the structure and data can be trusted enough to support reusable reporting views

If students skip design fidelity or verification here, the rest of the module inherits that drift.
