# Lesson 7.3: Backup and Recovery Basics Instructions

## Canonical Lesson Identity

- Lesson number: `7.3`
- Canonical title: `Backup and Recovery Basics`
- Canonical slug: `backup-and-recovery-basics`
- Module: `Module 7: Database Operation and Control`

## Required Output Paths

- Instruction file:
  `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-03-backup-and-recovery-basics/authoring-instructions.md`
- Student draft:
  `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-03-backup-and-recovery-basics/lesson.md`
- Instructor draft:
  `textbook/v4/modules/module-07-database-operation-and-control/lessons/lesson-07-03-backup-and-recovery-basics/instructor.md`

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

Teach students what backups are for, what recovery is trying to accomplish,
and how to recommend a sensible introductory response when an organization
needs to protect records and resume work after loss, damage, or a bad change.

## Module Context

- This lesson follows Lesson `7.1`, where students learned least-privilege
  access decisions.
- This lesson follows Lesson `7.2`, where students learned how transactions
  and concurrency controls protect truthful records while work is in progress.
- This lesson closes Module 7 by asking what responsible operation looks like
  after failure still occurs.
- This lesson directly supports the Module 7 `Operations Decision Memo`,
  especially the part asking students to choose and justify a basic backup or
  recovery response in a realistic case.

## Primary Strategy

- Primary learning type: `Principles`
- Secondary learning type: `Facts`
- Strategy pattern:
  - scenario-based explanation
  - consequence comparison
  - response-choice justification

## Required Coverage

The lesson must explicitly teach:

- backup as protection against loss, corruption, accidental deletion, or
  damaging changes
- recovery as restoring needed data and usable service after a disruption
- restore as one action inside recovery rather than a synonym for recovery
- why backup alone is not the same as being ready to recover
- how continuity pressure and tolerance for lost recent work affect what counts
  as a sensible introductory response
- the limits of a weak backup plan, such as stale copies, slow recovery, or
  undocumented steps

## Required Emphasis

- Keep the lesson practical, introductory, and business-facing.
- Focus on choosing sensible responses and understanding limits.
- Connect backup and recovery to trust, continuity, and responsible care for
  organizational records.
- Require explanation and judgment rather than detailed administration steps.
- Keep SQL Server as the default course environment without turning the lesson
  into vendor-specific backup tooling instruction.

## Required Case Design

Use at least one realistic scenario in which students must choose and justify
an introductory backup or recovery response. Suitable contexts include:

- order processing
- tuition or payment posting
- scheduling
- donor or membership records
- inventory or service dispatch

The main case should let students:

- identify what records and work must be protected
- explain why downtime or lost recent changes would matter
- compare a weaker and stronger basic response
- justify which response is more sensible for the case
- name at least one limitation that still remains

## Required Student Work

The student draft must include:

- lesson overview and lesson outcomes
- module and workflow fit
- key terms
- direct teaching of backup purpose and recovery purpose
- at least one worked scenario
- guided practice with support
- an assignment that asks students to choose and justify a basic backup or
  recovery response
- a project checkpoint or module connection
- a wrap-up that reconnects the lesson to responsible database operation

## Assessment Expectations

Assessment should match the module strategy:

- formative checks should compare stronger and weaker responses
- graded work should be scenario-based, short, and explanation-focused
- at least one task must ask students to explain why a proposed response is
  incomplete or risky
- do not rely on a polished artifact alone as evidence of learning

## Christian Integration Expectations

Keep integration embedded inside ordinary lesson elements. Appropriate
touchpoints include:

- why responsible backup and recovery practices support organizational trust
- how careless protection of records can harm customers, employees, students,
  donors, or other stakeholders
- how faithful business work includes preserving truthful records and restoring
  service responsibly after disruption

Do not add a stand-alone devotional section.

## Boundaries And Exclusions

Keep the scope tight. Do not turn this lesson into advanced DBA operations.

Do not cover in depth:

- detailed SQL Server backup commands
- recovery models and point-in-time administration detail
- high-availability architectures
- replication, clustering, or failover design
- storage hardware planning
- vendor comparison beyond the default SQL Server framing

## Quality Checks

Before finalizing, confirm that:

- the lesson explains what backups are for and what recovery is trying to
  accomplish
- at least one scenario asks students to choose and justify a basic backup or
  recovery response
- the lesson explains why a backup plan can still be incomplete
- the student and instructor drafts use the canonical lesson title and paths
- the lesson remains aligned to the v4 async, AI-available,
  judgment-centered course model
