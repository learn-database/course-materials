# Instructional Strategies for Lessons

## Purpose

This document maps each ITM-2100 lesson in `v4` to an instructional strategy pattern. It follows the same broad Smith and Ragan logic used in `v3`, but it also accounts for three v4 realities:

- the course is fully asynchronous
- students may use strong AI tools
- major assessments need second evidence beyond artifact production alone

This file is not meant to restate instructional design theory in the abstract. It is a course-specific strategy map for writing and reviewing lessons in v4.

## Core Rule

Each lesson should be taught according to its dominant learning type.

The lesson may contain multiple kinds of knowledge, but one type should govern:

- the teaching pattern
- the kinds of examples used
- the kind of practice learners do
- the kind of evidence used to judge learning

## v4-Specific Strategy Rules

### Async Rule

Student-facing lesson material must teach directly enough for independent use in an LMS. Do not assume live lecture clarification.

### AI-Available Rule

If AI can plausibly generate, test, or polish the main artifact for a lesson, then the lesson strategy must include explanation, diagnosis, comparison, adaptation, or verification work that still reveals whether the student understands the task.

### Second-Evidence Rule

When a lesson involves artifact production, pair it with one or more of these:

- timed case checks
- critique-and-repair tasks
- annotated walkthroughs
- output-verification tasks
- comparison of alternatives
- change-request responses
- short screencast defenses

### Christian Integration Rule

Where the lesson naturally allows it, embed Christian integration inside the same examples, common mistakes, project checkpoints, or decision prompts that already teach the technical content. Do not treat it as a separate devotional aside.

## Learning-Type Guide

### Facts / Declarative Knowledge

Use this pattern when learners need to remember, recognize, label, or distinguish discrete information.

Typical instructional moves:

- clear explanation
- organization of related facts
- recognition or recall checks
- short applied context

Typical evidence:

- labeling
- matching
- recognition checks
- short-response recall

### Concepts

Use this pattern when learners need to understand what something is and distinguish it from related ideas.

Typical instructional moves:

- definition
- critical attributes
- examples
- non-examples
- comparison
- classification

Typical evidence:

- concept sorting
- compare-and-contrast work
- classification tasks
- explanation of why an example fits or does not fit

### Principles

Use this pattern when learners need to make decisions based on rules, relationships, or generalizations.

Typical instructional moves:

- rule explanation
- contrasting cases
- correct-use and incorrect-use examples
- judgment prompts
- decision justification

Typical evidence:

- diagnosis tasks
- better-choice justification
- scenario judgment
- explanation of governing rules

### Procedures

Use this pattern when learners need to perform an ordered method or repeatable process.

Typical instructional moves:

- purpose of the procedure
- modeled demonstration
- ordered steps
- guided practice
- independent execution
- verification or feedback

Typical evidence:

- completed performance
- guided lab output
- successful execution
- verification against expected results

### Problem Solving / Judgment

Use this pattern when learners need to analyze, diagnose, design, repair, justify, compare, or revise in a realistic case.

Typical instructional moves:

- authentic case
- modeled reasoning
- guided analysis
- independent application
- revision or reflection

Typical evidence:

- case analysis
- diagnosis
- redesign
- repair
- written or recorded rationale

## Lesson Strategy Map

## Module 1: The Whole Database Workflow

### Lesson 1.1: Why Databases Matter

#### Primary Learning Type

Facts / declarative knowledge

#### Secondary Learning Type

Concepts

#### Strategy Pattern

- clear explanation
- labeled examples
- recognition and recall checks
- concept clarification in short cases

#### Practice Type

- classify business process, data, information, and database
- compare database use versus simpler tools
- identify likely harm from poor recordkeeping in a short scenario

#### Assessment Evidence

- students correctly identify when a database is or is not needed
- students distinguish core terms accurately
- students justify the choice with basic business reasoning

### Lesson 1.2: From Business Process to Database

#### Primary Learning Type

Problem solving / judgment

#### Secondary Learning Type

- concepts
- principles

#### Strategy Pattern

- whole-case walkthrough
- modeled reasoning
- guided case analysis
- staged handoff explanation

#### Practice Type

- trace a case from need to implementation
- match artifacts to workflow stages
- explain what the ERD shows and what the DBDD adds

