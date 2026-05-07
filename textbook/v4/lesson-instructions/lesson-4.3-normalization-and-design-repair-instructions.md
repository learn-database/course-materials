# Lesson 4.3 Writing Instructions

## Canonical Lesson Identity

- Lesson number: `4.3`
- Canonical title: `Normalization and Design Repair`
- Canonical slug: `normalization-and-design-repair`

## Required Sources

Read these before drafting or revising the lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/03-lesson-prompt.md`
3. `textbook/v4/05-lesson-writing-agent-index.md`
4. `textbook/v4/modules-plan/04-module-4-design-logic.md`
5. `textbook/christian_integration_guide.md`

Use `textbook/v4/01-module-content.md`,
`textbook/v4/02-instructional-strategies-for-lessons.md`, and
`textbook/v4/06-design-object-naming-and-notation-conventions.md`
as supporting references for module context, strategy, and notation.

## Lesson Focus

Draft Lesson 4.3 as the module lesson on anomaly diagnosis and defensible
decomposition.

Teach normalization as a way to defend stronger design choices, not as a
mechanical sequence of table-splitting steps.

## Required Emphasis

- connect update, insertion, and deletion anomalies to concrete business
  consequences
- compare better and worse decompositions rather than presenting only one
  repair path
- show at least one tidy-looking decomposition that still breaks the intended
  business meaning
- reinforce that students must verify whether a decomposition preserves the
  meaning of the original relation, especially in an AI-available workflow
- briefly explain denormalization as an intentional reporting or data-warehouse
  design choice, usually for read-only or read-mostly databases, not as a
  replacement for normalized operational design
- include at least one project-style checkpoint tied to stewardship of time,
  resources, or trust

## Deliverables

Create these files:

- `textbook/v4/lesson-instructions/lesson-4.3-normalization-and-design-repair-instructions.md`
- `textbook/v4/drafts/module-4-design-logic/lesson-4.3-normalization-and-design-repair.md`
- `textbook/v4/drafts/module-4-design-logic/lesson-4.3-normalization-and-design-repair-instructor.md`

## Acceptance Targets

The student and instructor drafts should ensure that:

- students learn how to identify update, insertion, and deletion anomalies and
  explain why those anomalies matter
- at least one example or practice task contrasts a sound decomposition with a
  weak one
- at least one project checkpoint connects design repair to stewardship of
  organizational time, resources, or trust
- the lesson fits Module 4's assessment strategy of comparison, explanation,
  diagnosis, and normalization judgment
- the lesson distinguishes normalized operational source-of-truth tables from
  denormalized reporting or data-warehouse tables
- the lesson also meets the shared v4 lesson structure and quality rules

## Suggested Case Pattern

Use one main weak relation for the core repair path so students can see:

- anomaly diagnosis
- dependency interpretation
- key-aware repair
- comparison of alternative decompositions
- verification that the repaired design still expresses the intended business
  meaning

Include one short contrast case where a decomposition looks tidy but either:

- leaves a dependency problem behind, or
- loses the business meaning of the original relation

## Scope Boundaries

- Keep the lesson inside Module 4 design logic rather than turning it into a
  full ERD or DBDD lesson.
- Keep ER Diagram and Database Design Diagram references brief and contextual.
- BCNF remains in scope as the strongest functional-dependency-based checkpoint
  for this course.
- Intersection tables may appear as repair logic, but full artifact treatment
  belongs later.
- Denormalization should be treated as a brief professional judgment topic for
  reporting/data warehousing, not as a deep performance-tuning unit.
