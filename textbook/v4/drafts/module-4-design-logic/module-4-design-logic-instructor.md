# Module 4 Overview: Design Logic

## Instructor-Facing Content

### Module Purpose

Module 4 teaches relational design judgment. Students should leave able to
justify functional dependencies, defend candidate keys, diagnose anomaly risk,
and compare normalization repairs without treating normalization as mechanical
symbol pushing.

### Role In The Course

This module sits between Module 3 conceptual modeling and Module 5 design
artifacts. The point is to strengthen design logic before students refine ERDs,
build DBDDs, or implement tables in SQL Server.

Lesson flow:

- `4.1` establishes dependency meaning and rejection of sample-only claims
- `4.2` turns that dependency logic into key reasoning with explicit
  sufficiency and minimality
- `4.3` uses both to diagnose anomalies, compare decompositions, and defend
  design repair

### Implementation Guidance

- Keep one small business case or relation stable across the module when
  possible so students can see the sequence from dependency meaning to keys to
  repair.
- Make students state what one row means before they judge dependencies, keys,
  or decompositions.
- Require plain-language justification for accepted and rejected claims.
- Keep closure and minimality separate during key work.
- Present `1NF`, `2NF`, `3NF`, and `BCNF` as distinct checkpoints for distinct
  weaknesses.
- Revisit business impact repeatedly: copied facts create waste,
  contradiction, and trust damage in billing, scheduling, inventory, advising,
  or service work.

### Alignment And Assessment

This module aligns best when graded work emphasizes explanation, comparison,
and diagnosis rather than standalone normalization output.

Strong module evidence includes:

- dependency judgments defended from business rules
- candidate-key reasoning that distinguishes sufficiency from minimality
- anomaly diagnosis with business-consequence explanation
- decomposition comparison that identifies the stronger repair and explains why

Suggested grading focus:

- validity of FD reasoning
- strength of key justification
- accuracy of anomaly diagnosis
- clarity of normalization defense
- ability to detect when a tidy-looking decomposition breaks row meaning

### Misconceptions To Watch

- sample uniqueness proves a dependency or a key
- a superkey is automatically a candidate key
- normalization means splitting until tables are small
- reduced redundancy automatically means preserved meaning
- anomalies are just user mistakes instead of structural design problems
- Module 4 is where students should start drawing final ERDs or DBDDs

### Boundary And Risk Notes

- Do not drift into ERD versus DBDD production. That belongs to Module 5.
- Do not substitute SQL constraint syntax for FD or key reasoning.
- Keep `BCNF` as the strongest functional-dependency-based checkpoint in scope,
  but do not expand into later normal forms.
- Treat intersection tables here as repair logic only, not as full artifact
  production.
- In an AI-available course, the main risk is uncritical acceptance of a
  generated decomposition. Require students to answer questions such as "What
  determinant owns this fact?" and "What row meaning does this repair preserve?"

### Christian Integration Notes

Keep integration brief and embedded inside normal examples, warnings, and
checkpoints. This module naturally supports stewardship, truthful reporting,
and neighbor-serving information work because weak design wastes resources and
can damage trust through inconsistent or misleading data.
