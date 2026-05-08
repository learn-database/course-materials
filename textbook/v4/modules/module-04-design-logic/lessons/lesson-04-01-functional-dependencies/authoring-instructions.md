# Lesson 4.1 Writing Instructions

## Canonical Lesson Identity

- Lesson number: `4.1`
- Canonical title: `Functional Dependencies`
- Canonical slug: `functional-dependencies`
- Module: `Module 4: Design Logic`

## Required Output Paths

- Instruction file: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-01-functional-dependencies/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-01-functional-dependencies/lesson.md`
- Instructor draft: `textbook/v4/modules/module-04-design-logic/lessons/lesson-04-01-functional-dependencies/instructor.md`

## Lesson Role In Module 4

This is the opening lesson for Module 4. It introduces the logic students need before they can reason about keys or judge decompositions. The lesson must frame normalization as design judgment, not as symbol pushing.

Students are coming from Module 3, where they learned to read requirements, identify entities and attributes, and draft conceptual ERDs. This lesson should reuse that business-analysis posture. It should teach students to ask which business thing determines a fact and whether a dependency claim is guaranteed by the business rules.

This lesson prepares directly for:

- Lesson `4.2`, where students reason about candidate keys
- Lesson `4.3`, where students diagnose anomalies and defend design repair
- the Module 4 normalization judgment task, where students must explain why a dependency set or decomposition is defensible

## Required Source Package

Read and use these files as the governing source package:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/04-module-4-design-logic.md`

## Primary Strategy

- Primary learning type: `Principles`
- Secondary learning type: `Concepts`
- Strategy pattern:
  - explain the governing rule
  - contrast defensible and indefensible cases
  - require judgment and justification
  - keep examples anchored in realistic business meaning

## Required Emphasis

The lesson must do all of the following:

- teach students to defend a dependency claim by pointing to a business rule
- teach students to reject a dependency claim when it is supported only by a short sample pattern
- distinguish structural truth from accidental sample-data regularity
- connect inconsistent copied facts to bad reporting, wasted effort, or harm to customers, staff, or service decisions
- keep the lesson at the dependency-reasoning level rather than drifting into full normalization procedure

## Required Content Boundaries

The lesson should include:

- what a functional dependency means in plain language
- the role of the determinant
- at least one accepted dependency claim tied to explicit business rules
- at least one rejected dependency claim that looks true in a sample but is not guaranteed by the business
- trivial dependencies as structurally true but usually weak for design diagnosis
- splitting and combining equivalent dependency statements

The lesson should not depend on:

- closure algorithms
- a full Armstrong's axioms treatment
- advanced normalization proof language
- implementation-level SQL constraint syntax as a substitute for dependency reasoning

## Case And Example Requirements

Use one small, realistic business case consistently enough that students can focus on reasoning instead of reloading context. The case should include:

- a compact relation schema
- a clear statement of what one row means
- explicit business rules
- a small sample that tempts students to infer a false dependency
- at least one consequence of inconsistent data that affects operations, reporting, or people

Examples must show the difference between:

- a dependency supported by business meaning
- a pattern that appears in the sample but is not justified
- a trivial dependency that is structurally true because the right side is already contained in the left side

## Christian Integration Guidance

Keep Christian integration embedded and brief. Appropriate touchpoints for this lesson include:

- truthfulness in reporting
- stewardship through reduced rework and reduced data inconsistency
- neighbor-serving systems that avoid preventable billing, scheduling, or service errors

Do not add a separate devotional section.

## Student Draft Requirements

The student draft should teach directly and include these sections:

- `# Lesson 4.1: Functional Dependencies`
- `## Lesson Overview`
- `## Why This Lesson Matters`
- `## Lesson Outcomes`
- `## How This Lesson Fits the Module`
- `## How This Lesson Fits the Larger Workflow`
- `## Key Terms`
- `## Readings and Media`
- `## Core Content`
- `## Examples and Case`
- `## Guided Practice`
- `## What to Do`
- `## Assignments`
- `## Deliverables`
- `## Project Checkpoint or Module Connection`
- `## Wrap-Up`

## Instructor Draft Requirements

The instructor draft should summarize instructional intent and include these sections:

- `# Lesson 4.1: Functional Dependencies`
- `## Instructor-Facing Content`
- `### Module`
- `### Lesson Purpose`
- `### Module Context`
- `### Primary Learning Type`
- `### Secondary Learning Type`
- `### Estimated Time`
- `### Lesson Outcomes`
- `### Module Alignment`
- `### Course Objective Alignment`
- `### Lesson Sequence Role`
- `### Required Prior Knowledge`
- `### Lesson Opening Guidance`
- `### Teaching Notes`
- `### Online Activities`
- `### Homework / Graded Assignments`
- `### Deliverables`
- `### Assessment Plan`
- `### Suggested Rubric Focus`
- `### Common Misconceptions`
- `### Christian Integration Notes`
- `### Workflow Connection`

## Acceptance Checklist

Before considering the lesson complete, confirm that:

- every major dependency claim is justified in business language
- at least one example exposes a sample pattern that looks like an FD but is not defensible
- at least one lesson touchpoint names the downstream impact of inconsistent data
- the lesson clearly supports the Module 4 normalization judgment assessment
- the lesson preserves the v4 AI-available rule by emphasizing explanation and judgment rather than artifact production alone
