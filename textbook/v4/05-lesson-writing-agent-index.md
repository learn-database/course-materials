# Lesson Writing Agent Index

Use this file as the canonical lesson manifest for AI writing agents in `v4`.

## Purpose

This file locks the naming convention, lesson slugs, and output paths used when an AI agent generates lesson materials. The goal is to prevent title drift, duplicate filenames, and inconsistent lesson output locations.

## Core Rule

For every lesson:

- the `lesson number` is the primary identifier
- the `canonical title` is display text
- the `canonical slug` is the stable filename key

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

### Lesson File Patterns

Use these patterns consistently:

- lesson instruction file: `textbook/v4/lesson-instructions/lesson-<module>.<lesson>-<canonical-slug>-instructions.md`
- student lesson draft: `textbook/v4/drafts/<module-folder>/lesson-<module>.<lesson>-<canonical-slug>.md`
- instructor lesson draft: `textbook/v4/drafts/<module-folder>/lesson-<module>.<lesson>-<canonical-slug>-instructor.md`

### Module File Patterns

Use these patterns consistently:

- module plan file: `textbook/v4/modules-plan/0<module>-module-<module>-<module-slug>.md`
- student module overview: `textbook/v4/drafts/<module-folder>/module-<module>-<module-slug>.md`
- instructor module overview: `textbook/v4/drafts/<module-folder>/module-<module>-<module-slug>-instructor.md`

## Agent Workflow Rule

Before generating content, the agent should:

1. read this file
2. resolve the requested lesson number to the canonical slug and output paths
3. write only to the declared paths
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

## Module Slug Registry

### Module 1

- module slug: `the-whole-database-workflow`
- module folder: `module-1-the-whole-database-workflow`
- module plan file: [textbook/v4/modules-plan/01-module-1-the-whole-database-workflow.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/01-module-1-the-whole-database-workflow.md)

### Module 2

- module slug: `sql-foundations`
- module folder: `module-2-sql-foundations`
- module plan file: [textbook/v4/modules-plan/02-module-2-sql-foundations.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/02-module-2-sql-foundations.md)

### Module 3

- module slug: `core-data-modeling`
- module folder: `module-3-core-data-modeling`
- module plan file: [textbook/v4/modules-plan/03-module-3-core-data-modeling.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/03-module-3-core-data-modeling.md)

### Module 4

- module slug: `design-logic`
- module folder: `module-4-design-logic`
- module plan file: [textbook/v4/modules-plan/04-module-4-design-logic.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/04-module-4-design-logic.md)

### Module 5

- module slug: `design-artifacts`
- module folder: `module-5-design-artifacts`
- module plan file: [textbook/v4/modules-plan/05-module-5-design-artifacts.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/05-module-5-design-artifacts.md)

### Module 6

- module slug: `sql-server-implementation`
- module folder: `module-6-sql-server-implementation`
- module plan file: [textbook/v4/modules-plan/06-module-6-sql-server-implementation.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/06-module-6-sql-server-implementation.md)

### Module 7

- module slug: `database-operation-and-control`
- module folder: `module-7-database-operation-and-control`
- module plan file: [textbook/v4/modules-plan/07-module-7-database-operation-and-control.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/07-module-7-database-operation-and-control.md)

### Module 8

- module slug: `procedural-logic-and-final-project-revision`
- module folder: `module-8-procedural-logic-and-final-project-revision`
- module plan file: [textbook/v4/modules-plan/08-module-8-procedural-logic-and-final-project-revision.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/modules-plan/08-module-8-procedural-logic-and-final-project-revision.md)

## Lesson Registry

## Module 1

- Lesson `1.1`
  Canonical title: `Why Databases Matter`
  Canonical slug: `why-databases-matter`
  Instruction file: [lesson-1.1-why-databases-matter-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-1.1-why-databases-matter-instructions.md)
  Student draft: [lesson-1.1-why-databases-matter.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.1-why-databases-matter.md)
  Instructor draft: [lesson-1.1-why-databases-matter-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.1-why-databases-matter-instructor.md)

- Lesson `1.2`
  Canonical title: `From Business Process to Database`
  Canonical slug: `from-business-process-to-database`
  Instruction file: [lesson-1.2-from-business-process-to-database-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-1.2-from-business-process-to-database-instructions.md)
  Student draft: [lesson-1.2-from-business-process-to-database.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.2-from-business-process-to-database.md)
  Instructor draft: [lesson-1.2-from-business-process-to-database-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.2-from-business-process-to-database-instructor.md)

