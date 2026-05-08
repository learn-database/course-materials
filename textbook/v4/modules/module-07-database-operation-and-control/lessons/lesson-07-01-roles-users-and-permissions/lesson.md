# Lesson 7.1: Roles, Users, and Permissions

## Lesson Overview

This lesson introduces one of the main operational-control questions in
database work: who should be allowed to do what?

A multi-user database is useful only when people can complete their jobs.
That same database becomes dangerous when access is broader than the work
requires. In this lesson, you will learn to distinguish users, roles, and
permissions, use a simple CRUD matrix to organize access decisions, and
justify least-privilege choices in plain language.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain the difference between a user, a role, and a permission
- identify what work a person in a scenario actually needs to do before
  recommending access
- distinguish read, change, delete, and administrative access in plain
  language
- use a simple CRUD matrix to support an access recommendation
- compare an over-permissioned choice to a least-privilege choice
- reject access that is technically possible but unjust, excessive, or careless

## Key Terms

- `user`: a specific person or account that signs in to the system
- `role`: a reusable job-based grouping of responsibilities with similar access
  needs
- `permission`: an allowed action on data or database objects
- `CRUD matrix`: a planning table that shows whether a role needs create, read,
  update, or delete capability for selected data objects
- `least privilege`: giving only the minimum access needed to complete the
  assigned work
- `administrative access`: stronger access used to manage security, accounts,
  or broader system settings
- `access drift`: extra permissions that accumulate over time without a clear
  job-based reason

## Readings And Media

- Read this lesson from start to finish before completing the assignment.
- Study the case and CRUD matrix carefully because the guided practice and
  assignment use the same kind of reasoning.
- Review `textbook/v4/modules-plan/07-module-7-database-operation-and-control.md`
  if you want to see how this lesson connects to the rest of Module 7.
- No separate video or external media is required.

## Core Content

## 1. Start With Job Responsibility, Not With The Strongest Permission

When an organization asks for database access, the first question is not
"Which permission is available?" The first question is "What work must this
person actually do?"

Suppose someone says, "Give the tutor full access so nothing gets in the way."
That sounds convenient, but it skips the real analysis. A tutor may need to
read student schedules and write session notes. That does not mean the tutor
should update invoices, delete student records, or manage user accounts.

Good access decisions start with the work:

- What tasks does this person perform?
- Which data objects are involved?
- What kind of action is actually required?
- Which stronger actions are not required?

This is the foundation of least privilege. Access should follow the job, not
the other way around.

## 2. User, Role, And Permission Are Different Ideas

These three terms work together, but they are not the same thing.

A `user` is a named person or account.

Examples:

- `Mia Chen`
- `programdirector@lakesidetutoring.org`

A `role` is a reusable grouping based on a job or responsibility.

Examples:

- `Tutor`
- `SchedulingCoordinator`
- `BillingClerk`

A `permission` is the allowed action.

Examples:

- read `Student`
- update `Session`
- create `Invoice`

Put together, an access statement might look like this:

- user: `Mia Chen`
- role: `Tutor`
- permission: read `Student`, read `Session`, create and update `SessionNote`

Why does this distinction matter?

Because databases are easier to manage when access is attached to roles instead
of rebuilt by hand for every individual. If five tutors all do the same work,
you should usually define the `Tutor` role once and assign the right people to
it.

## 3. Role-Based Access Is Usually Clearer Than Ad Hoc Access

Role-based access means you decide what a job role needs, then assign users to
that role.

That approach is usually stronger than ad hoc access such as this:

- one tutor gets note access
- another tutor also gets invoice access because someone asked quickly
- a third tutor keeps old permissions from a temporary assignment

That ad hoc pattern becomes hard to review. It is easier to miss unnecessary
permissions because the logic is scattered across individual accounts instead of
organized around the work itself.

Role-based access is usually better because it:

- makes the reasoning visible
- supports consistency across similar workers
- is easier to review later
- reduces accidental permission drift

The goal is not bureaucracy. The goal is responsible control that still lets
people do their jobs.

## 4. Permission Strength Should Match The Task

At an introductory level, you can think about four broad action types:

- `read`: see the data
- `create`: add a new record
- `update`: change an existing record
- `delete`: remove a record

You should also recognize a stronger category:

- `administer`: manage users, roles, broader security settings, or structural
  control

Do not assume that stronger access is automatically better access.

Examples:

- A tutor who reviews the day's schedule needs read access to session
  information.
- A scheduling coordinator who creates new tutoring appointments needs create
  and update access to `Session`.
- A database administrator may need administrative permissions because that role
  is responsible for security and system management.

