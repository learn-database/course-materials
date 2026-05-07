# Lesson-Level Assessment Map

## Purpose

This file lists the intended lesson-level assessment evidence for all 24 lessons in `v4`.

The goal is not to create 24 large graded assignments. The goal is to make clear what kind of evidence each lesson should produce or prepare students to produce.

## Module 1: The Whole Database Workflow

| Lesson | Assessment Evidence |
|---|---|
| `1.1 Why Databases Matter` | recognition and recall of key terms, short scenario classification, brief justification of whether a database is needed |
| `1.2 From Business Process to Database` | workflow ordering, artifact-to-stage matching, ERD versus DBDD explanation |

## Module 2: SQL Foundations

| Lesson | Assessment Evidence |
|---|---|
| `2.1 The SQL Server Environment` | correct environment navigation, script execution in the right context, explanation of client and server roles |
| `2.2 Optional Review of Set Operations on Relations` | concept sorting, explanation of how set-based thinking supports later query work |
| `2.3 Single-Table Queries` | identify whether a query answers the intended question, explain why a wrong query is wrong, revise a flawed query |
| `2.4 Aggregates and Grouping` | distinguish row-level and summary questions, diagnose grouping mistakes, explain summarized output honestly |
| `2.5 Joins` | explain joined-row meaning, identify flawed join logic, connect join structure to the business question |
| `2.6 Common Table Expressions` | use a CTE appropriately in a simple query, explain the intermediate result set, judge whether the CTE improves readability and reasoning |

## Module 3: Core Data Modeling

| Lesson | Assessment Evidence |
|---|---|
| `3.1 Entities, Attributes, and Identifiers` | classify entities, attributes, and identifiers accurately, justify stronger identifier choices, reject weak labels |
| `3.2 Relationships and Cardinality` | match relationship patterns to business rules, justify cardinality and optionality, detect relationship errors |
| `3.3 Discovering Requirements and Drafting a Conceptual ERD` | identify must-track information from a case, detect omissions or overreach, defend conceptual ERD choices from case evidence |

## Module 4: Design Logic

| Lesson | Assessment Evidence |
|---|---|
| `4.1 Functional Dependencies` | explain FD statements clearly, justify dependency claims from business meaning, reject unsupported FD claims |
| `4.2 Keys of Relations` | determine reasonable keys, justify why one choice is a key and another is not, explain structural uniqueness |
| `4.3 Normalization and Design Repair` | diagnose anomalies, compare stronger and weaker decompositions, justify a design repair in business and structural terms |

## Module 5: Design Artifacts

| Lesson | Assessment Evidence |
|---|---|
| `5.1 Refining Conceptual ERDs in Crow's Foot Notation` | correct Crow's Foot notation, preserve conceptual ERD boundaries, explain what does not belong in the ERD |
| `5.2 Database Design Diagrams` | build a DBDD that reflects the conceptual model, place implementation-ready detail in the correct artifact, explain relationship-to-table mapping |
| `5.3 From Logical Model to Implementation-Ready Design` | judge ERD-to-DBDD alignment, diagnose mapping errors, defend implementation-ready choices |

## Module 6: SQL Server Implementation

| Lesson | Assessment Evidence |
|---|---|
| `6.1 Creating Tables and Constraints` | build tables and constraints in dependency-aware order, explain why order and constraints matter, verify the built schema against the DBDD |
| `6.2 Inserting, Updating, and Deleting Data` | execute controlled data changes correctly, identify risky or over-broad conditions, explain integrity failures or risks |
| `6.3 Building Views` | create or revise a view that answers the intended question, explain what the view output means, identify when a view distorts the business question |

## Module 7: Database Operation and Control

| Lesson | Assessment Evidence |
|---|---|
| `7.1 Roles, Users, and Permissions` | recommend appropriate access levels, reject over-permissioned choices, justify least privilege clearly |
| `7.2 Concurrency and Transactions` | diagnose multi-user integrity risks, explain transaction boundaries in plain language, justify commit and rollback choices |
| `7.3 Backup and Recovery Basics` | explain backup and recovery purpose accurately, choose a sensible basic response for a scenario, justify why one response is incomplete or risky |

## Module 8: Procedural Logic and Final Project Revision

| Lesson | Assessment Evidence |
|---|---|
| `8.1 Stored Procedures` | justify whether a procedure is warranted, build and test a simple procedure, explain why it is useful for repeated work |
| `8.2 Triggers` | justify whether a trigger is appropriate, explain trigger behavior clearly, detect overuse or weak trigger logic |
| `8.3 Final Project Integration and Revision` | detect cross-artifact inconsistency, revise the project after a change request, justify revisions and verify alignment across the full package |

## Implementation Note

Most lesson-level evidence should be low-stakes or embedded inside practice, quick checks, short explanations, or prep work for the module assessment. The main graded weight should remain at the module and course levels.
