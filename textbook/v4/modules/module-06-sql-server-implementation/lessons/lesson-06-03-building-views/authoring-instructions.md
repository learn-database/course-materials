# Lesson 6.3 Building Views Instructions

## Canonical Lesson Identity

- Lesson number: `6.3`
- Canonical title: `Building Views`
- Canonical slug: `building-views`
- Instruction file: `textbook/v4/lesson-instructions/lesson-6.3-building-views-instructions.md`
- Student draft: `textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.3-building-views.md`
- Instructor draft: `textbook/v4/drafts/module-6-sql-server-implementation/lesson-6.3-building-views-instructor.md`

## Required Source Package

Read and follow these files before drafting or revising the lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/03-lesson-prompt.md`
3. `textbook/v4/05-lesson-writing-agent-index.md`
4. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
5. `textbook/v4/modules-plan/06-module-6-sql-server-implementation.md`
6. `textbook/christian_integration_guide.md`

## Lesson Role In Module 6

This lesson closes the core implementation sequence for Module 6.

- Lesson `6.1` established tables and constraints from the approved DBDD.
- Lesson `6.2` established careful data changes and verification habits.
- Lesson `6.3` should show how reusable reporting logic is built on top of that approved structure and verified data.
- The lesson should prepare students for the module's build-and-verify audit, where technically successful SQL is not enough unless it aligns to the intended design and business question.

## Lesson Focus

Teach students how to build views for reusable reporting logic, readable query packaging, and verification of outputs against business intent.

The lesson should make clear that a view is not a magic shortcut. It is a named reporting structure built from a tested query. A technically successful view can still be wrong if it answers the wrong question, hides needed context, or exposes unnecessary details.

## Required Emphasis

- present views as reusable reporting structures, not magic shortcuts
- include output-verification tasks, not only syntax coverage
- connect view design to transparency without oversharing
- keep the lesson tied to SQL Server and T-SQL
- reinforce the module's verification habit: test the logic first, package it second, verify the output third

## Strategy Requirements

Use the v4 lesson strategy for Lesson `6.3`.

- Primary learning type: `Procedures`
- Secondary learning type: `Problem solving / judgment`
- Strategy pattern:
  - modeled reusable query packaging
  - business-question alignment checks
  - output interpretation
- Practice type:
  - build a view from a reporting question
  - compare the view output to the intended question
  - detect when a view is technically valid but misleading

## Coverage Requirements

The lesson must explicitly teach all of the following:

- what problem a view solves
- when a view is appropriate and when an ad hoc query is more appropriate
- why the underlying `SELECT` should be tested before `CREATE VIEW`
- how to convert a tested query into a named view
- how to verify whether the resulting output answers the intended business question
- how a view can support transparent business decisions without exposing unnecessary details

At least one worked example or practice item must ask students to judge whether the output of a view answers the intended business question.

At least one touchpoint must ask students to decide whether a view includes unnecessary details such as personal or sensitive columns that do not serve the reporting purpose.

## Christian Integration Expectations

Keep integration inside normal teaching elements, not in a stand-alone devotional section.

Natural touchpoints for this lesson include:

- truthfulness in reporting
- stewardship of data visibility
- responsible data use in views
- transparency that serves decision-making without careless oversharing

## Suggested Case Direction

Use one practical reporting case across the lesson so students can focus on view judgment instead of rebuilding context repeatedly. A tutoring-center or similar service-operation case works well because it allows:

- repeatable reporting needs
- clear joins across several tables
- readable business-facing output
- a realistic privacy boundary between useful scheduling information and unnecessary personal details

## Acceptance Checks

The lesson is complete only if all of these are true:

- it explains what problem a view solves and when one is appropriate
- it includes at least one example or practice item that asks students to verify whether a view output answers the intended business question
- it includes at least one touchpoint asking how a view can support transparent decisions without exposing unnecessary details
- it preserves Module 6 context and prepares students for the build-and-verify audit
- it meets the shared v4 lesson acceptance criteria in `textbook/v4/03-lesson-prompt.md`
