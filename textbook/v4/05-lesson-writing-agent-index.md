# Lesson Writing Agent Index

Use this file as the canonical lesson manifest for AI writing agents in `v4`.

## Purpose

This file locks the naming convention, lesson slugs, and output paths used when an AI agent generates lesson materials. The goal is to prevent title drift, duplicate filenames, and inconsistent lesson output locations.

## Core Rule

For every lesson:

- the `lesson number` is the primary identifier
- the `canonical title` is display text
- the `canonical slug` is the stable lesson-folder key

Agents must not invent alternate slugs or output filenames.

## Standard Naming Convention

### Slug Style

Use:

- lowercase
- hyphen-separated words
- no spaces
- no punctuation except hyphens
- meaningful words preserved unless the canonical slug below says otherwise

Examples:

- `why-databases-matter`
- `from-business-process-to-database`
- `roles-users-and-permissions`

### Lesson Folder Pattern

Use this lesson-first pattern consistently:

`textbook/v4/modules/module-<two-digit-module>-<module-slug>/lessons/lesson-<two-digit-module>-<two-digit-lesson>-<canonical-slug>/`

Each lesson folder contains:

- `lesson.md`: student-facing lesson source
- `instructor.md`: instructor-facing notes
- `authoring-instructions.md`: AI/content-agent drafting prompt and constraints
- `import.yml`: workbook-player mapping for lesson segments, source sections, interactions, scoring mode, and ordering
- `assets/`: reserved for lesson-specific images, diagrams, or data files when needed

### Module File Pattern

Use this module-first pattern consistently:

- module plan file: `textbook/v4/modules-plan/0<module>-module-<module>-<module-slug>.md`
- module folder: `textbook/v4/modules/module-<two-digit-module>-<module-slug>/`
- student module source: `module.md`
- instructor module source: `instructor.md`
- module overview: `overview.md`

## Agent Workflow Rule

Before generating content, the agent should:

1. read this file
2. resolve the requested lesson number to the canonical lesson folder
3. write only to files inside that lesson folder unless the user explicitly requests a course- or module-level edit
4. keep the canonical title unchanged unless the user explicitly approves a rename
5. avoid creating duplicate files with alternate slugs

## Standard Handoff Package

For every lesson-writing assignment, provide these files:

- `textbook/v4/00-course-design-spec.md`
- `textbook/v4/01-module-content.md`
- `textbook/v4/02-instructional-strategies-for-lessons.md`
- `textbook/v4/05-lesson-writing-agent-index.md`
- `textbook/v4/06-design-object-naming-and-notation-conventions.md`
- `textbook/christian_integration_guide.md`
- the relevant module plan file listed below
- the relevant lesson folder listed below
- the lesson folder's `import.yml` file when the task affects workbook sequencing, block mapping, or knowledge-check placement

## Module Slug Registry

### Module 1

- module title: `The Whole Database Workflow`
- module slug: `the-whole-database-workflow`
- module folder: `textbook/v4/modules/module-01-the-whole-database-workflow`
- module plan file: `textbook/v4/modules-plan/01-module-1-the-whole-database-workflow.md`

### Module 2

- module title: `Module 2 Overview: SQL Foundations`
- module slug: `sql-foundations`
- module folder: `textbook/v4/modules/module-02-sql-foundations`
- module plan file: `textbook/v4/modules-plan/02-module-2-sql-foundations.md`

### Module 3

- module title: `Module 3 Overview: Core Data Modeling`
- module slug: `core-data-modeling`
- module folder: `textbook/v4/modules/module-03-core-data-modeling`
- module plan file: `textbook/v4/modules-plan/03-module-3-core-data-modeling.md`

### Module 4

- module title: `Module 4 Overview: Design Logic`
- module slug: `design-logic`
- module folder: `textbook/v4/modules/module-04-design-logic`
- module plan file: `textbook/v4/modules-plan/04-module-4-design-logic.md`

### Module 5

- module title: `Design Artifacts`
- module slug: `design-artifacts`
- module folder: `textbook/v4/modules/module-05-design-artifacts`
- module plan file: `textbook/v4/modules-plan/05-module-5-design-artifacts.md`

### Module 6

- module title: `Module 6 Overview: SQL Server Implementation`
- module slug: `sql-server-implementation`
- module folder: `textbook/v4/modules/module-06-sql-server-implementation`
- module plan file: `textbook/v4/modules-plan/06-module-6-sql-server-implementation.md`

### Module 7

- module title: `Module 7 Overview: Database Operation and Control`
- module slug: `database-operation-and-control`
- module folder: `textbook/v4/modules/module-07-database-operation-and-control`
- module plan file: `textbook/v4/modules-plan/07-module-7-database-operation-and-control.md`

### Module 8

- module title: `Module 8 Overview: Procedural Logic and Final Project Revision`
- module slug: `procedural-logic-and-final-project-revision`
- module folder: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision`
- module plan file: `textbook/v4/modules-plan/08-module-8-procedural-logic-and-final-project-revision.md`

## Lesson Registry

## Module 1

- Lesson `1.1`
  Canonical title: `Why Databases Matter`
  Canonical slug: `why-databases-matter`
  Lesson folder: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-01-why-databases-matter`
  Authoring instructions: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-01-why-databases-matter/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-01-why-databases-matter/lesson.md`
  Instructor notes: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-01-why-databases-matter/instructor.md`

