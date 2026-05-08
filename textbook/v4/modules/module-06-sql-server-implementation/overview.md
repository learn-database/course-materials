# Module 6 Overview: SQL Server Implementation

## Devotion

> *"Whatever you do, work at it with all your heart, as working for the Lord, not for human masters."*
> — Colossians 3:23

There is a kind of work that passes at a distance but does not hold up close. A schema that looks correct in a diagram but enforces nothing in the actual database. Constraints that are declared but written incorrectly. Data loaded without verifying that it landed where it should. Views that run without checking whether they answer the right question. Each of these is a small gap between intention and execution — and in a working database, small gaps accumulate into systems that organizations cannot trust.

This module is about closing those gaps. The technical work is implementation: writing `CREATE TABLE` statements, loading data, building views. But the underlying discipline is verification — checking that what you built is actually what the design called for, and that the constraints you defined actually protect what they were supposed to protect.

Faithful work is not just competent work. It is work done carefully enough that you can stand behind it — work that holds up when someone else examines it closely, or when the organization depends on it for something that matters.

That is the standard this module asks you to work toward.

## What This Module Is About

Module 6 is where the design becomes a real database. You will take the approved Database Design Diagram from Module 5 and implement it in SQL Server — creating the tables, enforcing the constraints, loading the data, and building views for repeatable reporting.

Three lessons. Each one covers a different phase of implementation:

- **Lesson 6.1** teaches you to translate a DBDD into `CREATE TABLE` statements and constraint definitions.
- **Lesson 6.2** teaches you to insert, update, and delete data in a controlled, dependency-aware way.
- **Lesson 6.3** teaches you to build views that encapsulate repeatable reporting logic.

## Why This Module Matters

Implementation is where design decisions become testable. When you run `CREATE TABLE`, SQL Server either enforces the constraint you defined or it does not. When you attempt an insert, the foreign key either allows it or rejects it. You can no longer reason abstractly — you have to verify.

This module also introduces a verification mindset that matters beyond the course. An implemented schema that has drifted from the approved DBDD means the organization is operating on a structure that does not match its own design decisions. That drift can be invisible until it causes reporting problems or integrity failures. Checking that what you built matches what you designed is part of responsible implementation work.

## How The Lessons Connect

| Lesson | Core Question | What You Will Do |
|--------|---------------|-----------------|
| 6.1: Creating Tables and Constraints | Does the SQL Server schema match the approved DBDD? | Translate DBDD columns, keys, and constraints into T-SQL; create tables in dependency order; verify the schema |
| 6.2: Inserting, Updating, and Deleting Data | How do you change data safely and deliberately? | Insert rows in dependency-aware order; write targeted updates with proper conditions; delete rows while respecting referential integrity |
| 6.3: Building Views | How do you make repeatable reporting logic reusable? | Identify when a view is appropriate; write and test a view; verify it returns correct output |

Lesson 6.1 builds the structure. Lesson 6.2 populates and modifies it. Lesson 6.3 creates a repeatable reporting layer on top of it.

## Where This Module Fits The Workflow

This module covers **stages 6 and 7** of the course workflow:

6. **Implement the design in SQL Server** — create the physical database from the approved DBDD
7. **Query and manipulate data** — load, modify, and retrieve data in ways that maintain integrity

Module 5 gave you the design. Module 6 turns it into a working database. The skills you develop here build directly on the DBDD you will produce in the project and are the prerequisite for Module 7's operational control work.

## What The Assessment Will Ask

The module assessment is a **Build-and-Verify Audit**. You will be given a partially built SQL Server schema with problems and asked to:

- identify constraints that are missing or incorrectly defined
- detect places where the schema has drifted from the reference DBDD
- explain what each problem would allow or prevent incorrectly
- write corrections and verify they work as expected

You are not only asked to build. You are asked to audit someone else's build and explain what is wrong with it.

## Key Terms To Watch For

- `DDL` — Data Definition Language; the SQL commands that create and modify database structure (`CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`)
- `DML` — Data Manipulation Language; the SQL commands that change data in tables (`INSERT`, `UPDATE`, `DELETE`)
- `CREATE TABLE` — the DDL statement that defines a table's columns and constraints
- `PRIMARY KEY constraint` — enforces uniqueness and non-nullability for the identifying column(s) of a table
- `FOREIGN KEY constraint` — enforces that values in one column reference valid values in another table's primary key
- `UNIQUE constraint` — enforces that no two rows have the same value in a specified column or column set
- `CHECK constraint` — enforces that column values meet a specified condition
- `DEFAULT` — a constraint that supplies a value automatically when a row is inserted without specifying that column
- `dependency order` — the sequence in which tables must be created (or rows inserted) so that referenced tables exist before tables that reference them
- `schema drift` — when the implemented database structure no longer matches the approved DBDD
- `view` — a saved query that can be referenced like a table, used to encapsulate repeatable reporting logic
- `referential integrity` — the guarantee that foreign key values always reference a row that exists in the referenced table

## A Note On Verification

Each lesson in this module follows a build-and-verify pattern. After you create a table, verify that it matches the DBDD. After you insert data, verify that the rows are what you expected. After you build a view, verify that its output correctly answers the business question.

This pattern is not extra work. It is the primary task. SQL Server will accept many things that are technically valid but substantively wrong. Verification is how you find the gap between what you intended and what you actually built.
