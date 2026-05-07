# Module 3 Overview: Core Data Modeling

## Instructor-Facing Content

### Module Purpose

Module 3 is the conceptual modeling core of the course. Students learn
to interpret requirements, identify entities and relationships, judge
identifier strength, and critique flawed conceptual ERDs before later
modules move into design-logic analysis or implementation-ready detail.

### Role In The Course

This module sits between early workflow awareness and later design
refinement. It returns the course to the business-analysis side of
database work after Module 2 and establishes the first formal model of
what the system must track.

### Lesson Arc

- Lesson `3.1` builds entity, attribute, identifier, and weak-entity
  judgment.
- Lesson `3.2` builds relationship, cardinality, optionality, and
  participation judgment.
- Lesson `3.3` integrates those ideas through requirement reading, scope
  control, conceptual ERD drafting, and model critique.

### Implementation Emphasis

- Keep the module business-first and interpretation-heavy.
- Treat entities, relationships, identifiers, and conceptual ERD critique
  as the module spine.
- Require students to justify choices from case evidence, not from
  diagram familiarity.
- Keep Christian integration embedded in ordinary modeling decisions by
  connecting careful requirements reading to visibility, human dignity,
  and truthful representation.
- Use AI-generated model suggestions only as critique targets or draft
  inputs, not as sufficient evidence of understanding.

### Scope Boundaries

- Keep all work at the conceptual ERD level.
- Do not introduce `PK`, `FK`, SQL data types, nullability, or table
  design detail as part of the module's main teaching target.
- Do not let the module drift into normalization, DBDD construction, or
  SQL Server implementation.

### Alignment And Grading Focus

The module aligns to the v4 assessment rule that artifact production
alone is weak evidence in an AI-available course. Grade students on:

- quality of entity and relationship judgment
- strength of identifier and cardinality justification
- ability to detect and repair conceptual-model flaws
- clarity about what the case does not require the system to store
- ability to defend conceptual boundary decisions in plain language

Useful evidence types:

- concept and classification checks
- critique-and-repair tasks
- annotated case analysis
- short written or recorded defenses of conceptual choices

### Common Misconceptions

- every important noun is an entity
- realistic detail automatically belongs in the model
- a clean-looking ERD is strong evidence of learning
- weak entity means unimportant entity
- conceptual ERDs should already include implementation-ready notation

### Boundary And Risk Notes

- Students may over-model because they confuse realism with scope.
- Students may under-model by hiding people, responsibilities, or service
  needs that the case actually requires.
- Students may let AI overreach unless they are required to point to case
  evidence for each major modeling decision.
- Students often need repeated reminders that Module 3 is about sound
  conceptual judgment before later modules test logical quality or build
  implementation-ready artifacts.
