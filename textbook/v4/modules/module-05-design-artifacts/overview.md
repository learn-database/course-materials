# Module 5 Overview: Design Artifacts

## Devotion

> *"Plans succeed through good counsel."*
> — Proverbs 15:22 (paraphrased from *"Plans fail for lack of counsel, but with many advisers they succeed."*)

A design artifact is a form of communication. The conceptual ER Diagram says: here is what the organization tracks and how those things connect. The Database Design Diagram says: here is exactly how to build it. Both documents are claims — about the business, about the design, about what was agreed to. When those documents are unclear, imprecise, or confused with each other, the people who depend on them cannot act on them well.

An ERD cluttered with data types and nullability decisions cannot be reviewed by a business stakeholder. A DBDD that does not specify foreign keys or data types cannot be implemented without guessing. Artifacts that mix conceptual and implementation detail create work for everyone downstream: developers have to guess what was intended, reviewers cannot evaluate what they are looking at, and errors introduced by the ambiguity are hard to trace back to their source.

Clarity in communication is a form of neighbor care. When you produce artifacts that others can read, understand, and act on — without filling in gaps yourself — you are doing your colleagues and your organization a service. This module asks you to take that responsibility seriously.

## What This Module Is About

Module 5 is about producing and evaluating the two main design artifacts in the database workflow: the **ER Diagram** and the **Database Design Diagram**. These are not two versions of the same thing. They are different artifacts that answer different questions and belong to different stages of the workflow.

Three lessons. Each one focuses on a different artifact task:

- **Lesson 5.1** teaches you to refine a first-pass conceptual ERD into a clearer, more precise model using Crow's Foot notation.
- **Lesson 5.2** introduces the Database Design Diagram as a separate implementation-ready artifact and explains what it must include.
- **Lesson 5.3** teaches you to map a conceptual ERD systematically to a DBDD, making the key decisions that convert modeling choices into table structure decisions.

## Why This Module Matters

The boundary between the ERD and the DBDD is one of the most consistently confused boundaries in introductory database work. Students (and AI-generated artifacts) frequently mix conceptual and implementation detail into the same document, or produce a DBDD that claims to follow an ERD but does not actually match it.

This module teaches you to keep those boundaries clear and to produce each artifact with enough precision that a developer could implement from the DBDD without guessing. Precision here is not about perfectionism. It is about accountability. An imprecise DBDD that is later implemented incorrectly means the organization stores data in a structure that does not match its actual business rules.

## How The Lessons Connect

| Lesson | Core Question | What You Will Do |
|--------|---------------|-----------------|
| 5.1: Refining Conceptual ERDs | Is this ERD clear, accurate, and appropriately scoped? | Improve an ERD's notation, identifiers, cardinality, and optionality without adding implementation detail |
| 5.2: Database Design Diagrams | What does an implementation-ready design artifact look like? | Read and evaluate a DBDD; identify what each element specifies and why |
| 5.3: From Logical Model to Implementation-Ready Design | How do you get from a conceptual ERD to a DBDD? | Map entities to tables, resolve relationships, assign data types and nullability, justify each decision |

Lessons 5.1 and 5.2 each focus on one artifact. Lesson 5.3 is the bridge — it teaches the systematic mapping that connects the two.

## Where This Module Fits The Workflow

This module covers **stages 4 and 5** of the course workflow:

4. **Create the conceptual ER Diagram** — refine the model from Module 3 to be clear and implementation-ready
5. **Convert the logical model into an implementation-ready Database Design Diagram** — make the design decisions that SQL Server implementation will depend on

Module 3 produced a first-pass conceptual ERD. Module 5 refines that ERD and converts it into the DBDD that Module 6 will implement. The ERD and DBDD together form the design package that everything downstream depends on.

## What The Assessment Will Ask

The module assessment is an **ERD versus DBDD Boundary Review**. You will be given a set of mixed artifacts and asked to:

- classify specific elements as conceptual (ERD-appropriate) or implementation-level (DBDD-appropriate)
- identify elements that are in the wrong artifact
- repair the artifact split so each document contains only what it should
- justify why each boundary decision is correct

You will not only be asked to produce new artifacts. You will be asked to evaluate existing ones and defend what belongs where.

## Key Terms To Watch For

- `conceptual ERD` — a diagram that shows entities, significant attributes, identifiers, and relationships without implementation detail
- `Crow's Foot notation` — a diagramming convention that uses specific line-end symbols to show cardinality and optionality
- `cardinality symbol` — the line-end mark showing whether the maximum is one or many
- `optionality symbol` — the line-end mark showing whether participation is mandatory or optional
- `implementation clutter` — data type, nullability, constraint, or other implementation-specific detail that does not belong in a conceptual ERD
- `Database Design Diagram (DBDD)` — an artifact showing tables, columns, primary keys, foreign keys, data types, and nullability decisions
- `primary key (PK)` — one or more columns that uniquely identify every row in a table
- `foreign key (FK)` — a column that references the primary key of another table to enforce a relationship
- `data type` — the defined type for a column, such as `INT`, `VARCHAR`, `DATE`, or `DECIMAL`
- `nullability` — whether a column is allowed to be empty (`NULL`) or must always have a value (`NOT NULL`)
- `resolution table` — a table created to implement a many-to-many relationship, holding the foreign keys of both related tables

## A Note On The ERD/DBDD Boundary

The most important habit this module develops is asking: does this detail belong in a conceptual ERD, or does it belong in a DBDD?

ERDs answer: what does the organization track and how are those things related?
DBDDs answer: how should those things be physically stored in SQL Server?

When you mix these, both artifacts become less useful — the ERD becomes hard to read for stakeholders who do not need implementation detail, and the DBDD becomes hard to verify against the actual business model. Keeping the boundary clean is a form of careful, responsible design communication.
