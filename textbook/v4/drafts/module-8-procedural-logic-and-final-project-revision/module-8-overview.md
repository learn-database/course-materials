# Module 8 Overview: Procedural Logic and Final Project Revision

## Devotion

> *"Let your 'Yes' be 'Yes,' and your 'No,' 'No.'"*
> — Matthew 5:37

When a stored procedure fires, it does exactly what it was written to do — no more, no less. When a trigger runs, it enforces the rule it was given, every time, regardless of who issued the command. Procedural logic does not negotiate or improvise. It is a commitment encoded in the system.

That predictability is the source of both its value and its risk. Logic that is well-bounded, well-tested, and clearly justified can consistently enforce rules that would otherwise be unevenly applied. Logic that is poorly scoped, untested, or built to automate something that required human judgment can enforce the wrong thing just as consistently — affecting real operations, real records, and real people who depend on those records being correct.

This module asks you to think carefully before you automate. Not every repeated operation should be a procedure. Not every rule should be a trigger. The first question is always: what problem does this solve, and is automation the right solution here? The answer shapes whether the logic you write becomes a reliable tool or a hidden liability.

The course closes with a revision task that asks the same kind of careful question about your whole project: when something changes, does your work hold together honestly? Not just technically, but as a coherent, truthful account of the business it was built to serve.

That follow-through — finishing well, being honest about limitations, keeping all the pieces consistent — is the final form of faithfulness this course asks of you.

## What This Module Is About

Module 8 does two things. First, it introduces procedural logic — stored procedures and triggers — as tools for automating specific, bounded operations within a database. Second, it asks you to take your entire database project and revise it in response to a change in business requirements.

Three lessons. Two are technical. One is integrative:

- **Lesson 8.1** teaches you to create parameterized stored procedures for operations that repeat with different inputs.
- **Lesson 8.2** teaches you to create DML triggers for event-driven logic that should fire automatically when data changes.
- **Lesson 8.3** asks you to revise the full project package — ERD, DBDD, implementation, queries — so that all artifacts stay consistent with each other after a business rule change.

## Why This Module Matters

Stored procedures and triggers are powerful tools. They are also easy to misuse. The central question this module keeps returning to is not "how do I write this?" but "should this be automated at all, and if so, how narrowly?"

A procedure that does too much, or a trigger that fires in unexpected contexts, creates logic that is hard to test, hard to correct, and easy to trust incorrectly. Automation that is not well-understood by the person who built it is automation that cannot be maintained responsibly.

Lesson 8.3 tests something different: whether you can hold the whole project together when something changes. Business requirements always change eventually. An artifact package that cannot be revised coherently — where a change to one document does not propagate correctly to the others — is a project that cannot serve the organization over time. This final lesson asks whether your database solution is actually maintainable.

## How The Lessons Connect

| Lesson | Core Question | What You Will Do |
|--------|---------------|-----------------|
| 8.1: Stored Procedures | Should this operation be a procedure, and how should it be bounded? | Decide when a procedure is justified; write and test a parameterized procedure; describe its expected behavior |
| 8.2: Triggers | Should this logic fire automatically, and is a trigger the right tool? | Compare trigger logic to other options; write and test a bounded trigger; identify side effects and fairness concerns |
| 8.3: Final Project Integration and Revision | When a business rule changes, can you revise every artifact consistently? | Trace the impact of a change across the full project; revise artifacts; explain why each revision is justified |

Lessons 8.1 and 8.2 are parallel in structure: both ask you to justify automation before building it, and both require testing. Lesson 8.3 uses the whole course as its context.

## Where This Module Fits The Workflow

This module covers **stages 8 and 9** of the course workflow:

8. **Manage introductory operational concerns** — including event-driven and reusable operation logic
9. **Revise the solution when requirements or constraints change** — the final stage of the workflow, which tests whether the whole system holds together

Module 8 closes the workflow loop that started in Module 1. Lesson 1.2 introduced the nine stages as a chain. Lesson 8.3 asks whether your work across the whole course actually forms one coherent, revisable chain.

## What The Assessment Will Ask

The module assessment is a **Change Request Revision**. You will receive a late business-rule change applied to your semester project case and asked to:

- identify which artifacts are affected by the change and why
- trace how the change moves from the ERD to the DBDD to the implementation to the queries
- revise each affected artifact so they remain consistent with each other
- explain the reasoning behind each revision
- state clearly what limitations remain in the revised solution

You will be evaluated on the coherence and honesty of your revision, not only on whether you made changes.

## Key Terms To Watch For

- `stored procedure` — a saved, named set of T-SQL statements that can be executed by name, often with parameters
- `parameter` — a named input that a stored procedure accepts so the same procedure can run with different values
- `EXEC` — the T-SQL command used to execute a stored procedure
- `reusable operation` — a task that is done repeatedly with different inputs and benefits from encapsulation in a procedure
- `bounded automation` — automation that does exactly the defined task and no more; avoids side effects
- `DML trigger` — a trigger that fires automatically when an `INSERT`, `UPDATE`, or `DELETE` statement runs on a specified table
- `AFTER trigger` — a trigger that fires after the DML operation completes successfully
- `INSTEAD OF trigger` — a trigger that fires in place of the DML operation
- `inserted` — a virtual table available inside a trigger that holds the new rows from an `INSERT` or `UPDATE`
- `deleted` — a virtual table available inside a trigger that holds the old rows from a `DELETE` or `UPDATE`
- `side effect` — an unintended consequence of trigger logic that fires in contexts where the behavior was not expected
- `cross-artifact consistency` — the state where all project documents — ERD, DBDD, implementation, and queries — agree with each other and reflect the current business rules

## A Note On Finishing Well

Lesson 8.3 is deliberately integrative. It does not introduce a new technical topic. It asks whether you can take what you have built across the course and revise it responsibly under pressure.

In real organizational work, this is common. Designs change. Requirements evolve. The skill of revising a whole solution coherently — without leaving artifacts out of sync, without hiding limitations, without pretending a partial fix is a complete one — is one of the most valuable skills a database professional can have.

This module asks you to demonstrate that skill, not just your ability to write T-SQL.