## Module 2

- Lesson `2.1`
  Canonical title: `The SQL Server Environment`
  Canonical slug: `the-sql-server-environment`
  Instruction file: [lesson-2.1-the-sql-server-environment-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-2.1-the-sql-server-environment-instructions.md)
  Student draft: [lesson-2.1-the-sql-server-environment.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.1-the-sql-server-environment.md)
  Instructor draft: [lesson-2.1-the-sql-server-environment-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.1-the-sql-server-environment-instructor.md)

- Lesson `2.2`
  Canonical title: `Optional Review of Set Operations on Relations`
  Canonical slug: `optional-review-of-set-operations-on-relations`
  Instruction file: [lesson-2.2-optional-review-of-set-operations-on-relations-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-2.2-optional-review-of-set-operations-on-relations-instructions.md)
  Student draft: [lesson-2.2-optional-review-of-set-operations-on-relations.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.2-optional-review-of-set-operations-on-relations.md)
  Instructor draft: [lesson-2.2-optional-review-of-set-operations-on-relations-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.2-optional-review-of-set-operations-on-relations-instructor.md)

- Lesson `2.3`
  Canonical title: `Single-Table Queries`
  Canonical slug: `single-table-queries`
  Instruction file: [lesson-2.3-single-table-queries-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-2.3-single-table-queries-instructions.md)
  Student draft: [lesson-2.3-single-table-queries.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.3-single-table-queries.md)
  Instructor draft: [lesson-2.3-single-table-queries-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.3-single-table-queries-instructor.md)

- Lesson `2.4`
  Canonical title: `Aggregates and Grouping`
  Canonical slug: `aggregates-and-grouping`
  Instruction file: [lesson-2.4-aggregates-and-grouping-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-2.4-aggregates-and-grouping-instructions.md)
  Student draft: [lesson-2.4-aggregates-and-grouping.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.4-aggregates-and-grouping.md)
  Instructor draft: [lesson-2.4-aggregates-and-grouping-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.4-aggregates-and-grouping-instructor.md)

- Lesson `2.5`
  Canonical title: `Joins`
  Canonical slug: `joins`
  Instruction file: [lesson-2.5-joins-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-2.5-joins-instructions.md)
  Student draft: [lesson-2.5-joins.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.5-joins.md)
  Instructor draft: [lesson-2.5-joins-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.5-joins-instructor.md)

- Lesson `2.6`
  Canonical title: `Common Table Expressions`
  Canonical slug: `common-table-expressions`
  Instruction file: [lesson-2.6-common-table-expressions-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-2.6-common-table-expressions-instructions.md)
  Student draft: [lesson-2.6-common-table-expressions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.6-common-table-expressions.md)
  Instructor draft: [lesson-2.6-common-table-expressions-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-2-sql-foundations/lesson-2.6-common-table-expressions-instructor.md)

## Module 3

- Lesson `3.1`
  Canonical title: `Entities, Attributes, and Identifiers`
  Canonical slug: `entities-attributes-and-identifiers`
  Instruction file: [lesson-3.1-entities-attributes-and-identifiers-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-3.1-entities-attributes-and-identifiers-instructions.md)
  Student draft: [lesson-3.1-entities-attributes-and-identifiers.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-3-core-data-modeling/lesson-3.1-entities-attributes-and-identifiers.md)
  Instructor draft: [lesson-3.1-entities-attributes-and-identifiers-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-3-core-data-modeling/lesson-3.1-entities-attributes-and-identifiers-instructor.md)

- Lesson `3.2`
  Canonical title: `Relationships and Cardinality`
  Canonical slug: `relationships-and-cardinality`
  Instruction file: [lesson-3.2-relationships-and-cardinality-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-3.2-relationships-and-cardinality-instructions.md)
  Student draft: [lesson-3.2-relationships-and-cardinality.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-3-core-data-modeling/lesson-3.2-relationships-and-cardinality.md)
  Instructor draft: [lesson-3.2-relationships-and-cardinality-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-3-core-data-modeling/lesson-3.2-relationships-and-cardinality-instructor.md)

