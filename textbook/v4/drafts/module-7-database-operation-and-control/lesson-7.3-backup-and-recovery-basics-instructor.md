# Lesson 7.3: Backup and Recovery Basics

## Instructor-Facing Content

### Module

Module 7: Database Operation and Control

### Lesson Purpose

Teach students to explain what backups protect, what recovery is trying to
accomplish, and how to justify a sensible introductory backup or recovery
response in a realistic scenario.

### Module Context

This lesson closes Module 7. Lesson 7.1 focused on who should have access to
the database. Lesson 7.2 focused on protecting truthful records while work is
in progress. Lesson 7.3 asks what responsible operation looks like when loss,
damage, or a bad change still occurs. It directly supports the Module 7
`Operations Decision Memo`, where students must recommend a basic backup or
recovery response and justify why weaker alternatives are incomplete.

### Primary Learning Type(s)

Principles

### Secondary Learning Type(s), If Any

Facts

### Estimated Time

70 to 85 minutes

### Lesson Outcomes

By the end of this lesson, students should be able to:

- explain what backups are for in plain language
- explain what recovery is trying to accomplish after a problem
- distinguish backup, restore, and recovery clearly
- compare a weaker and stronger basic response for a realistic scenario
- identify practical limits in a proposed backup or recovery plan
- choose and justify a sensible introductory backup or recovery response

### Module Alignment

- Supports the Module 7 objective to explain roles, permissions, concurrency,
  transactions, backup, and recovery basics.
- Supports the Module 7 objective to recommend least-privilege access and basic
  operational responses.
- Delivers the lesson coverage named in the module plan: backup purpose,
  recovery thinking, and operational tradeoffs and limitations.

### Course Objective Alignment

- Course objective 6: administer introductory backup, recovery, security, and
  concurrency control work

### Lesson Sequence Role

Completes Module 7 by shifting from preventive operational controls to
restoration reasoning after disruption.

### Required Prior Knowledge

- understanding from Lesson 7.1 that operational controls exist to protect
  privacy, trust, and appropriate data use
- understanding from Lesson 7.2 that truthful records require good habits
  during multi-user work
- general awareness that databases support ongoing organizational activity

### Lesson Opening Guidance

Open with the statement, "A backup is not the same as recovery." Ask students
to explain the difference before formal definitions appear. Then present a
contrast between a student-organization database and a same-day bakery order
database so students see immediately that continuity pressure changes what
counts as a sensible response.

### Teaching Notes

- Keep the lesson introductory and practical. Students are making operational
  judgments, not designing enterprise backup architectures.
- Emphasize that backup is protection before failure, while recovery is the
  effort to restore usable records and usable work after failure.
- Make restore concrete as one step inside recovery.
- Keep the main reasoning centered on two practical questions: how much recent
  work can be lost, and how long can work be interrupted?
- Require students to name limits in a proposed plan. This helps prevent empty
  statements such as "we have backups, so we are safe."
- Keep the lesson business-facing. Use cases where downtime, lost recent
  changes, or unclear recovery steps create understandable business harm.
- Avoid drifting into detailed SQL Server backup commands, recovery models,
  high-availability architecture, or disaster-recovery administration detail.

### Online Activities

- key-term classification on backup, restore, recovery, and continuity
- weaker-versus-stronger response comparison
- short scenario prompt on downtime and recent-change loss
- brief written explanation of why a plan is incomplete

### Homework / Graded Assignments

#### Assignment 1: Backup And Recovery Response

Students analyze one realistic case and submit a short response that explains
what must be protected, what recovery is trying to accomplish, what downtime or
recent-change loss would be unacceptable, and which basic response is more
sensible.

### Deliverables

- one short written backup-and-recovery recommendation
- one comparison of a weaker and stronger response
- one explanation of the main remaining limit in the recommended plan

### Assessment Plan

Formative evidence:

- students distinguish backup, restore, and recovery accurately
- students explain why continuity needs differ by scenario
- students identify why a weak response is incomplete or risky

Graded evidence:

- students choose a sensible basic response for a scenario
- students justify the response using downtime and recent-change reasoning
- students name at least one meaningful limitation that still remains

AI-resilient design note:

- The lesson does not rely on a polished artifact. Students must explain why a
  response fits the case, why a weaker option is inadequate, and what risk
  still remains after the recommendation.

Stronger performance looks like:

- connecting the response to actual records and work, not vague safety language
- distinguishing backup from recovery without collapsing the terms
- explaining limitations honestly instead of implying perfect protection

### Suggested Rubric Focus

- accuracy of backup, restore, and recovery distinctions
- clarity of continuity reasoning
- quality of weaker-versus-stronger response comparison
- practicality of the recommended basic response
- honesty and specificity in naming remaining limits

### Common Misconceptions

- "Backup and recovery are the same thing."
- "If a backup exists somewhere, the organization is ready."
- "Every database needs the same level of protection."
- "Recovery only means copying a file back."
- "Low-pressure databases do not need backups."
- "Backup planning replaces permissions and transaction controls."

### Christian Integration Notes

- Connect backup and recovery to responsible care for organizational records,
  especially when those records affect customers, donors, students, employees,
  or other stakeholders.
- Frame continuity and truthful record restoration as part of trustworthy,
  neighbor-serving business practice.
- Keep the integration embedded in scenario consequences and project
  checkpoint language rather than in a separate reflection section.

### Workflow Connection

This lesson completes the operational-control stage of the course workflow.
Students have already learned how to model, implement, query, secure, and
protect in-progress work. Here they learn how to protect records against loss
and restore useful service when disruption happens.
