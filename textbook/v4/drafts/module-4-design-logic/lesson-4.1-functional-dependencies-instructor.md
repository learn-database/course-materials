# Lesson 4.1: Functional Dependencies

## Instructor-Facing Content

### Module

Module 4: Design Logic

### Lesson Purpose

Teach students to identify and defend functional dependencies by business
meaning. The lesson should train students to reject claims supported only by
sample patterns, distinguish trivial structural truth from useful design logic,
and connect inconsistent copied facts to reporting risk and avoidable business
harm.

### Module Context

This lesson opens Module 4. It inherits the business-rule mindset developed in
Module 3, where students learned to read requirements, identify entities and
attributes, and describe what the business tracks. Here that same mindset is
applied to relation logic: students must decide which determinant actually owns
each fact.

Lesson `4.1` prepares directly for Lesson `4.2`, where students reason about
candidate keys, and Lesson `4.3`, where they diagnose anomalies and compare
decompositions. It also supports the module's normalization judgment task,
which depends on a defensible dependency set.

### Primary Learning Type

Principles

### Secondary Learning Type

Concepts

### Estimated Time

75 to 90 minutes

### Lesson Outcomes

By the end of this lesson, students should be able to:

- explain a functional dependency in plain language
- identify the determinant in a dependency statement
- defend a dependency claim with a stated business rule
- reject a proposed dependency that is supported only by a short sample pattern
- distinguish trivial dependencies from meaningful design claims
- split and combine equivalent dependency statements without changing their
  meaning

### Module Alignment

- Introduces the dependency reasoning required by Module 4 before key logic and
  normalization repair.
- Supports the module objective of teaching design judgment rather than
  mechanical normalization.
- Prepares students for the primary graded assessment, where they must justify
  valid dependencies and defend a stronger decomposition.

### Course Objective Alignment

- Objective 1: know basic database terminology
- Objective 2: evaluate a business process and determine what data must be
  stored
- Objective 4: normalize a database design appropriately

### Lesson Sequence Role

Introduces core design-logic judgment for the module.

### Required Prior Knowledge

- ability to read a compact relation schema
- familiarity with attributes, identifiers, and business rules from Module 3
- basic understanding that one relation should represent one coherent row
  meaning

### Lesson Opening Guidance

Open with a misleadingly clean sample. Show three rows in which each
`TechnicianID` appears with one `VanID`, then ask whether that proves
`TechnicianID -> VanID`. Use the question to establish the lesson's central
warning: a short sample can suggest a pattern without proving a dependency.

After that opening, make students state what one row means before evaluating
any FD. That keeps the lesson grounded in business meaning instead of symbol
pattern-matching.

### Teaching Notes

- Keep the lesson anchored in one small business case so students can focus on
  reasoning, not context switching.
- Require students to say which business rule supports an accepted FD. Do not
  accept notation alone as full reasoning.
- Keep the distinction clear between:
  - defensible dependency claims
  - accidental sample regularities
  - trivial dependencies that are structurally true
- Do not drift into candidate-key derivation beyond brief forward reference.
  That belongs in Lesson `4.2`.
- Do not substitute SQL constraint language for FD reasoning. The lesson is
  about design logic, not implementation syntax.
- Revisit the business consequence of inconsistent copied facts at least once.
  Students should hear that design flaws can create billing, scheduling, or
  service errors for real people.

### Online Activities

- short LMS classification check: `defensible`, `sample-only`, or `trivial`
- short-answer prompt requiring one business-rule justification
- rewrite activity where students split and combine equivalent dependencies
- discussion or text-entry checkpoint on which copied fact would most damage
  trust if inconsistent

### Homework / Graded Assignments

#### Assignment 1: Dependency Judgment Check

Students analyze the `ServiceAppointment` relation and:

- identify at least four defensible FDs
- reject at least two weak claims
- identify one trivial dependency
- explain one false claim as a sample-only pattern

#### Assignment 2: Short Written Defense

Students write `200` to `300` words defending one accepted FD and rejecting one
weak FD in explicit business language.

These assignments fit the v4 AI-available model because they require judgment
and explanation, not just generated notation.

### Deliverables

- one dependency-judgment submission
- one short written defense paragraph

### Assessment Plan

Formative evidence:

- determinant identification
- translation of FD notation into plain business language
- classification of claims as defensible, sample-only, or trivial
- correct split/combine rewrites

Graded evidence:

- dependency-judgment submission
- short written defense paragraph

Evidence of learning is strong when students:

- connect each accepted FD to an explicit business rule
- reject sample-only claims without relying on intuition alone
- explain trivial dependencies as structurally true but limited in design value
- name downstream consequences of inconsistency in business terms

This lesson avoids over-relying on AI-generable work by grading explanation,
diagnosis, and justification rather than a notation list by itself.

### Suggested Rubric Focus

- accuracy of accepted and rejected FD judgments
- strength of business-rule justification
- clarity in distinguishing structural truth from sample coincidence
- accuracy of split/combine rewrites
- ability to name meaningful business impact from inconsistent data

### Common Misconceptions

- If a pattern appears in three rows, it must be a valid FD.
- Any attribute that looks unique in a sample is automatically a determinant.
- Trivial dependencies are especially important because they are always true.
- A larger combined dependency is always equivalent to the smaller original
  statements.
- FD notation and SQL referential constraints mean the same thing.

### Christian Integration Notes

Keep the integration brief and embedded. This lesson naturally supports:

- truthfulness in reporting, because copied facts that drift apart make reports
  unreliable
- stewardship of time and resources, because inconsistent data creates avoidable
  cleanup and repeated correction work
- neighbor-serving information systems, because wrong fees, schedules, or
  service details can directly affect customers and staff

Use these points inside normal teaching notes, common mistakes, or project
checkpoints rather than as a stand-alone reflection block.

### Workflow Connection

This lesson sits between conceptual analysis and later design repair. In the
end-to-end workflow, students have already learned to understand the business
process and identify required data. Now they are judging which facts belong to
which determinants. That judgment supports later key analysis, normalization,
ERD refinement, and implementation-ready design choices.
