# Lesson 8.3 Writing Instructions

## Canonical Lesson Identity

- Lesson number: `8.3`
- Canonical title: `Final Project Integration and Revision`
- Canonical slug: `final-project-integration-and-revision`
- Module: `Module 8: Procedural Logic and Final Project Revision`

## Required Source Package

Read these files before drafting or revising the lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/08-module-8-procedural-logic-and-final-project-revision.md`

## Lesson Role In Module 8

This is the capstone lesson for the course. Lessons 8.1 and 8.2 teach students to justify and test stored procedures and triggers. Lesson 8.3 must then make students review the entire project package as one coherent system and respond to a late business-rule change with defensible revisions.

The lesson must support the Module 8 assessment strategy: a polished package alone is weak evidence in an AI-available course, so the stronger evidence is adaptation, diagnosis, revision, and justification after a change request.

## Lesson Focus

Teach students how to:

- review the full project package instead of isolated files
- detect cross-artifact inconsistencies
- trace one business-rule change across the whole system
- revise the project after a late change request
- justify what changed, what did not change, and why
- evaluate whether the final package is coherent, honest about limitations, and trustworthy for the stated business purpose

## Required Emphasis

Make cross-artifact revision explicit across these artifact types as relevant to the case:

- requirements or business-rule statements
- ER Diagram
- Database Design Diagram
- SQL table and constraint scripts
- views
- stored procedures
- triggers
- permissions or role-based access choices
- tests or verification evidence

The lesson must not imply that every project always needs every artifact. It should instead teach students to decide which artifacts must change, which may remain unchanged, and how to justify both decisions.

## Strategy And Learning Type

- Primary learning type: `Problem solving / judgment`
- Secondary learning types: `Principles`, `Procedures`

Use the matching v4 pattern:

- authentic case
- modeled reasoning
- guided analysis
- independent application
- revision and rationale

## Student-Facing Requirements

The student lesson must:

- teach directly for asynchronous independent study
- explain why final revision is alignment work, not cosmetic cleanup
- connect the lesson to the full course workflow, especially workflow step 9: revise the solution when constraints or requirements change
- include at least one worked change-request example that asks which artifacts must change and why
- include guided practice that checks cross-artifact coherence
- include an assignment or checkpoint that asks whether the final package is coherent, honest about limitations, and trustworthy for the stated business purpose
- keep ER Diagram and Database Design Diagram boundaries explicit
- treat AI as available for drafting and checking, while still requiring human verification and judgment

## Instructor-Facing Requirements

The instructor draft must:

- explain how Lesson 8.3 completes Module 8 and the course
- align the lesson to the change-request revision assessment
- specify what evidence shows real understanding
- identify common failure patterns such as surface-only fixes, hidden naming drift, unsupported automation, missing tests, or unjustified permissions
- reinforce Christian integration through faithful professional follow-through, truthfulness, stewardship, and honest communication about limits

## Case Guidance

Use one late-change case that can plausibly touch multiple artifacts. A strong case should require students to ask whether the change affects:

- conceptual structure in the ERD
- implementation detail in the DBDD
- schema objects and constraints
- views or reporting outputs
- procedures or triggers
- permissions
- test coverage

At least one part of the case should require students to explain why an artifact does not need to change.

## Christian Integration Guidance

Keep integration inside normal teaching elements. Appropriate touchpoints include:

- why a coherent package matters for truthful business reporting and trustworthy service
- a warning that hiding known limitations or drift is not faithful professional work
- a project checkpoint asking whether the final package is honest, reviewable, and bounded appropriately

Do not add a separate devotional section.

## Deliverables

Write these files only:

- `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-03-final-project-integration-and-revision/authoring-instructions.md`
- `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-03-final-project-integration-and-revision/lesson.md`
- `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-03-final-project-integration-and-revision/instructor.md`

## Acceptance Checks

Before considering the lesson complete, confirm:

1. the lesson teaches students how to trace one business-rule change across the whole project package
2. at least one example or practice element asks which artifacts must change and why
3. at least one checkpoint asks whether the final package is coherent, honest about limitations, and trustworthy for the stated business purpose
4. the lesson preserves the ER Diagram versus Database Design Diagram distinction
5. the lesson treats late change, coherence, and justification as the core performance
6. the lesson meets the shared v4 standards for direct teaching, module context, guided practice, assignment alignment, and AI-available verification
