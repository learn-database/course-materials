# Lesson 8.3: Final Project Integration and Revision

## Instructor-Facing Content

- Module: Module 8: Procedural Logic and Final Project Revision
- Lesson purpose: Teach students to review the final database project as one integrated package, trace a late business-rule change across the affected artifacts, revise the package in a defensible order, and explain both changes and limits honestly.
- Module context: This is the capstone lesson of Module 8 and the course. Lessons 8.1 and 8.2 taught justified procedural logic and behavior testing. Lesson 8.3 now makes adaptation the core performance by requiring change-response, cross-artifact coherence, and trustworthy final packaging.
- Primary learning type(s): Problem solving / judgment
- Secondary learning type(s), if any: Principles, Procedures
- Estimated time: 90 to 120 minutes
- Lesson outcomes:
  - Review a full project package for alignment across requirements, ERD, DBDD, SQL, views, procedures, triggers, permissions, and tests as relevant.
  - Identify which artifacts must change after one business-rule revision and justify why.
  - Revise from the earliest affected artifact to the latest implementation artifact.
  - Explain why one artifact did not need to change when that decision is justified.
  - Evaluate whether the final package is coherent, honest about limitations, and trustworthy for the stated business purpose.
- Module alignment:
  - Supports the Module 8 objective to revise the full project package for cross-artifact consistency after a new rule or constraint.
  - Delivers the module's primary graded evidence pattern: change-request revision rather than polished artifact submission alone.
  - Reinforces the module's Christian integration emphasis that revision, consistency, and final packaging are marks of faithful professional follow-through.
- Course objective alignment:
  - Objective 2: evaluate a business process and determine what data must be stored.
  - Objective 3: create ER Diagrams and Database Design Diagrams that reflect a given business process.
  - Objective 5: create and use SQL statements for querying and data manipulation.
  - Objective 6: administer introductory operational control work, including permissions and verification-related judgment.
- Lesson sequence role:
  - Follows Lesson 8.1 on stored procedures and Lesson 8.2 on triggers.
  - Completes the course workflow by focusing on adaptation after change.
  - Prepares the student for the module's change-request revision assessment and the final project handoff.
- Required prior knowledge:
  - Requirements analysis from Modules 1 and 3.
  - ERD versus DBDD boundary from Modules 3 and 5.
  - SQL implementation from Module 6.
  - Permissions, transaction, and operational judgment from Module 7.
  - Stored procedure and trigger justification from Lessons 8.1 and 8.2.
- Lesson opening guidance:
  - Open with a contrast between two final submissions: one with clean-looking files that disagree, and one with modest formatting but clear cross-artifact alignment.
  - Ask which package is more trustworthy and why. Use the discussion to move students from appearance-based judgment to evidence-based coherence judgment.
- Teaching notes:
  - Keep the lesson centered on one late-change case with enough reach to affect multiple artifacts.
  - Require students to distinguish `must change`, `might change`, and `does not need to change`. This prevents shallow "change everything" answers.
  - Preserve artifact boundaries carefully. Students should not collapse ERD and DBDD responsibilities during revision.
  - Treat triggers as optional here. The lesson should ask whether a trigger is warranted, not assume it must be added.
  - Press for evidence in every explanation. "I updated the project" is not enough. Students should name the rule, the artifact, and the reason.
  - Keep AI use realistic. Students may use AI to compare artifacts or draft revisions, but grading should focus on verification, diagnosis, and justification.
- Online activities:
  - Artifact reach table for the tutoring-center change request.
  - Earliest-artifact diagnosis prompt using a deliberately incomplete revision.
  - Short limitation-statement exercise.
  - Final-package trustworthiness checkpoint.
- Homework / graded assignments:
  - Change-Request Revision Matrix:
    - identify one late change or inconsistency
    - list each relevant artifact type
    - state whether it changed, needed review, or stayed unchanged
    - justify each decision briefly
  - Final Integration Memo:
    - explain revision path
    - justify at least one changed artifact and one unchanged artifact
    - evaluate coherence, honesty about limitations, and trustworthiness
- Deliverables:
  - one revision matrix
  - one revised project package or revised project sample
  - one final integration memo
- Assessment plan:
  - Formative:
    - artifact-reach classification
    - earliest-source diagnosis
    - brief trustworthiness and limitation checks
  - Graded:
    - change-request revision matrix
    - final integration memo
  - Evidence checklist:
    - Student can trace one business-rule change across the whole project package.
    - Student identifies which artifacts must change and why.
    - Student revises in a coherent source-to-downstream order.
    - Student preserves the ERD versus DBDD distinction.
    - Student addresses views, procedures, triggers, permissions, and tests as relevant rather than by reflex.
    - Student evaluates whether the final package is coherent, honest, and trustworthy.
- Suggested rubric focus:
  - Cross-artifact completeness: the response identifies the right affected artifacts and does not ignore an important downstream consequence.
  - Revision logic: the student starts at the earliest affected artifact and follows a defensible revision path.
  - Boundary discipline: the student keeps conceptual and implementation-ready artifacts distinct.
  - Justification quality: the student explains both changes and non-changes with case-based reasons.
  - Trustworthiness judgment: the student can assess limitations honestly instead of overselling the package.
- Common misconceptions:
  - "If the SQL works, the package is coherent."
  - "A late change only matters in the implementation script."
  - "Every change requires a trigger."
  - "Permissions are separate from design and do not need review."
  - "Tests are optional once the revision looks correct."
  - "A strong final memo should hide weaknesses so the package seems polished."
- Christian integration notes:
  - Tie revision quality to faithful professional follow-through, truthfulness, and stewardship of organizational trust.
  - Use the trustworthiness checkpoint as the main integration touchpoint rather than a separate reflection section.
  - Reinforce that honest communication about limitations is part of competent service, not an admission of failure.
- Workflow connection:
  - This lesson completes the course workflow by testing whether students can revise a full database solution after a late change request. It brings together requirement interpretation, conceptual modeling, implementation detail, procedural logic, access control, and verification into one final judgment task.

### Suggested Rubric

| Criteria | Meets Lesson Standard | Stronger Performance |
| --- | --- | --- |
| Change tracing | Identifies the main affected artifacts and explains why they matter | Traces the change across the full package, including downstream behavior, access, and tests |
| Revision path | Revises from an appropriate starting artifact and follows a logical sequence | Explains clearly why that starting point is the earliest valid source of the change |
| Artifact boundaries | Keeps ERD, DBDD, and implementation responsibilities distinct | Uses the distinctions to explain why certain edits belong in one artifact and not another |
| Justification | Gives concrete reasons for changes and non-changes | Shows strong judgment about when views, procedures, triggers, permissions, or tests are or are not warranted |
| Trustworthiness review | Assesses coherence and states limitations honestly | Connects technical revision quality to truthful reporting, responsible access, and professional trust |
