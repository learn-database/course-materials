# Lesson 3.3: Discovering Requirements and Drafting a Conceptual ERD

## Lesson overview

This lesson teaches the move from a business case to a first-pass conceptual ERD. The main job is not drawing boxes quickly. The main job is reading the case carefully enough to decide what the system must represent, what it does not need to represent, and why those choices fit the real work of the organization.

You will use the conceptual-modeling pieces from Lessons 3.1 and 3.2 together: entities, significant attributes, relationships, cardinality, and optionality. You will also keep the ERD within its proper boundary. This lesson is still about the conceptual ERD, not the later Database Design Diagram.

## Lesson outcomes

By the end of this lesson, you should be able to:

- read a narrative case for business purpose, scope, and must-track information
- separate business rules from background detail
- identify what the case does not require the system to store
- propose conceptual entities, significant attributes, and relationships from case evidence
- draft a first-pass conceptual ERD that stays within conceptual boundaries
- critique whether a proposed ERD reflects the true work and people involved in the case
- explain and defend inclusion, exclusion, and relationship choices in plain business language

## Key terms

- `requirement`: information or a rule the system must represent for the case in scope
- `business rule`: a statement in the case that constrains what can happen or what must be tracked
- `scope`: the boundary of what this model should include and what it should leave out
- `significant attribute`: an attribute that helps identify, describe, or support the work in scope
- `conceptual ERD`: a business-facing model that shows entities, significant attributes, relationships, cardinality, and optionality without implementation detail
- `over-modeling`: adding data elements the case does not require for the process being modeled

## Readings and media

- Read this lesson closely before drafting any diagram.
- Review [06-design-object-naming-and-notation-conventions.md](../../06-design-object-naming-and-notation-conventions.md), especially the sections on entity names, attribute names, and ERD versus DBDD boundaries.
- Use your course-approved diagramming tool or a clean hand-drafted layout for the first-pass conceptual ERD.

## Core content

### 1. Read for purpose before you read for nouns

Start by asking what business work the case is actually about. If you skip that step, every detail will feel equally important. Most cases include a mix of process facts, business rules, descriptive background, and side details. Your task is to separate them.

A useful opening question is: "What service, operation, or responsibility is this system supposed to support?" That question gives you the first scope boundary.

### 2. Mark must-track facts, rules, and background separately

On the second read, annotate the case in at least three categories:

- must-track business facts
- explicit or strongly implied business rules
- background or out-of-scope details

This step matters because conceptual ERDs should be driven by evidence from the case. If you cannot point to a sentence or business need that supports a model element, that element may not belong.

### 3. Control scope before you draft entities

Scope control prevents over-modeling. Real organizations contain far more detail than any one system needs to store. A good conceptual model reflects the process in scope, not the entire organization.

Good reasons to exclude a detail include:

- it belongs to another system
- it does not affect the process being modeled
- it does not change the entities, relationships, or important attributes in scope

Exclusion is not laziness. It is a design judgment.

### 4. Turn business meaning into entities and relationships

After you identify what matters, ask which things the system must track as business objects. Not every noun becomes an entity. Some nouns describe attributes. Some describe background conditions. Some name tools, locations, or preferences that do not belong in this model.

Then ask what work connects those business objects. Relationship choices should come from the actions and rules in the case, not from guesswork. If a session must involve one student and one tutor, those statements justify relationships and participation choices.

### 5. Choose only significant attributes

Conceptual ERDs include meaningful attributes, not every possible storage field. Keep attributes that help identify the thing, describe it in a useful way, or support the work being modeled.

If an attribute is merely interesting, convenient, or hypothetically useful someday, leave it out of the first pass.

### 6. Keep the ERD conceptual

For this lesson, the ERD should include:

- entities
- significant attributes
- relationships
- cardinality
- optionality

For this lesson, the ERD should not include:

- `PK`
- `FK`
- SQL data types
- nullability
- table structures or implementation-only notation

Those details belong later when the course moves to the Database Design Diagram.

### 7. Critique the model for truthful representation

A conceptual ERD should reflect the true work and people involved in the case. Ask questions such as:

- Which people or responsibilities become invisible if I leave this entity out?
- Which details am I storing even though the case never requires them?
- Does this relationship reflect the actual work, or did I add it because it seemed convenient?
- If another person read my ERD, would they understand the business structure without guessing?

### 8. Use AI as a draft assistant, not as a substitute for judgment

AI can suggest candidate entities, relationships, and first-pass diagrams. That can be useful for brainstorming. It does not remove your responsibility to verify the model against the case.

If you use AI, require it to show its reasoning and then check each proposed entity or relationship against the case yourself. A plausible diagram is not enough. You should be able to defend why each part belongs and why excluded details stay out.

## Examples and case

Use this case for the lesson work.

