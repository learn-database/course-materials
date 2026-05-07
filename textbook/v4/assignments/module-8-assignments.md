# Module 8 Assignments

## Lesson 8.1: Procedure or Plain Query?

### Scenarios

Classify each as `plain query`, `view`, `stored procedure`, or `other design choice`.

1. Show unpaid invoices for the manager every Monday.
2. Record a payment and update the related invoice balance using one repeatable operation.
3. List all active tutors with their subjects.
4. Enforce that a session cannot be created without an existing student.

### Tasks

1. Classify each scenario.
2. Explain two choices.
3. Write a simple stored procedure skeleton or call pattern for scenario 2.
4. Describe expected behavior for two test inputs.

### Submission

Submit classification table, explanation, procedure skeleton, and test note.

### Grading Criteria

- appropriate procedural choice
- distinction among query, view, procedure, and constraint logic
- useful test reasoning

## Lesson 8.2: Should This Be a Trigger?

### Scenarios

1. When a payment row is inserted, write a row to `PaymentAudit`.
2. When a student earns a low grade, automatically remove them from tutoring.
3. When a product price changes, store the old and new price in a history table.

### Tasks

1. Decide whether a trigger is justified, overused, or unsafe for each scenario.
2. For one justified trigger, identify the triggering event.
3. Write one test case that could reveal unexpected behavior.
4. Explain one case where human judgment or fairness should limit automation.

### Submission

Submit one section per scenario plus the test case.

### Grading Criteria

- justified trigger-use judgment
- correct event-driven logic
- recognition of automation risk
- useful behavior test

## Lesson 8.3: Late Change Impact Map

### Change Request

The tutoring center now allows one tutoring session to include more than one tutor when a group session needs multiple subject experts. The original design allowed each session to have exactly one tutor.

### Tasks

1. Identify what must change in the conceptual ERD.
2. Identify what must change in the DBDD.
3. Identify what SQL tables, constraints, views, procedures, triggers, permissions, or tests may need revision.
4. Revise one affected artifact or SQL excerpt.
5. Write a verification plan.
6. Explain why the revised package is more trustworthy than simply patching one table.

### Submission

Submit:

- impact map
- one revised artifact or SQL excerpt
- verification plan
- short defense of the revision

### Grading Criteria

- completeness of cross-artifact impact analysis
- correct handling of one-to-many or many-to-many change
- quality of revised artifact or SQL excerpt
- verification and defense of final package coherence