- Lesson `1.2`
  Canonical title: `From Business Process to Database`
  Canonical slug: `from-business-process-to-database`
  Lesson folder: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-02-from-business-process-to-database`
  Authoring instructions: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-02-from-business-process-to-database/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-02-from-business-process-to-database/lesson.md`
  Instructor notes: `textbook/v4/modules/module-01-the-whole-database-workflow/lessons/lesson-01-02-from-business-process-to-database/instructor.md`

## Module 2

- Lesson `2.1`
  Canonical title: `The SQL Server Environment`
  Canonical slug: `the-sql-server-environment`
  Lesson folder: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-01-the-sql-server-environment`
  Authoring instructions: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-01-the-sql-server-environment/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-01-the-sql-server-environment/lesson.md`
  Instructor notes: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-01-the-sql-server-environment/instructor.md`

- Lesson `2.2`
  Canonical title: `Optional Review of Set Operations on Relations`
  Canonical slug: `optional-review-of-set-operations-on-relations`
  Lesson folder: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-02-optional-review-of-set-operations-on-relations`
  Authoring instructions: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-02-optional-review-of-set-operations-on-relations/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-02-optional-review-of-set-operations-on-relations/lesson.md`
  Instructor notes: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-02-optional-review-of-set-operations-on-relations/instructor.md`

- Lesson `2.3`
  Canonical title: `Single-Table Queries`
  Canonical slug: `single-table-queries`
  Lesson folder: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries`
  Authoring instructions: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/lesson.md`
  Instructor notes: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-03-single-table-queries/instructor.md`

- Lesson `2.4`
  Canonical title: `Aggregates and Grouping`
  Canonical slug: `aggregates-and-grouping`
  Lesson folder: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping`
  Authoring instructions: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/lesson.md`
  Instructor notes: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-04-aggregates-and-grouping/instructor.md`

- Lesson `2.5`
  Canonical title: `Joins`
  Canonical slug: `joins`
  Lesson folder: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-05-joins`
  Authoring instructions: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-05-joins/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-05-joins/lesson.md`
  Instructor notes: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-05-joins/instructor.md`

- Lesson `2.6`
  Canonical title: `Common Table Expressions`
  Canonical slug: `common-table-expressions`
  Lesson folder: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-06-common-table-expressions`
  Authoring instructions: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-06-common-table-expressions/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-06-common-table-expressions/lesson.md`
  Instructor notes: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-06-common-table-expressions/instructor.md`

## Module 3

- Lesson `3.1`
  Canonical title: `Entities, Attributes, and Identifiers`
  Canonical slug: `entities-attributes-and-identifiers`
  Lesson folder: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-01-entities-attributes-and-identifiers`
  Authoring instructions: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-01-entities-attributes-and-identifiers/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-01-entities-attributes-and-identifiers/lesson.md`
  Instructor notes: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-01-entities-attributes-and-identifiers/instructor.md`

- Lesson `3.2`
  Canonical title: `Relationships and Cardinality`
  Canonical slug: `relationships-and-cardinality`
  Lesson folder: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-02-relationships-and-cardinality`
  Authoring instructions: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-02-relationships-and-cardinality/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-02-relationships-and-cardinality/lesson.md`
  Instructor notes: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-02-relationships-and-cardinality/instructor.md`

- Lesson `3.3`
  Canonical title: `Discovering Requirements and Drafting a Conceptual ERD`
  Canonical slug: `discovering-requirements-and-drafting-a-conceptual-erd`
  Lesson folder: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-03-discovering-requirements-and-drafting-a-conceptual-erd`
  Authoring instructions: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-03-discovering-requirements-and-drafting-a-conceptual-erd/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-03-discovering-requirements-and-drafting-a-conceptual-erd/lesson.md`
  Instructor notes: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-03-discovering-requirements-and-drafting-a-conceptual-erd/instructor.md`

## Module 4

- Lesson `4.1`
  Canonical title: `Functional Dependencies`
  Canonical slug: `functional-dependencies`
  Lesson folder: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-01-functional-dependencies`
  Authoring instructions: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-01-functional-dependencies/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-01-functional-dependencies/lesson.md`
  Instructor notes: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-01-functional-dependencies/instructor.md`

- Lesson `4.2`
  Canonical title: `Keys of Relations`
  Canonical slug: `keys-of-relations`
  Lesson folder: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-02-keys-of-relations`
  Authoring instructions: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-02-keys-of-relations/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-02-keys-of-relations/lesson.md`
  Instructor notes: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-02-keys-of-relations/instructor.md`

- Lesson `4.3`
  Canonical title: `Normalization and Design Repair`
  Canonical slug: `normalization-and-design-repair`
  Lesson folder: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-03-normalization-and-design-repair`
  Authoring instructions: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-03-normalization-and-design-repair/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-03-normalization-and-design-repair/lesson.md`
  Instructor notes: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-03-normalization-and-design-repair/instructor.md`