**Lakeside Tutoring Center scheduling case**

Lakeside Tutoring Center offers one-on-one tutoring sessions for college students. A student may request tutoring in more than one subject, and each tutor may teach multiple subjects. The center schedules sessions between one student and one tutor. Each session is for one subject and has a date, start time, and room. Students can have many sessions over a term, but a scheduled session must involve exactly one student and exactly one tutor.

After each session, the tutor records a short session note that summarizes what was covered and any follow-up recommendation. A session may have one note or no note if the tutor has not submitted it yet. Session notes are only meaningful in the context of a specific session.

The center also stores student emergency contact information in a separate campus safety system. Staff sometimes mention parking availability, printer issues, and tutor preference for whiteboard or tablet, but those details are not part of the scheduling process being modeled here.

**Case-to-model reasoning**

Start with the purpose in scope: scheduling tutoring sessions and recording session notes tied to those sessions.

Likely in-scope entities:

- `Student`
- `Tutor`
- `Subject`
- `Session`
- `SessionNote`

Likely out-of-scope details:

- emergency contact data stored in another system
- parking availability
- printer issues
- whiteboard or tablet preference

Possible significant attributes:

- `Student`: `StudentID`, `FirstName`, `LastName`
- `Tutor`: `TutorID`, `FirstName`, `LastName`
- `Subject`: `SubjectCode`, `SubjectName`
- `Session`: `SessionDate`, `StartTime`, `Room`
- `SessionNote`: `NoteText`, `FollowUpRecommendation`, `SubmittedAt`

Key relationship judgments:

- a `Student` can have many `Session` instances
- a `Tutor` can lead many `Session` instances
- a `Subject` can appear in many `Session` instances
- a `Session` may have zero or one `SessionNote`

## Guided practice

Work through these prompts before drafting the ERD.

1. Read the case once and write a one-sentence statement of the business process in scope.
2. Read it again and mark:
   - tracked business objects
   - business rules
   - out-of-scope details
3. List the facts that clearly require the system to store something.
4. List at least two details that the case does **not** require the system to store.
5. Explain why `SessionNote` is dependent on `Session` in this case.
6. Draft a plain-language list of relationships before you draw them.
7. Check whether every proposed entity represents true work, a real person, or a real responsibility in the case.

**Critique exercise: the over-modeled draft**

A student proposes these extra entities for the Lakeside case: `EmergencyContact`, `ParkingIssue`, `PrinterIssue`, and `TutorDevicePreference`.

Answer these questions:

1. Which of these does the case require the tutoring scheduling system to store?
2. Which of these are merely realistic details rather than system requirements?
3. Which item belongs to another system entirely?
4. How would adding these details weaken the conceptual model?

## What to do

Create a first-pass conceptual ERD for the Lakeside case.

Follow this process:

1. Annotate the case.
2. Write a short scope statement.
3. List entities, relationships, and significant attributes.
4. Note at least one detail the case does not require the system to store.
5. Draft the conceptual ERD.
6. Review the ERD for conceptual-boundary violations.
7. Write a short defense of one inclusion decision, one exclusion decision, and one relationship decision.

Use this verification checklist before submitting:

- Every entity is supported by the case.
- Every relationship is supported by the case.
- At least one excluded detail is named and justified.
- The ERD reflects the true work and people involved.
- No `PK`, `FK`, data types, nullability, or DBDD detail appears.

## Assignments

Submit one lesson packet with these parts:

- an annotated copy of the Lakeside case
- a scope note that states what the model covers and what it leaves out
- a first-pass conceptual ERD
- a short written defense that explains:
  - one inclusion decision
  - one exclusion decision
  - one relationship, cardinality, or optionality decision
  - why the ERD stays conceptual instead of implementation-ready
- a short critique of the over-modeled draft that explains what the case does not require the system to store

## Deliverables

- annotated case
- scope note
- conceptual ERD
- written defense and critique response

## Project checkpoint or module connection

Before leaving Module 3, apply the same process to your course project case.

Ask these checkpoint questions:

- What is the business process in scope for your project model?
- Which details sound realistic but are not required to be stored?
- Do your proposed entities and relationships reflect the true work and people involved, or did you accidentally make some responsibilities invisible?
- Does your ERD remain conceptual, or are implementation details starting to leak in?

Keep your project answer as a working draft. Module 4 will test whether the logic behind your choices is strong, and Module 5 will revisit the ERD versus DBDD boundary directly.

## Wrap-up

This lesson completes the first full move from case reading to conceptual modeling. The goal is not a polished final diagram. The goal is a defensible first-pass ERD built from careful reading, scope control, and honest representation of the work in the case.

If your diagram is accurate, it should show what the organization is actually responsible for tracking and should avoid storing what the case never requires. That discipline is what prepares you for later design judgment and artifact refinement.
