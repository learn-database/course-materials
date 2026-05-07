# ITM-2100 Textbook And Lesson Crosswalk

This document is the canonical Fall 2026 map between textbook chapters, `Knowledge Check Exercise` (KCE) lessons, and the `Seek Your Challenge` (SYC) series in `src/lib/lessons`.

## Alignment Model

- textbook chapters provide the primary instructional sequence
- KCE lessons provide chapter-linked guided practice, self-check, and low-stakes assessment
- SYC lessons provide longitudinal SQL retention practice after the early retrieval chapters
- Chapters 1, 2, and 15 remain course-framing chapters rather than one-to-one KCE replacements

## Stable Chapter-To-KCE Crosswalk

| Textbook chapter | Primary lesson support | Support status | Notes for Fall 2026 |
| --- | --- | --- | --- |
| Chapter 1. Why Databases Matter | No standalone KCE. Support comes from the chapter itself and the milestone framing in Chapter 15. | Indirect support | Launch-safe as a textbook-first chapter, but there is no dedicated practice lesson for business framing or anomaly motivation. |
| Chapter 2. SQL Server Environment | No standalone KCE. Environment/setup practice is embedded inside `b210002.json`, `b21000901.json`, `b21001001.json`, `b21001101.json`, `b21001201.json`, and `b21001301.json`. | Indirect support | Students do encounter live environment steps, but there is no single KCE devoted to safe workflow and SQL Server vocabulary. |
| Chapter 3. Querying a Single Table | `b210001.json` | Direct support | Stable one-to-one anchor for `SELECT`, `WHERE`, sorting, aliases, and introductory result reading. |
| Chapter 4. Joins, Grouping, and Common Table Expressions | `b210002.json`, `b21000202.json`, `b210003.json`, `b21000302.json` | Direct support | Stable cluster for aggregation, grouping, joins, and beginner-friendly multi-step query interpretation. |
| Chapter 5. Introduction to Data Modeling | `b21000601.json`, `b21000701.json` | Partial support | `b21000601.json` supports entity, attribute, identifier, and relationship discovery from scenarios, while `b21000701.json` begins the later transition from conceptual modeling into implementation choices. |
| Chapter 6. Functional Dependencies | `b21000401.json` | Direct support | Stable anchor for determinants, candidate-key reasoning, and dependency analysis. |
| Chapter 7. Normalization and Design Repair | `b21000402.json`, `b21000501.json`, `b21000801.json` | Direct support | `b21000402.json` covers BCNF decomposition, `b21000501.json` reinforces table quality through constrained sample data, and `b21000801.json` applies normalization during DBD transformation. |
| Chapter 8. Discovering Entities from Requirements | `b21000601.json` | Direct support | Stable ERD-entry lesson for entity discovery, attributes, identifiers, and relationship recognition from scenarios. |
| Chapter 9. ER Diagram in Crow's Foot Notation | `b21000601.json` | Direct support | The same ERD self-check lesson also anchors cardinalities, relationship notation, and diagram quality expectations. |
| Chapter 10. Database Design Diagram | `b21000701.json`, `b21000801.json` | Direct support | Stable two-part transformation sequence from ERD into normalized implementation-ready design. |
| Chapter 11. Creating Tables and Constraints in SQL Server | `b21000901.json` | Direct support | Stable implementation anchor for schema creation, table creation, PK/FK work, and initial sample data. |
| Chapter 12. Populating Data and Building Views | `b21001001.json` | Direct support | Stable lesson for update/delete cleanup, additional data work, and SQL Server views. |
| Chapter 13. Database Security, Concurrency, and Transactions | `b21001101.json` | Partial support | `b21001101.json` supports transaction workflow, but security and concurrency framing still depend more heavily on the textbook chapter. |
| Chapter 14. Triggers and Stored Procedures | `b21001201.json`, `b21001301.json` | Direct support | Stable implementation pair: procedures in `b21001201.json` and triggers in `b21001301.json`. |
| Chapter 15. Semester Project Playbook | No standalone KCE. Support comes from the milestone structure described in the textbook plan and course launch plan. | Indirect support | Canonical role is integration and project execution, not auto-graded lesson replacement. |

## Launch-Critical Coverage Summary

For Fall 2026, the launch-critical chapter set with direct or partial KCE support is Chapters 3 through 14.

- Chapters 3-4 are covered by the SQL retrieval KCE sequence.
- Chapters 5-10 are covered by the normalization, ERD, and DBD transformation sequence.
- Chapters 11-14 are covered by the SQL Server implementation sequence and adjacent launch-support materials.
- Chapters 1, 2, and 15 remain necessary, but they are textbook-led framing chapters with indirect lesson support instead of dedicated KCEs.

## Seek Your Challenge (SYC) Role

The SYC series is explicitly a course-long SQL retention strand, not a second chapter stream.

Aligned lessons:
- `b21009901.json`
- `b21009902.json`
- `b21009903.json`
- `b21009904.json`
- `b21009905.json`
- `b21009906.json`
- `b21009907.json`
- `b21009908.json`

Course-design role:
- begin SYC after Chapters 3-4 establish retrieval fundamentals
- continue assigning SYC while the course focus shifts to normalization, ERD, DBD, and implementation
- preserve join, grouping, filtering, and SQL interpretation fluency across the full semester
- treat SYC as low-stakes retrieval rehearsal that protects SQL retention while major graded work remains design- and project-centered

Fall 2026 interpretation:
- textbook chapters stay the main instructional spine
- KCE lessons stay the chapter-linked practice spine
- SYC stays the longitudinal SQL refresh spine running in parallel after the early SQL chapters

## Weak Alignment Areas And Revision Targets

- Chapter 1 has no dedicated KCE for business framing, milestone flow, or anomaly motivation. That is acceptable for launch, but it remains a weak spot for future textbook-to-practice cohesion.
- Chapter 2 has repeated setup instructions inside later KCEs, but no single reusable lesson for SQL Server environment setup, schemas, and safe execution workflow.
- Chapter 5 now spans both early conceptual-model support and later implementation-transition support, so students still rely on the textbook chapter to connect those stages cleanly.
- Chapter 7 spans three lessons because normalization shows up both as standalone decomposition work and as part of DBD transformation. The map is stable, but the instructional boundary is still broad.
- Chapter 15 has no direct KCE or self-check equivalent. Project management, packaging, and revision remain instructor-guided and manually graded.

## Practical Reading

Use this mental model during revision work:

- textbook chapters = primary instruction
- KCE lessons = chapter-linked guided practice
- SYC lessons = ongoing SQL retention after Chapters 3-4
- Chapter 1, Chapter 2, and Chapter 15 = textbook-led framing/integration chapters rather than standalone KCE targets