#### Assessment Evidence

- students explain the workflow in correct order
- students connect artifacts to the problem each one solves
- students explain the ERD versus DBDD boundary clearly

## Module 2: SQL Foundations

### Lesson 2.1: The SQL Server Environment

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Facts

#### Strategy Pattern

- interface walkthrough
- modeled setup demonstration
- guided execution check
- optional alternate-client comparison

#### Practice Type

- open the working environment
- identify client and server roles
- choose the correct database context
- run a provided script or starter statement
- inspect results and messages

#### Assessment Evidence

- students navigate the SQL Server environment used in the course
- students explain the client and server roles and the script-execution path
- students run a provided script in the correct context

### Lesson 2.2: Optional Review of Set Operations on Relations

#### Primary Learning Type

Concepts

#### Secondary Learning Type

Principles

#### Strategy Pattern

- definition and classification
- set-based examples and non-examples
- comparison of row thinking versus set thinking

#### Practice Type

- identify relation, row set, and attribute set ideas
- connect set thinking to selection, projection, and later SQL work

#### Assessment Evidence

- students distinguish set-based reasoning from record-by-record reasoning
- students explain how the concepts support later query work

### Lesson 2.3: Single-Table Queries

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Problem solving / judgment

#### Strategy Pattern

- clause-by-clause demonstration
- guided query reading
- controlled query revision
- business-question alignment checks

#### Practice Type

- read and explain `SELECT`, `FROM`, `WHERE`, and `ORDER BY`
- compare a correct and incorrect query
- interpret output against a business question

#### Assessment Evidence

- students identify whether a query answers the intended question
- students explain why a wrong query is wrong even if it runs
- students revise a flawed query and explain the change

### Lesson 2.4: Aggregates and Grouping

#### Primary Learning Type

Principles

#### Secondary Learning Type

Procedures

#### Strategy Pattern

- rule explanation for grouped versus ungrouped work
- contrasting examples
- output interpretation
- diagnosis of grouping mistakes

#### Practice Type

- determine when summarization is needed
- compare correct and incorrect grouping logic
- interpret summarized results honestly

#### Assessment Evidence

- students distinguish row-level questions from summary questions
- students diagnose grouped-query mistakes
- students explain what the output does and does not mean

### Lesson 2.5: Joins

#### Primary Learning Type

Principles

#### Secondary Learning Type

Procedures

#### Strategy Pattern

- relationship-based explanation
- join-path reasoning
- contrasting examples with row multiplication risks
- business-meaning interpretation

#### Practice Type

- explain why a join is needed
- choose the correct join path
- detect duplicated or missing rows caused by weak join logic

#### Assessment Evidence

- students explain the meaning of joined rows
- students identify flawed join logic
- students connect join structure to the business question

### Lesson 2.6: Common Table Expressions

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Problem solving / judgment

#### Strategy Pattern

- modeled query organization
- intermediate-result explanation
- readability comparison
- controlled revision

#### Practice Type

- use a CTE to separate query stages
- compare a readable and unreadable version
- explain why the CTE supports clearer reasoning

#### Assessment Evidence

- students use a CTE appropriately in a simple query
- students explain what intermediate result set the CTE represents
- students evaluate whether the CTE actually improves the query

## Module 3: Core Data Modeling

### Lesson 3.1: Entities, Attributes, and Identifiers

#### Primary Learning Type

Concepts

#### Secondary Learning Type

Principles

#### Strategy Pattern

- definition and classification
- examples and non-examples
- stronger-versus-weaker identifier comparison

#### Practice Type

- sort scenario elements into entities and attributes
- compare identifier choices
- justify classification decisions

#### Assessment Evidence

- students classify entities, attributes, and identifiers accurately
- students justify stronger identifier choices
- students reject weak or vague labels

### Lesson 3.2: Relationships and Cardinality

#### Primary Learning Type

Principles

#### Secondary Learning Type

Concepts

#### Strategy Pattern

- rule explanation
- diagram reading
- contrasting cases
- cardinality and optionality judgment

#### Practice Type

- identify one-to-many and many-to-many patterns
- justify optionality from business rules
- critique a weak relationship choice

#### Assessment Evidence

