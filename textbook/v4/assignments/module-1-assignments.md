# Module 1 Assignments

## Lesson 1.1: Database or Not? Scenario Sort

### Purpose

Practice deciding whether a business situation calls for a spreadsheet, a shared file, or a relational database.

### Scenarios

Classify each scenario:

| Scenario | Description |
|---|---|
| A | A club treasurer tracks 18 reimbursements for one semester and only needs a total by member. |
| B | A tutoring center schedules 42 tutors, tracks students, records sessions, and bills families monthly. |
| C | A manager keeps a PDF copy of each signed vendor contract and searches by vendor name twice a year. |
| D | A campus bookstore tracks inventory, suppliers, purchase orders, sales, returns, and reorder points. |
| E | A professor keeps a one-time list of guest speakers for a single event. |
| F | A clinic tracks patients, appointments, providers, insurance claims, payments, and follow-up notes. |

### Tasks

1. For each scenario, choose `spreadsheet`, `shared file`, or `relational database`.
2. Write a two-sentence justification for scenarios `B`, `D`, and `F`.
3. Choose one scenario where poor recordkeeping could harm people or distort reporting. Explain the risk in 2-3 sentences.

### Submission

Submit a table with columns:

- `Scenario`
- `Recommended tool`
- `Reason`
- `Risk or stewardship note`

### Grading Criteria

- correct tool-fit classification
- clear distinction between data, information, and database need
- realistic explanation of trust, reporting, or service risk

## Lesson 1.2: Workflow Stage Match

### Purpose

Practice connecting a business process to the database workflow and distinguishing ERD from DBDD.

### Case

Bright Path Tutoring wants to move from spreadsheets to a database. The business needs to track students, guardians, tutors, subjects, tutoring sessions, invoices, and payments. Managers want to know which tutors are available, which students attended sessions, and which invoices are unpaid.

### Shuffled Actions

- write `CREATE TABLE` statements
- identify entities and relationships
- interview the manager about billing rules
- draw a conceptual ERD
- choose data types and nullability
- build reports for unpaid invoices
- add primary keys and foreign keys to the DBDD
- decide whether each session must have exactly one tutor
- create backup and permission plan

### Tasks

1. Put the shuffled actions in a reasonable workflow order.
2. Label each action as `requirements`, `ERD`, `DBDD`, `SQL implementation`, `query/reporting`, or `administration`.
3. In 4-5 sentences, explain the difference between the ERD and the DBDD in this case.

### Submission

Submit:

- ordered workflow table
- ERD versus DBDD explanation
- one sentence explaining how the workflow helps the organization tell the truth about its operations

### Grading Criteria

- correct workflow sequence
- accurate artifact classification
- clear ERD versus DBDD boundary
- realistic accountability connection
