# Lesson 8.2: Triggers

## Lesson Overview

Lesson 8.1 focused on stored procedures as reusable operations that someone calls on purpose. Lesson 8.2 shifts to a different kind of procedural logic: code that runs because a data change happened. That difference matters because event-driven automation can protect data quality, but it can also hide logic, surprise users, and enforce the wrong rule at the wrong moment.

In this lesson, you will learn to treat triggers as justified, bounded tools. You will compare triggers with other options, match trigger logic to the correct event, build one trigger for a clear rule, and test both expected and unexpected behavior before deciding the automation is trustworthy.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain what a trigger is and how it differs from a stored procedure
- decide when a trigger is justified and when another approach is stronger
- match a trigger to the correct `INSERT`, `UPDATE`, or `DELETE` event
- write a simple SQL Server trigger for one bounded business rule
- test expected and unexpected trigger behavior
- identify side effects and fairness concerns that mean a rule should not be fully automated

## Key Terms

- `trigger`: database code that runs automatically when a specified event occurs
- `event-driven logic`: logic that runs because a data change happened
- `INSERT trigger`: a trigger that runs when new rows are added
- `UPDATE trigger`: a trigger that runs when existing rows are changed
- `DELETE trigger`: a trigger that runs when rows are removed
- `inserted`: the logical table that holds new rows for `INSERT` and new values for `UPDATE`
- `deleted`: the logical table that holds removed rows for `DELETE` and old values for `UPDATE`
- `side effect`: an additional result of automation that may be surprising, harmful, or outside the intended rule
- `bounded automation`: automation limited to one clear responsibility with known effects

## Readings And Media

- Read this lesson carefully before writing any trigger code.
- Review Lesson 8.1 if you need to refresh the difference between reusable operations and event-driven automation.
- Keep the Module 8 purpose in mind: the goal is justified and testable procedural logic, not automation for its own sake.

## Core Content

### What A Trigger Is

A trigger is database code that runs automatically when a specified event occurs on a table or view. In this course, you will focus on DML triggers tied to `INSERT`, `UPDATE`, and `DELETE`.

That automatic behavior is the key difference from a stored procedure. A stored procedure runs when someone explicitly calls it. A trigger runs because a change happened. If you only remember one trigger idea, remember this: a trigger is tied to an event, not to a user's decision to run a named operation.

### Start With The Rule, Not The Tool

The first trigger question is not "Can SQL Server do this?" The first question is "Should this rule be enforced with a trigger at all?"

That question matters because a trigger is not the strongest option in every case.

| If the need is... | Stronger option is often... | Why |
| --- | --- | --- |
| restrict one row to allowed values | constraint | the rule is simple, direct, and visible in the table definition |
| run a reusable operation on purpose | stored procedure | the action should be called intentionally, not hidden behind an event |
| answer a reporting question | query or view | no event-driven enforcement is needed |
| react automatically to a data change that can violate a cross-row or cross-table rule | trigger | the rule must run whenever the event happens |
| make a fairness-sensitive decision about a person or exception | workflow with human review | human judgment and accountable review still matter |

A trigger is justified when all of these are true:

- the rule is clear
- the rule must react automatically to a data change
- a simpler option does not enforce the rule well enough
- the behavior can be tested and explained

If you cannot justify the trigger against alternatives, the trigger probably should not exist.

### Match The Rule To The Event

Triggers are event-driven, so the event list must fit the actual rule.

Ask:

- Can this problem happen on `INSERT`?
- Can it happen on `UPDATE`?
- Can it happen on `DELETE`?
- Which events matter, and which ones do not?

Avoid writing `INSERT, UPDATE, DELETE` by habit. Each extra event expands the automation. That can create side effects, slower troubleshooting, and rules that block work they were never meant to block.

### Main Case: Preventing Invoice Overpayment

Use one bounded case for the rest of the lesson.

Assume a billing system contains these tables:

- `billing.Invoice(InvoiceID, CustomerID, InvoiceTotal, BalanceDue, StatusCode)`
- `billing.Payment(PaymentID, InvoiceID, PaymentDate, PaymentAmount, ReceivedBy)`

The rule is:

`Total payments for one invoice must not exceed InvoiceTotal.`

This rule is a reasonable trigger candidate because:

- it depends on payment changes
- it involves more than one row in `billing.Payment`
- the business wants the invalid change blocked immediately
- a plain query would only report the problem after the fact

This is also a good example of bounded automation. The trigger's only job is to stop overpayments. It is not also updating customer risk scores, closing invoices, sending emails, and changing employee dashboards. Those extra actions would make the automation harder to trust and harder to test.

