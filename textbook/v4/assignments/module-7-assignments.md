# Module 7 Assignments

## Lesson 7.1: Least-Privilege Access Matrix

### Scenario

A tutoring center has three database roles:

- `Tutor`
- `OfficeAssistant`
- `Manager`

Objects:

- `Student`
- `Tutor`
- `Session`
- `Invoice`
- `Payment`

### Tasks

1. Create a CRUD matrix for the three roles and five objects.
2. Explain two access decisions.
3. Identify one permission that would be excessive or careless.
4. Explain how your matrix protects privacy or accountability.

### Submission

Submit the CRUD matrix and short explanations.

### Grading Criteria

- appropriate access choices
- least-privilege reasoning
- recognition of excessive access
- privacy and accountability connection

## Lesson 7.2: Commit or Roll Back?

### Scenarios

1. A payment is recorded, but the invoice balance update fails.
2. A tutor's phone number is updated, but the audit note fails to save.
3. A student is moved from one session to another, but the new session is already full.

### Tasks

1. Decide which steps belong in one transaction for each scenario.
2. Recommend `COMMIT` or `ROLLBACK` after the described failure.
3. Explain the integrity risk if the steps are split incorrectly.

### Submission

Submit one short section per scenario.

### Grading Criteria

- correct transaction-boundary reasoning
- appropriate commit or rollback choice
- clear integrity-risk explanation

## Lesson 7.3: Recovery Response Choice

### Incident

At 3:40 p.m., a staff member accidentally deletes 47 unpaid invoice records. The last full backup was at midnight. Transaction log backups run every 15 minutes. The manager needs the unpaid invoice list restored as accurately as possible.

### Response Options

1. Recreate the invoices manually from memory.
2. Restore last midnight's backup and lose the rest of the day's work.
3. Restore using the full backup and transaction log backups to a point just before the deletion.

### Tasks

1. Choose the strongest response.
2. Explain why it fits the scenario.
3. Explain why one weaker response is incomplete or risky.
4. Name one limitation or question you would still need to resolve.

### Submission

Submit a short recovery decision memo, 250-400 words.

### Grading Criteria

- correct recovery choice
- practical explanation
- recognition of weaker-response risk
- realistic limitation or follow-up question
