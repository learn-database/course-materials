# Module 7 Overview: Database Operation and Control

## Devotion

> *"Now it is required that those who have been given a trust must prove faithful."*
> — 1 Corinthians 4:2

When an organization builds a database, it entrusts that system with some of the most sensitive information it holds: employee records, customer data, financial transactions, service history. The system is given access to that information on behalf of the people it serves — not as an end in itself, but as a tool for doing organizational work well.

That trust must be administered carefully. Who gets access to what, and on what basis? What happens when two people try to change the same record at the same time? What is the plan when a failure threatens to destroy records the organization depends on? These are not peripheral questions. They are the questions that determine whether the people responsible for a database can be trusted with it.

A person who builds a technically sound database and then grants every user full administrative access has not finished the job. A system with no transaction boundaries can silently corrupt records that nobody can recover. A database with no backup plan is one hardware failure away from losing records that may represent months of organizational work.

This module treats database operation as stewardship — as the ongoing responsibility to protect what has been entrusted to your care. The technical skills it teaches exist in service of that responsibility.

## What This Module Is About

A database does not run itself. Once a system is built and loaded with data, it needs to be operated responsibly: the right people need access to the right things, multiple users need to work without corrupting each other's changes, and the organization needs a plan for what happens when something fails.

Module 7 introduces three areas of operational control:

- **Lesson 7.1** covers access control: who gets what permissions and why.
- **Lesson 7.2** covers concurrency and transactions: how SQL Server handles multiple users making changes at the same time.
- **Lesson 7.3** covers backup and recovery: how organizations protect their data and respond to failures.

## Why This Module Matters

Most database courses end with implementation. This one does not, because building a database is only part of the responsibility. An organization that builds a well-designed database and then grants every staff member full administrative access, or that runs critical operations without transaction boundaries, or that has no backup plan, has incomplete stewardship of its own records.

Access control decisions affect real people. Over-permissioned staff can see private records they have no reason to see. Under-permissioned staff cannot do their jobs. Poor transaction handling can result in partial updates that leave data in a contradictory state. Weak backup practices mean that a hardware failure or mistake can permanently lose records that people and operations depended on.

These are not just technical risks. They are accountability and service risks.

## How The Lessons Connect

| Lesson | Core Question | What You Will Do |
|--------|---------------|-----------------|
| 7.1: Roles, Users, and Permissions | Who should be able to do what, and why? | Distinguish users, roles, and permissions; analyze a scenario using a CRUD matrix; apply least-privilege reasoning |
| 7.2: Concurrency and Transactions | How do you protect integrity when multiple users are changing data at the same time? | Identify concurrency risks; group operations into transactions; justify commit and rollback choices |
| 7.3: Backup and Recovery Basics | How does an organization protect its records and recover from failure? | Compare backup strategies; explain recovery goals; identify what introductory recovery can and cannot address |

The three lessons are related but largely independent in their technical content. Each one addresses a different operational concern.

## Where This Module Fits The Workflow

This module covers **stage 8** of the course workflow:

8. **Manage introductory operational concerns** — control who can access data, protect integrity during concurrent use, and maintain the ability to recover from failures

Modules 1 through 6 built the database. Module 7 asks: now that it exists, how do you run it responsibly? This is the last technical topic before Module 8's procedural logic and project revision work.

## What The Assessment Will Ask

The module assessment is an **Operations Decision Memo**. You will be given a multi-part scenario describing a database environment and asked to:

- recommend a role and permission structure using least-privilege reasoning
- identify a concurrency risk in a described operation and explain what could go wrong
- recommend whether a specific operation should be wrapped in a transaction and justify that choice
- describe a basic backup and recovery approach appropriate to the described situation

You will be expected to explain your reasoning in each case, not just state a recommendation.

## Key Terms To Watch For

- `user` — a database account that can connect to SQL Server and issue commands
- `role` — a named group of permissions that can be assigned to users
- `permission` — the right to perform a specific action on a specific database object
- `least privilege` — the principle that users should have only the permissions they need to do their work, no more
- `CRUD matrix` — a table showing which operations (Create, Read, Update, Delete) each role or user type needs on each object
- `concurrency` — the situation where multiple users are reading or changing data at the same time
- `transaction` — a group of SQL operations treated as a single unit: either all succeed or all fail
- `BEGIN TRANSACTION` — marks the start of a transaction
- `COMMIT` — saves all changes made in the current transaction
- `ROLLBACK` — reverses all changes made in the current transaction
- `isolation` — the property that prevents one transaction from seeing or corrupting another transaction's in-progress changes
- `backup` — a saved copy of a database that can be used to restore the system after a failure
- `recovery` — the process of restoring a database to a usable state after a failure or mistake
- `recovery point objective (RPO)` — how much data loss is acceptable; determines how frequently backups must occur
- `recovery time objective (RTO)` — how long recovery can take before it becomes unacceptable for the organization

## A Note On Judgment Over Procedure

Each topic in this module involves judgment, not just procedure. Knowing how to grant a permission is not enough — you need to be able to say why a particular permission assignment is appropriate for a particular role. Knowing that transactions exist is not enough — you need to be able to identify when grouping operations into a transaction protects something that would otherwise be at risk.

The assessment asks for explained reasoning, not just correct labels. That is intentional. Operational decisions that are not understood by the person making them are operational decisions waiting to go wrong.
