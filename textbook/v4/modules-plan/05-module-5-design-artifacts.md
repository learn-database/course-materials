# Module 5: Design Artifacts

### Purpose

- Refine the conceptual ERD and build the implementation-ready Database Design Diagram as a separate artifact.
- Preserve the ERD versus DBDD boundary in instruction and assessment.

### Objectives

- refine a conceptual ERD in Crow's Foot notation
- keep the ERD true to its conceptual purpose
- critique ERDs that drift into implementation detail
- convert entities into tables
- add PKs, FKs, data types, and nullability in a DBDD
- resolve many-to-many relationships into intersection tables

### Human Must Know

- what belongs in an ERD versus a DBDD
- why PKs, FKs, data types, and nullability belong in one artifact but not the other
- how table structure should trace back to conceptual meaning
- how to detect boundary violations

### AI May Assist With

- diagram cleanup and formatting
- DBDD first drafts
- PK and FK suggestions
- candidate data types and nullability proposals

### Christian Integration Focus

- connect ERD and DBDD clarity to trustworthy communication and faithful professional follow-through
- frame PK, FK, nullability, and mapping precision as protection against hidden errors that can harm people or operations

### Integration Touchpoints

- include one review prompt asking whether another person could understand the model without guesswork
- include one project checkpoint asking where design precision protects users, customers, staff, or records from confusion or loss

### Lessons

#### Lesson 5.1: Refining Conceptual ERDs in Crow's Foot Notation
- improve conceptual clarity
- correct notation without adding implementation clutter

#### Lesson 5.2: Database Design Diagrams
- convert conceptual structures into tables, keys, and implementation-ready detail

#### Lesson 5.3: From Logical Model to Implementation-Ready Design
- trace the move from ERD to DBDD and justify structural choices

### Assessment Strategy

This module should explicitly test artifact boundaries. AI can produce both diagrams quickly, but students still need to know whether the right information is in the right artifact and whether the conversion makes sense.

### Primary Graded Assessment

#### ERD versus DBDD Boundary Review

- Format: students receive mixed-up design artifacts that blend conceptual and implementation-ready details
- Students classify which elements belong where, repair the artifact split, and justify selected boundary decisions

### Secondary Evidence

- short screencast or annotation explaining one ERD-to-DBDD conversion choice
- timed classification quiz on artifact-boundary decisions

### What To Grade

- correctness of artifact classification
- ability to explain why a detail belongs in one artifact and not the other
- quality of translation from conceptual model to DBDD
- consistency of keys and relationships across both artifacts
- ability to name a real accountability or trust risk caused by poor artifact clarity or weak mapping decisions

### Module Assessment Tasks

- classify details as ERD-only, DBDD-only, both, or neither
- repair a design that mixes conceptual and implementation detail
- justify PK, FK, data type, and nullability placement
- explain how one relationship becomes implementation-ready structure

### Why This Assessment Holds Up Better

- it directly tests the boundary students often blur
- it makes "what belongs where" the graded performance
- it uses generated diagrams as material for evaluation rather than mere submission