### How `inserted` And `deleted` Help The Trigger See The Change

Inside a SQL Server trigger, you examine the changed rows through logical tables:

- `inserted` contains new rows for `INSERT`
- `inserted` contains new values for `UPDATE`
- `deleted` contains removed rows for `DELETE`
- `deleted` contains old values for `UPDATE`

For the overpayment rule, the trigger needs to know which invoice IDs were touched by the current statement. That is why the trigger reads invoice IDs from `inserted`. This helps the trigger stay focused on the current change instead of guessing which rows might matter.

### Example Trigger

```sql
CREATE OR ALTER TRIGGER billing.trgPaymentNoOverpayment
ON billing.Payment
AFTER INSERT, UPDATE
AS
BEGIN
    SET NOCOUNT ON;

    IF EXISTS
    (
        SELECT 1
        FROM
        (
            SELECT DISTINCT InvoiceID
            FROM inserted
        ) AS changed
        JOIN billing.Invoice AS i
            ON i.InvoiceID = changed.InvoiceID
        CROSS APPLY
        (
            SELECT SUM(p.PaymentAmount) AS TotalPaid
            FROM billing.Payment AS p
            WHERE p.InvoiceID = changed.InvoiceID
        ) AS totals
        WHERE totals.TotalPaid > i.InvoiceTotal
    )
    BEGIN
        ROLLBACK TRANSACTION;
        THROW 51000, 'Total payments cannot exceed the invoice total.', 1;
    END;
END;
```

Read the trigger in parts:

- `ON billing.Payment` ties the trigger to the table where the event occurs.
- `AFTER INSERT, UPDATE` means the rule is checked after a payment is added or changed.
- `SELECT DISTINCT InvoiceID FROM inserted` limits the work to invoices affected by the current statement.
- `SUM(p.PaymentAmount)` calculates the current total paid for each changed invoice.
- `WHERE totals.TotalPaid > i.InvoiceTotal` identifies a rule violation.
- `ROLLBACK TRANSACTION` and `THROW` block the invalid change and make the problem visible.

### Why `DELETE` Is Not Included

Deleting a payment lowers the total amount paid for an invoice. That action does not create an overpayment problem, so `DELETE` is not part of this trigger.

This is what justified event selection looks like. The event list is part of the design decision. If an event does not belong, leave it out.

### When Another Approach Is Stronger

Not every business rule belongs in a trigger.

Examples:

- If a value must be positive, a `CHECK` constraint is usually stronger because the rule is simple and visible.
- If a billing clerk should run a standard "close invoice" operation, a stored procedure is usually stronger because the action should be called intentionally.
- If leadership wants a list of overdue invoices, a query or view is stronger because reporting is not the same as rule enforcement.
- If a system would automatically send an account to collections the moment a balance becomes overdue, a trigger may be the wrong tool because disputes, hardship arrangements, and fairness-sensitive exceptions often require human review.

The last example matters. Just because the database can automate a consequence does not mean it should. When automation affects a person's access, reputation, employment, service, or financial options, ask whether the rule is truly objective and whether fairness still requires human judgment.

### Testing Expected And Unexpected Behavior

A trigger is not done when it compiles. You need evidence that it behaves correctly.

For this lesson, test at least three things:

1. an expected change that should succeed
2. an unexpected change that should be blocked
3. the resulting table state after each test

Assume `InvoiceID = 3001` has `InvoiceTotal = 500.00` and already has a payment of `200.00`.

Expected behavior test:

```sql
INSERT INTO billing.Payment
    (InvoiceID, PaymentDate, PaymentAmount, ReceivedBy)
VALUES
    (3001, '2026-03-21', 100.00, 'AReed');
```

Expected result:

- the statement succeeds
- total paid becomes `300.00`
- the new payment row remains in the table

Unexpected behavior test:

```sql
INSERT INTO billing.Payment
    (InvoiceID, PaymentDate, PaymentAmount, ReceivedBy)
VALUES
    (3001, '2026-03-21', 350.00, 'AReed');
```

Expected result:

- the statement is blocked
- the error message explains the rule failure
- the attempted row is not left in the table

After each test, verify with a query. Do not assume the rollback happened just because the message looked correct.

```sql
SELECT
    InvoiceID,
    SUM(PaymentAmount) AS TotalPaid
FROM billing.Payment
WHERE InvoiceID = 3001
GROUP BY InvoiceID;
```

### Test For Side Effects, Not Just Rule Checks

A trigger can be logically correct and still be poorly designed if it causes unintended side effects.

Ask:

- Did the trigger block only the invalid change, or did it interfere with unrelated work?
- Does the trigger do one job, or has it become a hidden script that changes multiple business processes?
- Can another developer understand why the trigger fired and what it changed?
- If the trigger fails, can the business explain the outcome to a user or customer?

