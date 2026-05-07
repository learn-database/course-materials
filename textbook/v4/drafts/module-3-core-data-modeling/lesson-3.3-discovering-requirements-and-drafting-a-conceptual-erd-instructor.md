# Lesson 3.3: Discovering Requirements and Drafting a Conceptual ERD

## Instructor-Facing Content

### Module

Module 3: Core Data Modeling

### Lesson purpose

Students learn how to move from a narrative case to a first-pass conceptual ERD through disciplined requirement interpretation. The lesson emphasizes careful reading, scope control, conceptual-only modeling, and critique of whether the proposed model represents the true work and people involved in the case.

### Module context

Lessons `3.1` and `3.2` taught the parts of conceptual modeling separately: entities, attributes, identifiers, relationships, cardinality, and optionality. Lesson `3.3` applies those ideas together in a realistic case and closes Module 3 by shifting from part recognition to whole-case judgment. It prepares students for Module 4, where design logic and quality judgments become more explicit, and for Module 5, where students must preserve the ERD versus DBDD boundary.

### Primary learning type(s)

- Problem solving / judgment

### Secondary learning type(s), if any

- Concepts

### Estimated time

- 75 to 90 minutes

### Lesson outcomes

By the end of the lesson, students should be able to:

- extract business rules and must-track information from a narrative case
- distinguish in-scope requirements from background detail and out-of-scope noise
- identify what the case does not require the system to store
- propose entities, significant attributes, and relationships from evidence in the case
- draft a first-pass conceptual ERD without drifting into DBDD detail
- critique whether a model reflects the true work, people, and responsibilities in the case
- defend inclusion, exclusion, and relationship choices in plain business language

### Module alignment

- Directly supports Module 3 objectives on identifying candidate entities, significant attributes, and relationship structures from a business process.
- Satisfies the module requirement that students create and critique a first conceptual ERD.
- Supports the module assessment strategy by prioritizing critique, repair, and defense over polished diagram production.

### Course objective alignment

- Objective 2: evaluate a business process and determine what data must be stored
- Objective 3: create ER Diagrams and Database Design Diagrams that reflect a given business process

### Lesson sequence role

- Applies and integrates module knowledge
- Concludes Module 3 by turning conceptual components into a defensible first-pass artifact plus rationale

### Required prior knowledge

- entity, attribute, identifier, strong entity, and weak entity ideas from Lesson `3.1`
- relationship, cardinality, and optionality reasoning from Lesson `3.2`
- ERD versus DBDD boundary rules from the course design spec and notation guide

### Lesson opening guidance

Open by stating that the central skill is not drawing quickly but reading truthfully. Students should hear that a conceptual ERD is only as good as the requirement interpretation behind it. Reinforce that this lesson completes Module 3 by asking them to move from case facts to modeling judgments without adding implementation detail.

### Teaching notes

- Keep the case central from beginning to end rather than switching examples midstream.
- Model the thinking path explicitly: process in scope, must-track facts, business rules, exclusions, entity choices, relationship choices, conceptual-boundary check.
- Ask repeatedly, "What in the case requires this?" and "What in the case does not require this?"
- Treat exclusions as evidence of good scope judgment, not as missing work.
- Push students to name people and responsibilities made visible by the model.
- If students add `PK`, `FK`, data types, or nullability, redirect them to Module 5 artifact work.
- If students use AI, require them to verify each suggested model element against the case and explain where the AI overreached or missed something.

### Online activities

- annotated case worksheet
- conceptual ERD draft submission
- short critique response on an over-modeled draft
- brief written defense of conceptual choices

### Homework / graded assignments

- Graded lesson packet:
  - annotated case
  - scope note
  - conceptual ERD
  - short written defense
  - short critique of what the case does not require the system to store

### Deliverables

- one annotated narrative case
- one scope note
- one first-pass conceptual ERD
- one written defense and critique response

### Assessment plan

Formative evidence:

- guided annotation of the Lakeside case
- relationship and exclusion discussion during guided practice
- critique of the over-modeled draft

Graded evidence:

- annotated case and scope note
- first-pass conceptual ERD
- short written defense and critique response

Evidence of learning:

- students can separate requirements from background detail
- students can explain at least one exclusion decision accurately
- students can justify entities and relationships from case evidence
- students can keep the artifact conceptual
- students can critique whether the model represents the true work and people involved

How the lesson avoids over-relying on an AI-generable artifact:

- the ERD is paired with a defense and critique task
- students must explain what the case does not require the system to store
- students must connect modeling choices to specific case evidence

Stronger performance looks like:

- disciplined scope boundaries
- entity and relationship choices tied directly to the case
- explicit rejection of tempting but unsupported storage detail
- accurate conceptual-boundary control
- thoughtful reflection on visibility, service, and truthful representation

### Suggested rubric focus

- requirement discovery accuracy
- scope control
- quality of entity and relationship justification
- clarity about what the case does not require the system to store
- conceptual ERD boundary discipline
- ability to connect modeling choices to the real work and people in the case

### Common misconceptions

- "Every noun in the case should become an entity."
- "If a detail is realistic, it belongs in the model."
- "A conceptual ERD is incomplete without `PK` and `FK` labels."
- "Weak entity means unimportant entity."
- "If AI produced a plausible ERD, the reasoning is probably correct."
- "Diagram neatness matters more than requirement accuracy."

### Christian integration notes

Keep integration inside ordinary modeling decisions. Requirement discovery can be framed as careful listening that helps keep people, responsibilities, and service relationships visible. Ask students who becomes invisible when a model is careless, and connect accurate conceptual modeling to truthful representation, responsible stewardship of organizational attention, and neighbor-serving information systems.

### Workflow connection

This lesson covers the workflow move from understanding the business process and identifying requirements to drafting the first conceptual ERD. It closes Module 3 and creates the starting point for later design-logic judgment in Module 4 and artifact-boundary refinement in Module 5. The key workflow rule is that the ERD here remains conceptual and should not slide into implementation-ready structure.