- Lesson `3.3`
  Canonical title: `Discovering Requirements and Drafting a Conceptual ERD`
  Canonical slug: `discovering-requirements-and-drafting-a-conceptual-erd`
  Instruction file: [lesson-3.3-discovering-requirements-and-drafting-a-conceptual-erd-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-3.3-discovering-requirements-and-drafting-a-conceptual-erd-instructions.md)
  Student draft: [lesson-3.3-discovering-requirements-and-drafting-a-conceptual-erd.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-3-core-data-modeling/lesson-3.3-discovering-requirements-and-drafting-a-conceptual-erd.md)
  Instructor draft: [lesson-3.3-discovering-requirements-and-drafting-a-conceptual-erd-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-3-core-data-modeling/lesson-3.3-discovering-requirements-and-drafting-a-conceptual-erd-instructor.md)

## Module 4

- Lesson `4.1`
  Canonical title: `Functional Dependencies`
  Canonical slug: `functional-dependencies`
  Instruction file: [lesson-4.1-functional-dependencies-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-4.1-functional-dependencies-instructions.md)
  Student draft: [lesson-4.1-functional-dependencies.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-4-design-logic/lesson-4.1-functional-dependencies.md)
  Instructor draft: [lesson-4.1-functional-dependencies-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-4-design-logic/lesson-4.1-functional-dependencies-instructor.md)

- Lesson `4.2`
  Canonical title: `Keys of Relations`
  Canonical slug: `keys-of-relations`
  Instruction file: [lesson-4.2-keys-of-relations-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-4.2-keys-of-relations-instructions.md)
  Student draft: [lesson-4.2-keys-of-relations.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-4-design-logic/lesson-4.2-keys-of-relations.md)
  Instructor draft: [lesson-4.2-keys-of-relations-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-4-design-logic/lesson-4.2-keys-of-relations-instructor.md)

- Lesson `4.3`
  Canonical title: `Normalization and Design Repair`
  Canonical slug: `normalization-and-design-repair`
  Instruction file: [lesson-4.3-normalization-and-design-repair-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-4.3-normalization-and-design-repair-instructions.md)
  Student draft: [lesson-4.3-normalization-and-design-repair.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-4-design-logic/lesson-4.3-normalization-and-design-repair.md)
  Instructor draft: [lesson-4.3-normalization-and-design-repair-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-4-design-logic/lesson-4.3-normalization-and-design-repair-instructor.md)

## Module 5

- Lesson `5.1`
  Canonical title: `Refining Conceptual ERDs in Crow's Foot Notation`
  Canonical slug: `refining-conceptual-erds-in-crows-foot-notation`
  Instruction file: [lesson-5.1-refining-conceptual-erds-in-crows-foot-notation-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-5.1-refining-conceptual-erds-in-crows-foot-notation-instructions.md)
  Student draft: [lesson-5.1-refining-conceptual-erds-in-crows-foot-notation.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-5-design-artifacts/lesson-5.1-refining-conceptual-erds-in-crows-foot-notation.md)
  Instructor draft: [lesson-5.1-refining-conceptual-erds-in-crows-foot-notation-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-5-design-artifacts/lesson-5.1-refining-conceptual-erds-in-crows-foot-notation-instructor.md)

- Lesson `5.2`
  Canonical title: `Database Design Diagrams`
  Canonical slug: `database-design-diagrams`
  Instruction file: [lesson-5.2-database-design-diagrams-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-5.2-database-design-diagrams-instructions.md)
  Student draft: [lesson-5.2-database-design-diagrams.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-5-design-artifacts/lesson-5.2-database-design-diagrams.md)
  Instructor draft: [lesson-5.2-database-design-diagrams-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-5-design-artifacts/lesson-5.2-database-design-diagrams-instructor.md)

- Lesson `5.3`
  Canonical title: `From Logical Model to Implementation-Ready Design`
  Canonical slug: `from-logical-model-to-implementation-ready-design`
  Instruction file: [lesson-5.3-from-logical-model-to-implementation-ready-design-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-5.3-from-logical-model-to-implementation-ready-design-instructions.md)
  Student draft: [lesson-5.3-from-logical-model-to-implementation-ready-design.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-5-design-artifacts/lesson-5.3-from-logical-model-to-implementation-ready-design.md)
  Instructor draft: [lesson-5.3-from-logical-model-to-implementation-ready-design-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-5-design-artifacts/lesson-5.3-from-logical-model-to-implementation-ready-design-instructor.md)

## Module 6

