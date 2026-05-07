# Lesson 7.2: Concurrency and Transactions Instructions

## Canonical Lesson Identity

- Lesson number: `7.2`
- Canonical title: `Concurrency and Transactions`
- Canonical slug: `concurrency-and-transactions`
- Module: `Module 7: Database Operation and Control`

## Required Output Paths

- Instruction file: `textbook/v4/lesson-instructions/lesson-7.2-concurrency-and-transactions-instructions.md`
- Student draft: `textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.2-concurrency-and-transactions.md`
- Instructor draft: `textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.2-concurrency-and-transactions-instructor.md`

## Source Order

Read these sources before drafting or revising the lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/07-module-7-database-operation-and-control.md`

## Lesson Purpose

Teach students how multi-user work can damage data integrity, how to recognize a transaction as one unit of work, and how `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK` express trust-preserving operational decisions in SQL Server.

## Module Context

- This lesson follows Lesson `7.1`, where students learned least privilege and role-based access decisions.
- This lesson shifts the module from "who should be allowed to act" to "how shared work should be protected while people act at the same time."
- This lesson prepares Lesson `7.3`, where students will decide how backup and recovery support trustworthy operations after failure.
- This lesson directly supports the Module 7 `Operations Decision Memo`, especially the parts asking students to identify concurrency risks and justify when work should commit or roll back together.

## Primary Strategy

- Primary learning type: `Principles`
- Secondary learning type: `Procedures`
- Strategy pattern:
  - multi-user case analysis
  - transaction-boundary reasoning
  - small T-SQL transaction examples

## Required Coverage

The lesson must explicitly teach:

- concurrency as a multi-user integrity problem, not just a vocabulary word
- at least one concrete concurrency risk students can name clearly, such as overselling inventory, double-booking a time slot, or leaving status records out of sync
- transaction boundaries as a judgment question based on whether partial completion would create contradictory or incomplete data
- the plain-language meaning of `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK`
- commit versus rollback decisions tied to realistic operational outcomes
- isolation at a basic conceptual level only, as protection against harmful interference between overlapping work

## Required Emphasis

- Use realistic multi-user cases instead of isolated command syntax.
- Frame transactions as trust-preserving operational habits.
- Connect concurrency mistakes to integrity failures students can name clearly.
- Keep the lesson business-facing and operational rather than advanced-administration heavy.
- Require explanation and judgment, not just code pattern recognition.

## Required Case Design

Use at least one coherent scenario in which more than one user or process touches related data at nearly the same time. Suitable contexts include:

- warehouse allocation
- appointment scheduling
- service dispatch
- tuition or payment posting
- seat reservation

The main case should let students:

- identify the overlapping work
- name the likely integrity failure
- decide which actions belong in one transaction
- explain whether the case should end in `COMMIT` or `ROLLBACK`

Include one small T-SQL example, but keep it narrow and directly tied to the case.

## Required Student Work

The student draft must include:

- lesson overview and lesson outcomes
- module and workflow fit
- key terms
- direct teaching of concepts and principles
- at least one worked multi-user case
- guided practice with support
- an assignment that asks students to justify a commit or rollback outcome
- a project checkpoint or module connection
- a wrap-up that reconnects the lesson to responsible database operation

## Assessment Expectations

Assessment should match the module strategy:

- formative checks should diagnose concurrency risk and transaction-boundary reasoning
- graded work should be scenario-based, short, and explanation-focused
- at least one task must ask whether grouped work should be committed or rolled back as a unit
- do not rely on a polished SQL artifact alone as evidence of learning

## Christian Integration Expectations

Keep integration embedded inside ordinary lesson elements. Appropriate touchpoints include:

- why transaction habits preserve organizational trust
- how careless multi-user handling can misstate service, inventory, or payment reality
- how faithful business work includes protecting people and organizations from avoidable data contradictions

Do not add a stand-alone devotional section.

## Boundaries And Exclusions

Keep the scope tight. Do not turn this lesson into an advanced administration topic.

Do not cover in depth:

- deadlocks
- lock hints
- savepoints
- nested transactions
- distributed transactions
- detailed isolation-level tuning
- vendor comparison beyond the default SQL Server / T-SQL framing

## Quality Checks

Before finalizing, confirm that:

- the lesson explains when a set of actions belongs in one transaction
- at least one example asks students to decide whether work should commit or roll back as a unit
- the lesson names at least one concrete concurrency risk and its likely impact
- the student and instructor drafts use the canonical lesson title and paths
- the lesson remains aligned to the v4 async, AI-available, judgment-centered course model
