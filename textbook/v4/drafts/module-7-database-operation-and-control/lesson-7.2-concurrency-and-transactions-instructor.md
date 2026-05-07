# Lesson 7.2: Concurrency and Transactions

## Instructor-Facing Content

### Module

Module 7: Database Operation and Control

### Lesson Purpose

Teach students to diagnose multi-user integrity risk, decide when related work belongs in one transaction, and justify `COMMIT` or `ROLLBACK` choices in realistic SQL Server scenarios.

### Module Context

This lesson follows Lesson 7.1 on roles, users, and permissions. Students have already considered who should be allowed to perform work. Lesson 7.2 shifts the focus to how shared work should be protected once authorized users begin acting on the same data. It prepares Lesson 7.3 by establishing that responsible operation involves both preventing bad in-progress outcomes and planning for failure after the fact. It also supplies core reasoning for the Module 7 `Operations Decision Memo`, where students must identify concurrency risks and justify unit-of-work decisions.

### Primary Learning Type(s)

Principles

### Secondary Learning Type(s), If Any

Procedures

### Estimated Time

75 to 90 minutes

### Lesson Outcomes

By the end of this lesson, students should be able to:

- explain how concurrent work can create integrity risk in a multi-user database
- identify at least one concrete concurrency risk and its likely impact
- decide when several related actions belong in one transaction
- explain the purpose of `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK`
- justify whether a realistic case should commit or roll back as one unit
- explain isolation at a basic conceptual level as protection against harmful overlap

### Module Alignment

- Supports the Module 7 objective to explain roles, permissions, concurrency, transactions, backup, and recovery basics.
- Supports the Module 7 objective to analyze simple security and multi-user scenarios.
- Supports the Module 7 objective to justify commit and rollback choices.
- Delivers the lesson coverage named in the module plan: multi-user risks, transaction units of work, and `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK`.

### Course Objective Alignment

- Course objective 6: administer introductory backup, recovery, security, and concurrency control work

### Lesson Sequence Role

Deepens module knowledge by moving from access-control reasoning to multi-user integrity protection, then prepares later recovery reasoning.

### Required Prior Knowledge

- basic SQL Server and T-SQL reading ability
- familiarity with `INSERT` and `UPDATE`
- understanding from Lesson 7.1 that operational controls exist to protect organizational trust, privacy, and accuracy

### Lesson Opening Guidance

Open with a short warehouse or scheduling case in which two authorized users both appear to follow the normal process, yet the database can still end up wrong. Ask students what false story the database could tell if both actions overlap badly. This frames concurrency as an integrity problem before any syntax appears.

### Teaching Notes

- Keep the lesson centered on scenario judgment. Students should explain why grouped work belongs together rather than merely reciting command definitions.
- Use one main case consistently so concurrency risk, transaction boundaries, syntax, and commit-versus-rollback reasoning all connect.
- Keep the T-SQL example small. This is not the place for production-grade exception handling or deep transaction theory.
- Keep isolation conceptual. Students only need to understand that overlapping work requires control to prevent harmful interference.
- Reinforce the difference between permissions and concurrency. Lesson 7.1 asked "who may act." Lesson 7.2 asks "how should simultaneous action be protected."
- Do not drift into deadlocks, savepoints, nested transactions, lock hints, or isolation-level tuning.

### Online Activities

- short-answer concurrency-risk diagnosis
- transaction-boundary decision prompt
- fill-in-the-blank T-SQL transaction check
- commit-versus-rollback comparison response

### Homework / Graded Assignments

#### Assignment 1: Concurrency And Transaction Judgment

Students analyze one realistic multi-user scenario and submit a short explanation that identifies the concurrency risk, names the likely integrity failure, explains which actions belong in one transaction, and justifies whether the outcome should commit or roll back.

### Deliverables

- one short written concurrency-and-transaction analysis
- one completed or annotated T-SQL transaction block
- one plain-language commit-or-rollback justification

### Assessment Plan

Formative evidence:

- students correctly name a concurrency risk such as overselling or double-booking
- students explain why the risk comes from overlapping work rather than a single isolated mistake
- students identify the boundary of one business event

Graded evidence:

- students decide when work belongs in one transaction and justify the choice in scenario language
- students explain what `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK` mean in context
- students choose commit or rollback based on whether the full unit of work succeeded

AI-resilient design note:

- The lesson avoids relying on a polished SQL artifact alone. Students must explain why the transaction exists, what integrity failure it prevents, and why the case should commit or roll back.

Stronger performance looks like:

- naming the concrete business harm clearly
- tying the transaction boundary to one business event rather than counting statements mechanically
- explaining rollback as integrity protection rather than as generic failure handling

### Suggested Rubric Focus

- accuracy of concurrency-risk diagnosis
- clarity of transaction-boundary reasoning
- correct contextual interpretation of `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK`
- quality of commit-versus-rollback justification
- accurate introductory explanation of isolation

### Common Misconceptions

- "If both users follow the correct steps, concurrency cannot create a problem."
- "A transaction is just any SQL statement."
- "Commit should happen as soon as the first step succeeds."
- "Rollback is only for syntax errors."
- "More transaction blocks are always safer."
- "Isolation means permissions or backup."

### Christian Integration Notes

- Frame transaction habits as part of faithful, trustworthy business work: the goal is not merely to make code run, but to preserve truthful records.
- Use examples where bad multi-user handling harms customers, students, patients, or staff through inaccurate promises, delayed service, or conflicting status records.
- Keep the integration tied to accountability and trust rather than adding a separate reflection section.

### Workflow Connection

This lesson sits in the operational-control stage of the course workflow. Students have already learned how to model and implement a database. Here they learn how to protect shared work once the database is live and supporting real organizational activity.