- Lesson `6.1`
  Canonical title: `Creating Tables and Constraints`
  Canonical slug: `creating-tables-and-constraints`
  Instruction file: [lesson-6.1-creating-tables-and-constraints-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-6.1-creating-tables-and-constraints-instructions.md)
  Student draft: [lesson-6.1-creating-tables-and-constraints.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.1-creating-tables-and-constraints.md)
  Instructor draft: [lesson-6.1-creating-tables-and-constraints-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.1-creating-tables-and-constraints-instructor.md)

- Lesson `6.2`
  Canonical title: `Inserting, Updating, and Deleting Data`
  Canonical slug: `inserting-updating-and-deleting-data`
  Instruction file: [lesson-6.2-inserting-updating-and-deleting-data-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-6.2-inserting-updating-and-deleting-data-instructions.md)
  Student draft: [lesson-6.2-inserting-updating-and-deleting-data.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.2-inserting-updating-and-deleting-data.md)
  Instructor draft: [lesson-6.2-inserting-updating-and-deleting-data-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.2-inserting-updating-and-deleting-data-instructor.md)

- Lesson `6.3`
  Canonical title: `Building Views`
  Canonical slug: `building-views`
  Instruction file: [lesson-6.3-building-views-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-6.3-building-views-instructions.md)
  Student draft: [lesson-6.3-building-views.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.3-building-views.md)
  Instructor draft: [lesson-6.3-building-views-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.3-building-views-instructor.md)

## Module 7

- Lesson `7.1`
  Canonical title: `Roles, Users, and Permissions`
  Canonical slug: `roles-users-and-permissions`
  Instruction file: [lesson-7.1-roles-users-and-permissions-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-7.1-roles-users-and-permissions-instructions.md)
  Student draft: [lesson-7.1-roles-users-and-permissions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.1-roles-users-and-permissions.md)
  Instructor draft: [lesson-7.1-roles-users-and-permissions-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.1-roles-users-and-permissions-instructor.md)

- Lesson `7.2`
  Canonical title: `Concurrency and Transactions`
  Canonical slug: `concurrency-and-transactions`
  Instruction file: [lesson-7.2-concurrency-and-transactions-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-7.2-concurrency-and-transactions-instructions.md)
  Student draft: [lesson-7.2-concurrency-and-transactions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.2-concurrency-and-transactions.md)
  Instructor draft: [lesson-7.2-concurrency-and-transactions-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.2-concurrency-and-transactions-instructor.md)

- Lesson `7.3`
  Canonical title: `Backup and Recovery Basics`
  Canonical slug: `backup-and-recovery-basics`
  Instruction file: [lesson-7.3-backup-and-recovery-basics-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-7.3-backup-and-recovery-basics-instructions.md)
  Student draft: [lesson-7.3-backup-and-recovery-basics.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.3-backup-and-recovery-basics.md)
  Instructor draft: [lesson-7.3-backup-and-recovery-basics-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.3-backup-and-recovery-basics-instructor.md)

## Module 8

- Lesson `8.1`
  Canonical title: `Stored Procedures`
  Canonical slug: `stored-procedures`
  Instruction file: [lesson-8.1-stored-procedures-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-8.1-stored-procedures-instructions.md)
  Student draft: [lesson-8.1-stored-procedures.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.1-stored-procedures.md)
  Instructor draft: [lesson-8.1-stored-procedures-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.1-stored-procedures-instructor.md)

- Lesson `8.2`
  Canonical title: `Triggers`
  Canonical slug: `triggers`
  Instruction file: [lesson-8.2-triggers-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-8.2-triggers-instructions.md)
  Student draft: [lesson-8.2-triggers.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.2-triggers.md)
  Instructor draft: [lesson-8.2-triggers-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.2-triggers-instructor.md)

- Lesson `8.3`
  Canonical title: `Final Project Integration and Revision`
  Canonical slug: `final-project-integration-and-revision`
  Instruction file: [lesson-8.3-final-project-integration-and-revision-instructions.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/lesson-instructions/lesson-8.3-final-project-integration-and-revision-instructions.md)
  Student draft: [lesson-8.3-final-project-integration-and-revision.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.3-final-project-integration-and-revision.md)
  Instructor draft: [lesson-8.3-final-project-integration-and-revision-instructor.md](/Users/hye/Documents/GitHub/dbm-materials/textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.3-final-project-integration-and-revision-instructor.md)

## Rename Rule

If a lesson title changes later:

- keep the existing slug unless you explicitly approve a rename
- update display text first
- update links only after an intentional filename migration

This prevents the AI agent from creating duplicate lesson files from title drift.
