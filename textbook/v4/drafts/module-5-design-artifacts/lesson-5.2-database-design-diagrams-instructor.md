# Lesson 5.2: Database Design Diagrams

## Instructor-Facing Content

### Module

Module 5: Design Artifacts

### Lesson purpose

Students learn to convert a reviewed conceptual ERD into a separate implementation-ready Database Design Diagram (`DBDD`). The lesson introduces tables, `PK`, `FK`, SQL Server data types, nullability, and intersection tables as correct `DBDD` content rather than as clutter added to the conceptual ERD.

### Module context

This lesson sits at the center of Module 5's artifact-boundary work.

- Lesson 5.1 kept the ERD conceptual and corrected notation without implementation detail.
- Lesson 5.2 introduces the implementation-ready detail that belongs in the `DBDD`.
- Lesson 5.3 will move from direct instruction into critique, repair, and justification of ERD-to-DBDD conversion choices.

The lesson should make the `DBDD` feel like a separate artifact with a separate job, not a more decorated ERD.

### Primary learning type(s)

- Procedures

### Secondary learning type(s), if any

- Principles

### Estimated time

- 70 to 85 minutes

### Lesson outcomes

By the end of the lesson, students should be able to:

- explain what belongs in a `DBDD` that does not belong in a conceptual ERD
- convert conceptual entities and relationships into first-pass tables and keys
- justify `PK`, `FK`, data type, and nullability choices from business meaning
- resolve a many-to-many relationship with an intersection table
- classify details as `ERD-only`, `DBDD-only`, `both`, or `neither`
- explain how implementation-ready precision protects against hidden operational errors

### Module alignment

- supports Module 5 objectives on converting entities into tables and adding `PK`, `FK`, data types, and nullability in a `DBDD`
- reinforces the module rule that ERDs and `DBDD`s must remain distinct artifacts
- supports the module's primary assessment pattern, which asks students to classify, repair, and justify artifact-boundary decisions
- prepares students for Lesson 5.3 and for Module 6, where the approved `DBDD` becomes SQL Server implementation

### Course objective alignment

- Objective 3: create ER Diagrams and Database Design Diagrams that reflect a given business process
- Objective 4: normalize a database design appropriately

### Lesson sequence role

This is the first lesson where implementation-ready detail belongs in the artifact itself. Students should leave with a reliable conversion procedure and with a sharper sense of the ERD-versus-`DBDD` boundary before they are asked to critique and defend conversion choices in Lesson 5.3.

### Required prior knowledge

- entities, attributes, identifiers, relationships, cardinality, and optionality from Module 3
- key logic and normalization awareness from Module 4
- conceptual ERD refinement from Lesson 5.1
- naming and notation conventions from `textbook/v4/06-design-object-naming-and-notation-conventions.md`

### Lesson opening guidance

Open with a reviewed conceptual ERD and ask, "What is still missing if we want to build this in SQL Server?" Use the answers to surface tables, keys, data types, and nullability. Then make the boundary explicit: the conceptual ERD was not incomplete because it was poor; it was incomplete for implementation because that was not its job.

### Teaching notes

- Keep repeating the artifact boundary. Students should hear both questions often:
  - what does the ERD mean?
  - what does the `DBDD` need to add?
- Require business-language explanations for `PK`, `FK`, data type, and nullability decisions before accepting shorthand notation alone.
- Use one coherent case so students can watch conceptual meaning stay stable while implementation detail is added.
- Include at least one nullability example that breaks the simplistic rule that every optional relationship means a nullable foreign key.
- Treat data types and nullability as design decisions tied to business meaning, not as memorized syntax choices.
- Keep SQL enforcement syntax out of scope. Module 6 will implement these choices in `CREATE TABLE` statements.

### Online activities

- guided case conversion from reviewed conceptual ERD to first-pass `DBDD`
- short classification check using `ERD-only`, `DBDD-only`, `both`, and `neither`
- brief rationale prompt for one `PK`, one `FK`, one data type, and one nullability choice

### Homework / graded assignments

- submit a `DBDD` for the reviewed case
- submit a short written rationale explaining selected implementation-ready choices
- complete a short artifact-boundary classification check

### Deliverables

- one Database Design Diagram
- one short written design rationale
- one completed boundary-classification activity or quiz

### Assessment plan

Primary evidence:

- completed `DBDD` for the reviewed case

Secondary evidence:

- short written rationale
- short boundary-classification check

What to verify:

- the table set matches the conceptual model or a required many-to-many resolution
- `PK` and `FK` choices are structurally correct and explainable
- data types and nullability choices trace back to business meaning
- the student places implementation-ready detail in the correct artifact
- the student can classify mixed details as `ERD-only`, `DBDD-only`, `both`, or `neither`

### Suggested rubric focus

- artifact-boundary accuracy
- quality of ERD-to-`DBDD` translation
- correctness of `PK` and `FK` placement
- quality of data type and nullability reasoning
- clarity of written justification

### Common misconceptions

- "`DBDD` just means adding labels onto the ERD."
- "`PK`, `FK`, data types, and nullability belong in the conceptual ERD once the model is refined enough."
- "Every optional relationship means the foreign key should be nullable."
- "A data type is chosen by what looks numeric instead of what the value means."
- "If the diagram looks polished, the design decisions must be sound."

### Christian integration notes

Keep the integration embedded in the technical lesson. A strong place is the warning that imprecise `PK`, `FK`, data type, or nullability choices can create hidden downstream errors in records, scheduling, billing, or follow-up work. Frame careful `DBDD` precision as trustworthy communication and faithful professional follow-through that protects people and operations from avoidable confusion.

Use the project checkpoint question from the module plan:

- where does design precision protect users, customers, staff, or records from confusion or loss?

### Workflow connection

This lesson occupies the handoff between conceptual modeling and implementation. Students have already identified entities, relationships, and optionality in earlier workflow stages. Here they convert that meaning into tables and implementation-ready structure. Module 6 will then take the approved `DBDD` and turn it into actual SQL Server tables and constraints.
