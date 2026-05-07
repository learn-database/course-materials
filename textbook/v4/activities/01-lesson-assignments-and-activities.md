# Lesson Assignments and Activities

## Purpose

This file gives one concrete assignment or activity for each v4 lesson.

Most of these should be low-stakes or practice-oriented. They prepare students for the module assessments in `textbook/v4/assessments/02-module-level-assessment-briefs.md`.

## Shared Student Instructions

- AI may be used for drafting, checking, or generating examples unless the LMS version of the activity says otherwise.
- Students remain responsible for explaining, verifying, and correcting the final answer.
- When AI is used, students should briefly state what it helped with and what they personally checked.
- Short answers should be specific to the scenario, query, diagram, or artifact in the activity.

## Module 1: The Whole Database Workflow

### Lesson 1.1: Why Databases Matter

Assignment: `Database or Not? Scenario Sort`

Students receive six short business scenarios. For each scenario, they classify the best tool fit as spreadsheet, shared file, or relational database.

Deliverable:

- classification table
- two-sentence justification for three selected scenarios
- one note identifying who could be harmed by poor recordkeeping in one scenario

Evidence:

- scenario classification
- tool-fit reasoning
- trust or stewardship implication

### Lesson 1.2: From Business Process to Database

Assignment: `Workflow Stage Match`

Students receive a short case and a shuffled list of workflow actions and artifacts. They place the actions in order and label each artifact as ERD, DBDD, SQL implementation, query/reporting, or administration.

Deliverable:

- ordered workflow list
- artifact classification table
- short explanation of the ERD versus DBDD boundary

Evidence:

- workflow reasoning
- artifact-boundary recognition
- explanation of what each artifact is for

## Module 2: SQL Foundations

### Lesson 2.1: The SQL Server Environment

Assignment: `Environment Verification Check`

Students open the course SQL environment, run a provided starter script, and verify database context and output messages.

Deliverable:

- screenshot or copied output showing successful execution
- database context used
- short explanation of client role, server role, and why context matters

Evidence:

- successful setup
- accurate environment vocabulary
- verification habit

### Lesson 2.2: Optional Review of Set Operations on Relations

Assignment: `Set Thinking Mini-Sort`

Students classify short descriptions as relation, row, column, projection, selection, or not a relational idea.

Deliverable:

- completed classification table
- two corrections of common misunderstandings
- one sentence explaining how set thinking helps SQL work

Evidence:

- concept recognition
- comparison of set thinking versus record-by-record thinking
- preparation for SQL interpretation

### Lesson 2.3: Single-Table Queries

Assignment: `One Table, Three Queries`

Students receive one business question and three candidate single-table queries. One is correct, one has a filter problem, and one has a sorting or selected-column problem.

Deliverable:

- choice of best query
- explanation of why each rejected query is wrong
- corrected version of one flawed query

Evidence:

- query reading
- business-question alignment
- controlled revision

### Lesson 2.4: Aggregates and Grouping

Assignment: `Summary Result Check`

Students receive a reporting question, a small result set, and two grouped queries. They identify which query answers the question and explain the difference between row-level and grouped output.

Deliverable:

- selected query
- explanation of the grouping logic
- warning about one misleading interpretation of the output

Evidence:

- grouping judgment
- output interpretation
- honest reporting awareness

### Lesson 2.5: Joins

Assignment: `Join Path Diagnosis`

Students receive a simple schema diagram, a business question, and two join options. They identify the correct join path and diagnose the likely error in the weaker query.

Deliverable:

- selected join path
- plain-language explanation of what each joined row represents
- one risk caused by duplicated, missing, or mismatched rows

Evidence:

- join reasoning
- row-meaning explanation
- business consequence of bad join logic

### Lesson 2.6: Common Table Expressions

Assignment: `Name the Intermediate Result`

Students rewrite a hard-to-read query using one CTE and explain what the CTE represents before the final result is produced.

Deliverable:

- rewritten query using a CTE
- explanation of the CTE result set
- judgment about whether the CTE improves readability

Evidence:

- procedural use of CTE syntax
- intermediate-result reasoning
- readability and verification judgment

