# Lesson 7.3: Backup and Recovery Basics

## Lesson Overview

This lesson explains what backups protect, what recovery tries to restore, and
how to choose a sensible basic response when a database problem interrupts
work. The focus is not advanced DBA administration. The focus is practical
operational judgment: what should be protected, how quickly work needs to
resume, and what limits still remain even when backups exist.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain what backups are for in plain language
- explain what recovery is trying to accomplish after a problem
- distinguish backup, restore, and recovery clearly
- compare a weaker and stronger basic response for a realistic scenario
- identify practical limits in a proposed backup or recovery plan
- choose and justify a sensible introductory backup or recovery response for a
  short case

## Key Terms

- `backup`: a protected copy of data kept so the organization can recover after
  loss, damage, or a bad change
- `restore`: the act of bringing backed-up data back into use
- `recovery`: the larger process of returning the database and needed service
  to a usable state after a disruption
- `downtime`: the period when the database or related service cannot be used
  normally
- `continuity`: the ability to keep work going or resume it within an
  acceptable time
- `recent-change loss`: the amount of recent work the organization may need to
  re-enter if the latest usable copy is older than the failure
- `operational response`: the practical action plan for protecting records and
  restoring work after a problem

## Readings And Media

- Read this lesson from `Lesson Overview` through `Wrap-Up`.
- Study the two scenarios in `Examples And Case`.
- Work through the guided practice before completing the assignment.
- No separate video or external media is required for this lesson.

## Core Content

### 1. Backups Protect Against Loss, Damage, And Bad Changes

A backup is a protected copy of data. Its purpose is to give the organization a
reliable way to recover after something has gone wrong.

That problem might be:

- accidental deletion
- an incorrect update
- file corruption
- a server or storage failure
- a ransomware or malware event that makes the working copy unusable

A backup is not valuable just because it exists somewhere. It is valuable
because it can help restore records the organization still needs.

### 2. Recovery Tries To Restore Usable Records And Usable Work

Recovery is bigger than backup. Recovery means returning the database and the
related work to a usable state after disruption.

That can include:

- deciding which copy or backup should be used
- restoring the database
- checking what recent work may need to be re-entered
- confirming that the system is usable again
- getting staff back to normal work

So backup answers a protection question before failure. Recovery answers a
restoration question after failure.

### 3. Restore Is One Step Inside Recovery

Students often collapse three ideas into one word. Keep them separate:

- `backup` is the protected copy
- `restore` is the act of bringing that copy back into use
- `recovery` is the whole process of restoring records and service

If a manager says, "We have backups, so we are fine," that statement is still
incomplete. A backup may exist, but recovery may still be slow, confusing, or
missing too much recent work.

### 4. Two Practical Questions Shape A Sensible Response

You can make many good introductory backup and recovery decisions by asking two
plain-language questions:

1. How much recent work can the organization afford to lose?
2. How long can the organization afford to be down?

If the latest usable backup is from last night, then anything entered this
morning may need to be re-entered. For some organizations, that is
inconvenient but manageable. For others, it is too disruptive.

If recovery takes several hours, some organizations can continue with temporary
workarounds. Others cannot.

You do not need advanced disaster-recovery vocabulary to reason well at this
level. You do need to connect backup and recovery choices to real continuity
needs.

### 5. A Backup Plan Can Still Be Incomplete

A weak plan can sound safer than it really is. Common limits include:

- the newest backup may still be too old for the business need
- the organization may not know which copy to restore first
- restore steps may not be documented clearly
- the database may come back, but staff may still need to re-enter missing work
- backups do not prevent bad permissions, weak transaction handling, or user
  mistakes in the first place

This matters because backup is not a substitute for all other controls. Lesson
7.1 and Lesson 7.2 still matter. Access control, transaction habits, and
backup planning work together.

### 6. Stronger And Weaker Responses Depend On Context

There is no single backup schedule or recovery plan that fits every database.
A sensible response depends on what records matter most, how quickly they
change, and how serious downtime would be.

Compare these two introductory responses:

- Weaker response: "We save one copy occasionally and assume that is enough."
- Stronger response: "We protect the data on a regular schedule that matches
  the organization's pace of change, and we know how those backups would be
  restored if needed."

The stronger response is better because it connects protection to recovery
instead of treating backup as a checkbox.

### 7. A Simple Way To Recommend A Basic Response

When you read a backup or recovery scenario, use this sequence:

1. identify the records and tasks that matter most
2. explain what harm downtime would cause
3. explain what harm losing recent changes would cause
4. recommend a basic level of protection that fits the case
5. explain how the organization would recover from that protection
6. name at least one limit that still remains

