# Lesson 1.1: Why Databases Matter

## Lesson Overview

This lesson starts with the business problem, not the software. Organizations need records because they run recurring processes: they schedule appointments, sell products, serve customers, pay workers, and answer questions about what happened. When those records become hard to update, hard to connect, or hard to trust, the organization has a data problem.

In this opening lesson, you will compare three common approaches to that problem: spreadsheets, disconnected files, and databases. You will also practice using the core terms `business process`, `data`, `information`, and `database` so you can explain why a database is or is not warranted in a realistic case.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- distinguish `business process`, `data`, `information`, and `database`
- compare spreadsheet, disconnected-file, and database approaches
- explain when a database is warranted and when a simpler tool is enough
- identify `table`, `row`, and `column` in a simple example
- justify a tool recommendation with business-facing reasoning about updates, relationships, reporting, and trust

## Key Terms

- **`business process`**: the recurring work an organization performs to achieve an outcome, such as scheduling service, recording sales, or tracking payments
- **`data`**: recorded facts, such as a customer name, order date, or payment amount
- **`information`**: data organized to answer a question or support a decision
- **`database`**: an organized system for storing, relating, updating, and retrieving data consistently
- **`spreadsheet`**: a grid-based tool that works well for small, simple, or temporary recordkeeping and analysis
- **`disconnected files`**: separate documents, exports, or lists that are stored and updated independently rather than as one coordinated source
- **`table`**: an organized structure that stores one main kind of record
- **`row`**: one complete record in a table
- **`column`**: one field or attribute stored for every row in a table

## Readings And Media

- Read this lesson from beginning to end.
- Review the tutoring-center case and the comparison scenarios in the `Examples and Case` section.
- Complete the guided practice before moving to the assignments.
- No separate video or external media is required for this lesson.

## Core Content

### Start With The Work, Not The Tool

A database supports a `business process`. A business process is the recurring work an organization performs. For a campus tutoring center, that work includes scheduling sessions, assigning tutors, recording attendance, and tracking payment status. For a retailer, it might include managing products, sales, returns, and inventory.

Notice what the business process is not. It is not a spreadsheet, a PDF report, or a folder of files. Those are tools or outputs. The business process is the work itself.

That distinction matters because tool choice should follow the work. If the work is simple and temporary, a simple tool may be enough. If the work is recurring, involves related records, and depends on accurate reporting, the organization may need a database.

### Distinguish Business Process, Data, Information, And Database

These terms are related, but they are not interchangeable.

| Term | What it means in plain language | Example from a tutoring center |
| --- | --- | --- |
| `business process` | the recurring work the organization performs | scheduling sessions and recording attendance |
| `data` | one recorded fact | `TutorRate = 25.00` |
| `information` | organized data that answers a question | weekly list of unpaid sessions |
| `database` | a structured system that stores and connects data for ongoing use | a system that keeps students, tutors, sessions, and payments coordinated |

A useful rule is this:

- `data` is what gets recorded
- `information` is what the organization learns when data is organized for use

If you confuse these terms now, later workflow reasoning becomes weak. In this course, careful naming is part of careful thinking.

### Three Common Ways Organizations Keep Records

Organizations often start with simple tools. The problem is not that those tools exist. The problem is using a weak tool after the work has outgrown it.

| Approach | Best fit | Strengths | Warning signs |
| --- | --- | --- | --- |
| Spreadsheet | small, simple, mostly flat data; one person or a very limited group; short-term use | fast to create, easy to edit, good for quick summaries | repeated facts across rows, manual cross-checking, fragile reporting |
| Disconnected files | separate forms, exports, reports, or lists used for a narrow purpose | easy to create locally, useful for one-off documents | version drift, conflicting copies, no shared source of truth, difficult cross-file reporting |
| Database | recurring operations with related records, repeated updates, multiple users, and accountable reporting | shared structure, connected records, more consistent updates and retrieval | requires more upfront design and should not be used when the work is truly simple |

The key judgment is tool fit, not tool prestige.

### When A Spreadsheet Is Enough

A spreadsheet can be the right choice when the work is small, temporary, and low-risk.

Example: one staff member needs a Saturday volunteer sign-up list with ten names, phone numbers, and shirt sizes. The list will be used once and then archived. A database would probably be unnecessary overhead because:

- the data is limited
- the record types are not complex or highly related
- the reporting need is minimal
- the work does not depend on repeated updates across many users

This lesson is not anti-spreadsheet. It is anti-mismatch.

### Why Disconnected Files Often Create Hidden Problems

Disconnected files are more dangerous than they first appear because they look organized while still allowing records to drift apart.

Imagine a tutoring center stores:

- student contact details in a spreadsheet
- tutor rates in a separate document
- session attendance in a shared folder of files
- unpaid-session summaries in a weekly PDF

Each file may make sense by itself. Together, they create risk:

- the same student may appear differently across files
- tutor rates may be updated in one place but not another
- reports may be built from stale exports instead of current records
- staff may not know which file is the authoritative one

This is a trust problem as much as a convenience problem. If the director asks, "How many unpaid sessions do we have this week?" and the answer depends on which file someone opened, the organization cannot report truthfully with confidence.

### When A Database Is Warranted

A database is warranted when the organization needs one coordinated structure for recurring, related, and frequently updated records.

Common signs include:

- several kinds of records must stay connected, such as customers, orders, products, and returns
- the same facts are being repeated in many places
- staff need consistent reports from the same source
- records are updated regularly
- multiple people depend on the same information
- poor recordkeeping could harm service, reporting, billing, or decision-making

A database is not just a bigger spreadsheet. It is a system designed so the organization can store, relate, update, and retrieve data more consistently.

### A Simple Recognition Example: Table, Row, And Column

