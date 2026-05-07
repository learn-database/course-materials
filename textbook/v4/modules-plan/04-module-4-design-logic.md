# Module 4: Design Logic

### Purpose

- Teach the logic behind relational design quality through dependency analysis, key reasoning, anomaly diagnosis, and normalization.
- Shift emphasis from performing normalization mechanically to judging whether a decomposition is defensible.

### Objectives

- identify functional dependencies
- determine keys of relations
- distinguish partial and transitive dependencies
- explain anomalies
- normalize through BCNF when appropriate
- resolve many-to-many relationships with intersection tables

### Human Must Know

- what makes a dependency claim valid
- how to tell a real key from a weak candidate
- why anomalies matter
- how to judge whether a decomposition preserves the intended meaning

### AI May Assist With

- generating FD notation
- suggesting candidate keys and decompositions
- checking closure-like reasoning in simple cases
- producing practice examples and anomaly scenarios

### Christian Integration Focus

- present dependency reasoning and normalization as protection against inconsistency, waste, and untrustworthy reporting
- connect anomalies to downstream harm in billing, scheduling, inventory, or service decisions

### Integration Touchpoints

- include one anomaly discussion that names the business or neighbor impact of inconsistent data
- include one project checkpoint asking where design repair improves stewardship of time, resources, or trust

### Lessons

#### Lesson 4.1: Functional Dependencies
- identify defensible dependencies
- reject accidental sample patterns

#### Lesson 4.2: Keys of Relations
- reason about candidate keys, prime attributes, and structural uniqueness

#### Lesson 4.3: Normalization and Design Repair
- identify anomalies
- compare decompositions
- repair weak relation designs

### Assessment Strategy

This module should not rely on "normalize this relation" as a standalone take-home task. AI can do much of that work. The stronger assessment is to compare competing decompositions and justify which one is acceptable.

### Primary Graded Assessment

#### Normalization Judgment Task

- Format: students receive one relation, stated business rules, and two candidate decompositions
- Students identify valid dependencies and keys, explain anomalies, and defend which decomposition is stronger

### Secondary Evidence

- timed quiz on FD meaning and key logic
- short critique of a decomposition that appears tidy but breaks business meaning

### What To Grade

- validity of FD reasoning
- quality of key justification
- anomaly diagnosis
- ability to defend or reject a normalization decision
- ability to explain why a weak design would damage truthfulness, consistency, or responsible decision-making

### Module Assessment Tasks

- identify which dependency claims are justified by business meaning
- determine the key or keys of a relation
- explain what anomaly exists and why it matters
- compare two decompositions and justify the better design

### Why This Assessment Holds Up Better

- it treats normalization as judgment, not symbol pushing
- it exposes whether students can distinguish a correct-looking answer from a sound one
- it tests whether students know what "better design" actually means
