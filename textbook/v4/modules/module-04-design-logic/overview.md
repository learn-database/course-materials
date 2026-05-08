# Module 4 Overview: Design Logic

## Devotion

> *"Differing weights and differing measures — the Lord detests them both."*
> — Proverbs 20:10

The image in Proverbs is a merchant using one set of weights when buying and another when selling — measures that appear accurate but consistently distort the truth. The harm is not always visible in any single transaction. It accumulates in the pattern, in the asymmetry between what was promised and what was actually delivered.

A poorly structured relational table works the same way. When a single row encodes multiple independent facts — when changing one correct value silently breaks another — the table has become an unreliable measure. Staff spend time reconciling records that should agree. Reports contain inconsistencies that no one can trace. Decisions are made on data that quietly contradicts itself. The organization cannot consistently tell the truth about its own operations.

This module teaches you to find that structural unreliability before it is built into the system. The tools — functional dependency reasoning, key analysis, normalization — are analytical, not just procedural. They ask: does this table give an honest account of the facts it is supposed to hold? And if not, how should it be repaired?

Honest design is a form of honest business practice. That is what this module is working toward.

## What This Module Is About

Module 4 teaches you to evaluate the internal quality of a relational table design. A table can look reasonable on the surface while hiding structural problems that cause reporting errors, update failures, and data that contradicts itself. The tools for detecting and fixing those problems are `functional dependencies`, `keys`, and `normalization`.

Three lessons. Each one builds a layer of reasoning:

- **Lesson 4.1** teaches you to read and justify functional dependency claims using business rules.
- **Lesson 4.2** teaches you to identify keys — the minimal sets of attributes that uniquely identify a row.
- **Lesson 4.3** teaches you to diagnose structural problems and repair them through normalization.

## Why This Module Matters

This module is the most analytically demanding in the course. It asks you to reason carefully about what determines what in a set of data, and to justify that reasoning with stated business rules rather than pattern-matching against a sample.

That rigor matters for a practical reason. A poorly structured table has real consequences. Staff waste time correcting inconsistencies. Reports misstate what actually happened. Routine changes — updating a department name, recording a new assignment — can corrupt records elsewhere without anyone noticing. Good design prevents those failures before they occur.

It also matters for a professional reason. AI tools can produce table structures quickly. But a generated structure that looks plausible may still have hidden anomalies. This module gives you the reasoning skills to evaluate those structures, not just accept them.

## How The Lessons Connect

| Lesson | Core Question | What You Will Do |
|--------|---------------|-----------------|
| 4.1: Functional Dependencies | What determines what in this data? | Identify determinants; defend or reject dependency claims with business rules |
| 4.2: Keys of Relations | Which attribute sets uniquely identify a row? | Test superkeys for minimality; identify candidate keys; distinguish prime and nonprime attributes |
| 4.3: Normalization and Design Repair | Does this structure cause anomaly problems, and how should it be repaired? | Diagnose partial and transitive dependency violations; compare decomposition options; defend a repair |

The three lessons form a chain. You cannot identify normalization violations without understanding keys. You cannot reason about keys without understanding functional dependencies. Start at 4.1 and follow the progression.

## Where This Module Fits The Workflow

This module supports **stage 3** of the course workflow:

3. **Identify entities, attributes, and relationships** — specifically, ensuring the attributes assigned to each entity are correctly structured, non-redundant, and free of anomaly-causing dependencies

Module 3 asked you to decide what the organization tracks. Module 4 asks you to examine the structure of those decisions more rigorously. The cleaned design you produce here feeds directly into Module 5, where it becomes the conceptual ERD that will be refined and eventually implemented.

## What The Assessment Will Ask

The module assessment is a **Normalization Judgment Task**. You will be given a partially or incorrectly structured relation and two proposed decompositions, and asked to:

- identify the functional dependencies in the original relation
- identify the key or keys
- diagnose which normal form violation(s) exist and why they cause anomalies
- compare the two decompositions and explain which is stronger and why
- defend your preferred design with specific business-rule reasoning

You will not simply be asked to apply a rote normalization procedure. You will be asked to explain the problem, compare solutions, and defend a choice.

## Key Terms To Watch For

- `functional dependency` — a relationship where knowing the value of one attribute determines the value of another; written as `A → B`
- `determinant` — the attribute (or set of attributes) on the left side of a functional dependency
- `superkey` — any attribute set that uniquely identifies every row in a relation
- `candidate key` — a minimal superkey; no attribute can be removed and still leave it unique
- `prime attribute` — an attribute that belongs to at least one candidate key
- `nonprime attribute` — an attribute that does not belong to any candidate key
- `partial dependency` — when a nonprime attribute depends on only part of a composite key
- `transitive dependency` — when a nonprime attribute depends on another nonprime attribute rather than directly on the key
- `update anomaly` — when changing a fact requires updating it in multiple rows, with risk of inconsistency
- `insertion anomaly` — when a fact cannot be recorded without creating an unwanted or incomplete row
- `deletion anomaly` — when deleting a row loses information about an unrelated fact
- `normalization` — the process of restructuring a relation to remove dependency violations and eliminate anomalies

## A Note On Business Rules Versus Sample Data

A common mistake in this module is to read a sample table and conclude that a dependency exists because two columns happen to match in the sample rows. That is not a justified dependency. Dependencies must be supported by a stated business rule — something that is always true about how the organization works, not just something that appears to be true in a few example rows.

Lesson 4.1 focuses directly on this distinction. Take it seriously. The reasoning habit it builds is what separates defensible design analysis from plausible-looking guesses.