If the task is only to review completed sessions, then read access may be
enough. Giving update, delete, or administrative access does not improve the
task. It only broadens the risk.

## 5. Delete Should Be Justified, Not Assumed

Students often assume that if a role can update something, it should also be
able to delete it. That does not follow automatically.

Deletion is often riskier because it can remove records needed for history,
billing, auditing, or later review. In many organizations, a safer choice is to
update a status rather than delete the record.

Ask this question before granting delete access:

Does the work require true deletion, or only correction and status changes?

If the scenario does not show a real need for deletion, leave it out.

## 6. Least Privilege Means Minimum Necessary Access

Least privilege does not mean making work impossible. It means giving enough
access to complete the assigned work, but no more than that.

Compare these two recommendations for the `Tutor` role:

- Recommendation A: read `Student`, read `Session`, create and update
  `SessionNote`
- Recommendation B: full create, read, update, and delete access to `Student`,
  `Session`, `SessionNote`, `Invoice`, and `Payment`

Recommendation B is stronger, but it is not better. It gives access to billing
data and broad deletion power without a job-based reason.

Recommendation A is better because it:

- supports the tutor's actual work
- avoids unrelated billing access
- avoids unnecessary delete access
- reduces the chance of accidental or improper changes

Least privilege is therefore a decision principle. You use it to compare a
justified access plan to a broader one and explain why the broader one is worse.

## 7. Why Excessive Access Can Be Unjust

Excessive access is not only inefficient. It can also be unfair.

If a volunteer, tutor, or general staff worker can see unpaid balances, family
hardship notes, or private academic details without a job-based reason, people
may be judged or treated differently because of information they should never
have seen.

That matters because database access affects real people:

- privacy can be lost
- embarrassment can be created
- decisions can become biased
- accountability can disappear because too many people can change or view the
  same sensitive data

## Examples And Case

## Main Case: Lakeside Tutoring Center

Lakeside Tutoring Center stores data in tables such as:

- `Student`
- `Session`
- `SessionNote`
- `Invoice`
- `Payment`

The center has these roles:

- `SchedulingCoordinator`
  - registers students
  - schedules and reschedules sessions
  - reviews tutor availability
- `Tutor`
  - views assigned students and session schedules
  - writes or updates notes for completed tutoring sessions
- `BillingClerk`
  - reviews completed sessions
  - creates invoices
  - records payments
- `ProgramDirector`
  - reviews summary reports
  - approves unusual exceptions
  - does not perform daily billing or tutoring data entry
- `DatabaseAdministrator`
  - manages users, roles, and broader database security

Now translate those responsibilities into likely access.

The `Tutor` role needs:

- read access to assigned `Student` information
- read access to `Session`
- create and update access to `SessionNote`

The `Tutor` role does not automatically need:

- access to `Invoice`
- access to `Payment`
- delete access to `Student`
- administrative control of the database

The `BillingClerk` role needs:

- read access to `Session` so completed tutoring work can be verified
- read access to `Student` for billing accuracy
- create and update access to `Invoice`
- create and update access to `Payment`

The `BillingClerk` role does not automatically need:

- update access to `SessionNote`
- delete access to student records
- administrative control of database security

## A Simple CRUD Matrix

CRUD stands for create, read, update, and delete. A CRUD matrix is a useful
lightweight tool for checking whether the recommended access matches the role.

Use this example:

|Role|Student|Session|SessionNote|Invoice|Payment|
|---|---|---|---|---|---|
|`SchedulingCoordinator`|C, R, U|C, R, U|R|||
|`Tutor`|R|R|C, R, U|||
|`BillingClerk`|R|R||C, R, U|C, R, U|
|`ProgramDirector`|R|R|R|R|R|

Read the matrix carefully.

What does it show?

- The `SchedulingCoordinator` can register students and manage sessions, so
  `Student` and `Session` have create, read, and update entries.
- The `Tutor` can read student and session information and can create or update
  `SessionNote`.
- The `BillingClerk` can review session results and work with `Invoice` and
  `Payment`.
- The `ProgramDirector` reads across the system for oversight, but does not
  perform ordinary create, update, or delete work.

The blank cells matter because they show where access is not justified from the
facts we have.

Notice what is also missing:

- daily work roles do not receive delete access by default
- daily work roles do not receive administrative permissions
- tutors do not receive billing access just because they work with students

The matrix does not make the decision for you, but it makes the reasoning
visible.

## Judgment Scenario: Technically Possible Is Not The Same As Appropriate

Lakeside's director asks for a new rule:

> "Give all tutors read access to `Invoice` and `Payment`. If they can see who
> still owes money, they might pressure families to pay sooner."

That request is technically possible. A database administrator could grant the
permission.

