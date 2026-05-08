# Lesson 3.3 Writing Instructions

## Lesson Identity

- Lesson number: `3.3`
- Canonical title: `Discovering Requirements and Drafting a Conceptual ERD`
- Canonical slug: `discovering-requirements-and-drafting-a-conceptual-erd`
- Module: `Module 3: Core Data Modeling`

## Output Paths

- Instruction file: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-03-discovering-requirements-and-drafting-a-conceptual-erd/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-03-discovering-requirements-and-drafting-a-conceptual-erd/lesson.md`
- Instructor draft: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-03-discovering-requirements-and-drafting-a-conceptual-erd/instructor.md`

## Required Source Order

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/03-module-3-core-data-modeling.md`
8. `textbook/v4/03-lesson-prompt.md`

## Lesson Role Inside Module 3

- This lesson completes Module 3.
- Lessons `3.1` and `3.2` introduced the parts of conceptual modeling.
- Lesson `3.3` requires students to use those parts together on a realistic case.
- The lesson should prepare students for Module 4 design-judgment work and Module 5 artifact-boundary work without drifting into implementation detail.

## Required Emphasis

- Teach careful case reading before diagramming.
- Teach scope control explicitly, including why some realistic details should stay out of the model.
- Show a clear process for moving from case facts and business rules to conceptual ERD choices.
- Keep the ERD conceptual:
  - include entities, significant attributes, relationships, cardinality, and optionality
  - exclude `PK`, `FK`, SQL data types, nullability, and other DBDD detail
- Connect requirement accuracy to human visibility, responsible service, and truthful representation.

## Required Practice And Assessment Elements

- Include at least one guided or critique element that asks what the case does **not** require the system to store.
- Include at least one project-style checkpoint that asks whether the proposed entities and relationships reflect the true work and people involved in the case.
- Because AI can draft plausible ERDs, require explanation, critique, and defense in addition to diagram production.
- Keep the major graded evidence aligned to the module strategy:
  - requirement interpretation
  - conceptual modeling judgment
  - critique of omissions, overreach, or boundary violations

## Suggested Case Direction

- Use a realistic business or service case with identifiable people, responsibilities, and scope boundaries.
- Include at least one detail that belongs to another system or is merely background noise.
- Include at least one dependent object that supports weak-entity reasoning at a conceptual level.

## Writing Reminders

- Follow the section structure required by `textbook/v4/03-lesson-prompt.md`.
- Keep Christian integration embedded in normal lesson elements, not as a stand-alone devotional section.
- Make the student-facing content strong enough for independent asynchronous study.
- Preserve the canonical title and paths exactly.