- students match relationship patterns to business rules
- students justify cardinality and optionality decisions
- students detect relationship errors in a model

### Lesson 3.3: Discovering Requirements and Drafting a Conceptual ERD

#### Primary Learning Type

Problem solving / judgment

#### Secondary Learning Type

Concepts

#### Strategy Pattern

- case reading
- guided extraction of tracked information
- first-pass conceptual modeling
- critique and revision

#### Practice Type

- distinguish scope from background detail
- identify candidate entities and relationships
- critique a flawed conceptual ERD

#### Assessment Evidence

- students identify must-track information from the case
- students detect modeling omissions or overreach
- students defend conceptual ERD choices from case evidence

## Module 4: Design Logic

### Lesson 4.1: Functional Dependencies

#### Primary Learning Type

Principles

#### Secondary Learning Type

Concepts

#### Strategy Pattern

- rule explanation
- business-meaning justification
- contrasting true dependencies and sample-only patterns

#### Practice Type

- identify determinants and dependents
- reject accidental sample patterns
- explain why a dependency is or is not defensible

#### Assessment Evidence

- students explain dependency statements clearly
- students justify FD claims from business meaning
- students reject unsupported FD claims

### Lesson 4.2: Keys of Relations

#### Primary Learning Type

Principles

#### Secondary Learning Type

Concepts

#### Strategy Pattern

- key reasoning walkthrough
- contrasting candidate keys and weak choices
- decision justification

#### Practice Type

- test likely keys
- distinguish candidate keys from non-keys
- explain why minimality matters

#### Assessment Evidence

- students determine reasonable keys of a relation
- students justify why one choice is a key and another is not
- students explain structural uniqueness clearly

### Lesson 4.3: Normalization and Design Repair

#### Primary Learning Type

Problem solving / judgment

#### Secondary Learning Type

Principles

#### Strategy Pattern

- anomaly diagnosis
- modeled decomposition reasoning
- comparison of alternative repairs
- revision and defense

#### Practice Type

- identify anomalies
- compare decompositions
- justify a design repair

#### Assessment Evidence

- students diagnose insert, update, or delete anomalies
- students compare stronger and weaker decompositions
- students justify a design repair in business and structural terms

## Module 5: Design Artifacts

### Lesson 5.1: Refining Conceptual ERDs in Crow's Foot Notation

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Principles

#### Strategy Pattern

- notation review
- guided refinement
- critique of conceptual-boundary drift

#### Practice Type

- read and revise Crow's Foot notation
- improve conceptual ERD clarity
- remove implementation clutter from an ERD

#### Assessment Evidence

- students read and correct Crow's Foot patterns accurately
- students maintain conceptual ERD boundaries
- students explain why certain details do not belong in the ERD

### Lesson 5.2: Database Design Diagrams

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Principles

#### Strategy Pattern

- modeled conversion from conceptual to implementation-ready detail
- table and key explanation
- guided artifact translation

#### Practice Type

- convert entities to tables
- add PKs, FKs, data types, and nullability appropriately
- explain implementation-ready detail

#### Assessment Evidence

- students build a DBDD that reflects the conceptual model
- students place implementation-ready detail in the correct artifact
- students explain how one relationship is carried into table structure

### Lesson 5.3: From Logical Model to Implementation-Ready Design

#### Primary Learning Type

Problem solving / judgment

#### Secondary Learning Type

Procedures

#### Strategy Pattern

- case-based conversion analysis
- boundary checks
- critique and repair

#### Practice Type

- evaluate whether a DBDD reflects the ERD faithfully
- detect mapping mistakes
- justify implementation-ready design choices

#### Assessment Evidence

- students explain why the DBDD does or does not align to the ERD
- students diagnose boundary violations or weak mapping
- students defend implementation-ready choices clearly

## Module 6: SQL Server Implementation

### Lesson 6.1: Creating Tables and Constraints

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Principles

#### Strategy Pattern

- modeled DDL build
- dependency-order demonstration
- execution with verification
- failure diagnosis

#### Practice Type

- write `CREATE TABLE` statements from a DBDD
- add PK and FK constraints
- explain dependency-aware build order
- verify the built structure

#### Assessment Evidence

