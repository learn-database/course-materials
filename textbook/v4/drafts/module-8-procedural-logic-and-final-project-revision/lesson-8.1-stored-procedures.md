# Lesson 8.1: Stored Procedures

## Lesson Overview

This lesson introduces stored procedures as a way to package repeated database work into a named, reusable operation. The goal is not to treat every useful query as a procedure. The goal is to decide when a procedure solves a real problem, when a plain query is enough, and how to test the behavior before trusting the database with that work.

By this point in the course, you have already written queries, created tables and constraints, built views, and studied operational controls such as transactions and permissions. Module 8 now moves into justified automation. That means asking not only "Can this be automated?" but also "Should it be automated, and how will we keep it bounded and accountable?"

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain what problem a stored procedure solves
- distinguish a stored procedure from a one-time plain query
- explain how parameters make a procedure reusable
- create and execute a simple parameterized stored procedure in T-SQL
- describe expected behavior and basic tests for a stored procedure
- justify when a task should stay a query or remain under human judgment instead of becoming a procedure

## Key Terms

- `stored procedure`: a named set of SQL statements stored in the database and executed as a unit
- `parameter`: an input value passed into a procedure when it runs
- `EXEC`: the T-SQL command used to execute a stored procedure
- `expected behavior`: the result the procedure should produce for a given input or situation
- `reusable operation`: a task the database needs to perform repeatedly with consistent logic
- `bounded automation`: automation kept narrow enough to stay reviewable, testable, and accountable

## Readings and Media

- Read this full lesson.
- Study the billing-office case in the `Examples and Case` section.
- Review both procedure examples and the testing checklist.
- No additional video is required for this lesson.

## Core Content

### What problem does a stored procedure solve?

A stored procedure solves the problem of repeated database work that should be performed in a consistent way. Instead of rewriting the same logic each time, you create a named object once and execute it whenever that task is needed.

In SQL Server, a procedure can:

- return a consistent result set
- accept changing input values through parameters
- package several SQL statements into one repeatable operation
- support controlled execution by giving users or applications one stable entry point

The important phrase is "repeatable operation." If the work does not repeat, or if it is simple enough to stay as a one-time query, a procedure may not add value.

### When a plain query is enough

Not every useful SQL statement needs to become a stored procedure.

A plain query is often enough when:

- the need is one-time or infrequent
- the logic is short and easy to read directly
- the user is exploring data rather than performing a standard operation
- wrapping the logic in a procedure would add naming, maintenance, and testing overhead without clear benefit

Example of a plain query that may be enough:

```sql
SELECT InvoiceID,
       InvoiceDate,
       BalanceDue
FROM billing.Invoice
WHERE CustomerID = 42
  AND BalanceDue > 0
ORDER BY InvoiceDate;
```

If an analyst needs this answer once while investigating an account, the query itself may be the right tool. Turning every one-time lookup into a procedure would create unnecessary clutter.

### When a stored procedure is appropriate

A stored procedure becomes more useful when the same task must be performed repeatedly, especially when the input changes from one execution to the next.

Use a stored procedure when these conditions are present:

- the operation has a clear business purpose
- the same logic will be reused
- parameters can make the operation flexible without rewriting the SQL
- the expected behavior should remain predictable each time

Stored procedures are especially useful for:

- repeatable reports with changing filter values
- standard data-entry or update operations
- multi-step actions that should run together
- application features that need one stable database operation

That does not mean a procedure is always better than a view, constraint, query, or human review step. Choose the smallest reliable tool that fits the job.

### How parameters make reuse possible

Parameters allow a procedure to keep the same logic while changing the input values. That is what turns a fixed script into a reusable operation.

Here is a simple parameterized reporting procedure:

```sql
CREATE OR ALTER PROCEDURE billing.uspGetOpenInvoicesByCustomer
    @CustomerID INT
AS
BEGIN
    SET NOCOUNT ON;

    SELECT InvoiceID,
           InvoiceDate,
           BalanceDue
    FROM billing.Invoice
    WHERE CustomerID = @CustomerID
      AND BalanceDue > 0
    ORDER BY InvoiceDate;
END;
```

You execute it like this:

```sql
EXEC billing.uspGetOpenInvoicesByCustomer @CustomerID = 42;
```

Why this procedure is appropriate:

- the billing staff may need the same lookup many times
- the logic stays the same while the `CustomerID` changes
- the procedure gives the database one clear, reusable operation

Why this same task might still remain a query in another situation:

