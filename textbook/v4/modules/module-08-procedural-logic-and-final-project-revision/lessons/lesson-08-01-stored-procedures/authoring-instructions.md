# Lesson 8.1 Writing Instructions

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file for this lesson.

## Canonical Lesson Identity

- Lesson number: `8.1`
- Canonical title: `Stored Procedures`
- Canonical slug: `stored-procedures`
- Module: `Module 8: Procedural Logic and Final Project Revision`

## Canonical Output Paths

- Instruction file: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-01-stored-procedures/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-01-stored-procedures/lesson.md`
- Instructor draft: `textbook/v4/modules/module-08-procedural-logic-and-final-project-revision/lessons/lesson-08-01-stored-procedures/instructor.md`

## Required Source Package

Read these files before drafting:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/03-lesson-prompt.md`
5. `textbook/v4/05-lesson-writing-agent-index.md`
6. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
7. `textbook/christian_integration_guide.md`
8. `textbook/v4/modules-plan/08-module-8-procedural-logic-and-final-project-revision.md`

## Lesson Focus

Teach procedure purpose, reusable operations, parameter use, and basic testing so students can judge when a stored procedure is appropriate.

## Module Context To Preserve

- This is the opening lesson in Module 8.
- The lesson should build on prior SQL, implementation, and transaction knowledge from earlier modules.
- It should prepare students for Lesson 8.2 on triggers by making the stored procedure boundary clear.
- It should also prepare students for Lesson 8.3 by treating procedural logic as one part of a larger, revisable database solution.

## Required Emphasis

- teach procedure justification, not just procedure syntax
- include at least one comparison between a stored procedure and a plain-query alternative
- include basic testing guidance tied to expected behavior, not only successful execution
- frame automation as delegated authority that must stay bounded and accountable
- keep the lesson business-facing and appropriate for SQL Server and T-SQL

## Required Content Moves

The student-facing lesson should explicitly do all of the following:

- explain what problem a stored procedure solves
- explain when a plain query is enough
- explain when repeated work, controlled execution, or parameterized input make a procedure useful
- show at least one parameterized T-SQL procedure example
- include guidance for testing success, no-match, and invalid-input behavior where appropriate
- include one prompt asking what should not be automated because human judgment, fairness, or review still matters

The instructor-facing lesson should stay lean and focus on:

- lesson purpose and sequence role
- alignment to the module assessment pattern
- grading focus for justification and testing quality
- common misconceptions about overusing procedures

## Acceptance Checklist

Confirm all of these before considering the lesson complete:

- the lesson explains what problem a stored procedure solves and when it is appropriate
- at least one example or practice item asks students to compare a procedure with a plain-query alternative
- the lesson includes basic testing guidance tied to expected behavior
- the lesson keeps automation bounded, testable, and accountable
- the student-facing content teaches directly for independent online learning
- the instructor-facing content does not duplicate the full student lesson
- the files use the canonical title, slug, and paths exactly

## Suggested Drafting Reminder

Use the instructional strategy for Lesson `8.1` from `textbook/v4/02-instructional-strategies-for-lessons.md`:

- Primary learning type: `Procedures`
- Secondary learning type: `Problem solving / judgment`
- Strategy pattern:
  - modeled code creation
  - repeated-operation reasoning
  - parameterized execution
  - test-and-verify practice
