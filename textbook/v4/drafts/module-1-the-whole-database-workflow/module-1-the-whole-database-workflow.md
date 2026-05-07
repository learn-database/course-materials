# Module 1: The Whole Database Workflow

## Module Overview

Module 1 gives you the course map before later modules ask you to do each part of the work in detail. You will begin with the business need, trace the stages that lead to a working database, and learn why the `ERD` and the `DBDD` are related but not interchangeable.

This module is intentionally broad rather than deep. Its purpose is not to make you master modeling, normalization, SQL Server implementation, or operational control yet. Its purpose is to help you see how those later topics fit together inside one whole-system workflow.

## Why This Module Matters

Students often meet database topics as disconnected skills: diagrams in one place, SQL in another, and administration somewhere later. Real database work does not happen as disconnected units. Each stage hands work to the next stage, and weak thinking early in the workflow creates problems later in reports, updates, and decision-making.

This module also sets an important expectation for the whole course. AI can help generate diagrams, lists, explanations, or first-pass artifacts. That does not remove your responsibility to decide whether the artifact matches the business process, whether the workflow is being followed correctly, and whether the database choice supports truthful, trustworthy work.

## What This Module Is For

By the end of this module, you should be able to:

- describe the overall workflow from business process to working database
- distinguish an `ERD` from a `DBDD`
- explain where SQL, normalization, implementation, querying, and operational control fit in the larger process
- judge when a scenario calls for a database and when a simpler tool is enough

## The Workflow Map

Use this sequence as your high-level map for the course:

1. understand the business process
2. identify data requirements and business rules
3. identify entities, attributes, and relationships
4. create the conceptual `ERD`
5. convert the logical model into an implementation-ready `DBDD`
6. implement the design in SQL Server
7. query and manipulate data
8. manage introductory operational concerns
9. revise the solution when requirements or constraints change

You are not expected to perform every stage in technical depth yet. In Module 1, you are expected to know what each stage is for, what kind of output it produces, and why the stages should stay in order.

## ERD Versus DBDD

One of the main jobs of this module is to keep two artifacts separate from the beginning.

- The `ERD` is a conceptual model. It shows entities, important attributes, relationships, cardinality, and optionality.
- The `DBDD` is an implementation-ready design. It shows tables, columns, `PK`s, `FK`s, data types, nullability, and other build-ready details.

That difference matters because a polished diagram is not enough by itself. You need to know what question the artifact is answering. If you confuse conceptual structure with implementation detail, later design and implementation choices become harder to justify and harder to verify.

## How The Lessons Fit Together

This module has two lessons, and each one answers a different question in the workflow:

- [lesson-1.1-why-databases-matter.md](./lesson-1.1-why-databases-matter.md): asks when a business situation really needs a database and when a simpler tool is enough
- [lesson-1.2-from-business-process-to-database.md](./lesson-1.2-from-business-process-to-database.md): shows the end-to-end workflow from business process to working database and explains the `ERD` versus `DBDD` boundary

Taken together, the lessons give you the starting judgment for the rest of the course:

- first, decide whether the case actually needs a database
- next, understand how database work proceeds from that need to a usable system

## What Judgment You Are Expected To Develop

This module is not mainly about producing a finished artifact. It is about learning to judge whether the work is heading in the right direction.

You should leave this module able to answer questions such as:

- What business process is the organization actually trying to support?
- What information must the organization track in order to serve people and make sound decisions?
- Does this case justify a database, or would a simpler tool be more appropriate?
- Which details belong in an `ERD`, and which belong in a `DBDD`?
- Where would weak workflow discipline distort later reporting, implementation, or revision?

That is the kind of judgment the course will keep developing. Later modules go deeper into individual skills, but they still depend on this early ability to frame the work correctly.

## AI And Your Responsibility

In this course, you should assume that AI can help generate first-pass work quickly. It may produce a workflow summary, suggest entities, or draft a diagram explanation in seconds. That speed is useful, but it is not the same as understanding.

In Module 1, your responsibility is to verify:

- whether the database recommendation fits the business process
- whether the workflow stages are in the correct order
- whether the `ERD` stays conceptual
- whether the `DBDD` adds implementation-ready detail without changing the underlying business meaning

A generated artifact can save time. It cannot replace judgment about what makes the database decision correct.

## Trust, Stewardship, And Truthful Reporting

Database work is not only about efficiency. Good structure helps an organization tell the truth about its operations, serve customers and coworkers responsibly, and avoid avoidable confusion or rework. Poor structure can lead to duplicated facts, inconsistent records, and reports that decision-makers should not trust.

For Christian business practice, that makes database judgment a neighbor-serving and stewardship issue as well as a technical one. A well-designed workflow helps an organization use resources wisely, follow through competently, and report honestly about what it is doing.

## How You Will Show Learning

In this module, strong evidence of learning comes from explanation and classification, not from a polished standalone artifact.

You should expect work such as:

- deciding whether a short scenario needs a database or a simpler tool
- placing workflow stages in the correct order
- identifying what information a case must track
- explaining what the `ERD` shows and what the `DBDD` adds
- justifying why a workflow or artifact choice supports accurate and trustworthy reporting

## Module Boundaries

Keep the scope of this module clear.

- You are previewing normalization, SQL, implementation, querying, and operational control.
- You are not expected to master those later-module skills here.
- You are learning the workflow, the purpose of the major artifacts, and the kind of verification good database work requires.

If you finish Module 1 with a clear map of the whole process, the rest of the course will feel like deeper work on a known system rather than a series of disconnected topics.