- if only one analyst runs it once
- if the logic is still changing during exploration
- if reuse has not been established yet

### Procedures can package more than one statement

Some procedures do more than return rows. They package a repeated business event into one controlled operation.

The example below records a payment and updates the invoice balance in one procedure:

```sql
CREATE OR ALTER PROCEDURE billing.uspApplyPayment
    @InvoiceID INT,
    @PaymentDate DATE,
    @PaymentAmount DECIMAL(10, 2),
    @ReceivedBy NVARCHAR(60)
AS
BEGIN
    SET NOCOUNT ON;

    BEGIN TRY
        BEGIN TRANSACTION;

        IF @PaymentAmount <= 0
        BEGIN
            THROW 50001, 'PaymentAmount must be greater than 0.', 1;
        END;

        IF NOT EXISTS
        (
            SELECT 1
            FROM billing.Invoice
            WHERE InvoiceID = @InvoiceID
        )
        BEGIN
            THROW 50002, 'InvoiceID was not found.', 1;
        END;

        INSERT INTO billing.Payment
            (InvoiceID, PaymentDate, PaymentAmount, ReceivedBy)
        VALUES
            (@InvoiceID, @PaymentDate, @PaymentAmount, @ReceivedBy);

        UPDATE billing.Invoice
        SET BalanceDue = BalanceDue - @PaymentAmount
        WHERE InvoiceID = @InvoiceID;

        COMMIT TRANSACTION;
    END TRY
    BEGIN CATCH
        IF @@TRANCOUNT > 0
        BEGIN
            ROLLBACK TRANSACTION;
        END;

        THROW;
    END CATCH;
END;
```

This procedure is justified because:

- recording a payment is a repeated operation
- the inputs vary each time
- the insert and update belong to the same business event
- the database should either complete the event or reject it cleanly

This procedure is still bounded:

- it performs one clear business operation
- it validates basic inputs
- it does not try to automate dispute handling, exceptions, or judgment-heavy billing decisions

### What should not become a stored procedure

Do not use a stored procedure just because the database can do something automatically.

Avoid turning a task into a procedure when:

- a plain query already solves the problem cleanly
- a view or constraint is the more direct solution
- the task depends on human judgment or fairness review
- the business rule is not stable enough to automate yet

Example: a billing manager may decide whether to waive a late fee after reviewing a customer complaint. That decision may involve context, policy exceptions, and fairness concerns. A procedure could support the final approved change, but it should not replace the judgment process itself.

This is where bounded automation matters. A procedure can carry delegated authority only for work that is clear, repeatable, and reviewable.

### How to test a stored procedure

A stored procedure is not finished when it compiles. It is finished when you can explain what it should do and show evidence that it does that.

Start with expected behavior:

- What should happen for a normal input?
- What should happen if the input is valid but returns no matching rows?
- What should happen if the input is invalid or breaks a stated rule?

Then test deliberately:

1. choose controlled input values
2. state the expected behavior before execution
3. run the procedure with `EXEC`
4. inspect result sets, messages, and changed data
5. compare actual behavior to expected behavior
6. note any mismatch that needs correction

For `billing.uspGetOpenInvoicesByCustomer`, basic tests could include:

- `@CustomerID = 42` for a customer with known open invoices: the procedure should return only that customer's open invoices
- `@CustomerID = 77` for a customer with no open invoices: the procedure should return zero rows, not an error
- `@CustomerID = NULL` if the design allows the call: the behavior should be documented and checked, not guessed

For `billing.uspApplyPayment`, basic tests could include:

- a valid payment for an existing invoice: the payment row should be inserted and the invoice balance should decrease
- a negative payment amount: the procedure should raise an error and leave the data unchanged
- an unknown `InvoiceID`: the procedure should raise an error and leave the data unchanged

Testing is part of responsible automation. If you delegate authority to the database, you are responsible for knowing how that authority behaves.

## Examples and Case

### Main Case: Small Business Billing Office

Bright Path Services sends invoices to customers each week. Staff members need two kinds of database help:

- they frequently check open invoices by customer while answering account questions
- they record customer payments throughout the day

The office manager wants consistency, but she does not want the database to make judgment calls about disputed charges, customer hardship, or exception handling.

This case is a good fit for Lesson 8.1 because it separates three kinds of work:

- one-time lookup work that may stay a query
- repeated operational work that may justify a procedure
- judgment-heavy work that should stay under human review

### Example 1: Plain Query or Procedure?