## Module 3: Core Data Modeling

### Lesson 3.1: Entities, Attributes, and Identifiers

Assignment: `Entity or Attribute?`

Students receive a business narrative and a list of candidate nouns. They classify each as entity, attribute, identifier, background detail, or unclear.

Deliverable:

- classification table
- justification for three choices
- stronger identifier recommendation for one weak identifier

Evidence:

- concept classification
- identifier judgment
- scope control

### Lesson 3.2: Relationships and Cardinality

Assignment: `Cardinality Defense`

Students receive four relationship statements from a case. They choose one-to-one, one-to-many, or many-to-many and identify optionality where relevant.

Deliverable:

- relationship classification table
- two short cardinality justifications from business rules
- one critique of an incorrect relationship claim

Evidence:

- relationship-pattern recognition
- cardinality and optionality reasoning
- critique of weak modeling

### Lesson 3.3: Discovering Requirements and Drafting a Conceptual ERD

Assignment: `Requirements to First ERD`

Students read a short case, identify must-track information, and draft a first conceptual ERD.

Deliverable:

- list of must-track entities and relationships
- conceptual ERD draft
- annotation explaining two choices and one excluded detail

Evidence:

- requirement extraction
- conceptual modeling
- defense of scope and modeling decisions

## Module 4: Design Logic

### Lesson 4.1: Functional Dependencies

Assignment: `Defensible or Accidental?`

Students receive a relation, sample rows, and stated business rules. They classify proposed FDs as defensible, unsupported, or false.

Deliverable:

- FD classification table
- explanation of two defensible dependencies
- rejection of one sample-only pattern

Evidence:

- FD interpretation
- business-rule reasoning
- rejection of accidental data patterns

### Lesson 4.2: Keys of Relations

Assignment: `Candidate Key Check`

Students receive a relation and business rules. They test several possible keys and identify which are candidate keys, superkeys, or non-keys.

Deliverable:

- key classification table
- explanation of minimality for one candidate key
- rejection of one weak key candidate

Evidence:

- key reasoning
- structural uniqueness explanation
- minimality judgment

### Lesson 4.3: Normalization and Design Repair

Assignment: `Repair the Weak Relation`

Students receive a relation with anomalies and two proposed repairs. They identify the anomaly and choose the stronger repair.

Deliverable:

- anomaly diagnosis
- selected repair
- explanation of why the weaker repair still fails or loses meaning

Evidence:

- anomaly recognition
- decomposition comparison
- business and structural defense

## Module 5: Design Artifacts

### Lesson 5.1: Refining Conceptual ERDs in Crow's Foot Notation

Assignment: `Clean the Conceptual ERD`

Students receive a conceptual ERD with notation problems and implementation clutter. They correct the notation and remove details that do not belong.

Deliverable:

- revised conceptual ERD
- list of removed implementation details
- explanation of why one removed item belongs in the DBDD instead

Evidence:

- Crow's Foot notation correction
- conceptual boundary control
- artifact separation reasoning

### Lesson 5.2: Database Design Diagrams

Assignment: `Build the DBDD Slice`

Students receive a small conceptual model and convert one slice into a DBDD with tables, columns, PKs, FKs, data types, and nullability.

Deliverable:

- DBDD slice
- explanation of one PK or FK choice
- explanation of one data type or nullability choice

Evidence:

- implementation-ready artifact construction
- mapping from concept to table structure
- design-choice explanation

### Lesson 5.3: From Logical Model to Implementation-Ready Design

Assignment: `ERD to DBDD Alignment Review`

Students receive an ERD and a proposed DBDD. They identify whether the DBDD preserves the meaning of the ERD and repair one mapping problem.

Deliverable:

- alignment checklist
- corrected DBDD element
- explanation of why the correction preserves business meaning

Evidence:

- artifact alignment judgment
- mapping-error diagnosis
- implementation-ready defense

## Module 6: SQL Server Implementation

### Lesson 6.1: Creating Tables and Constraints

Assignment: `DDL Build Order Check`