- students build tables and constraints in a dependency-aware order
- students explain why order and constraints matter
- students verify the built schema against the DBDD

### Lesson 6.2: Inserting, Updating, and Deleting Data

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Problem solving / judgment

#### Strategy Pattern

- stepwise execution
- controlled data-change practice
- failure or near-failure diagnosis
- verification after each change

#### Practice Type

- insert parent rows before child rows
- update with safe conditions
- delete with dependency awareness
- verify results after each action

#### Assessment Evidence

- students execute controlled data changes correctly
- students identify risky or over-broad conditions
- students explain integrity-related failures or risks

### Lesson 6.3: Building Views

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Problem solving / judgment

#### Strategy Pattern

- modeled reusable query packaging
- business-question alignment checks
- output interpretation

#### Practice Type

- build a view from a reporting question
- compare the view output to the intended question
- detect when a view is technically valid but misleading

#### Assessment Evidence

- students create or revise a view that answers the intended question
- students explain what the view output means
- students identify when a view distorts the business question

## Module 7: Database Operation and Control

### Lesson 7.1: Roles, Users, and Permissions

#### Primary Learning Type

Principles

#### Secondary Learning Type

Problem solving / judgment

#### Strategy Pattern

- rule explanation
- realistic access scenarios
- CRUD-supported reasoning
- least-privilege justification

#### Practice Type

- match responsibilities to access needs
- compare stronger and weaker permission choices
- defend role-based access decisions

#### Assessment Evidence

- students recommend appropriate access levels
- students reject over-permissioned choices
- students justify least privilege clearly

### Lesson 7.2: Concurrency and Transactions

#### Primary Learning Type

Principles

#### Secondary Learning Type

Procedures

#### Strategy Pattern

- multi-user case analysis
- transaction-boundary reasoning
- small T-SQL transaction examples

#### Practice Type

- identify concurrency risk
- decide what belongs in one transaction
- justify commit or rollback choices

#### Assessment Evidence

- students diagnose multi-user integrity risks
- students explain transaction boundaries in plain language
- students justify commit and rollback choices appropriately

### Lesson 7.3: Backup and Recovery Basics

#### Primary Learning Type

Principles

#### Secondary Learning Type

Facts

#### Strategy Pattern

- scenario-based explanation
- consequence comparison
- response-choice justification

#### Practice Type

- explain backup purpose
- compare stronger and weaker recovery responses
- identify limits of a proposed protection plan

#### Assessment Evidence

- students explain backup and recovery purpose accurately
- students choose a sensible basic response for a scenario
- students justify why one response is incomplete or risky

## Module 8: Procedural Logic and Final Project Revision

### Lesson 8.1: Stored Procedures

#### Primary Learning Type

Procedures

#### Secondary Learning Type

Problem solving / judgment

#### Strategy Pattern

- modeled code creation
- repeated-operation reasoning
- parameterized execution
- test-and-verify practice

#### Practice Type

- decide whether a task should be a query or procedure
- add parameters
- test with multiple inputs
- explain expected behavior

#### Assessment Evidence

- students justify whether a procedure is warranted
- students build and test a simple procedure
- students explain why the procedure is useful for repeated work

### Lesson 8.2: Triggers

#### Primary Learning Type

Problem solving / judgment

#### Secondary Learning Type

Procedures

#### Strategy Pattern

- justified-use analysis
- event-driven logic explanation
- controlled behavior testing

#### Practice Type

- decide whether a rule belongs in a trigger
- match logic to the triggering event
- test expected and unexpected behavior

#### Assessment Evidence

- students justify whether a trigger is appropriate
- students explain trigger behavior clearly
- students detect overuse or weak trigger logic

### Lesson 8.3: Final Project Integration and Revision

#### Primary Learning Type

Problem solving / judgment

#### Secondary Learning Type

Procedures

#### Strategy Pattern

- cross-artifact review
- change-request revision
- consistency checking
- evidence-based rationale

#### Practice Type

- identify inconsistencies across ERD, DBDD, SQL, and procedural logic
- respond to a new business rule
- explain what must change and why

#### Assessment Evidence

- students detect cross-artifact inconsistency
- students revise the project after a change request
- students justify revisions and verify alignment across the full package
