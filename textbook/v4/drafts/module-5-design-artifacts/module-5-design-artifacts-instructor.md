# Module 5: Design Artifacts

## Instructor-Facing Content

### Module purpose

Module 5 teaches the artifact boundary between the conceptual `ERD` and the implementation-ready `DBDD`. Students should leave able to refine the `ERD`, build a separate `DBDD`, and justify how conceptual meaning becomes implementation-ready structure without drifting into Module 6 SQL build work.

### Module alignment

- aligns to the module plan goal of preserving the conceptual-versus-implementation boundary while refining `ERD`s and building `DBDD`s
- uses Lesson 5.1 for conceptual refinement, Lesson 5.2 for implementation-ready artifact construction, and Lesson 5.3 for critique, repair, and design-rationale work
- supports Course Objective 3 by strengthening both `ERD` and `DBDD` performance
- supports Course Objective 4 indirectly by requiring students to make structurally sound implementation-ready choices without turning this module into a normalization reteach

### Implementation guidance

- Keep the student-facing emphasis on two separate artifacts with two separate jobs.
- Reuse one coherent case across the module so students can see the same business meaning carried from refined `ERD` to `DBDD`.
- Require short business-language justifications for key conversion choices, not just polished diagrams.
- Keep SQL syntax, `CREATE TABLE` statements, and enforcement details out of scope here. Students should be implementation-ready by the end of the module, not yet implementing.

### What to grade

Primary evidence:

- artifact-boundary accuracy across the `ERD` and `DBDD`
- quality of the translation from conceptual relationships to tables, `PK`, `FK`, intersection tables, data types, and nullability

Secondary evidence:

- short critique, classification, or repair task on mixed-up artifacts
- brief written or recorded explanation of one important conversion choice

Look for whether students can explain why a detail belongs in one artifact and not the other. A visually polished diagram alone is weak evidence in this module.

### Common misconceptions

- "`DBDD` means a more detailed `ERD` instead of a separate artifact."
- "Once the `ERD` is refined enough, `PK`, `FK`, data types, and nullability can be added there."
- "Optional relationship automatically means nullable foreign key."
- "If AI generated a clean artifact, the design reasoning must also be sound."
- "This module is already SQL implementation."

### Boundary and risk notes

- The main risk is scope drift into Module 6. Stop before `CREATE TABLE`, constraint syntax, or tool-specific build steps.
- The second risk is backward drift into Module 3 or 4 reteaching. Use prior knowledge, but keep the focus on artifact separation and handoff logic.
- Watch for students who preserve notation accuracy but quietly change business meaning during conversion.
- Treat nullability choices as a high-value diagnostic point because they often expose whether students actually understand optionality versus row existence.

### Christian integration note

Keep the integration embedded in ordinary design decisions. A natural touchpoint is that artifact clarity and careful mapping are forms of trustworthy communication and accountable professional follow-through. Ask where poor `PK`, `FK`, data type, or nullability choices could create hidden confusion, loss, or harm for users, staff, customers, or records.