You do not need technical depth yet, but you should recognize the basic structure of tabular data.

| StudentID | StudentName | StudentEmail | Subject |
| --- | --- | --- | --- |
| S101 | Ava Chen | achen@example.edu | Statistics |
| S102 | Luis Ortiz | lortiz@example.edu | Accounting |

In this example:

- the entire structure is a `table`
- `S101 | Ava Chen | achen@example.edu | Statistics` is one `row`
- `StudentEmail` is a `column`

Later lessons will go deeper into data modeling and implementation. For now, this vocabulary is enough.

## Examples And Case

### Main Case: Campus Tutoring Center

The Campus Tutoring Center supports students in math, writing, accounting, and science courses. The office manager schedules sessions, keeps tutor assignments, records attendance, tracks payment status, and prepares weekly summaries for the director.

Right now, the center uses:

- one spreadsheet for student sign-ups
- separate files for tutor rates and schedules
- exported weekly reports for unpaid sessions

Staff have noticed three problems:

- student contact information is repeated in multiple places
- tutor rates do not always match across records
- the unpaid-session report often needs correction before it can be trusted

This case points toward a database because the center has recurring work, related records, repeated updates, and a need for reliable reporting from one source.

### Contrast Case: One-Time Volunteer Event

A student club needs a one-time volunteer list for a weekend service event. The organizer tracks ten names, phone numbers, and shirt sizes. No recurring reporting is required, the list will not be reused, and only one organizer maintains it.

This case does not strongly justify a database. A simple spreadsheet is likely enough.

### Contrast Case: Department Folder Full Of Files

A small department stores vendor contacts in one spreadsheet, invoices in PDF files, status updates in email attachments, and payment notes in a shared document. Staff keep asking which file is correct when information does not match.

This case may look manageable because each file exists, but it has the warning signs of disconnected-file failure. The main problem is not just quantity. It is that the department lacks one coordinated source for related records and reporting.

## Guided Practice

### 1. Classify The Terms

For each item, decide whether it is `business process`, `data`, or `information`.

- scheduling a tutoring session between a student and a tutor
- `StudentEmail = achen@example.edu`
- weekly count of unpaid tutoring sessions
- recording that a student attended a session
- `PaymentStatus = Unpaid`

Check yourself:

- `business process` describes work the organization performs
- `data` is one recorded fact
- `information` organizes data to answer a question

### 2. Compare The Tool Fit

For each scenario, decide which approach is the best fit right now: `spreadsheet`, `disconnected files`, or `database`.

- a one-time event roster maintained by one person
- a folder of separate files that regularly disagree with each other
- a store tracking customers, orders, products, and returns every day

Then write one sentence explaining why your choice fits the work.

### 3. Ask The Harm Question

Return to the tutoring-center case. If poor structure causes the unpaid-session report to miss several records, who could be harmed?

Name at least two affected people or groups and explain what the harm could look like. Possible stakeholders include students, tutors, office staff, or the director.

This is not a separate ethics exercise. It is part of database reasoning. If structure distorts service or reporting, the design problem has human consequences.

### 4. Verify An AI Recommendation

Read this AI-generated recommendation:

> "The tutoring center should definitely use a database because databases are more professional and can store more data than spreadsheets."

What is weak about this recommendation? In two or three sentences, identify at least two missing or underdeveloped reasons.

Use this check:

- Does the answer describe the actual business process?
- Does it explain why related records and repeated updates matter?
- Does it address reporting trust or service consequences?
- Does it consider whether a simpler tool might be enough?

## What To Do

1. Read the lesson and review the three comparison cases.
2. Complete the guided practice before starting the assignments.
3. Keep your reasoning business-facing and conceptual.
4. Focus on tool fit, not on technical detail or software features.

## Assignments

### Assignment 1: Tool-Fit Case Check

For each scenario below, choose the best current fit: `spreadsheet`, `disconnected files`, or `database`. Then justify your answer in 2 to 4 sentences.

1. A faculty member tracks RSVPs for one banquet and only needs names, meal choices, and phone numbers.
2. A retail shop tracks products, customers, sales, and returns in several tabs and exported files. Managers no longer trust the monthly category-sales report.
3. A nonprofit keeps donor contact details, pledge records, and event attendance in separate files that different staff update independently.

Your justification should mention the factors that matter most in each case, such as:

- related records
- repeated updates
- shared source of truth
- reporting needs
- whether a database would be warranted or unnecessary overhead

### Assignment 2: Recommendation Critique

Read this short recommendation:

> "North Ridge Outfitters needs a database because spreadsheets are old-fashioned and a database will fix the company's reporting problems."

Write 150 to 250 words that:

- judge whether the recommendation is adequate
- revise the reasoning so it reflects the real business process
- explain whether a database is actually warranted
- identify who could be harmed if weak structure continues to distort reporting or service

Checklist for success:

- I described the business work, not just the files.
- I explained why the current structure is weak or why it may still be sufficient.
- I made a clear judgment about whether a database is warranted.
- I connected the recommendation to trust, stewardship, reporting, or service.
- I improved the reasoning instead of only rewriting the wording.

## Deliverables

- one completed tool-fit case check
- one short recommendation critique

## Project Checkpoint Or Module Connection

As you begin thinking about a semester project case, ask this question first: what recurring business process needs reliable records, and does it truly need a database?

That question will carry forward into Lesson `1.2`, where you will connect the business need to the full workflow from process to implementation.

## Wrap-Up

Databases matter because organizations need reliable, connected records for recurring work. This lesson introduced the basic language for explaining that need and the judgment required to compare spreadsheets, disconnected files, and databases honestly.

The key takeaway is not that every organization needs a database. The key takeaway is that tool choice must match the work. In the next lesson, you will move from that tool-fit judgment into the full database workflow.
