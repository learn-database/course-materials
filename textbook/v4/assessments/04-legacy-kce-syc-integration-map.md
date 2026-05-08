# Legacy KCE And Seek Your Challenge Integration Map

Status: draft  
Source system: `dbm-materials/src/lib/lessons/b*.json`  
Target system: v4 workbook platform import contract

## Purpose

The legacy `src` folder contains a useful exercise bank that should not be copied directly into the v4 lesson text. The v4 source should keep `lesson.md` readable and import each Knowledge Check Exercise or Seek Your Challenge file as its own standalone workbook lesson inside the assigned module.

This file maps the current legacy exercises into the v4 module sequence.

## Source Exercise Sets

Use the decoded files with the `b` prefix as the source of truth. Do not use the encoded `210*.json` files in the new platform.

| Legacy file | Legacy title | Primary topic | Question types |
|---|---|---|---|
| `b210001.json` | Knowledge Check Exercise #1 | single-table `SELECT` | `sql`, `sql short answer` |
| `b210002.json` | Knowledge Check Exercise #2 | aggregates and grouping | `multiple choice`, `short answer` |
| `b21000202.json` | Knowledge Check Exercise #2b | aggregates and grouping with SQL output checks | `sql short answer` |
| `b210003.json` | Knowledge Check Exercise #3 | joins and subqueries | `multiple choice`, `short answer` |
| `b21000302.json` | Knowledge Check Exercise #3b | joins with SQL output checks | `sql multiple choice`, `sql short answer` |
| `b21000401.json` | Knowledge Check Exercise #4.1 | functional dependencies and normal forms | `multiple choice`, `multiple answers`, `short answer`, `essay` |
| `b21000402.json` | Knowledge Check Exercise #4.2 | BCNF repair practice | `multiple choice`, `essay` |
| `b21000501.json` | Knowledge Check Exercise #5 | referential integrity and dependency-aware design | `text block`, `multiple choice`, `multiple answers`, `short answer`, `essay` |
| `b21000601.json` | Knowledge Check Exercise #6 | conceptual ERD design and self-check | `self check` |
| `b21000701.json` | Knowledge Check Exercise #7 | first part of ERD-to-DBD transformation | `matching`, `multiple choice`, `multiple answers`, `self check` |
| `b21000801.json` | Knowledge Check Exercise #8 | relationship implementation in DBD | `multiple choice`, `self check` |
| `b21000901.json` | Knowledge Check Exercise #9 | creating tables and inserting data | `text block`, `multiple choice` |
| `b21001001.json` | Knowledge Check Exercise #10 | update, delete, and views | `text block`, `multiple choice` |
| `b21001101.json` | Knowledge Check Exercise #11 | transactions, isolation, and CRUD permission thinking | `text block`, `multiple choice`, `multiple answers`, `matching`, `matrix multiple answers` |
| `b21001201.json` | Knowledge Check Exercise #12 | stored procedures | `text block`, `multiple choice` |
| `b21001301.json` | Knowledge Check Exercise #13 | triggers | `text block`, `multiple choice` |

## KCE To Module Map

| v4 module | Legacy KCE lessons | Integration purpose | Notes |
|---|---|---|---|
| Module 1: The Whole Database Workflow | no direct legacy KCE | use v4-native checks only | Legacy KCE starts after basic workflow concepts. |
| Module 2: SQL Foundations | KCE #1, #2, #2b, #3, #3b | provide frequent SQL fluency checks for select, aggregate, grouping, joins, and subqueries | Import each KCE file as a standalone lesson using all original questions. |
| Module 3: Core Data Modeling | KCE #6 | provide conceptual ERD scenario practice and self-check rubrics | Import KCE #6 as its own lesson using all seven original questions. |
| Module 4: Design Logic | KCE #4.1, #4.2 | provide functional dependency, normal form, and BCNF repair checks | Import each KCE file as a standalone lesson using all original questions. |
| Module 5: Design Artifacts | KCE #5, #7, #8 | support referential integrity, ERD-to-DBD transformation, datatype/nullability, and relationship implementation | KCE #7 and #8 are especially strong for implementation-ready design artifacts. |
| Module 6: SQL Server Implementation | KCE #9, #10 | practice table creation, data modification, and views | Import each KCE file as a standalone lesson using all original questions. |
| Module 7: Database Operation and Control | KCE #11 | practice transaction boundaries, isolation levels, and CRUD/permission reasoning | KCE #11 supports both transaction and role/permission topics. |
| Module 8: Procedural Logic and Final Project Revision | KCE #12, #13 | practice stored procedures and triggers | Import each KCE file as a standalone lesson using all original questions. |