It is still the wrong recommendation.

Why?

- Tutors do not need billing access to teach or document tutoring sessions.
- Sharing family payment status with tutors creates unnecessary privacy loss.
- The access could influence how students are treated, which creates fairness
  and justice concerns.
- Broadening access would weaken accountability because more people could see
  and potentially discuss sensitive financial information.

A better answer is:

- keep `Invoice` and `Payment` access with the `BillingClerk`
- let tutors see only the scheduling and note information needed for tutoring
- if leadership needs payment follow-up, design a separate process with the
  right role ownership

This is a good example of rejecting access that is technically possible but
still unjust, excessive, and careless.

## Compare Two Program Director Plans

Which access plan is better for `ProgramDirector`?

- Plan A: read summary information across `Student`, `Session`, `SessionNote`,
  `Invoice`, and `Payment`, with no day-to-day editing power
- Plan B: full create, read, update, and delete access to every table so the
  director can "step in anytime"

Plan A is usually stronger because it fits the director's oversight role while
preserving accountability for the workers who own the daily tasks.

Plan B may sound flexible, but it weakens control by mixing oversight with
routine operational power. It also makes it harder to tell who should have made
or corrected a change.

## Guided Practice

Work through these prompts before starting the assignment.

## Practice 1: Classify The Access Statement

Classify each item as a `user`, `role`, or `permission`.

- `Ava Johnson`
- `BillingClerk`
- read `Session`
- update `SessionNote`

## Practice 2: Match The Task To The Minimum Needed Access

For each task below, choose the minimum likely access.

- review tomorrow's tutoring schedule
- record a payment that was received today
- correct a typo in a completed session note
- manage who belongs to the `Tutor` role

## Practice 3: Reject The Over-Permissioned Choice

A scheduling coordinator asks for delete access on `Payment` because "it would
be faster to remove mistakes than ask billing to fix them."

Write one or two sentences explaining why that access is too strong and what
should happen instead.

## Practice 4: Read The CRUD Matrix

Using the Lakeside matrix above, answer these questions.

- Why is `Tutor` blank under `Invoice` and `Payment`?
- Why is `ProgramDirector` mostly read-only?
- Why is delete missing from the daily work roles?

## What To Do

Complete the lesson assignment after you finish the guided practice.

Use this order:

1. identify the real job responsibilities in the scenario
2. separate named users from reusable roles
3. match each task to the minimum needed access
4. use a CRUD matrix or short role map to organize the recommendation
5. remove permissions that are not supported by the work
6. explain at least one technically possible permission that should still be
   rejected

## Assignments

## Assignment: Access Recommendation Memo

Use this scenario:

Riverbend Student Support Services tracks tutoring appointments, tutoring notes,
student accounts, invoices, and payments. A new staff review found that several
workers have leftover permissions from older temporary assignments. Leadership
wants a cleaner role-based access plan.

Roles to evaluate:

- `SchedulingCoordinator`
- `Tutor`
- `BillingClerk`
- `ProgramDirector`

Data objects to evaluate:

- `Student`
- `Session`
- `SessionNote`
- `Invoice`
- `Payment`

Your task:

- complete a simple CRUD matrix or equivalent role map
- recommend appropriate access for each role
- identify one access request that is technically possible but should still be
  rejected as unjust, excessive, or careless
- explain how your final recommendation follows least privilege

## How This Assignment Shows Learning

This assignment is not only about producing a table. AI can help draft a CRUD
matrix quickly. What matters is whether you can defend the reasoning behind the
table.

Your explanation should therefore make clear:

- why each role needs the access you recommend
- why one stronger alternative is worse
- how your plan protects privacy and accountability without blocking the work

## Deliverables

Submit:

- one completed CRUD matrix or role-permission map
- one short memo of about 300 to 500 words that justifies the recommendation

## Project Checkpoint Or Module Connection

Module 7's primary graded task is an operations decision memo. This lesson is
the first piece of that larger pattern.

As you complete this lesson, keep this checkpoint question in mind:

How does your access plan protect privacy, fairness, and trustworthy business
practice while still letting people do their jobs?

That question will matter again when the module later asks you to justify
transaction choices, concurrency safeguards, and recovery decisions.

## Wrap-Up

Roles, users, and permissions are basic ideas, but the judgment behind them is
not trivial.

Strong access control starts with job responsibility, not convenience. Role
definitions help organize that judgment. CRUD matrices make it visible. Least
privilege helps you compare a justified access plan to a broader and weaker one.

Most important, a permission is not good simply because it can be granted.
Database professionals have to decide whether access is appropriate, fair, and
accountable for the people affected by the system.
