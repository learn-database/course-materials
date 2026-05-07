# Lesson 7.1 Draft Instructions

## Canonical Lesson Identity

- Lesson number: `7.1`
- Canonical title: `Roles, Users, and Permissions`
- Canonical slug: `roles-users-and-permissions`

## Required Source Package

Read these files before revising this lesson:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/christian_integration_guide.md`
6. `textbook/v4/modules-plan/07-module-7-database-operation-and-control.md`

## Output Paths

- Student draft: `textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.1-roles-users-and-permissions.md`
- Instructor draft: `textbook/v4/drafts/module-7-database-operation-and-control/lesson-7.1-roles-users-and-permissions-instructor.md`

## Lesson Focus

Draft Lesson 7.1 as the Module 7 access-control lesson. The lesson should teach:

- the difference between users, roles, and permissions
- basic permission types in plain language
- role-based access as a clearer alternative to ad hoc user-by-user grants
- CRUD matrices as a light planning and review tool
- least privilege as the governing decision principle

## Module Context To Preserve

- Module 7 is about operational judgment, not vendor-specific
  administration detail.
- Lesson 7.1 introduces access-control reasoning that later lessons extend
  into transactions, concurrency, backup, and recovery.
- The lesson should prepare students for the module's operations decision
  memo by asking them to justify stronger and weaker access choices in
  realistic scenarios.

## Required Emphasis

- Keep the lesson centered on appropriate access and least privilege.
- Use realistic role scenarios instead of abstract permission lists alone.
- Connect excessive access to injustice, privacy loss, and accountability
  failure.
- Include at least one scenario where students must reject access that is
  technically possible but unjust, excessive, or careless.
- Include at least one simple CRUD matrix or role-mapping example tied to a
  realistic case.

## Learning Strategy

From `textbook/v4/02-instructional-strategies-for-lessons.md`,
Lesson 7.1 should be written primarily as a `Principles` lesson with a
secondary `Concepts` emphasis. The teaching pattern should therefore
include:

- rule explanation
- contrasting cases
- correct-use and incorrect-use examples
- judgment prompts
- decision justification

## Christian Integration Guardrails

- Keep Christian integration embedded in normal lesson elements.
- Use themes such as human dignity, neighbor-serving systems, stewardship,
  privacy, justice, trust, and accountability only where they directly
  support the access-control decision.
- Do not add a stand-alone devotional section.

## Draft Expectations

The student-facing lesson should:

- work as primary instructional material for independent online study
- explain the core terms in plain language
- teach students how to reason from job responsibility to minimum necessary
  access
- show why read, change, delete, and administrative powers should not be
  granted by convenience
- give a realistic case with roles, data objects, and at least one explicit
  over-permissioned choice to reject

The instructor-facing lesson should:

- explain how Lesson 7.1 supports Module 7 and the larger course workflow
- clarify what the instructor should watch for in student reasoning
- align activities and grading with the module's scenario-based assessment
  strategy
- highlight common misconceptions such as "more access is safer" or
  "update automatically implies delete"

## Acceptance Checklist

Before considering this lesson complete, confirm that:

- roles, users, permissions, and least privilege are explained in plain language
- a realistic scenario requires students to reject unjust or excessive access
- a simple CRUD matrix or role map is included and interpreted
- the lesson clearly connects to Module 7's operations decision memo
- the lesson follows the shared v4 lesson structure and online-learning assumptions
