# Module 6: SQL Server Implementation

### Purpose

- Implement the approved design in SQL Server through controlled data changes and reusable views.
- Emphasize verification that the built database matches the intended design.

### Objectives

- create tables and constraints in SQL Server from the approved DBDD
- load and change data in a dependency-aware and integrity-aware way
- create views that package reusable query logic for reporting
- verify that the implementation aligns with the approved design

### Human Must Know

- whether implementation choices actually reflect the DBDD
- why dependency order and integrity constraints matter
- how to detect mismatches between design and built schema
- how to judge whether a view or data change is safe and meaningful

### AI May Assist With

- generating DDL and DML
- proposing build order
- creating views
- executing scripts, capturing errors, and iterating on fixes

### Christian Integration Focus

- present constraints and implementation verification as practical expressions of accountability and business-rule fidelity
- treat views, sample data, and data changes as stewardship work that should clarify reality without oversharing or distorting it

### Integration Touchpoints

- include one implementation check asking which constraint is most important for trustworthy operations in the case
- include one view or data-loading prompt asking how the design supports transparent decisions without exposing unnecessary details

### Lessons

#### Lesson 6.1: Creating Tables and Constraints
- DDL basics
- `CREATE TABLE`
- PK and FK constraints
- dependency-aware build order

#### Lesson 6.2: Inserting, Updating, and Deleting Data
- dependency-aware inserts
- condition-aware updates
- careful deletes and verification

#### Lesson 6.3: Building Views
- reusable reporting logic
- readable query packaging
- verifying view outputs against business intent

### Assessment Strategy

Since AI can write and test working SQL scripts, this module should grade build auditing, error diagnosis, and alignment to design rather than script generation alone.

### Primary Graded Assessment

#### Build-and-Verify Audit

- Format: students receive a DBDD, a build script, sample outputs, and one or more failures or inconsistencies
- Students diagnose what is wrong, propose corrections, and explain how to verify final alignment to the DBDD

### Secondary Evidence

- timed implementation quiz focused on dependency order and integrity behavior
- short annotation of one corrected schema or view decision

### What To Grade

- accuracy of mismatch detection
- quality of DDL, DML, or view diagnosis
- explanation of why an error occurs
- verification logic against the approved design
- ability to identify when a technically successful implementation still creates a trust, privacy, or integrity problem

### Module Assessment Tasks

- identify where a script fails to implement the DBDD correctly
- explain a constraint or dependency-order failure
- detect unsafe update or delete logic
- verify whether a view output answers the intended business question

### Why This Assessment Holds Up Better

- it makes correctness depend on design alignment, not just successful execution
- it tests whether students can diagnose subtle implementation drift
- it treats SQL output as evidence to inspect, not proof by itself