This method keeps the lesson practical. You are not writing a full DBA policy.
You are making a sensible, introductory operational recommendation.

## Examples And Case

### Contrast Case A: Student Organization Membership Database

The database stores:

- member names and contact information
- volunteer interests
- event sign-ups

Operational situation:

- the organization can continue for several hours by using email records and
  recent exports
- recent changes matter, but some re-entry would be manageable
- downtime is frustrating, but it does not stop same-day revenue operations

Basic response:

- regular backups are still necessary because the records are important
- recovery can be somewhat slower because temporary workarounds exist
- some recent-change loss may be acceptable if the organization can re-enter it
  responsibly

### Main Case B: Regional Bakery Order Database

The database stores:

- same-day customer orders
- delivery routes
- payment status
- special order instructions

Operational situation:

- the morning production window is time-sensitive
- lost recent changes can lead to missed orders or wrong deliveries
- downtime quickly affects customers, staff coordination, and revenue

Compare these two responses:

- Response 1: Keep a nightly backup and figure out recovery steps only when a
  failure happens.
- Response 2: Keep more frequent protection during the workday, know which data
  must be restored first, and document the basic recovery steps.

Why Response 2 is stronger:

- same-day order changes matter too much to rely on only a much older copy
- the bakery needs a faster, clearer recovery path during business hours
- staff need trustworthy records to resume work without guessing

What limit still remains:

- even a stronger basic plan may still require some re-entry of very recent
  work, and recovery will still take time

## Guided Practice

### Practice 1: Label The Purpose

For each statement, decide whether it describes `backup`, `restore`,
`recovery`, or `continuity`.

1. "The organization brings yesterday's protected copy back into use."
2. "Staff return the ordering system to a usable state after a file problem."
3. "The company keeps a protected copy in case a damaging update ruins the
   live data."
4. "Managers decide the database cannot be unavailable for most of the workday."

### Practice 2: Compare A Weaker And Stronger Response

Case:

"A campus bookstore uses a database for online orders and same-day pickup.
During exam week, students depend on timely order status and inventory
availability."

Answer:

1. Why is "we back up occasionally" a weak response for this case?
2. What would make a stronger basic response more sensible?
3. What limitation might still remain even with the stronger response?

### Practice 3: Choose A Response

Case:

"A small nonprofit tracks donors, pledges, and thank-you letters in a
database. If the system is unavailable for half a day, staff can still answer
some questions from recent reports. Losing a full week of recent donations,
however, would create trust and recordkeeping problems."

Answer:

1. What records and work must be protected most carefully?
2. Is a very weak, occasional backup plan sensible here? Why or why not?
3. What kind of basic recovery thinking should the nonprofit have ready?
4. What recent-change loss would probably be unacceptable?

### Practice 4: Explain The Limit

Read this statement:

"We have backups, so our database is safe."

Answer:

1. Why is this statement incomplete?
2. What question about downtime is missing?
3. What question about lost recent work is missing?
4. What question about actual recovery steps is missing?

## What To Do

1. Read the lesson carefully and make sure you can explain the difference
   between backup, restore, and recovery.
2. Work through the guided practice in order.
3. Check whether your answers connect the response to real continuity needs.
4. Complete the assignment for submission.
5. Re-read the main bakery case and explain why the stronger response fits the
   scenario better.

## Assignments

### Assignment 1: Backup And Recovery Response

Write a short scenario response for one provided case, such as order
processing, payment posting, scheduling, or donor records. Your response must:

- explain what the backup is trying to protect
- explain what recovery is trying to accomplish
- identify what downtime would interrupt
- identify what recent-change loss would be hard to accept
- recommend a sensible basic backup or recovery response
- explain why a weaker response would be incomplete or risky
- name at least one limitation that would still remain

## Deliverables

- one short written backup-and-recovery recommendation
- one plain-language comparison of a weaker and stronger response
- one explanation of the main remaining limit in the recommended plan

## Project Checkpoint Or Module Connection

For the Module 7 `Operations Decision Memo`, identify which records in your
project database or case would be hardest to reconstruct after a damaging
change. Explain what level of backup and recovery planning would be sensible
for those records, and connect your answer to organizational trust,
accountability, and responsible care for people affected by the data.

## Wrap-Up

Backup and recovery belong together, but they are not the same thing. Backup
protects against loss, damage, and bad changes. Recovery restores usable
records and usable work after disruption. Restore is one action inside that
larger recovery process.

A sensible response depends on continuity needs, tolerance for lost recent
work, and honest recognition of what limits still remain. Responsible database
operation is not only about making systems run. It is also about caring for
organizational records in ways that preserve trust, support continuity, and
help the organization serve people faithfully when problems occur.
