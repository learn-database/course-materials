# Lesson 5.2 Instructions: Database Design Diagrams

## Canonical Lesson Identity

- Lesson number: `5.2`
- Canonical title: `Database Design Diagrams`
- Canonical slug: `database-design-diagrams`
- Instruction file: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-02-database-design-diagrams/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-02-database-design-diagrams/lesson.md`
- Instructor draft: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-02-database-design-diagrams/instructor.md`

## Lesson Purpose

Draft Lesson 5.2 as the implementation-ready design lesson for Module 5. The lesson should teach students how to convert conceptual structures into tables, primary keys, foreign keys, data types, nullability, and other implementation-ready details in a Database Design Diagram (`DBDD`).

The lesson must make the `DBDD` feel like a distinct artifact with a distinct job, not just a more detailed ERD.

## Required Source Package

Read and follow these files before revising the lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/05-module-5-design-artifacts.md`

## Module Context

- Module 5 preserves the conceptual-versus-implementation boundary while refining ERDs and building DBDDs.
- Lesson 5.1 prepared students to refine a conceptual ERD without implementation clutter.
- Lesson 5.2 introduces the implementation-ready details that belong in the DBDD itself.
- Lesson 5.3 will extend this work by treating ERD-to-DBDD conversion as a larger critique, repair, and justification task.
- Module assessment emphasizes boundary review, classification, repair, and explanation rather than polished artifact production alone.

## Instructional Strategy

- Primary learning type: `Procedures`
- Secondary learning type: `Principles`
- Strategy pattern:
  - modeled conversion from conceptual to implementation-ready detail
  - table and key explanation
  - guided artifact translation
- Practice type:
  - convert entities to tables
  - add PKs, FKs, data types, and nullability appropriately
  - explain implementation-ready detail
- Assessment evidence:
  - students build a DBDD that reflects the conceptual model
  - students place implementation-ready detail in the correct artifact
  - students explain how one relationship is carried into table structure

## Required Emphasis

- Make `PK`, `FK`, data type, and nullability decisions trace back to conceptual meaning.
- Keep the ERD versus DBDD boundary explicit throughout the lesson.
- Frame precision as protection against hidden operational errors.
- Keep the lesson business-facing and implementation-ready without drifting into full SQL syntax instruction.
- Reinforce that AI may help draft a DBDD, but students still need to verify, classify, and justify the design choices.

## Student-Facing Draft Requirements

The student lesson should:

- teach directly for independent online learning
- explain clearly what belongs in a DBDD that does not belong in a conceptual ERD
- show how conceptual entities and relationships become tables and keys
- tie data type and nullability choices to business meaning rather than guesswork
- explain at least one caution where conceptual optionality does not map to nullability in a simplistic way
- include at least one example or exercise that asks students to classify details as `ERD-only`, `DBDD-only`, `both`, or `neither`
- include a worked case with realistic business objects and implementation-ready reasoning
- connect design precision to trustworthy communication, faithful follow-through, and protection against hidden business errors

## Instructor-Facing Draft Requirements

The instructor lesson should:

- stay lean and implementation-focused
- explain how Lesson 5.2 fits between Lessons 5.1 and 5.3
- align activities and grading to the module's boundary-review assessment strategy
- emphasize explanation and justification, not diagram polish alone
- identify common misconceptions about ERD/DBDD boundaries, FK placement, data types, and nullability
- include at least one Christian integration touchpoint embedded in normal technical teaching or project checkpoints

## Acceptance Checklist

The lesson set is complete when all of the following are true:

- all three files exist at the canonical v4 paths
- the title and slug match the locked lesson registry exactly
- the lesson clearly explains what belongs in a DBDD that does not belong in a conceptual ERD
- table, `PK`, `FK`, data type, and nullability examples are tied to business meaning
- at least one example or exercise asks students to classify details as `ERD-only`, `DBDD-only`, `both`, or `neither`
- the student-facing lesson teaches directly and works without live lecture support
- the instructor-facing lesson does not duplicate the full student lesson
- practice and assessment guidance match Module 5's artifact-boundary strategy
- at least one Christian integration touchpoint appears inside normal technical instruction or checkpoints
- the lesson stays business-facing, technically grounded, and appropriate for ITM-2100
