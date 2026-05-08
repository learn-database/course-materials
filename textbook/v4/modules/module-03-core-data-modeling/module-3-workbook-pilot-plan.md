# Module 3 Workbook Pilot Plan

Status: draft  
Pilot scope: all Module 3 lessons plus KCE #6 as a standalone legacy lesson

## Goal

Pilot the full content-to-workbook workflow for Module 3 before scaling the importer to the rest of the course.

The pilot should prove that the platform can handle:

- multiple lessons in one module
- student-readable `lesson.md` flow
- `import.yml` as the runtime contract
- reading cards, case cards, written responses, and project checkpoints
- a standalone legacy KCE lesson imported from `dbm-materials/src` without copying it into the v4 lesson text
- all original questions from the legacy file

## Module 3 Lessons

| Lesson | Current source status | Pilot action |
|---|---|---|
| Lesson 3.1: Entities, Attributes, and Identifiers | `lesson.md` follows player flow; `import.yml` exists | import as a v4-native workbook lesson |
| Lesson 3.2: Relationships and Cardinality | `lesson.md` follows player flow; `import.yml` exists | keep as the reference implementation without embedded legacy KCE links |
| Lesson 3.3: Discovering Requirements and Drafting a Conceptual ERD | `lesson.md` follows player flow; `import.yml` exists | import as a v4-native workbook lesson |

## Legacy KCE #6 Lesson

Use `dbm-materials/src/lib/lessons/b21000601.json`.

KCE #6 should be imported as a fourth Module 3 lesson:

| Field | Value |
|---|---|
| Stable ID | `module-3.legacy-kce-6` |
| Title | `Knowledge Check Exercise #6` |
| Module | Module 3 |
| Lesson order | after Lesson 3.3 |
| Source | `legacy:dbm-materials/src/lib/lessons/b21000601.json` |
| Questions | all seven original questions |
| Runtime type | each legacy `self check` becomes a `checklist_interaction` |

Do not split KCE #6 questions across Lessons 3.1-3.3. Students should experience it as a practice lesson that belongs to Module 3.

## Lesson 3.1 Target Flow

Recommended player sequence:

1. `Before You Start`
2. `Tracked Things Versus Descriptive Facts`
3. `Identifier Judgment`
4. `Strong And Weak Entities`
5. `Model People And Responsibilities Carefully`
6. `Apply And Check Your Work`

Recommended interactions:

- existing guided practice for sorting scenario elements
- existing guided practice for comparing identifier choices
- existing guided practice for strong or weak entities
- project checkpoint for listing candidate entities, attributes, and identifiers in the student's project case

## Lesson 3.2 Target Flow

Current player sequence:

1. `Before You Start`
2. `Relationships Begin With Business Meaning`
3. `Relationship Patterns`
4. `Avoid False Business Stories`
5. `Model People Truthfully`

Recommended interactions:

- keep the existing relationship critique assignment as the main Lesson 3.2 evidence
- do not embed KCE #6 questions in this lesson; KCE #6 appears as its own module practice lesson

## Lesson 3.3 Target Flow

Recommended player sequence:

1. `Before You Start`
2. `Read For Purpose And Scope`
3. `Extract Must-Track Requirements`
4. `Draft The Conceptual ERD`
5. `Critique And Defend The Model`
6. `Project Transfer`

Recommended interactions:

- existing guided practice for separating facts, rules, and background
- existing guided practice for rejecting out-of-scope detail
- project checkpoint for a first-pass conceptual ERD and short defense

## Platform Work Required

The platform currently imports only Lesson 3.2. To pilot the whole module, update the workbook platform to:

1. Generalize the Lesson 3.2 importer into a reusable lesson-folder importer.
2. Import all lessons in `module-03-core-data-modeling/lessons`.
3. Read each lesson's `import.yml`.
4. Add support for standalone `legacy:` lesson sources that resolve decoded `dbm-materials/src/lib/lessons/b*.json`.
5. Convert every legacy question in the source file into a workbook interaction.
6. Convert legacy `self check` questions into `checklist_interaction`.
7. Preserve legacy sample solution content as feedback or expected result, not as initial visible answer.
8. Show imported Module 3 lessons on the dashboard as selectable lesson cards.
9. Keep the app using the latest imported course version.

## Acceptance Criteria

The pilot is complete when:

- Lesson 3.1, 3.2, and 3.3 each have an `import.yml`.
- `npm run import:module-3` imports all three v4 lessons plus KCE #6 into one course version.
- The dashboard lists all four Module 3 lessons.
- Opening each lesson shows reading blocks and interactions in the intended flow.
- KCE #6 appears as its own lesson and includes all seven original questions.
- No encoded legacy lesson files are required by the importer.
- The import can be repeated append-only, creating a new draft course version each time.

## Implementation Order

1. Create `import.yml` for Lesson 3.1 and Lesson 3.3.
2. Keep KCE #6 out of the v4 lesson `import.yml` files.
3. Generalize the importer in `workbook-platform`.
4. Implement standalone legacy KCE lesson conversion for all questions.
5. Import Module 3 and verify in the app UI.
6. Commit the content and platform changes together or in two coordinated commits.
