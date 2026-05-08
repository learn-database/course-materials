# Lesson 4.2: Keys of Relations

## Instructor-Facing Content

### Module

Module 4: Design Logic

### Lesson Purpose

Teach students to identify and defend candidate keys from functional dependencies and business meaning. The lesson should move students away from "looks unique" reasoning and toward explicit judgment about sufficiency, minimality, and row grain.

### Module Context

This lesson inherits Lesson 4.1's dependency reasoning and prepares Lesson 4.3's normalization and design-repair work.

- From Lesson 4.1, students bring the ability to justify dependencies from business meaning rather than sample patterns.
- In this lesson, they use those dependencies to test strong and weak key candidates.
- In Lesson 4.3, they will need sound key reasoning to recognize partial dependencies, transitive dependencies, and structural anomalies.

This lesson directly supports the module's normalization judgment task because students cannot defend a decomposition well if they never proved the key correctly.

### Primary Learning Type(s)

Principles

### Secondary Learning Type(s), If Any

Concepts

### Estimated Time

75 to 90 minutes

### Lesson Outcomes

By the end of this lesson, students should be able to:

- explain the difference between a superkey and a candidate key
- identify strong and weak key candidates in business terms
- test whether a proposed attribute set determines the whole relation
- test minimality explicitly instead of assuming sufficiency is enough
- identify prime attributes only as far as later relational reasoning requires
- reject a plausible but weak key candidate with a clear structural explanation

### Module Alignment

- Supports the Module 4 objective to determine keys of relations.
- Extends Lesson 4.1's dependency logic into key judgment.
- Prepares students for Lesson 4.3's anomaly diagnosis and design repair.
- Reinforces the module-wide shift from mechanical normalization to defensible structural reasoning.

### Course Objective Alignment

- Objective 1: know basic database terminology
- Objective 2: evaluate a business process and determine what data must be stored
- Objective 4: normalize a database design appropriately

### Lesson Sequence Role

Deepens module knowledge by turning dependency claims into tested key arguments and by setting up later normalization judgment.

### Required Prior Knowledge

- ability to read compact relation schemas
- understanding of determinant and functional dependency from Lesson 4.1
- habit of defending design claims from business meaning instead of sample patterns

### Lesson Opening Guidance

Open with two claims that both sound plausible:

- `StudentID, SectionID`
- `StudentEmail, SectionID`

Ask which proposal is structurally stronger and why. Use the discussion to surface three ideas immediately:

- row grain matters
- descriptive contact data can look strong while remaining structurally weak
- closure and minimality are tools for defending the answer, not vocabulary to memorize

### Teaching Notes

- Keep returning to the phrase `what one row means`. Students often rush into notation before locking the row grain.
- Make students separate two different tests: sufficiency and minimality.
- Compare strong and weak key candidates in business language before formal closure work.
- Use prime-attribute terminology lightly. Students mainly need the term so later normalization reasoning can refer to prime versus nonprime attributes without re-teaching the key logic.
- Do not drift into implementation-level primary-key selection debates. The lesson is about candidate-key reasoning inside relational design logic.
- Require at least one explicit rejection of a plausible weak candidate such as `StudentEmail, SectionID`. That step is part of the acceptance criteria, not optional enrichment.
- Reinforce that weak candidates fail in different ways: unsupported dependency direction, wrong row grain, or unnecessary attributes.

### Online Activities

- short LMS classification check on `not a superkey`, `superkey only`, and `candidate key`
- guided closure exercise with one worked step and one student-completed step
- short-answer prompt requiring rejection of a plausible but weak candidate
- brief prime-versus-nonprime classification task tied to the main case

### Homework / Graded Assignments

#### Assignment 1: Key Reasoning Worksheet

Students should:

- test at least two candidate proposals
- show sufficiency reasoning
- test minimality for the strongest proposal
- identify the final candidate key or keys
- reject one plausible but weak key candidate in business terms

#### Assignment 2: Short Defense Paragraph

Students explain why structural defensibility is stronger than sample uniqueness when choosing a key and describe how weak key logic would interfere with later normalization reasoning.

### Deliverables

- one completed key reasoning worksheet
- one short defense paragraph

### Assessment Plan

Formative evidence:

- classification of proposals as neither, superkey only, or candidate key
- closure checkpoints
- short rejection of a weak candidate
- prime/nonprime identification from the main case

Graded evidence:

- worksheet showing explicit reasoning
- paragraph showing explanation and transfer to later normalization work

Evidence of learning is strongest when the student:

- states what one row means before testing keys
- uses closure or equivalent dependency reasoning correctly
- separates sufficiency from minimality
- rejects a weak candidate for the right reason
- explains how wrong key logic would distort later structural judgment

This lesson avoids over-relying on an AI-generable artifact because students must defend and reject alternatives, not just present a final key label.

### Suggested Rubric Focus

- accuracy of sufficiency reasoning
- accuracy of minimality reasoning
- quality of strong-versus-weak key comparison in business terms
- correct and limited use of prime-attribute language
- explicit rejection of at least one plausible but weak key candidate
- clear connection between key reasoning and later normalization judgment

### Common Misconceptions

- "If a value looks unique in the sample, it is good enough for a key."
- "If a set determines the whole relation, it is automatically a candidate key."
- "Adding more attributes makes a key stronger."
- "Email, phone number, or name is fine as a key because people recognize it."
- "Prime attribute language is the main point of the lesson."

### Christian Integration Notes

Connect this lesson to trustworthy business practice, not to a separate devotional aside.

- Weak key logic can support misleading reports, duplicate records, or confused scheduling and billing.
- Strong key judgment is part of truthful, careful, neighbor-serving information work because it protects the integrity of later reporting and decision-making.
- A useful checkpoint question is: which key choice better protects trust and reduces wasted correction work later?

Keep the integration subordinate to the technical lesson goal. The technical focus remains candidate-key reasoning.

### Workflow Connection

In the full database workflow, this lesson belongs to the stage where designers test structure before they normalize and before they build implementation-ready artifacts.

- earlier work identified business requirements, entities, attributes, and defensible dependencies
- this lesson proves what makes the relation structurally unique
- later work uses that proof to judge decompositions, repair weak designs, and carry stronger logic into ERD refinement, DBDD work, and SQL Server implementation
