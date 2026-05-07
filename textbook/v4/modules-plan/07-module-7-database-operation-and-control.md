# Module 7: Database Operation and Control

### Purpose

- Introduce the operational controls and administrative reasoning needed for responsible database use in multi-user environments.
- Keep the focus on judgment rather than vendor-specific administration detail.

### Objectives

- explain roles, permissions, concurrency, transactions, backup, and recovery basics
- analyze simple security and multi-user scenarios
- justify commit and rollback choices
- recommend least-privilege access and basic operational responses

### Human Must Know

- what access is appropriate for a role
- when a transaction boundary is necessary
- what concurrency risk exists in a scenario
- what a sensible backup or recovery response should be

### AI May Assist With

- drafting CRUD matrices
- proposing role-based access plans
- generating transaction syntax examples
- simulating basic scenario alternatives

### Christian Integration Focus

- connect least privilege, privacy, and operational control to justice, accountability, and responsible care for people and information
- treat transaction and recovery choices as trust-preserving operational habits rather than abstract DBA mechanics

### Integration Touchpoints

- include one permissions scenario that asks what access would be unjust, excessive, or careless even if technically possible
- include one project checkpoint asking how operational controls protect privacy, fairness, and trustworthy business practice

### Lessons

#### Lesson 7.1: Roles, Users, and Permissions
- role-based access
- permission types
- CRUD matrices
- least privilege

#### Lesson 7.2: Concurrency and Transactions
- multi-user risks
- transaction units of work
- `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK`

#### Lesson 7.3: Backup and Recovery Basics
- backup purpose
- recovery thinking
- operational tradeoffs and limitations

### Assessment Strategy

This module should use realistic scenario analysis rather than syntax-heavy build tasks. The graded work should ask students to justify operational choices and reject unsafe or excessive ones.

### Primary Graded Assessment

#### Operations Decision Memo

- Format: scenario-based memo plus short case checks
- Students recommend role access, justify least privilege, identify concurrency risks, decide whether actions belong in one transaction, and explain a backup or recovery choice

### Secondary Evidence

- timed scenario quiz
- short comparison of a stronger and weaker operational plan

### What To Grade

- quality of least-privilege reasoning
- correctness of transaction-boundary decisions
- identification of multi-user integrity risks
- practicality of backup and recovery recommendations
- ability to justify why a stronger control choice supports privacy, justice, accountability, or organizational trust

### Module Assessment Tasks

- recommend permissions for roles in a realistic scenario
- explain why one permission level is too strong
- identify when a unit of work should commit or roll back as one whole
- choose a basic backup or recovery response and justify it

### Why This Assessment Holds Up Better

- it tests judgment directly
- it is harder to fake well without understanding the scenario
- it evaluates whether students can explain operational risk in plain language
