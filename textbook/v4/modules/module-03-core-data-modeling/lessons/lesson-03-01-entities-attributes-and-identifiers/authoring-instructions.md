# Lesson 3.1 Writing Instructions

## Canonical Lesson Identity

- Lesson number: `3.1`
- Canonical title: `Entities, Attributes, and Identifiers`
- Canonical slug: `entities-attributes-and-identifiers`
- Instruction file: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-01-entities-attributes-and-identifiers/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-01-entities-attributes-and-identifiers/lesson.md`
- Instructor draft: `textbook/v4/modules/module-03-core-data-modeling/lessons/lesson-03-01-entities-attributes-and-identifiers/instructor.md`

## Source Package

Read these sources before revising this lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/03-module-3-core-data-modeling.md`

## Lesson Role

This is the entry lesson for Module 3. It introduces conceptual data modeling by teaching students to:

- separate tracked things from descriptive facts
- judge whether a scenario element belongs as an entity or an attribute
- compare stronger and weaker identifier choices
- explain why a stronger identifier is stronger in business terms

This lesson prepares students for:

- Lesson `3.2`, where they reason about relationships, cardinality, optionality, and identifying relationships
- Lesson `3.3`, where they extract requirements and draft a first conceptual ERD
- the module critique-and-defense assessment, where they must repair and justify conceptual modeling choices instead of submitting a polished diagram alone

## Required Emphasis

The lesson must explicitly do all of the following:

- give students a repeatable way to distinguish entities from attributes
- compare identifier choices in terms of `uniqueness`, `stability`, and `business meaning`
- help students reject weak identifier choices with specific reasoning rather than vague preference
- keep the lesson at conceptual ERD scope and avoid implementation-ready detail such as `PK`, `FK`, SQL data types, or nullability
- connect careful modeling to visibility, responsible service, and truthful representation
- include at least one touchpoint that asks what or who becomes invisible when requirements are read carelessly

## Strategy Requirements

Use the Module 3 Lesson `3.1` strategy map from `textbook/v4/02-instructional-strategies-for-lessons.md`.

- Primary learning type: `Concepts`
- Secondary learning type: `Principles`
- Strategy pattern:
  - definition and classification
  - examples and non-examples
  - stronger-versus-weaker identifier comparison
- Practice type:
  - sort scenario elements into entities and attributes
  - compare identifier choices
  - justify classification decisions

The student-facing lesson should teach directly enough for independent online learning. It should not assume live lecture support.

## Content Boundaries

Keep the lesson focused on these core ideas:

- `Entity`
- `Attribute`
- `Identifier`
- `Instance`
- `Strong entity`
- `Weak entity`
- descriptive property versus tracked object

Keep weak entities at a conceptual level only. The lesson may preview identifying relationships in words, but it should not turn into a notation lesson.

## Case And Example Guidance

Use a consistent running case so students can compare decisions instead of restarting in each section.

The case should make it easy to show:

- a clear entity-versus-attribute contrast
- at least one borderline classification decision
- a stronger-versus-weaker identifier comparison
- at least one weak-entity example that depends on another entity for full identification
- a visibility prompt about whose needs or work disappear if the requirements are read carelessly

When listing conceptual examples, follow the shared naming conventions in `textbook/v4/06-design-object-naming-and-notation-conventions.md`.

## Student Draft Requirements

The student draft must include these sections:

- `Lesson overview`
- `Why this lesson matters`
- `Lesson outcomes`
- `How this lesson fits the module`
- `How this lesson fits the larger workflow`
- `Key terms`
- `Readings and media`
- `Core content`
- `Examples and case`
- `Guided practice`
- `What to do`
- `Assignments`
- `Deliverables`
- `Project checkpoint or module connection`
- `Wrap-up`

Inside the lesson, include:

- a repeatable classification method students can reuse on later cases
- examples and non-examples of entities and attributes
- direct comparison of stronger and weaker identifiers
- at least one reflection or critique prompt tied to visibility, faithful service, or truthful business representation
- a bridge statement that shows how better entity, attribute, and identifier choices make later relationship work and ERD critique easier

## Instructor Draft Requirements

The instructor draft must include these sections:

- `Module`
- `Lesson purpose`
- `Module context`
- `Primary learning type(s)`
- `Secondary learning type(s), if any`
- `Estimated time`
- `Lesson outcomes`
- `Module alignment`
- `Course objective alignment`
- `Lesson sequence role`
- `Required prior knowledge`
- `Lesson opening guidance`
- `Teaching notes`
- `Online activities`
- `Homework / graded assignments`
- `Deliverables`
- `Assessment plan`
- `Suggested rubric focus`
- `Common misconceptions`
- `Christian integration notes`
- `Workflow connection`

The instructor draft should:

- reconnect the lesson to the module critique-and-defense assessment
- show how AI can help generate candidate lists but not replace explanation and verification
- include grading criteria or a checklist aligned to the expected evidence

## Acceptance Checklist

Before considering the lesson complete, verify that:

- the student draft gives a repeatable method for entity-versus-attribute judgment
- identifier comparisons explicitly use uniqueness, stability, and business meaning
- the lesson asks students to explain why a weak identifier is weak
- the lesson remains conceptual and does not drift into DBDD detail
- at least one touchpoint asks what or who becomes invisible when requirements are read carelessly
- Christian integration stays embedded in ordinary instruction rather than in a separate devotional section
- the instructor draft includes a usable assessment plan and rubric focus
- both drafts clearly show how Lesson `3.1` supports Lessons `3.2` and `3.3` and the Module 3 critique-and-defense assessment
