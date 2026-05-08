# Lesson 7.1: Roles, Users, and Permissions

## Instructor-Facing Content

### Module

Module 7: Database Operation and Control

### Lesson Purpose

Teach students to recommend appropriate role-based database access by
distinguishing users, roles, and permissions, using a simple CRUD matrix to
support decisions, and defending least privilege in realistic business
scenarios.

### Module Context

This lesson opens Module 7. Earlier modules asked students to analyze business
requirements, design database structures, and implement approved designs. Lesson
7.1 shifts from building the database to operating it responsibly in a
multi-user environment.

Within Module 7, this lesson prepares the logic that later lessons extend:

- Lesson 7.2 moves from access control into concurrency and transaction
  judgment.
- Lesson 7.3 moves from safe daily use into backup and recovery thinking.

This lesson also lays the foundation for the module's operations decision memo
by requiring students to justify stronger and weaker access choices in plain
language.

### Primary Learning Type(s)

Principles

### Secondary Learning Type(s)

Concepts

### Estimated Time

60 to 75 minutes

### Lesson Outcomes

By the end of this lesson, students should be able to:

- distinguish users, roles, and permissions in plain language
- identify the job responsibilities that should control access decisions
- match read, create, update, delete, and administrative access to realistic
  responsibilities
- use a simple CRUD matrix or equivalent role map to support a recommendation
- compare an over-permissioned choice to a least-privilege choice
- reject access that is technically possible but still unjust, excessive, or
  careless

### Module Alignment

- Supports the Module 7 objective of explaining roles, permissions, and
  operational control in multi-user environments.
- Directly covers the Lesson 7.1 elements specified in the module plan:
  role-based access, permission types, CRUD matrices, and least privilege.
- Aligns with the module assessment strategy by emphasizing scenario analysis
  and justification rather than vendor-specific administration syntax.

### Course Objective Alignment

- Objective 1: know basic database terminology
- Objective 6: administer introductory backup, recovery, security, and
  concurrency control work

### Lesson Sequence Role

Introduces module knowledge and establishes the judgment pattern used by the
rest of Module 7.

### Required Prior Knowledge

- basic understanding of tables and business data from earlier modules
- familiarity with the course workflow through design and implementation
- ability to read simple role descriptions and table names

### Lesson Opening Guidance

Open with a short mismatch example: a tutor needs to record session notes, but
someone proposes full billing and delete access "just in case." Ask students
whether that extra access helps the tutor do the job or only broadens the risk.

Use the discussion to frame the central lesson rule:

Access should follow actual responsibility, not convenience or curiosity.

### Teaching Notes

- Keep the lesson principle-centered. Students do not need SQL Server security
  syntax here.
- Push for plain-language justifications, not only correct labels.
- Use the Lakeside Tutoring Center case consistently so students can compare
  role decisions without reloading context.
- Emphasize that delete access and administrative access require separate
  justification.
- Reinforce that a CRUD matrix is a support tool. Students still need to defend
  the reasoning behind each cell.
- Connect excessive access to privacy loss, injustice, and accountability
  failure when those risks naturally arise from the case.

### Online Activities

- concept check on `user`, `role`, `permission`, and `least privilege`
- short scenario prompt asking students to reject one unnecessary permission
- CRUD matrix interpretation activity focused on blank cells and omitted delete
  permissions
- short written comparison of a stronger and weaker access plan

### Homework / Graded Assignments

#### Access Recommendation Memo

Students submit:

- one completed CRUD matrix or equivalent role map
- one short memo that:
  - recommends role-based access for the scenario
  - identifies the minimum needed access for each role
  - rejects one technically possible but unjust, excessive, or careless access
    request
  - explains how the final plan follows least privilege

### Deliverables

- completed CRUD matrix or role map
- short access recommendation memo

### Assessment Plan

#### Formative

- classification checks on user versus role versus permission
- short-response judgments about stronger and weaker permission choices
- matrix-reading prompts that ask why certain cells are blank

#### Graded

- scenario-based access recommendation memo with attached matrix or role map

#### Evidence Of Learning

Strong evidence appears when students:

- connect access directly to stated job responsibilities
- distinguish user, role, and permission accurately
- use the CRUD matrix to support rather than replace judgment
- reject at least one over-permissioned choice with a concrete reason
- explain how the final plan protects privacy, fairness, or accountability

#### AI-Available Assessment Note

The artifact alone is not enough. A CRUD matrix can be drafted quickly with AI.
The memo is therefore necessary second evidence because it forces students to
justify why the access plan is appropriate and why a stronger alternative is
worse.

### Suggested Rubric Focus

- Responsibility-to-access match: Do permissions clearly follow the role's
  actual work?
- Least-privilege judgment: Does the student remove permissions that are not
  justified?
- Role-based reasoning: Does the student organize access by roles instead of
  ad hoc user exceptions?
- Ethical and operational justification: Does the student explain how the plan
  supports privacy, justice, accountability, or trust?
- Clarity: Is the recommendation understandable in plain language?

### Common Misconceptions

- "More access helps people work faster, so it is safer."
- "If someone can update a record, they should also be allowed to delete it."
- "Managers should always receive full access because they are in charge."
- "A CRUD matrix is the answer by itself, so no written justification is
  needed."
- "If a permission is technically possible to grant, it must be acceptable."

### Christian Integration Notes

Keep integration inside the normal access-control reasoning. This lesson fits
the course-wide themes of human dignity, privacy, justice, stewardship, and
trust because database permissions affect how people are seen, treated, and
protected.

Useful framing points:

- limiting access can be an act of responsible data stewardship
- broad visibility into sensitive information can create unfair treatment
- role ownership supports accountability and trustworthy service

Do not add a stand-alone devotional section.

### Workflow Connection

Lesson 7.1 sits at the start of the operational-control stage of the larger
database workflow. Students have already moved from business process to design
to implementation. Now they must decide how the finished system should be used
responsibly by different kinds of workers.

That operational judgment continues in later Module 7 lessons:

- Lesson 7.2 asks how multi-user work should be grouped and protected through
  transaction reasoning.
- Lesson 7.3 asks how organizations prepare for disruption through backup and
  recovery decisions.
