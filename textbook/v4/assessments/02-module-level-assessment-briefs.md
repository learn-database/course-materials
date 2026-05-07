# Module-Level Assessment Briefs

## Purpose

This file defines the eight major module-level assessment artifacts for `v4`.

Each module assessment includes:

- the primary graded performance
- the secondary evidence type
- the artifact scope
- what students must explain or defend
- what should be graded

## Module 1: Case Framing Check

### Format

- timed quiz plus short written justification

### Prompt Shape

Students receive a short business scenario and must:

- decide whether the case calls for a database or a simpler tool
- identify the information the system must track
- place workflow stages in order
- distinguish which details belong in an ERD and which belong in a DBDD

### Secondary Evidence

- short artifact-boundary classification exercise
- one annotated scenario explanation

### Grade What Matters

- scenario classification
- workflow reasoning
- ERD versus DBDD distinction
- ability to name a trust, stewardship, or accountability implication when appropriate

## Module 2: Query Verification Lab

### Format

- candidate-query comparison with result interpretation

### Prompt Shape

Students receive multiple candidate queries and one business question. They must:

- choose the best query
- reject the others
- explain the failure mode in each wrong query
- interpret the result set in plain language

### Secondary Evidence

- timed quiz on query reading and result interpretation
- short clause-by-clause annotation of one query

### Grade What Matters

- business-question alignment
- recognition of incorrect filters, grouping, joins, or row duplication
- quality of result interpretation
- explanation of why a misleading result is a business-integrity problem

## Module 3: Model Critique and Defense

### Format

- critique-and-repair task plus short defense

### Prompt Shape

Students receive a short business case and a flawed conceptual ERD. They must:

- identify modeling errors
- revise the model
- defend selected fixes in writing or a short screencast

### Secondary Evidence

- timed concept check on entities, attributes, identifiers, and relationships
- conceptual-versus-irrelevant-detail classification task

### Grade What Matters

- entity and relationship identification
- identifier and cardinality justification
- error detection
- conceptual ERD boundary control
- ability to explain stakeholder harm or invisibility where relevant

## Module 4: Normalization Judgment Task

### Format

- decomposition comparison and design defense

### Prompt Shape

Students receive one relation, stated business rules, and two candidate decompositions. They must:

- identify valid dependencies
- determine keys
- explain anomalies
- defend which decomposition is stronger

### Secondary Evidence

- timed quiz on FD meaning and key logic
- short critique of a tidy-but-wrong decomposition

### Grade What Matters

- FD validity
- key justification
- anomaly diagnosis
- strength of the normalization decision
- ability to explain why a weak design damages consistency and trust

## Module 5: ERD versus DBDD Boundary Review

### Format

- classification, repair, and explanation task

### Prompt Shape

Students receive mixed-up design artifacts that blend conceptual and implementation-ready details. They must:

- classify which elements belong where
- repair the artifact split
- justify selected boundary decisions

### Secondary Evidence

- short screencast or annotation of one ERD-to-DBDD conversion choice
- timed artifact-boundary classification quiz

### Grade What Matters

- correctness of artifact classification
- explanation of why a detail belongs in one artifact and not the other
- translation quality from conceptual model to DBDD
- consistency of keys and relationships across both artifacts

## Module 6: Build-and-Verify Audit

### Format

- design-to-implementation audit

### Prompt Shape

Students receive a DBDD, a build script, sample outputs, and one or more failures or inconsistencies. They must:

- diagnose what is wrong
- propose corrections
- explain how to verify final alignment to the DBDD

### Secondary Evidence

- timed implementation quiz on dependency order and integrity behavior
- short annotation of one corrected schema or view decision

### Grade What Matters

- mismatch detection
- diagnosis of DDL, DML, or view problems
- explanation of why an error occurs
- verification logic against the approved design
- recognition of trust, privacy, or integrity problems even when code runs

## Module 7: Operations Decision Memo

### Format

- scenario-based memo plus short case checks

### Prompt Shape

Students receive a database operations scenario and must:

- recommend role access
- justify least privilege
- identify concurrency risks
- decide whether actions belong in one transaction
- explain a backup or recovery choice

### Secondary Evidence

- timed scenario quiz
- short comparison of a stronger and weaker operational plan

### Grade What Matters

- least-privilege reasoning
- transaction-boundary decisions
- multi-user integrity-risk identification
- practicality of backup and recovery recommendations
- ability to justify operational choices in terms of privacy, justice, accountability, and trust

## Module 8: Change Request Revision

### Format

- late-change revision and defense

### Prompt Shape

Students receive a late business-rule change after building or reviewing a project package. They must:

- explain what changes in the ERD, DBDD, SQL implementation, views, procedures, triggers, permissions, or tests
- submit the revised pieces
- justify the revisions

### Secondary Evidence

- short procedural-logic justification task
- annotation or screencast defending one stored-procedure or trigger decision

### Grade What Matters

- whether the procedural choice is justified
- quality of test reasoning
- completeness of cross-artifact revision
- clarity about what changed and why
- ability to explain whether the automation and final package are fair, bounded, accountable, and trustworthy

## Shared Module Rule

No module assessment should depend on a polished artifact alone. The scored work must reveal explanation, diagnosis, comparison, adaptation, verification, or a defensible judgment.
