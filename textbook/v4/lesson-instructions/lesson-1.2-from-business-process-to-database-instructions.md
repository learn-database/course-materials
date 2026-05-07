# Lesson 1.2 Instructions: From Business Process to Database

## Canonical Lesson Identity

- Lesson number: `1.2`
- Canonical title: `From Business Process to Database`
- Canonical slug: `from-business-process-to-database`
- Instruction file: `textbook/v4/lesson-instructions/lesson-1.2-from-business-process-to-database-instructions.md`
- Student draft: `textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.2-from-business-process-to-database.md`
- Instructor draft: `textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.2-from-business-process-to-database-instructor.md`

## Purpose

Draft Lesson 1.2 as the workflow-bridge lesson that completes Module 1. The lesson should show students how the course moves from a business process to a working database and give them a reusable map for the rest of ITM-2100.

## Required Source Package

Read and apply these files:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/01-module-1-the-whole-database-workflow.md`

## Lesson Role Inside Module 1

- This lesson follows Lesson 1.1, which established why databases matter and when a database is warranted.
- This lesson gives students the whole-course workflow map before later modules study individual stages in depth.
- This lesson supports the Module 1 assessment pattern by preparing students to place workflow stages in order, classify artifacts correctly, and explain the ERD versus DBDD boundary in a timed setting.

## Required Emphasis

- keep the workflow explicit, memorable, and easy to revisit later
- make the ERD versus DBDD boundary unmistakable
- connect workflow discipline to organizational truthfulness, stewardship, and accountability
- show that polished artifacts are not enough; students must explain why each artifact belongs where it does

## Lesson Strategy

Use the Module 1 Lesson 1.2 strategy defined in `03-lesson-prompt.md` and `02-instructional-strategies-for-lessons.md`:

- Primary learning type: problem solving / judgment
- Secondary learning types: concepts and principles
- Strategy pattern:
  - whole-case walkthrough
  - modeled reasoning
  - guided case analysis
  - staged handoff explanation

## Content Requirements

The student-facing lesson must:

- walk through the full workflow from business process to working database use
- name the purpose of each stage, not just the stage label
- match artifacts and outputs to workflow stages
- explain what problem the ERD solves
- explain what additional implementation-ready detail the DBDD adds
- place implementation, querying, and introductory operational control after design
- include at least one quick-check or practice activity that asks students to place artifacts in the correct workflow stage
- include AI-aware verification guidance so students know they must check generated summaries, diagrams, and explanations

## Artifact Boundary Rules

Keep these distinctions explicit:

- ERD:
  - conceptual or logical artifact
  - entities
  - identifiers
  - significant attributes
  - relationships
  - cardinality
  - optionality
- DBDD:
  - implementation-ready artifact
  - tables
  - columns
  - primary keys
  - foreign keys
  - data types
  - nullability

Do not blur the artifacts or treat them as interchangeable.

## Suggested Case Direction

Use a simple recurring business case, such as a campus tutoring center, so students can track one scenario across the workflow:

- business need
- information to track
- likely entities and relationships
- ERD-level structure
- DBDD-level implementation detail
- later use through SQL, reporting, and operational control

## Christian Integration Expectations

Integrate the course-wide themes inside normal instruction:

- show that careful workflow discipline helps an organization tell the truth about its operations
- connect poor structure or skipped stages to wasted effort, distorted reporting, and avoidable harm to people who depend on accurate records
- keep the language business-facing and tied to technical choices

Do not add a stand-alone devotional section.

## Deliverables

Create all three files:

1. `textbook/v4/lesson-instructions/lesson-1.2-from-business-process-to-database-instructions.md`
2. `textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.2-from-business-process-to-database.md`
3. `textbook/v4/drafts/module-1-the-whole-database-workflow/lesson-1.2-from-business-process-to-database-instructor.md`

## Acceptance Criteria

The lesson is complete when:

- the lesson shows the full workflow from business process to working database
- the lesson clearly distinguishes the purpose of the ERD and the DBDD
- at least one practice or quick-check element asks students to place artifacts in the correct workflow stage
- the lesson preserves Module 1 context and prepares students for the module’s classification-based assessment
- the lesson meets shared v4 expectations for direct teaching, async readiness, and AI-aware verification
