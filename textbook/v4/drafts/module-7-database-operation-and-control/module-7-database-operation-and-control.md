# Module 7 Overview: Database Operation and Control

## Student-Facing Content

### Module Overview

Module 7 is the operational-judgment module of ITM-2100. Earlier modules
focused on understanding business requirements, designing the database, and
implementing that design in SQL Server. This module asks a different set of
questions:

- who should be allowed to do what
- how shared work should stay accurate when more than one user is active
- how the organization should prepare to recover when something still goes
  wrong

The focus is practical and business-facing. You are not becoming an advanced
database administrator in this module. You are learning how to make and defend
responsible operational choices in plain language.

### Why This Module Matters

A database can be designed correctly and still be used badly.

Problems often appear after the system is already live:

- a worker receives broader access than the job requires
- two people update the same business process at nearly the same time
- a partial change leaves records telling conflicting stories
- an accidental deletion or system failure interrupts work

These are not just technical mistakes. They are trust problems. Poor access
control can expose private information. Weak transaction thinking can distort
inventory, scheduling, billing, or status records. Weak recovery preparation
can leave an organization unable to restore truthful records when people depend
on them.

This means operational control is connected to justice, accountability,
privacy, and organizational trust. In a Christian business setting, caring for
data responsibly is part of caring for neighbors, serving honestly, and using
organizational resources with stewardship and wisdom.

### Module Purpose

The purpose of Module 7 is to teach operational judgment for permissions,
concurrency, transactions, backup, and recovery through realistic scenario
analysis.

By the end of the module, you should be able to explain not only what these
terms mean, but why one operational choice is stronger, safer, or more
responsible than another in a specific business case.

### How This Module Fits The Larger Workflow

The larger course workflow moves from business process to working database:

1. understand the business process
2. identify the needed data and business rules
3. design the structure
4. implement the design
5. query and use the database
6. operate the database responsibly

Module 7 sits in step 6. The database already exists and supports real work.
The main question is no longer only "Can the database store and retrieve the
right data?" The question is also "Can the organization use this database in a
way that protects people, preserves accuracy, and sustains trust?"

### The Module Throughline

The three lessons in Module 7 fit together as one operational story.

Lesson 7.1 begins with permissions. Before a database can be used well, the
organization must decide which roles need which actions. This lesson teaches
you to use least privilege so people can complete their work without receiving
careless or excessive access.

Lesson 7.2 moves from access to in-progress work. Even when the right people
have the right permissions, overlapping activity can still create false or
incomplete records. This lesson teaches you to recognize concurrency risk,
decide when several actions belong in one transaction, and justify `COMMIT` or
`ROLLBACK` decisions.

Lesson 7.3 closes the module by asking what happens when failure, loss, or a
damaging change still occurs. This lesson teaches you to distinguish backup,
restore, and recovery, compare weaker and stronger operational responses, and
recommend a basic recovery approach that fits the organization's continuity
needs.

Taken together, the lessons move through three related responsibilities:

1. allow the right work
2. protect the truth of shared work while it is happening
3. restore useful and trustworthy records when disruption happens

### What Kind Of Judgment You Are Developing

This module is not mainly about memorizing vendor settings or copying long
administration procedures. It is about learning to make operational judgments
such as:

- when a permission is appropriate, excessive, or unjust
- when several database actions should succeed or fail together
- what kind of multi-user risk a scenario creates
- when a case should commit and when it should roll back
- what backup or recovery response is sensible for the business need
- what limitation still remains even after a reasonable control is chosen

Strong performance in this module means you can explain these judgments in
clear business language, not only identify the technical term.

### How You Should Work Through The Module

- Read this overview first so you can see how the lessons connect.
- Work through Lessons 7.1, 7.2, and 7.3 in order because each one extends the
  operational logic of the previous lesson.
- Pay close attention to scenarios, contrasts, and warnings. Those are where
  the main judgment patterns appear.
- When you study each case, ask what risk the control is trying to reduce and
  why the choice is stronger than an easier or more careless alternative.
- Use the module assessment as a chance to explain your reasoning, not merely
  to produce a technical artifact.

### How You Will Show Learning

The main evidence in this module is operational reasoning in realistic cases.
The core assessment is the Module 7 `Operations Decision Memo`, supported by
shorter case checks. You will likely be asked to do work such as:

- recommend least-privilege access for several roles
- identify a concurrency risk and explain its likely harm
- decide whether related actions belong in one transaction
- justify whether a case should commit or roll back
- recommend a basic backup or recovery response
- explain why a weaker alternative is incomplete or unsafe

### Success Checklist

By the end of Module 7, you should be able to say:

- I can explain the difference between a user, a role, and a permission.
- I can defend least privilege in plain business language.
- I can identify a realistic multi-user integrity risk.
- I can explain why some related actions belong in one transaction.
- I can justify `COMMIT` and `ROLLBACK` as business-logic decisions, not only
  as SQL words.
- I can distinguish backup, restore, and recovery clearly.
- I can recommend a practical operational response and name its remaining
  limits.
- I can connect operational control to privacy, accountability, fairness, and
  organizational trust.

### Scope Reminder

Keep this module at the introductory operational level. The goal is not deep
security engineering, advanced backup architecture, or performance tuning. The
goal is to develop sound judgment about permissions, transactions, multi-user
risk, and basic recovery thinking in realistic business situations.

### Wrap-Up

Module 7 teaches what responsible database use looks like after the system is
already built. A good database is not only well designed. It is also operated
with appropriate access, truthful transaction handling, and sensible recovery
thinking. That is the kind of judgment this module is designed to build.