Students receive a DBDD slice and a flawed `CREATE TABLE` order. They correct the order and explain one PK or FK constraint.

Deliverable:

- corrected build order
- corrected or annotated DDL snippet
- verification note explaining how the schema matches the DBDD

Evidence:

- dependency-aware implementation
- constraint reasoning
- schema verification

### Lesson 6.2: Inserting, Updating, and Deleting Data

Assignment: `Safe Data Change Review`

Students receive three DML statements. One insert violates dependency order, one update is too broad, and one delete risks referential-integrity failure.

Deliverable:

- diagnosis of each DML risk
- corrected statement or safer alternative for two items
- verification query or check for one correction

Evidence:

- DML safety judgment
- integrity-risk explanation
- result verification

### Lesson 6.3: Building Views

Assignment: `View Output Verification`

Students receive a reporting question, a view definition, and sample output. They decide whether the view answers the question and revise the view if needed.

Deliverable:

- judgment of whether the view is correct
- corrected view or explanation of no change needed
- explanation of what the output does and does not prove

Evidence:

- reusable query packaging
- output interpretation
- business-question verification

## Module 7: Database Operation and Control

### Lesson 7.1: Roles, Users, and Permissions

Assignment: `Least-Privilege Access Matrix`

Students receive a small workplace scenario with three roles. They complete a CRUD matrix and flag any excessive access.

Deliverable:

- CRUD matrix
- least-privilege justification for two role decisions
- rejection of one over-permissioned access choice

Evidence:

- access-level judgment
- least-privilege reasoning
- privacy and accountability awareness

### Lesson 7.2: Concurrency and Transactions

Assignment: `Commit or Roll Back?`

Students receive three multi-step scenarios. They decide which actions should belong in one transaction and whether the scenario should commit or roll back after a failure.

Deliverable:

- transaction-boundary decisions
- commit or rollback recommendation
- explanation of the integrity risk if the steps are split incorrectly

Evidence:

- transaction reasoning
- concurrency-risk diagnosis
- plain-language operational explanation

### Lesson 7.3: Backup and Recovery Basics

Assignment: `Recovery Response Choice`

Students receive a simple incident scenario and three possible backup or recovery responses. They choose the strongest response and explain the limits of a weaker one.

Deliverable:

- selected response
- explanation of why it fits the scenario
- critique of one incomplete or risky response

Evidence:

- backup and recovery purpose
- scenario judgment
- operational tradeoff explanation

## Module 8: Procedural Logic and Final Project Revision

### Lesson 8.1: Stored Procedures

Assignment: `Procedure or Plain Query?`

Students receive four repeated-work scenarios. They decide whether each should be handled by a plain query, view, stored procedure, or another design choice.

Deliverable:

- scenario classification table
- one simple procedure skeleton or call pattern
- test note describing expected behavior for two inputs

Evidence:

- procedure justification
- parameter and testing reasoning
- distinction between reusable operation types

### Lesson 8.2: Triggers

Assignment: `Should This Be a Trigger?`

Students receive three rule-enforcement scenarios. They decide whether a trigger is justified, overused, or unsafe.

Deliverable:

- trigger-use judgment for each scenario
- explanation of the triggering event for one justified case
- test case that would reveal unexpected behavior

Evidence:

- trigger justification
- event-driven logic explanation
- bounded automation judgment

### Lesson 8.3: Final Project Integration and Revision

Assignment: `Late Change Impact Map`

Students receive a late business-rule change for a project case. They identify which artifacts and SQL objects must change and explain how they would verify the revision.

Deliverable:

- impact map across ERD, DBDD, SQL, views, procedures, triggers, permissions, and tests as relevant
- revised artifact or SQL excerpt for one affected area
- verification plan and brief defense of the revision

Evidence:

- cross-artifact consistency
- change-request adaptation
- final-package verification and defense

## Instructor Implementation Notes

- These activities can become LMS assignments, practice checks, discussion prompts, or quiz items.
- Use the module assessment briefs to decide which activities carry grade weight.
- Keep the activity prompts short enough for asynchronous completion.
- Where students submit generated or AI-assisted work, require a brief verification or correction note.