## Module 5

- Lesson `5.1`
  Canonical title: `Refining Conceptual ERDs in Crow's Foot Notation`
  Canonical slug: `refining-conceptual-erds-in-crows-foot-notation`
  Lesson folder: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-01-refining-conceptual-erds-in-crows-foot-notation`
  Authoring instructions: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-01-refining-conceptual-erds-in-crows-foot-notation/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-01-refining-conceptual-erds-in-crows-foot-notation/lesson.md`
  Instructor notes: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-01-refining-conceptual-erds-in-crows-foot-notation/instructor.md`

- Lesson `5.2`
  Canonical title: `Database Design Diagrams`
  Canonical slug: `database-design-diagrams`
  Lesson folder: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-02-database-design-diagrams`
  Authoring instructions: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-02-database-design-diagrams/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-02-database-design-diagrams/lesson.md`
  Instructor notes: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-02-database-design-diagrams/instructor.md`

- Lesson `5.3`
  Canonical title: `From Logical Model to Implementation-Ready Design`
  Canonical slug: `from-logical-model-to-implementation-ready-design`
  Lesson folder: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-03-from-logical-model-to-implementation-ready-design`
  Authoring instructions: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-03-from-logical-model-to-implementation-ready-design/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-03-from-logical-model-to-implementation-ready-design/lesson.md`
  Instructor notes: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-03-from-logical-model-to-implementation-ready-design/instructor.md`

## Module 6

- Lesson `6.1`
  Canonical title: `Creating Tables and Constraints`
  Canonical slug: `creating-tables-and-constraints`
  Lesson folder: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-01-creating-tables-and-constraints`
  Authoring instructions: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-01-creating-tables-and-constraints/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-01-creating-tables-and-constraints/lesson.md`
  Instructor notes: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-01-creating-tables-and-constraints/instructor.md`

- Lesson `6.2`
  Canonical title: `Inserting, Updating, and Deleting Data`
  Canonical slug: `inserting-updating-and-deleting-data`
  Lesson folder: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-02-inserting-updating-and-deleting-data`
  Authoring instructions: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-02-inserting-updating-and-deleting-data/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-02-inserting-updating-and-deleting-data/lesson.md`
  Instructor notes: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-02-inserting-updating-and-deleting-data/instructor.md`

- Lesson `6.3`
  Canonical title: `Lesson 6.3 Building Views`
  Canonical slug: `building-views`
  Lesson folder: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-03-building-views`
  Authoring instructions: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-03-building-views/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-03-building-views/lesson.md`
  Instructor notes: `textbook/v4/modules/module-06-sql-server-implementation/lessons/lesson-06-03-building-views/instructor.md`

## Module 7

- Lesson `7.1`
  Canonical title: `Roles, Users, and Permissions`
  Canonical slug: `roles-users-and-permissions`
  Lesson folder: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-01-roles-users-and-permissions`
  Authoring instructions: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-01-roles-users-and-permissions/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-01-roles-users-and-permissions/lesson.md`
  Instructor notes: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-01-roles-users-and-permissions/instructor.md`

- Lesson `7.2`
  Canonical title: `Concurrency and Transactions`
  Canonical slug: `concurrency-and-transactions`
  Lesson folder: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-02-concurrency-and-transactions`
  Authoring instructions: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-02-concurrency-and-transactions/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-02-concurrency-and-transactions/lesson.md`
  Instructor notes: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-02-concurrency-and-transactions/instructor.md`

- Lesson `7.3`
  Canonical title: `Backup and Recovery Basics`
  Canonical slug: `backup-and-recovery-basics`
  Lesson folder: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-03-backup-and-recovery-basics`
  Authoring instructions: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-03-backup-and-recovery-basics/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-03-backup-and-recovery-basics/lesson.md`
  Instructor notes: `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-03-backup-and-recovery-basics/instructor.md`

## Module 8

- Lesson `8.1`
  Canonical title: `Stored Procedures`
  Canonical slug: `stored-procedures`
  Lesson folder: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-01-stored-procedures`
  Authoring instructions: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-01-stored-procedures/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-01-stored-procedures/lesson.md`
  Instructor notes: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-01-stored-procedures/instructor.md`

- Lesson `8.2`
  Canonical title: `Triggers`
  Canonical slug: `triggers`
  Lesson folder: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-02-triggers`
  Authoring instructions: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-02-triggers/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-02-triggers/lesson.md`
  Instructor notes: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-02-triggers/instructor.md`

- Lesson `8.3`
  Canonical title: `Final Project Integration and Revision`
  Canonical slug: `final-project-integration-and-revision`
  Lesson folder: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-03-final-project-integration-and-revision`
  Authoring instructions: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-03-final-project-integration-and-revision/authoring-instructions.md`
  Student lesson: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-03-final-project-integration-and-revision/lesson.md`
  Instructor notes: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-03-final-project-integration-and-revision/instructor.md`

## Rename Rule

If a lesson title changes later:

- keep the existing slug unless you explicitly approve a rename
- update display text first
- update links only after an intentional filename migration

This prevents the AI agent from creating duplicate lesson files from title drift.
