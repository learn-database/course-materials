# Lesson 5.1 Writing Instructions

## Canonical Lesson Identity

- Lesson number: `5.1`
- Canonical title: `Refining Conceptual ERDs in Crow's Foot Notation`
- Canonical slug: `refining-conceptual-erds-in-crows-foot-notation`
- Module: `Module 5: Design Artifacts`

## Required Output Paths

- Student draft: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-01-refining-conceptual-erds-in-crows-foot-notation/lesson.md`
- Instructor draft: `textbook/v4/modules/module-05-design-artifacts/lessons/lesson-05-01-refining-conceptual-erds-in-crows-foot-notation/instructor.md`

## Source Package

Read these before drafting:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/05-module-5-design-artifacts.md`

## Lesson Role In Module 5

Lesson 5.1 is the notation-refinement lesson for conceptual models. Students already built a first conceptual ERD earlier in the course. This lesson teaches them how to improve that ERD by correcting Crow's Foot notation, clarifying identifiers and significant attributes, and removing conceptual-boundary violations without turning the ERD into a DBDD.

This lesson should repeatedly signal:

- it follows the first conceptual ERD work from Module 3
- it applies the design-discipline habits reinforced in Module 4
- it prepares students for Lesson 5.2, where implementation-ready DBDD detail is introduced as a separate artifact

## Required Emphasis

- reinforce that notation improvement does not justify implementation detail drift
- keep examples visually and conceptually clear
- connect model clarity to trustworthy communication and professional follow-through
- preserve the ERD versus DBDD boundary in every example, prompt, and assignment

## Strategy Requirements

Use the Lesson 5.1 strategy from `02-instructional-strategies-for-lessons.md`:

- Primary learning type: `Procedures`
- Secondary learning type: `Principles`
- Strategy pattern:
  - notation review
  - guided refinement
  - critique of conceptual-boundary drift

The student draft must therefore show a repeatable refinement process, not just list qualities of a good ERD.

## Content Requirements

The lesson must teach students how to:

- read Crow's Foot notation in plain language
- verify cardinality and optionality from business rules rather than visual habit
- refine conceptual identifiers and significant attributes
- remove implementation clutter from a conceptual ERD
- keep the ERD readable without forcing implementation-style formatting choices

The lesson must include:

- at least one example or critique item asking students to remove implementation clutter from a conceptual ERD
- at least one touchpoint asking whether another person could understand the model without guesswork
- at least one connection between clear modeling and trustworthy professional communication

## Boundary Rules

The lesson must keep the ERD conceptual. It may include:

- entities
- conceptual identifiers
- significant attributes
- relationships
- cardinality
- optionality

It must explicitly exclude implementation-ready detail such as:

- `PK`
- `FK`
- SQL data types
- nullability markers
- table-level implementation annotations

## Christian Integration Guidance

Apply the module focus and course guide in ordinary teaching elements. Keep the integration subordinate to the technical lesson. Good fits for this lesson include:

- why diagram clarity matters for trustworthy communication
- critique prompts about whether another reviewer could understand the model without guesswork
- project checkpoint language about faithful professional follow-through and protecting others from confusion caused by weak design communication

Do not add a stand-alone devotional section.

## Assessment Alignment

The lesson should support Module 5's boundary-review assessment by requiring students to:

- identify details that belong in the ERD versus the DBDD
- repair a conceptual ERD that has drifted toward implementation detail
- explain why a refinement improves conceptual clarity instead of merely making the diagram look more technical

Because AI can help clean up diagrams quickly, require second evidence through explanation, critique, classification, or short written justification.

## Deliverable Expectations

### Student Draft

Create a complete LMS-ready student lesson with these sections:

- Lesson overview
- Why this lesson matters
- Lesson outcomes
- How this lesson fits the module
- How this lesson fits the larger workflow
- Key terms
- Readings and media
- Core content
- Examples and case
- Guided practice
- What to do
- Assignments
- Deliverables
- Project checkpoint or module connection
- Wrap-up

### Instructor Draft

Create a separate instructor-facing lesson file with these sections:

- Module
- Lesson purpose
- Module context
- Primary learning type(s)
- Secondary learning type(s)
- Estimated time
- Lesson outcomes
- Module alignment
- Course objective alignment
- Lesson sequence role
- Required prior knowledge
- Lesson opening guidance
- Teaching notes
- Online activities
- Homework / graded assignments
- Deliverables
- Assessment plan
- Suggested rubric focus
- Common misconceptions
- Christian integration notes
- Workflow connection

## Acceptance Checklist

Before considering the lesson complete, confirm:

- the lesson teaches how to refine notation while preserving conceptual scope
- the lesson shows that improved notation is not permission to add implementation detail
- the lesson includes removal of implementation clutter from a conceptual ERD
- the lesson asks whether another person could understand the model without guesswork
- the lesson aligns with Module 5's trust-and-follow-through emphasis
- the student and instructor drafts use the canonical lesson title and output paths
