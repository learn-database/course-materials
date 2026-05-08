# Lesson 3.1: Entities, Attributes, and Identifiers

## Instructor-Facing Content

### Module

Module 3: Core Data Modeling

### Lesson Purpose

Teach students how to distinguish tracked business things from descriptive facts, how to compare stronger and weaker identifier choices, and how to explain those decisions in business terms before they move into relationships and first-pass ERD drafting.

### Module Context

Module 3 emphasizes requirement interpretation, entity judgment, and critique of flawed conceptual models. This opening lesson establishes the conceptual categories students will use throughout the module and gives them a repeatable classification method they can defend in later critique-and-repair work. It also supports the module's Christian integration focus by connecting careful requirements reading to visibility, responsible service, and truthful representation.

### Primary Learning Type(s)

`Concepts`

### Secondary Learning Type(s), if any

`Principles`

### Estimated Time

90 to 120 minutes

### Lesson Outcomes

By the end of the lesson, students should be able to:

- classify scenario elements as entities, attributes, and identifier candidates
- use a repeatable entity-versus-attribute method instead of intuition alone
- compare stronger and weaker identifiers using uniqueness, stability, and business meaning
- explain why a weak identifier choice is weak
- distinguish strong entities from weak entities at a conceptual level
- identify who or what becomes invisible when requirements are read carelessly

### Module Alignment

This lesson supports Module 3 objectives to:

- identify entities, attributes, identifiers, and relationship types
- identify candidate entities and significant attributes from a business process
- distinguish strong entities from weak entities at a conceptual level
- critique conceptual modeling choices instead of trusting a polished artifact alone

### Course Objective Alignment

- Course Objective `2`: evaluate a business process and determine what data must be stored
- Course Objective `3`: create ER Diagrams and Database Design Diagrams that reflect a given business process

### Lesson Sequence Role

This is the entry point to conceptual data modeling in Module 3. It follows the earlier course workflow work from Module 1 and prepares directly for:

- Lesson `3.2`, where students will connect these entities through relationships, cardinality, optionality, and identifying relationships
- Lesson `3.3`, where students will extract requirements from a case and draft a first conceptual ERD
- the module critique-and-defense assessment, where students must explain why entity, attribute, and identifier choices are correct

### Required Prior Knowledge

- basic understanding that databases store business information for a purpose
- familiarity with the idea that requirements must be interpreted, not copied word-for-word
- awareness that a conceptual ERD is different from an implementation-ready Database Design Diagram

### Lesson Opening Guidance

Start with three quick contrasts:

- `Customer` versus `PhoneNumber`
- `RepairOrder` versus `Status`
- `ServiceVisit` versus `VisitDate`

Ask students which items the organization tracks as separate things and which items only describe those things. After the quick sort, introduce the lesson's repeatable method:

1. `Track`: is the organization tracking this as its own thing?
2. `Describe`: is this mainly a fact about something else?
3. `Distinguish`: how would we tell one instance apart from another?

Use the opening to break the habit of turning every important noun into an entity.

### Teaching Notes

- Keep the lesson conceptual. Do not introduce `PK`, `FK`, SQL data types, nullability, or DBDD detail.
- Use one running case so students can compare decisions across sections instead of restarting with new vocabulary each time.
- Require justification language. Students should say "the organization tracks this independently" or "this describes another tracked thing."
- When discussing identifiers, insist on the three tests: uniqueness, stability, and business meaning.
- Treat weak entities conceptually. The goal is dependence in identification, not notation mechanics.
- If students rely on AI to generate candidate entities or identifiers, require them to critique the AI output and explain why one choice is stronger. This lesson should reward verification and defense, not list production alone.
- Reconnect the lesson often to the module's assessment pattern: a clean-looking ERD is weak evidence if the student cannot explain why an item is an entity, an attribute, or a weak identifier choice.

### Online Activities

- Short concept-sort activity in which students classify scenario items as entity, attribute, or borderline case.
- Auto-graded identifier comparison check using stronger-versus-weaker pairs.
- Brief discussion or reflection prompt on visibility: ask what or who becomes invisible when requirements are read carelessly.
- Optional AI-verification exercise in which students compare their own classifications to an AI-generated list and identify one AI mistake or weak assumption.

### Homework / Graded Assignments

Assign one conceptual-modeling worksheet based on the `North Harbor Repair Shop` case. Students should:

- classify scenario items into entities, attributes, and identifier candidates
- explain one borderline classification decision using the lesson method
- compare stronger and weaker identifiers for `Customer`, `RepairOrder`, and `DiagnosticNote`
- judge identifier choices using uniqueness, stability, and business meaning
- distinguish strong and weak entities at a conceptual level
- answer a short visibility prompt tied to stakeholder representation

### Deliverables

- one completed worksheet or short written response

The submission should include:

- classifications
- identifier comparisons
- one borderline-case explanation
- strong-versus-weak entity decisions
- one short visibility reflection

### Assessment Plan

Formative checks:

- guided classification of case elements
- quick identifier comparison questions
- strong-versus-weak entity classification
- short visibility reflection in discussion or exit-ticket form

Graded evidence:

- one conceptual worksheet or short written response showing classification, identifier critique, and explanation

Because AI can produce plausible first-pass lists, the graded response should emphasize explanation and critique:

- Why is one classification defensible?
- Why is one identifier stronger?
- Why is one weak entity dependent?
- What is lost when the case is read too narrowly?

### Suggested Rubric Focus

- `Classification accuracy`: distinguishes tracked objects from descriptive facts in most cases
- `Borderline-case reasoning`: uses the repeatable lesson method instead of unsupported intuition
- `Identifier judgment`: compares choices using uniqueness, stability, and business meaning
- `Strong-versus-weak entity reasoning`: explains dependence in plain language
- `Visibility and responsibility`: identifies a meaningful stakeholder or business-work element that careless modeling would hide

Suggested checklist:

- Student identifies the core entities in the case.
- Student keeps descriptive facts as attributes unless independent tracking is justified.
- Student names at least one identifier candidate for each major entity.
- Student rejects at least one weak identifier with specific reasoning.
- Student identifies the weak-entity example correctly.
- Student explains one visibility risk from careless requirements reading.
- Student stays at conceptual model scope.

### Common Misconceptions

- "If it matters to the business, it must be an entity."
- "Any field that looks official is automatically a strong identifier."
- "Weak entity means less important entity."
- "Repeated detail should always become its own entity."
- "A polished ERD proves the model is correct."

### Christian Integration Notes

Keep Christian integration embedded in normal instruction rather than isolated from the technical content.

- Connect careful requirements reading to neighbor-serving systems and truthful representation.
- Use the visibility prompt to ask whose work, needs, or responsibilities disappear when the model is rushed.
- Frame strong classification work as stewardship: good modeling reduces rework, poor reporting, and avoidable service mistakes.
- Keep the language business-facing. The point is not a devotional aside. The point is that conceptual models affect how organizations see people, work, and obligations.

### Workflow Connection

This lesson sits at the workflow step where students move from understanding a business process to identifying what data the system must track. Better entity, attribute, and identifier choices make later relationship work in Lesson `3.2` more coherent and make the first conceptual ERD in Lesson `3.3` easier to defend. The lesson also previews later design-quality work by showing that weak early classification decisions can create structural problems that become harder to repair later.
