# Lesson 3.2: Relationships and Cardinality

## Instructor-Facing Content

### Module

Module 3: Core Data Modeling

### Lesson Purpose

Teach students to interpret relationships as business rules, distinguish one-to-many from many-to-many patterns, and justify optionality and participation from realistic scenarios before they draft a full conceptual ERD.

### Module Context

Lesson 3.1 established entities, attributes, identifiers, and weak entities. Lesson 3.2 teaches how those entities connect and what the connection means. Lesson 3.3 will require students to carry those decisions into a first conceptual ERD and defend them against flawed alternatives.

This lesson also supports the Module 3 assessment pattern: students should not only draw plausible relationships, but critique incorrect ones and justify corrections from the case.

### Primary Learning Type(s)

- Principles

### Secondary Learning Type(s), if any

- Concepts

### Estimated Time

- 75 to 90 minutes

### Lesson Outcomes

By the end of the lesson, students should be able to:

- explain a relationship as a business rule rather than as notation alone
- distinguish `one-to-many` from `many-to-many` patterns in a short scenario
- justify `cardinality`, `optionality`, and `participation` from case evidence
- explain how a wrong cardinality choice misrepresents real work or accountability
- critique a flawed relationship choice and replace it with a defensible one

### Module Alignment

- Supports Module 3 objectives on identifying relationship types, distinguishing one-to-many from many-to-many, and reasoning about optionality.
- Builds the conceptual judgment students need before Lesson 3.3 asks them to draft and critique a full conceptual ERD.
- Reinforces the module rule that explanation and critique are stronger evidence than diagram polish alone.

### Course Objective Alignment

- Objective 2: evaluate a business process and determine what data must be stored
- Objective 3: create ER Diagrams and Database Design Diagrams that reflect a given business process

### Lesson Sequence Role

- Comes after students learn what the system tracks.
- Prepares students to justify how tracked entities connect in a first conceptual ERD.
- Foreshadows later critique, repair, and defense work in Module 3 and later modules.

### Required Prior Knowledge

- entity, attribute, identifier, and weak-entity thinking from Lesson 3.1
- understanding that the conceptual ERD is distinct from the implementation-ready Database Design Diagram
- familiarity with plain business naming conventions such as `Customer`, `Order`, `Student`, and `Course`

### Lesson Opening Guidance

Open with two short contrasts:

- one `Customer` may place many `Order` instances; each `Order` belongs to one `Customer`
- one `Student` may take many `Course` instances; one `Course` may include many `Student` instances

Ask students what business story changes between those two examples. Push them to answer in plain language first. Delay notation vocabulary until they can explain what the organization allows and requires.

### Teaching Notes

- Follow the v4 strategy for Lesson 3.2: rule explanation, diagram reading, contrasting cases, and cardinality or optionality judgment.
- Keep the lesson conceptual. Do not teach implementation repair for many-to-many or foreign-key placement.
- Use short scenarios that force students to read both sides of the relationship.
- Require students to separate maximum participation from minimum participation.
- Include at least one case where the first sentence suggests one pattern, but a later sentence changes the correct answer. This helps break the habit of reading only surface wording.
- Keep examples tied to real business meaning so students see why wrong cardinality choices distort reporting, accountability, or service history.

### Online Activities

- short case classification: match business rules to one-to-many or many-to-many patterns
- optionality check: identify which side is optional or required from a written scenario
- critique prompt: repair one flawed relationship choice and explain what the original model falsely claimed
- short discussion: explain one relationship from a project case in plain language before any diagram is drawn

### Homework / Graded Assignments

Assign one short written critique rather than a polished diagram:

- classify two relationship patterns from a business case
- justify optionality and participation from specific case sentences
- critique one incorrect cardinality choice
- explain what business reality the flawed model would misrepresent

This structure fits the module's critique-and-defense logic and remains valid in an AI-available course.

### Deliverables

- one short written relationship analysis
- one critique of a flawed relationship choice
- plain-language justification for cardinality, optionality, and participation decisions

### Assessment Plan

Formative checks:

- classify one-to-many versus many-to-many from brief cases
- identify required versus optional participation
- explain one relationship from both directions in plain language

Graded evidence:

- short critique-and-defense response aligned to the module's model critique and defense assessment

Evidence to look for:

- the student matches the relationship pattern to the business rule
- the student uses case evidence rather than symbol guessing
- the student distinguishes maximum participation from minimum participation
- the student detects and corrects a weak relationship choice

### Suggested Rubric Focus

- `Relationship meaning`
  - Meets: explains the relationship as a business rule and reads both sides clearly.
  - Partly meets: identifies the entities but gives only label-level explanation.
  - Does not meet: cannot explain what the relationship means in the business.

- `Cardinality judgment`
  - Meets: correctly distinguishes one-to-many from many-to-many and supports the choice from the scenario.
  - Partly meets: chooses the right label but gives weak or partial support.
  - Does not meet: misclassifies the relationship or contradicts the case.

- `Optionality and participation`
  - Meets: explains minimum participation on each side and names which side is optional or required.
  - Partly meets: recognizes one side correctly but blends maximum and minimum logic.
  - Does not meet: confuses optionality with cardinality.

- `Critique and correction`
  - Meets: identifies what is false in the flawed model and explains a better replacement.
  - Partly meets: senses that the model is weak but cannot explain the consequence clearly.
  - Does not meet: accepts the flawed model or critiques it without business reasoning.

### Common Misconceptions

- "Cardinality and optionality mean the same thing."
- "Plural nouns prove many-to-many."
- "If one side can have many, the whole relationship must be many-to-many."
- "Many-to-many is always wrong in a conceptual ERD."
- "Optional participation means the relationship itself is unimportant."
- "Notation tells me the answer even if I have not read the case carefully."

### Christian Integration Notes

- Connect careful relationship judgment to truthful representation of business reality.
- Use one prompt that asks which stakeholders, responsibilities, or service events become invisible when a relationship is modeled carelessly.
- Keep the integration inside normal modeling judgment. The goal is not a separate reflection section, but a reminder that accurate conceptual models help organizations serve people honestly and responsibly.

### Workflow Connection

This lesson sits at the point in the workflow where students move from identifying tracked objects to explaining how those objects relate in the real business process. It prepares them for Lesson 3.3, where they will annotate a case, draft a first conceptual ERD, and defend their modeling choices. It also supports the wider course emphasis that good database work requires explanation, verification, and truthful representation, not just a polished artifact.
