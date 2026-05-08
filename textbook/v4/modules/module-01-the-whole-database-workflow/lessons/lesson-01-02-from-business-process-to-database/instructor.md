# Lesson 1.2: From Business Process to Database

## Instructor-Facing Content

### Module

Module 1: The Whole Database Workflow

### Lesson Purpose

Give students a reusable map of the whole course workflow from business process to working database, with special emphasis on artifact-stage handoffs and the ERD versus DBDD boundary.

### Module Context

Lesson 1.1 established why databases matter and when a database is warranted. Lesson 1.2 completes Module 1 by showing what happens after an organization identifies a real business need. The lesson is a bridge lesson: it prepares students to revisit the same workflow across later modules while preventing early confusion about the ERD and the DBDD.

### Primary Learning Type(s)

- Problem solving / judgment

### Secondary Learning Type(s), If Any

- Concepts
- Principles

### Estimated Time

- 70 to 90 minutes

### Lesson Outcomes

By the end of this lesson, students should be able to:

- explain the workflow from business process to working database use in the correct order
- connect artifacts and outputs to the workflow stages they belong to
- explain what the ERD shows and why it stays conceptual
- explain what the DBDD adds and why it is implementation-ready
- describe how workflow discipline supports truthful, accountable organizational reporting

### Module Alignment

- Supports Module 1’s purpose of giving students a simple end-to-end view of the database process.
- Delivers the module objective to distinguish the ERD from the DBDD.
- Prepares students for the module’s classification-based assessment pattern rather than a polished artifact-only submission.

### Course Objective Alignment

- Objective 1: know basic database terminology
- Objective 2: evaluate a business process and determine what data must be stored
- Objective 3: create ER Diagrams and Database Design Diagrams that reflect a given business process
- Objective 5: create and use SQL statements for querying and data manipulation
- Objective 6: administer introductory backup, recovery, security, and concurrency control work

### Lesson Sequence Role

- Follows Lesson 1.1, which addressed why a database may be needed.
- Prepares students for later modules that unpack individual workflow stages in depth.
- Functions as the orientation lesson students should mentally revisit throughout the course.

### Required Prior Knowledge

- Lesson 1.1 vocabulary: business process, data, information, database
- basic awareness that organizations use records to support recurring work and later reporting

### Lesson Opening Guidance

- Begin by reminding students that deciding to use a database is not the same as knowing how database work proceeds.
- Frame this lesson as the workflow map for the rest of the course.
- State early that the ERD and DBDD are connected but not interchangeable.
- Tell students that the lesson favors stage purpose and artifact judgment over technical detail.

### Teaching Notes

- Use one simple recurring case such as a campus tutoring center.
- Keep the workflow explicit from start to finish so students can reuse the map later.
- Reinforce the handoff logic:
  - business need leads to requirements
  - requirements lead to conceptual modeling
  - conceptual modeling leads to implementation-ready design
  - implementation-ready design leads to SQL Server implementation
  - implementation supports querying, operation, and revision
- Keep the ERD versus DBDD boundary exact. Do not place data types, nullability, or implementation-focused PK and FK notation inside ERD explanations.
- Keep SQL Server implementation, query work, and operational control conceptual in this lesson. Detailed execution belongs to later modules.
- Name the AI-available reality directly. Students may use AI to draft lists or explanations, but they still must verify stage order, artifact boundaries, and business fit.

### Online Activities

- workflow-order check using drag-and-drop, matching, or equivalent LMS format
- artifact-to-stage placement exercise
- ERD-versus-DBDD classification check
- short written explanation of why skipping workflow stages can distort reporting or weaken accountability

### Homework / Graded Assignments

- short case framing response:
  - students explain the workflow stages for a small scenario in order
  - students identify which artifact belongs where
- artifact-boundary comparison:
  - students explain what the ERD shows
  - students explain what the DBDD adds

### Deliverables

- one workflow explanation or classification response
- one ERD-versus-DBDD comparison using the lesson case or a short parallel case

### Assessment Plan

Formative checks:

- quick check on workflow order
- artifact-stage matching practice
- ERD-versus-DBDD classification practice

Summative alignment with Module 1:

- timed case framing and classification
- short justification of why a given detail belongs in an ERD or DBDD

Evidence to look for:

- stage order is correct
- stage purpose is explained accurately
- ERD remains conceptual
- DBDD is described as implementation-ready
- students can connect workflow discipline to trustworthy reporting and accountable business practice

### Suggested Rubric Focus

- workflow sequence accuracy
- artifact-stage matching accuracy
- clarity of ERD versus DBDD distinction
- quality of explanation, not just terminology recall
- ability to connect technical discipline to truthful, responsible organizational use of data

### Common Misconceptions

- "The ERD and DBDD are basically the same diagram."
- "If a table name exists, the work is already implementation-ready."
- "Any detail mentioned in a case belongs in the database."
- "Query writing is the beginning of database work."
- "If AI can draft the explanation, verification is unnecessary."

### Christian Integration Notes

- Tie workflow discipline to truthful business reporting and accountability.
- Show that weak structure is not only inefficient but also a stewardship problem because it wastes time, creates rework, and can misstate reality.
- Use short prompts such as:
  - How does careful workflow discipline help an organization tell the truth about its operations?
  - Who could be harmed if the database stores the wrong information or reports incompletely?
- Keep the integration inside normal teaching and assessment elements rather than in a separate devotional section.

### Workflow Connection

This lesson is the course map. Students should leave knowing where later lessons fit:

- Module 3 expands the conceptual modeling stages
- Module 5 returns to ERDs and DBDDs explicitly
- Module 6 implements the DBDD in SQL Server
- Module 7 addresses operational control
- Module 8 revisits revision and change

If students retain that map, later lessons will feel like deeper work on a known workflow rather than disconnected technical units.
