# Learn Database Course Materials

This repository is the content-development home for the Learn Database course materials.

## How This Repository Is Used

Use this repository for course content development, review, and versioning.

This repo answers:

- What should the course teach?
- What are the modules, lessons, cases, assignments, and assessments?
- What is the official student-facing and instructor-facing content?
- What source material should the interactive workbook and LMS platform use?

Do not use this repo for the production web application, LTI integration, Canvas grade passback, or student response storage. Those belong in the separate `learn-database/workbook-platform` repository.

## Source Of Truth

The Markdown files in this repo are the source of truth for course content.

The future interactive workbook should be generated from, or explicitly aligned to, these files. Do not treat generated workbook JSON, LMS pages, or platform database records as the canonical authoring source.

Recommended content flow:

```text
course-materials
  Markdown drafts, cases, assignments, assessments
        |
        | validate / transform / publish
        v
workbook-platform
  interactive workbook runtime, LTI launch, grades, analytics
```

## Repository Structure

- `textbook/v4/`: v4 course design, module plans, lesson drafts, activities, assignments, assessments, cases, and lesson-writing instructions.
- `textbook/christian_integration_guide.md`: course-wide Christian integration guide used by v4 authoring.
- `textbook/curriculum_crosswalk.md`: crosswalk between existing materials and course coverage.
- `textbook/references.md`: shared references.
- `textbook/textbook_review_rubric.md`: review rubric for textbook materials.
- `textbook/course-material-plan-workflow.md`: planning and workflow notes.
- `textbook/agents.md`: agent-oriented authoring notes.

Important v4 folders:

- `textbook/v4/modules/`: lesson-first module folders containing student lessons, instructor notes, and authoring instructions.
- `textbook/v4/modules-plan/`: module-level instructional plans.
- `textbook/v4/cases/`: running course cases, including Lakeside Tutoring Center and Cedar Valley Community Clinic.
- `textbook/v4/activities/`: lesson-level activity patterns.
- `textbook/v4/assignments/`: actual assignment drafts by module.
- `textbook/v4/assessments/`: lesson-, module-, and course-level assessment plans.

Lesson-first v4 pattern:

```text
textbook/v4/modules/module-03-core-data-modeling/
  overview.md
  module.md
  instructor.md
  lessons/
    lesson-03-02-relationships-and-cardinality/
      lesson.md
      instructor.md
      authoring-instructions.md
      import.yml
```

## Authoring Workflow

Use this workflow for ordinary content changes:

1. Edit the relevant Markdown source files.
2. Check related files for alignment.
3. Keep Lakeside as the primary running case unless a lesson explicitly calls for the clinic alternative.
4. Keep Christian integration inside normal instructional elements, using `textbook/christian_integration_guide.md`.
5. Commit the content change with a clear message.
6. When the workbook platform exists, run the content validation/publish process before deploying.

For a lesson update, check at least these files:

```text
textbook/v4/modules/module-XX-{module-slug}/lessons/lesson-XX-YY-{lesson-slug}/lesson.md
textbook/v4/modules/module-XX-{module-slug}/lessons/lesson-XX-YY-{lesson-slug}/instructor.md
textbook/v4/modules/module-XX-{module-slug}/lessons/lesson-XX-YY-{lesson-slug}/authoring-instructions.md
textbook/v4/modules/module-XX-{module-slug}/lessons/lesson-XX-YY-{lesson-slug}/import.yml
textbook/v4/activities/01-lesson-assignments-and-activities.md
textbook/v4/assignments/module-n-assignments.md
textbook/v4/assessments/
```

For a case update, check:

```text
textbook/v4/cases/
textbook/v4/modules/
textbook/v4/assignments/
textbook/v4/activities/
```

## Relationship To The Workbook Platform

The `workbook-platform` repo should consume this repo's content. It should not become the main authoring location.

Planned responsibilities:

- `course-materials`: authored course content, workbook source, cases, assignments, and reviewable changes.
- `workbook-platform`: Next.js/NestJS app, database, LTI 1.3 integration, Canvas grade passback, student attempts, and analytics.

Future publishing model:

```text
Markdown/YAML in course-materials
        |
        | content build script
        v
validated workbook package
        |
        | publish
        v
platform database / runtime JSON
```

## Content Development Rules

- Preserve the v4 course objectives. Do not invent new course objectives unless the official course design changes.
- Keep v4 naming conventions consistent with `textbook/v4/06-design-object-naming-and-notation-conventions.md`.
- Use Lakeside Tutoring Center as the primary case.
- Use Cedar Valley Community Clinic as the alternative, advanced, or discussion case.
- Treat recursive hierarchy as self-referencing `1:N`.
- Treat recursive network as self-referencing `M:N` / `N:M`.
- Treat denormalization as a deliberate reporting or data-warehouse choice, usually for read-only or read-mostly scenarios.
- Keep instructor-facing content lean. Do not repeat the full student-facing lesson unless the instructor needs different guidance.
- Avoid artifact-only assignments when AI can generate the artifact easily. Prefer reasoning, critique, verification, revision, and defense.

## AI Agent Guidance

When using an AI agent to draft or revise content:

1. Give the agent the relevant lesson folder and `authoring-instructions.md`.
2. Give the agent the module plan and course design spec.
3. Tell the agent whether it is drafting student-facing or instructor-facing content.
4. Require alignment with the Lakeside/clinic case strategy.
5. Review the output for course objective alignment, Christian integration, assessment alignment, and naming consistency.

The `authoring-instructions.md` file inside each lesson folder is the best starting point for content-generation prompts.
