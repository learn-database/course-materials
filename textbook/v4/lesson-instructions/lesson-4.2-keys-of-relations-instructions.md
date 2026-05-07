# Lesson 4.2 Writing Instructions: Keys of Relations

## Canonical Lesson Identity

- Lesson number: `4.2`
- Canonical title: `Keys of Relations`
- Canonical slug: `keys-of-relations`
- Module: `Module 4: Design Logic`

## Required Output Paths

- Instruction file: `textbook/v4/lesson-instructions/lesson-4.2-keys-of-relations-instructions.md`
- Student draft: `textbook/v4/drafts/module-4-design-logic/lesson-4.2-keys-of-relations.md`
- Instructor draft: `textbook/v4/drafts/module-4-design-logic/lesson-4.2-keys-of-relations-instructor.md`

## Source Package

Read these sources before drafting or revising the lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/04-module-4-design-logic.md`

## Lesson Role In Module 4

Lesson 4.2 sits between Lesson 4.1 on functional dependencies and Lesson 4.3 on normalization and design repair.

- It inherits dependency reasoning from Lesson 4.1.
- It prepares students to judge partial dependency, transitive dependency, and anomaly claims in Lesson 4.3.
- It supports the module's primary graded assessment by making students defend key claims instead of treating normalization as symbol pushing.

## Primary Strategy

- Primary learning type: `Principles`
- Secondary learning type: `Concepts`
- Strategy pattern:
  - key reasoning walkthrough
  - contrasting candidate keys and weak choices
  - decision justification

## Required Emphasis

The lesson must:

- teach students to identify and defend candidate keys from business meaning and dependency logic
- compare strong and weak key candidates in business terms, not only in formal notation
- keep the focus on reasoning rather than memorized jargon
- use prime-attribute language only to the extent needed for later relational reasoning
- show how weak key logic creates structural confusion in later normalization work
- include at least one practice element in which students reject a plausible but weak key candidate

## Scope Boundaries

Keep the lesson focused on relational key reasoning.

- Do explain `superkey`, `candidate key`, `minimality`, `attribute closure`, and `prime attribute`.
- Do not turn the lesson into a full normalization lesson.
- Do not drift into implementation-only primary key selection advice.
- Do not rely on sample-data uniqueness as the main basis for a key claim.
- Do not overload the lesson with prime-attribute terminology beyond what students need for later dependency analysis.

## Content Expectations

The student-facing lesson should:

- start from what one row means before naming likely keys
- model a repeatable process for testing candidate keys
- contrast at least one strong key candidate with at least one plausible but weak candidate
- explain why weak candidates often borrow descriptive or changeable attributes that do not truly define the row
- connect key reasoning to later anomaly diagnosis and normalization judgment

The instructor-facing lesson should:

- explain why the lesson sits where it does in Module 4
- name what students often confuse about sufficiency, minimality, and "looks unique"
- align practice and grading to the module's normalization judgment task
- include Christian integration notes that stay subordinate to the technical goal and connect weak key logic to trust, waste, or untrustworthy reporting

## Recommended Case Direction

Use one compact business case that makes the row grain explicit and supports both strong and weak key proposals.

Recommended pattern:

- one row means one student's registration in one specific section
- a strong candidate key respects that grain
- plausible weak candidates ignore the grain or rely on descriptive contact data that can change

## Acceptance Checklist

Confirm all of these before considering the lesson complete:

- the lesson explains how to identify and defend candidate keys
- prime-attribute language is limited to what supports later relational reasoning students actually need
- at least one practice element asks students to reject a plausible but weak key candidate
- the student-facing content is strong enough for independent asynchronous study
- the instructor-facing content focuses on alignment, implementation, misconceptions, and assessment
- the lesson clearly connects Lesson 4.1 to Lesson 4.3
- the lesson supports the shared v4 lesson acceptance criteria in `textbook/v4/03-lesson-prompt.md`
