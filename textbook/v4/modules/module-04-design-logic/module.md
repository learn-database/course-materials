# Module 4 Overview: Design Logic

## Module Overview

Module 4 is the design-quality module for relational structure. In Module 3,
you learned to read requirements, identify entities and relationships, and
draft a conceptual model. In this module, you test whether the logic behind a
relation is actually defensible.

That means you will study functional dependencies, keys, anomalies, and
normalization as connected ideas. The goal is not to push symbols around until
the notation looks formal. The goal is to explain why facts belong where they
belong, why one key is stronger than another, and why one repair preserves the
truth of the business case better than a weaker alternative.

## Why This Module Matters

A relation can look tidy and still be poorly designed. Weak design often hides
until someone updates a copied fact, deletes the last row of a category, or
tries to report from inconsistent data. Then the cost shows up as rework,
waste, contradiction, and damaged trust.

This module teaches you to see those problems earlier. Dependency reasoning,
key logic, and normalization help you protect the database from storing facts
under the wrong owner or combining different levels of meaning in one place.
In a Christian business setting, that is also a stewardship issue: good design
uses time and organizational resources more wisely and supports truthful
reporting that serves coworkers, managers, customers, and other neighbors well.

## What This Module Is For

By the end of this module, you should be able to:

- defend functional dependency claims from business meaning instead of sample
  patterns
- determine which attribute sets are real candidate keys and which are only
  superkeys or weak guesses
- explain why insert, update, and delete anomalies are structural problems
  rather than isolated data-entry mistakes
- use `1NF`, `2NF`, `3NF`, and `BCNF` as checkpoints for specific weaknesses
- compare design repairs and justify which decomposition is stronger

## How The Lessons Fit Together

You should read the lessons in order because each lesson supplies reasoning the
next one needs.

### Lesson 4.1: Functional Dependencies

Lesson 4.1 asks, "What determines what?" You will learn to defend dependency
claims from business rules, reject accidental sample patterns, and separate
meaningful design logic from trivial structural truth.

This lesson matters because weak dependency claims create weak key reasoning
later. If you place a fact under the wrong determinant at the start, the rest
of the design analysis becomes unreliable.

### Lesson 4.2: Keys of Relations

Lesson 4.2 asks, "What actually makes one row unique?" You will use the
dependency reasoning from Lesson 4.1 to test candidate keys, distinguish
superkeys from candidate keys, and keep sufficiency separate from minimality.

This lesson is the bridge between dependency meaning and normalization. Before
you can diagnose partial dependency, transitive dependency, or a weak
decomposition, you need to know what the real key is and what one row is
supposed to mean.

### Lesson 4.3: Normalization and Design Repair

Lesson 4.3 asks, "What should be repaired, and why?" You will identify
anomalies, connect them to business consequences, compare decompositions, and
defend a repair that preserves the intended meaning of the data.

This is where the whole module comes together. Functional dependencies explain
which facts belong together. Key logic explains the row grain. Normalization
uses both ideas to repair weak structure without losing the business story the
relation is supposed to tell.

## The Judgment This Module Builds

This module is not mainly about memorizing labels. It is about learning to make
defensible design judgments.

You are expected to develop these habits:

- start with what one row means before you trust any notation
- ask which business thing owns each fact
- reject claims that only look true in a short sample
- treat closure and minimality as separate tests
- treat normalization as design repair, not as a race to split tables
- compare alternatives and explain why one design is stronger than another

Strong performance in this module sounds like explanation, not just output. A
good answer does more than say "this is in 3NF" or "this is the key." A good
answer explains why the dependencies are valid, why the key is defensible, what
anomaly risk exists, and why the chosen repair better protects consistency,
reduces waste, and preserves trustworthy meaning.

## What This Module Is And Is Not

This module is about:

- dependency reasoning
- key logic
- anomaly diagnosis
- normalization through `BCNF` when appropriate
- repair of weak relation designs

This module is not about:

- producing the final ER Diagram or Database Design Diagram
- choosing SQL Server data types or writing constraint syntax
- treating every tidy-looking decomposition as automatically correct
- moving into later advanced normal forms beyond this course's scope

Module 5 will take stronger relational logic and express it in cleaner design
artifacts. Module 4 prepares that work by making sure the logic is worth
representing in the first place.

## How To Succeed In This Module

- Read the lessons in sequence instead of skipping to normalization rules.
- Keep asking what one row means in each relation you analyze.
- Tie every accepted dependency to a stated business rule.
- Do not confuse a value that looks unique in a sample with a structurally
  sound key.
- When you identify an anomaly, name the business harm it can cause, such as
  duplicate correction work, inconsistent reporting, billing confusion, or lost
  scheduling information.
- When you compare decompositions, ask whether the repair preserves the real
  meaning of the original case.

## Module Assignments And Evidence

The main work in this module should ask you to explain and defend design
judgment, not only to generate a final decomposition.

Expect module evidence such as:

- a dependency-and-key analysis where you accept or reject claims and justify
  your reasoning
- an anomaly diagnosis task where you explain why the weakness matters
- a normalization judgment task where you compare competing decompositions and
  defend the stronger one

These tasks fit an AI-aware course because they test whether you can verify and
defend the logic, not merely produce notation that looks correct.

## Wrap-Up

Module 4 sits between conceptual modeling and later design-artifact work. By
the end of the module, you should be able to judge whether a relation design is
structurally sound, explain what makes it weak when it is not, and defend a
repair that supports clearer, more trustworthy database work.