Compare these two needs:

1. A supervisor asks once for a list of all invoices above `$5,000` from last month.
2. Billing staff look up open invoices by customer dozens of times each week.

The first need can stay a plain query because it is a one-time question.

The second need is a stronger case for a procedure because:

- the task repeats
- the input changes
- the logic should stay consistent

The question is not "Can I make a procedure?" The question is "What problem am I solving by making one?"

### Example 2: Expected Behavior Before Execution

Suppose you plan to run:

```sql
EXEC billing.uspApplyPayment
    @InvoiceID = 1054,
    @PaymentDate = '2026-04-15',
    @PaymentAmount = 200.00,
    @ReceivedBy = 'KPatel';
```

Before running it, write the expected behavior:

- a new row should appear in `billing.Payment`
- the invoice with `InvoiceID = 1054` should have its `BalanceDue` reduced by `200.00`
- no other invoice should change

Now compare that with this test:

```sql
EXEC billing.uspApplyPayment
    @InvoiceID = 1054,
    @PaymentDate = '2026-04-15',
    @PaymentAmount = -25.00,
    @ReceivedBy = 'KPatel';
```

Expected behavior:

- the procedure should raise an error
- no payment row should be inserted
- the invoice balance should remain unchanged

That is expected-behavior reasoning. You are not just checking whether SQL Server displays a message. You are checking whether the database acted the way the business rule said it should.

## Guided Practice

### 1. Decide what tool fits

For each task, decide whether it is best handled as a plain query, a stored procedure, or a human-reviewed step that should not be automated directly.

- A manager wants a one-time list of overdue invoices for a board meeting.
- A clerk looks up open invoices by customer throughout the day.
- A billing specialist may waive a late fee after reviewing a dispute and supporting notes.
- An application records approved payments many times each day.

Write one sentence of justification for each answer.

### 2. Identify the parameter need

A team keeps rerunning the same open-invoice lookup for different customers. Answer these questions:

- What should stay the same in the logic?
- What should become a parameter?
- Why would a procedure help more than copying and editing the SQL each time?

### 3. Plan three tests

For one procedure idea of your own, list:

- one normal test case
- one no-match or boundary test case
- one invalid-input or blocked case if the procedure enforces a rule

For each test, state the expected behavior in one sentence.

## What to Do

1. Read the full lesson and study both procedure examples.
2. Complete the guided practice.
3. Draft one simple procedure decision for your project or a provided case.
4. Write expected behavior for at least three tests before you run anything.

## Assignments

### Assignment 1: Procedure Justification Check

Read this scenario:

North Ridge Outfitters keeps customer, invoice, and payment data in SQL Server. One analyst needs a one-time list of invoices above `$10,000` for an audit question. Meanwhile, the accounts-receivable team checks open invoices by customer every day, and an internal application records approved payments throughout the week.

In `200` to `300` words:

- identify which task should stay a plain query
- identify which task should become a stored procedure
- identify any task that still requires human judgment before automation
- justify each choice in business and technical terms

AI may help you brainstorm options, but your submission must explain the choice logic and the expected behavior in your own words.

### Assignment 2: Draft and Test a Simple Stored Procedure

Create one simple stored procedure for your project schema or an instructor-provided schema.

Requirements:

- use at least one parameter
- state the business purpose of the procedure
- execute at least three tests
- include expected behavior for each test
- explain whether the procedure is the right tool or only a temporary draft

Your procedure may be read-only or data-changing. If it changes data, your tests must confirm the data change or non-change, not just show that the procedure ran.

## Deliverables

- one short justification response for Assignment 1
- one T-SQL script for Assignment 2
- one testing log or table showing:
  - test input
  - expected behavior
  - actual behavior
  - whether the result matched expectations

## Project Checkpoint or Module Connection

Look at your final-project database or case design and name:

- one repeated operation that probably should become a stored procedure
- one task that should remain a plain query
- one decision that should remain under human review instead of being automated

This checkpoint matters because Module 8 is about justified automation, not automation for its own sake. A trustworthy project package makes the boundary visible.

## Wrap-Up

Stored procedures are useful when they solve a real repetition problem, accept clear inputs, and produce predictable behavior. They are not a reward for writing more SQL. They are a design choice.

In Module 8, that design choice carries responsibility. If a procedure exists, you should be able to explain why it belongs, what authority it has been given, and how you tested that authority. The next lesson extends that reasoning to triggers, where the automation boundary becomes even more important.