## Seek Your Challenge To Module Map

The `Seek Your Challenge` files are all NorthWind SQL challenge sets. They should be reused from Modules 2-8 to keep SQL practice active throughout the course, even when the primary module topic shifts back to design or operations.

| v4 module | Legacy challenge lessons | Purpose |
|---|---|---|
| Module 2 | `b21009901.json`, `b21009902.json` | reinforce foundational `SELECT`, filtering, joins, grouping, and business reports |
| Module 3 | `b21009903.json` | keep SQL retrieval practice active while students work on conceptual modeling |
| Module 4 | `b21009904.json` | reinforce reporting queries while students study design logic |
| Module 5 | `b21009905.json` | reinforce aggregate reporting while students move from ERD to DBD |
| Module 6 | `b21009906.json` | connect implementation work with operational reporting about late orders |
| Module 7 | `b21009907.json` | keep analytical SQL practice active while studying operations and control |
| Module 8 | `b21009908.json` | provide final cumulative sales-report SQL practice alongside procedural logic |

## Runtime Mapping Rules

Legacy exercise types should map to the workbook runtime as follows:

| Legacy type | Workbook kind | Default scoring |
|---|---|---|
| `text block` | `content_block` | no score or completion-only |
| `multiple choice` | `choice_interaction` | `automatic` |
| `multiple answers` | `multi_select_interaction` | `automatic` |
| `short answer` | `short_answer_interaction` | `automatic` when answer is deterministic; otherwise `self_graded` |
| `essay` | `written_response_interaction` | `grading_prompt` |
| `self check` | `checklist_interaction` | `self_graded` |
| `matching` | `matching_interaction` | `automatic` |
| `matrix multiple answers` | `matrix_interaction` | `automatic` |
| `sql` | `sql_interaction` | `automatic` after SQL execution/grading support exists |
| `sql multiple choice` | `sql_choice_interaction` | `automatic` |
| `sql short answer` | `sql_short_answer_interaction` | `automatic` |

## Authoring Rule

Do not paste full legacy KCE or SYC content into `lesson.md`. Instead:

- Keep `lesson.md` focused on the student learning flow.
- Import each legacy KCE or SYC file as a standalone workbook lesson inside the assigned module.
- Preserve every original question from the legacy file unless the instructor explicitly retires the entire file.
- Preserve legacy prompts, options, hints, solutions, feedback, and point values in the imported interactions.
- Add v4 tags such as `check-your-knowledge`, `seek-your-challenge`, `legacy-kce`, `legacy-syc`, `self-graded`, or `sql-practice`.

Example:

```yaml
legacyLessons:
  - id: module-3.legacy-kce-6
    source: "legacy:dbm-materials/src/lib/lessons/b21000601.json"
    title: Knowledge Check Exercise #6
    moduleNumber: 3
    lessonNumber: 4
    slug: knowledge-check-exercise-6
    label: Check Your Knowledge
    tags:
      - legacy-kce
      - check-your-knowledge
      - conceptual-erd
```

## Module 3 Pilot Mapping

Module 3 should pilot the legacy-KCE-as-lesson import flow with KCE #6 because it directly targets conceptual ERD judgment.

| Module 3 lesson | Purpose |
|---|---|---|
| Lesson 3.1: Entities, Attributes, and Identifiers | v4-native lesson flow |
| Lesson 3.2: Relationships and Cardinality | v4-native lesson flow |
| Lesson 3.3: Discovering Requirements and Drafting a Conceptual ERD | v4-native lesson flow |
| Knowledge Check Exercise #6 | standalone legacy lesson containing all seven original KCE #6 questions |

The pilot should import all three Module 3 lessons plus KCE #6 as a fourth standalone lesson before expanding legacy imports to other modules.
