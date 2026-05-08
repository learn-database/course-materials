# Lesson 8.2: Triggers

## Instructor-Facing Content

### Module

Module 8: Procedural Logic and Final Project Revision

### Lesson Purpose

Teach students to judge whether a trigger should exist at all, connect event-driven logic to a specific business rule, and test behavior with both allowed and blocked changes. The lesson should frame triggers as bounded automation rather than as the default answer for every rule.

### Module Context

Lesson 8.1 introduced stored procedures as reusable operations that are called intentionally. Lesson 8.2 adds event-driven enforcement and asks students to compare triggers against constraints, procedures, queries, and human review. Lesson 8.3 then uses change-request revision to test whether students can adjust the broader solution when procedural logic must change.

This sequence matters. Students need to see triggers as one procedural option inside the module's larger judgment task, not as an isolated syntax topic.

### Primary Learning Type(s)

Problem solving / judgment

### Secondary Learning Type(s), If Any

Procedures

### Estimated Time

75 to 90 minutes

### Lesson Outcomes

By the end of the lesson, students should be able to:

- explain what a trigger is and how it differs from a stored procedure
- justify when a trigger is appropriate and when another approach is stronger
- match trigger logic to the correct `INSERT`, `UPDATE`, or `DELETE` event
- build a simple SQL Server trigger for one bounded rule
- test expected and unexpected behavior and verify table state afterward
- identify fairness or side-effect concerns that mean a rule should not be fully automated

### Module Alignment

This lesson supports Module 8 objectives to:

- decide when a trigger is justified
- test procedural behavior with controlled inputs and changes
- explain expected versus unexpected behavior for procedural logic
- judge whether automation is fair, bounded, accountable, and trustworthy

### Course Objective Alignment

- Course Objective 5: create and use SQL statements for querying and data manipulation
- Course Objective 6: administer introductory backup, recovery, security, and concurrency control work

### Lesson Sequence Role

Deepens Module 8 procedural judgment and prepares students for cross-artifact revision in Lesson 8.3.

### Required Prior Knowledge

- writing `INSERT`, `UPDATE`, and `DELETE` statements
- understanding tables, keys, and constraints
- basic transaction success and rollback reasoning from Module 7
- introductory procedural-choice reasoning from Lesson 8.1

### Lesson Opening Guidance

Open with a short comparison prompt:

`A new payment could overpay an invoice. Should that rule live in a constraint, stored procedure, trigger, report, or staff review process?`

Use the answers to establish that triggers are not automatically stronger than alternatives. Then introduce triggers as event-driven automation that must be justified and bounded.

### Teaching Notes

- Keep one main case through the lesson so students can focus on reasoning rather than switching scenarios.
- Emphasize that trigger selection begins with the rule and the event, not with enthusiasm for automation.
- Require students to name at least one stronger alternative when they reject or accept trigger use.
- Treat testing as behavior verification, not as "the code ran once."
- Include side-effect reasoning. Students should ask what else the trigger might affect and what should remain outside the automation boundary.
- Keep SQL Server terminology practical. `inserted` and `deleted` should support beginner understanding, not open a deep implementation detour.
- Do not drift into advanced topics such as recursion, nested triggers, or performance tuning.

### Online Activities

- trigger-or-not classification activity using four short rules
- event-matching activity for `INSERT`, `UPDATE`, and `DELETE`
- expected-versus-unexpected behavior prediction check before students run tests
- short reflection prompt on what should not be automated because fairness or human judgment still matters

### Homework / Graded Assignments

Lesson check with two evidence types:

- a trigger justification response comparing alternatives
- a small trigger build or revision with one expected-behavior test, one unexpected-behavior test, and a written explanation of the observed results

This combination matters because trigger code alone is weak evidence in an AI-available course.

### Deliverables

- one SQL file with trigger code and test statements
- one short written explanation covering rule justification, event choice, expected versus unexpected behavior, verification results, and one non-automation judgment

### Assessment Plan

Formative evidence:

- students classify when a trigger is or is not justified
- students identify the correct event for a rule
- students predict expected versus unexpected behavior before execution

Graded evidence:

- students submit trigger logic tied to one clear rule
- students provide both allowed and blocked tests
- students verify resulting table state
- students explain why the trigger is appropriate and where automation should stop

To stay aligned with v4, do not grade the SQL artifact alone. Grade the explanation, comparison, and testing quality with equal seriousness.

### Suggested Rubric Focus

- trigger choice is justified against at least one alternative
- event selection matches the business rule
- trigger logic is bounded to one clear responsibility
- testing covers expected and unexpected behavior
- explanation identifies side effects, fairness boundaries, or reasons not to automate further

### Common Misconceptions

- "A trigger is the best option whenever a rule exists."
- "If the trigger compiles, the design is finished."
- "Automation is automatically more professional than review by a person."
- "The event list does not matter much as long as the trigger runs."
- "Testing the success path is enough."
- "A trigger that also updates several other processes is efficient rather than risky."

### Christian Integration Notes

Keep integration inside the technical decision. A trigger is delegated authority inside the database. That makes bounded automation, fairness, and accountable behavior part of the lesson's normal reasoning.

Useful prompts:

- Which rule is objective enough for automatic enforcement?
- Where would full automation risk unfair treatment or hide necessary human judgment?
- Can the business explain the trigger's behavior clearly to the people affected by it?

The goal is trustworthy business practice, not a detached reflection section.

### Workflow Connection

This lesson sits after implementation, data-change statements, and transaction basics. Students already know how data changes happen. Lesson 8.2 adds the narrower question of whether the database should react automatically to those changes. That judgment supports the module's final change-request work because students must be able to revise and defend automation choices as part of the full database solution.
