# Lesson 8.2 Writing Instructions: Triggers

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file for this lesson.

## Canonical Lesson Identity

- Lesson number: `8.2`
- Canonical title: `Triggers`
- Canonical slug: `triggers`
- Instruction file: `textbook/v4/lesson-instructions/lesson-8.2-triggers-instructions.md`
- Student draft: `textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.2-triggers.md`
- Instructor draft: `textbook/v4/drafts/module-8-procedural-logic-and-final-project-revision/lesson-8.2-triggers-instructor.md`

## Required Source Package

Read these files before drafting, in this order:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/08-module-8-procedural-logic-and-final-project-revision.md`

## Module Context To Preserve

- Module: `Module 8: Procedural Logic and Final Project Revision`
- Previous lesson: `Lesson 8.1: Stored Procedures`
- Next lesson: `Lesson 8.3: Final Project Integration and Revision`
- Module purpose: add reusable procedural logic where justified and use change-driven revision to test whether students can adapt the whole database solution
- Human-must-know emphasis: whether a procedure or trigger should exist at all, what counts as expected behavior, and how to judge trustworthiness and bounded automation

This lesson should feel like the middle procedural-judgment lesson in Module 8, not a detached syntax chapter.

## Lesson Strategy Requirements

From `textbook/v4/02-instructional-strategies-for-lessons.md`:

- Primary learning type: `Problem solving / judgment`
- Secondary learning type: `Procedures`
- Strategy pattern:
  - justified-use analysis
  - event-driven logic explanation
  - controlled behavior testing
- Practice type:
  - decide whether a rule belongs in a trigger
  - match logic to the triggering event
  - test expected and unexpected behavior
- Assessment evidence:
  - students justify whether a trigger is appropriate
  - students explain trigger behavior clearly
  - students detect overuse or weak trigger logic

## Required Lesson Focus

Teach triggers as event-driven automation that must be justified, bounded, and testable.

The lesson must explicitly teach students to ask:

- what rule is being enforced
- why a trigger is stronger or weaker than a constraint, stored procedure, query, application workflow, or human review
- which event should fire the trigger
- what expected behavior should happen
- what unexpected or harmful side effects could happen

## Required Emphasis

The lesson must:

- teach students to ask whether a trigger should exist at all
- include testing and unintended-side-effect reasoning
- connect trigger design to fairness, bounded automation, and accountable behavior
- reflect the module framing that automation is delegated authority and is not automatically good

## Content Expectations

The student-facing lesson should:

- define triggers in SQL Server terms
- distinguish trigger use from constraints, stored procedures, and non-automation alternatives
- include at least one realistic T-SQL trigger example
- explain how `INSERT`, `UPDATE`, and `DELETE` relate to trigger design
- use `inserted` and `deleted` only as needed to support beginner understanding
- include at least one example or practice item where students identify expected versus unexpected trigger behavior
- include at least one touchpoint asking what should not be automated because human judgment or fairness still matters
- include verification guidance that goes beyond "the trigger compiled"

The instructor-facing draft should:

- explain why Lesson 8.2 sits after stored procedures and before final project revision
- align activities to the module change-request assessment model
- highlight misconceptions about overusing triggers and assuming automation is automatically good
- grade explanation, comparison, and behavior testing rather than trigger code alone

## Suggested Case Direction

Use one bounded business rule case rather than several disconnected trigger demos.

Recommended case traits:

- one clear integrity or business rule
- one or two relevant DML events
- visible expected and blocked outcomes
- a realistic opportunity to discuss unintended side effects

## Christian Integration Requirements

Keep integration embedded and technically grounded.

Good touchpoints for this lesson:

- automation as delegated authority that must remain bounded, testable, and accountable
- fairness and human dignity when automation affects people
- trustworthy database behavior as part of faithful business work

Do not add a stand-alone devotional section.

## Acceptance Checklist

Before considering the lesson complete, confirm that:

- the lesson explains when a trigger is justified and when another approach is stronger
- at least one example or practice item asks students to identify expected versus unexpected trigger behavior
- at least one touchpoint asks what should not be automated because human judgment or fairness still matters
- the student lesson teaches directly enough for independent online use
- the instructor draft focuses on alignment, assessment, and implementation guidance rather than repeating the whole lesson
- both drafts reflect the v4 AI-available assessment model by requiring verification and explanation, not code submission alone