Bounded automation is accountable automation. If the trigger has too many responsibilities, troubleshooting and fairness both get harder.

### Responsible Automation And Fairness

A trigger acts on behalf of the organization without asking for permission each time. That means the automation should be limited to rules that are clear, testable, and appropriate for automatic enforcement.

When the rule has significant human consequences, ask tougher questions:

- Is the rule objective enough for full automation?
- Could a legitimate exception be treated unfairly?
- Would a review queue be more responsible than an automatic block or penalty?
- Can the organization explain the trigger's behavior honestly and clearly?

A trustworthy database does not only enforce rules. It enforces the right rules in the right way.

## Examples And Case

### Example 1: Expected Versus Unexpected Behavior

For the overpayment trigger, classify each statement before you run it.

1. Insert a `100.00` payment when the invoice already has `200.00` paid against a `500.00` total.
2. Update an existing `150.00` payment to `325.00` when the invoice total is still `500.00`.
3. Delete a `50.00` payment from an invoice.

For each one, answer:

- Should the trigger fire?
- Should the statement succeed or fail?
- What table state should you verify afterward?

### Example 2: What Should Not Be Automated

A company proposes this rule:

`When a customer account becomes 15 days overdue, automatically change StatusCode to Collections.`

Technically, a trigger could do this. That does not make it a strong choice.

Reasons to hesitate:

- the account may be in dispute
- the customer may already have an approved payment plan
- sending an account to collections can affect a person significantly
- fairness and accountable review may matter more than immediate automation

A better design might be a report, work queue, or stored procedure that supports staff review instead of an automatic trigger.

## Guided Practice

Complete these tasks before moving to the assignment.

1. Decide which option is strongest for each rule: constraint, stored procedure, trigger, query/view, or human review workflow.
   - `QuantityOnHand` cannot be negative.
   - Total payments on one invoice cannot exceed the invoice total.
   - Finance staff need a repeatable month-end close routine.
   - An employee should be flagged for discipline after three late arrivals.
2. For the overpayment case, explain why `AFTER INSERT, UPDATE` fits and why `DELETE` does not.
3. Predict expected versus unexpected behavior for these two statements before you run them.

```sql
UPDATE billing.Payment
SET PaymentAmount = 250.00
WHERE PaymentID = 9004;

UPDATE billing.Payment
SET PaymentAmount = 410.00
WHERE PaymentID = 9004;
```

4. Write one sentence describing what you would verify after each test besides the error message.
5. Name one possible side effect you would try to avoid if someone asked to expand the trigger to update invoice status automatically.

## What To Do

Work through the lesson in this order:

1. Read the decision table and explain when a trigger is justified.
2. Study the billing case and trace why the rule belongs to `INSERT` and `UPDATE`.
3. Read the example trigger line by line.
4. Run or trace one allowed change and one blocked change.
5. Verify the resulting table state after each test.
6. Write a short explanation of one rule that should not be automated fully because human judgment or fairness still matters.

If you use AI to draft trigger code or test cases, you are still responsible for verifying the output, correcting weak assumptions, and explaining why the final design is appropriate.

## Assignments

Complete the lesson check in two parts.

### Part A: Trigger Justification

Write a short response that:

- states the business rule
- explains why a trigger is appropriate or inappropriate
- compares the trigger to at least one stronger alternative
- identifies one fairness or accountability concern if the rule affects people directly

### Part B: Trigger Build And Behavior Test

Create one simple trigger for a justified rule or revise the provided overpayment trigger. Then submit:

- the trigger script
- one expected-behavior test
- one unexpected-behavior test
- one verification query showing the resulting table state
- a short explanation of what happened and why

## Deliverables

Submit:

- one SQL file with the trigger and test statements
- one short written explanation covering trigger justification, event choice, expected versus unexpected behavior, and what should not be automated blindly

## Project Checkpoint Or Module Connection

Your final project revision in Lesson 8.3 may force you to change procedural logic after a business-rule change. This lesson prepares you for that work by making you document three things now:

- why the trigger exists
- what events it should respond to
- how you know the behavior is correct

If you cannot defend those choices, the trigger is not ready for a larger project package.

## Wrap-Up

Triggers are powerful because they are automatic. That is also why they require restraint. A good trigger enforces one clear rule at the right event, produces predictable behavior, and is tested against both normal and problematic cases. A poor trigger automates whatever seems convenient, hides logic, and creates side effects no one can explain.

The practical standard for this course is simple: if a trigger is worth building, it is worth justifying, bounding, and testing.
