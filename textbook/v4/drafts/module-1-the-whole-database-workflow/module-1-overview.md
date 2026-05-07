# Module 1 Overview: The Whole Database Workflow

## Devotion

> *"Whoever can be trusted with very little can also be trusted with much, and whoever is dishonest with very little will also be dishonest with much."*
> — Luke 16:10

Every organization runs on records. Someone recorded a sale, a service, a payment, a promise. Those records shape what leaders believe, what staff do, and how well the organization serves the people who depend on it.

This module opens the course by asking whether those records are trustworthy — not in a technical sense, but in a basic one: does the system actually reflect what happened? A spreadsheet full of copied entries, disconnected files that no longer agree, reports built from stale exports — these are not only inefficiency problems. They are faithfulness problems. When records are unreliable, the organization cannot tell the truth about its own work.

Good database thinking begins with that responsibility. Before a single table is designed or a single query is written, we ask: what does this organization actually need to track, and what does it owe the people who depend on those records?

That question is where this module begins — and it is the question the whole course is built around.

## What This Module Is About

Before you learn to build anything in SQL Server or draw an ER Diagram, you need to understand why organizations need databases and what the path from a business problem to a working database looks like. That is this module's job.

Module 1 gives you the end-to-end view of the database workflow. Two lessons. One question each.

- **Lesson 1.1** asks: Is a database even the right tool for this situation?
- **Lesson 1.2** asks: If a database is warranted, what happens between the business need and a working system?

By the time you finish this module, you will have a mental map of the whole course. Later modules will zoom in on individual stages of that map.

## Why This Module Matters

Students who skip this orientation often treat database work as a collection of disconnected skills: a diagram here, some SQL there, maybe a permissions step at the end. That disconnection shows in their work. A design that is not grounded in the actual business process will not support honest reporting. SQL that is not tied to a business question may run without answering anything useful.

This module establishes the standard that runs through the entire course: the purpose of a database is to support truthful, reliable organizational records. Every technical decision you make later connects back to that purpose.

## How The Lessons Connect

The two lessons in this module build on each other directly.

| Lesson | Core Question | What You Will Do |
|--------|---------------|-----------------|
| 1.1: Why Databases Matter | Is a database warranted here? | Compare spreadsheets, disconnected files, and databases; justify tool-fit decisions |
| 1.2: From Business Process to Database | What is the workflow from need to system? | Map the nine-stage workflow; identify what each stage produces; distinguish the ERD from the DBDD |

Lesson 1.1 gives you the vocabulary and the judgment. Lesson 1.2 gives you the map. You need both before the course advances into technical depth.

## Where This Module Fits The Workflow

This module covers **stages 1 through 2** of the course workflow:

1. **Understand the business process** — what recurring work does the organization perform?
2. **Identify data requirements and business rules** — what does the organization need to track, and why?

Later modules cover the remaining stages. But those later stages only make sense if you understand why the workflow starts here.

## What The Assessment Will Ask

The module assessment is a **Case Framing Check**. You will read short business scenarios and:

- decide whether a database is warranted or whether a simpler tool is enough
- identify what information must be tracked and why
- explain the workflow stages that would follow if a database is justified
- evaluate a weak database recommendation and revise it with business-facing reasoning

The assessment is not asking you to build anything. It is asking you to think carefully about whether and why a database fits a situation.

## Key Terms To Watch For

As you read, pay attention to how these terms are used and how they differ from each other:

- `business process` — the recurring work an organization performs
- `data` — one recorded fact
- `information` — data organized to answer a question or support a decision
- `database` — a structured system for storing, connecting, and retrieving records
- `ER Diagram` — the conceptual model showing entities and relationships
- `Database Design Diagram` — the implementation-ready artifact showing tables, columns, and constraints
- `workflow` — the ordered stages that connect a business need to a working database

## A Note On Judgment

A tool that looks organized is not the same as a tool that is the right fit. Someone, including an AI assistant, can quickly produce a database recommendation or a diagram. That does not mean the recommendation fits the actual business work.

This module asks you to develop the judgment to tell the difference. That judgment is what the rest of the course builds on.
