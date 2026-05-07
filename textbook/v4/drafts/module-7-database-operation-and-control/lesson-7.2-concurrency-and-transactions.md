# Lesson 7.2: Concurrency and Transactions

## Lesson Overview

This lesson explains what can go wrong when more than one person or process works with the same data at nearly the same time. It also explains how transactions protect the database from half-finished work. You will learn how to recognize a concurrency risk, decide when several actions belong in one transaction, and explain what `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK` mean in plain language.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain how concurrent work can create integrity risk in a multi-user database
- identify at least one concrete concurrency risk and its likely impact
- decide when several related actions belong in one transaction
- explain the purpose of `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK`
- justify whether a realistic case should commit or roll back as one unit
- explain isolation at a basic conceptual level as protection against harmful overlap

## Key Terms

- `concurrency`: overlapping database work by more than one user or process
- `transaction`: one logical unit of work whose related changes should succeed together or fail together
- `BEGIN TRANSACTION`: the T-SQL statement that marks the start of a transaction block
- `COMMIT`: the statement that makes a successful transaction permanent
- `ROLLBACK`: the statement that undoes uncommitted work in a transaction
- `isolation`: the database's control of how simultaneous work is separated so one user's in-progress work does not damage another user's result
- `integrity failure`: a state in which the data becomes inaccurate, contradictory, incomplete, or misleading
- `overselling`: promising or allocating more inventory than is actually available because overlapping work was not controlled
- `double-booking`: assigning the same resource, person, or time slot to more than one event when only one should have been allowed

## Readings And Media

- Read this lesson from `Lesson Overview` through `Wrap-Up`.
- Study the warehouse allocation case in `Examples And Case`.
- Read the short T-SQL transaction example in `Core Content` and explain what each part does before you move on.
- Complete the guided practice without outside notes first, then revise if needed.
- No separate video or external media is required for this lesson.

## Core Content

### 1. Concurrency Is A Multi-User Risk, Not Just A Timing Detail

Concurrency means that more than one user or process is working with related data during overlapping time.

That overlap is normal in a real organization. The risk appears when the overlapping work can interfere with data integrity. A concurrency problem is not just "someone made a mistake." It is often a situation where each person follows a reasonable process, but the combined effect creates bad data.

Consider these two situations:

- Low-risk overlap: one employee updates a donor address while another updates a different donor's phone number.
- Higher-risk overlap: two employees try to reserve the same remaining item quantity, seat, or appointment slot.

In the first case, the work touches different records. In the second case, the work competes for the same limited resource. That is where integrity problems become likely.

Common concurrency risks students should be able to name:

- `overselling inventory`: two users each believe the last units are available
- `double-booking a time slot`: two schedulers assign the same technician to the same visit window
- `stale status data`: one table is updated but the related completion or approval status does not match

These are integrity failures because the database no longer describes business reality accurately.

### 2. A Transaction Marks One Unit Of Work

A transaction groups related actions that should succeed together or fail together.

The key question is not "How many SQL statements are there?" The key question is "Do these statements describe one business event that would become misleading if only part of it were saved?"

Use this decision rule:

- If partial completion would leave the database incomplete, contradictory, or misleading, the actions belong in one transaction.

Consider a warehouse allocation process. The system may need to:

1. reduce available inventory
2. insert an allocation record
3. update the order status to `Allocated`

Those steps belong together. If the inventory is reduced but the allocation row is missing, inventory looks lower for no recorded reason. If the allocation row exists but the order status still says `Pending`, the process record tells a conflicting story. The database now contains a business event that only half happened.

Not every pair of statements needs one transaction. If two actions are unrelated and partial completion would not misstate the business event, they may stay separate. Transaction boundaries should follow the logic of the work, not a habit of wrapping everything.

### 3. What `BEGIN TRANSACTION`, `COMMIT`, And `ROLLBACK` Mean

In SQL Server, a simple transaction pattern uses three key commands:

- `BEGIN TRANSACTION`: start the unit of work
- `COMMIT`: keep the work because the whole unit succeeded
- `ROLLBACK`: undo the work because the whole unit should not be kept

Read this example slowly:

```sql
BEGIN TRANSACTION;

UPDATE dbo.InventoryItem
SET QuantityOnHand = QuantityOnHand - 3
WHERE ItemID = 200
  AND QuantityOnHand >= 3;

IF @@ROWCOUNT = 1
BEGIN
    INSERT INTO dbo.OrderAllocation (OrderID, ItemID, QuantityAllocated)
    VALUES (4102, 200, 3);

    UPDATE dbo.SalesOrder
    SET OrderStatus = 'Allocated'
    WHERE OrderID = 4102;

    COMMIT;
END
ELSE
BEGIN
    ROLLBACK;
END;
```

Read the transaction in plain language:

1. start one unit of work
2. try to reduce inventory only if enough stock exists
3. if that required step succeeds, save the allocation record
4. update the order status so it matches the allocation
5. commit only after the full unit makes sense
6. otherwise roll the work back

This example is intentionally small. Its purpose is not to teach every production detail. Its purpose is to show how T-SQL expresses the start, success point, and undo point of one business event.

### 4. When A Case Should Commit

`COMMIT` is appropriate when the intended unit of work is complete and internally consistent.

For the warehouse case, commit makes sense when:

- enough inventory existed
- inventory was reduced correctly
- the allocation row was inserted
- the order status now matches the actual allocation outcome

Commit is not just "the first statement worked." Commit means "the transaction accomplished the business event as intended."

Premature commit is a common mistake. If you commit immediately after reducing inventory, a later failure could leave stock reduced without any matching allocation record or order-status change. The database would preserve a contradiction.

### 5. When A Case Should Roll Back

`ROLLBACK` is appropriate when the full unit of work did not finish correctly or should not be preserved.

For the warehouse case, rollback makes sense when:

- there is not enough inventory to fulfill the request
- one required step fails after the transaction begins
- the final state would leave the order records and inventory records out of sync

Rollback is not wasted effort. It is protection against false records. It prevents the database from saving a partial business event as if it were complete.

### 6. Isolation Explains Why Simultaneous Work Needs Control

Isolation is the broader idea that simultaneous work should be separated enough that one user's in-progress changes do not corrupt another user's result.

Keep the meaning basic in this lesson. You do not need to tune isolation levels here. You do need to understand why isolation matters.

Isolation helps reduce situations such as:

- two employees both claiming the last available item
- one scheduler acting on a time slot that another scheduler is already changing
- one process reading half-finished data from another process and making a bad decision from it

What isolation is not:

- it is not the same as permissions
- it is not the same as backup and recovery
- it is not a reason to lock everything forever

For this lesson, keep the main idea simple:

- isolation helps protect integrity when work overlaps

### 7. A Repeatable Way To Analyze A Concurrency Case

When you see a multi-user situation, use this sequence:

1. identify the records or resources that more than one user or process may touch
2. name the likely integrity failure if the work overlaps badly
3. decide which steps together describe one business event
4. mark where the transaction should begin
5. decide what must be true before the work can commit
6. decide what should trigger rollback instead
7. explain how isolation helps prevent harmful interference

This method matters more than memorizing one code sample. In practice, you will often need to justify why the transaction exists, not just copy a familiar pattern.

## Examples And Case

### Main Case: Warehouse Order Allocation

Use this simplified database context:

- `InventoryItem(ItemID, ItemName, QuantityOnHand)`
- `SalesOrder(OrderID, OrderStatus)`
- `OrderAllocation(OrderID, ItemID, QuantityAllocated)`

Scenario:

- Order `SO-4102` requests 3 units of `ItemID = 200`.
- Only 3 units remain on hand.
- Another employee begins allocating the same item to a different order at nearly the same time.
- The system must reduce inventory, record the allocation, and update the order status.

What could go wrong:

- both employees read the same quantity before either operation is fully protected
- each employee thinks the inventory is still available
- the company oversells the item, creating a promise it cannot keep
- one part of the allocation process succeeds while another part fails, leaving contradictory records

Why one transaction is appropriate:

- the inventory change, allocation row, and order status describe one business event
- partial completion would create misleading data
- the business needs to preserve trust in order status and stock counts

Commit outcome:

- the requested quantity is available and every required step succeeds

Rollback outcome:

- there is not enough stock, or one required step fails before the unit of work is complete

### Contrast Case: Service Dispatch Scheduling

Suppose a service company schedules repair visits. A scheduling action includes:

1. insert the work order
2. assign the technician
3. reserve the required replacement part
4. update the work-order status to `Scheduled`

Ask yourself:

- If step 2 succeeds but step 3 fails, should the database keep the technician assignment anyway?
- If the answer is no because the company does not want "scheduled" work orders without parts reserved, then the steps should commit or roll back together.

This is the same transaction-boundary logic in a different business setting. The exact syntax may change, but the reasoning stays the same.

## Guided Practice

### Practice 1: Name The Concurrency Risk

Read this case:

"Two schedulers try to assign the same technician to the same one-hour time slot for different service calls within seconds of each other."

Answer:

1. What makes this a concurrency risk instead of a single-user data-entry mistake?
2. What integrity failure could happen if the overlap is not controlled?
3. Which concrete name fits the risk best: `double-booking`, `overselling`, or `stale status data`?

### Practice 2: Decide The Transaction Boundary

A student account process includes these actions:

1. insert a tuition payment row
2. update the student's account balance
3. update the invoice status to `Paid`

Answer:

1. Should these actions belong in one transaction?
2. What misleading result could appear if step 1 succeeds but step 3 never happens?
3. What business event is the transaction trying to represent truthfully?

### Practice 3: Fill In The Transaction Words

Complete the missing control statements:

```sql
_____________;

UPDATE dbo.InventoryItem
SET QuantityOnHand = QuantityOnHand - 1
WHERE ItemID = 315
  AND QuantityOnHand >= 1;

IF @@ROWCOUNT = 1
BEGIN
    INSERT INTO dbo.OrderAllocation (OrderID, ItemID, QuantityAllocated)
    VALUES (5201, 315, 1);

    _____________;
END
ELSE
BEGIN
    _____________;
END;
```

Then explain what each missing statement means in plain language.

### Practice 4: Commit Or Roll Back As A Unit

Case A:

- a payment row is inserted
- the student balance is updated
- the invoice status changes to `Paid`

Case B:

- the payment row is inserted
- the balance update fails
- the invoice status still says `Open`

Answer:

1. Which case should end with `COMMIT`?
2. Which case should end with `ROLLBACK`?
3. Why should the result be treated as one unit instead of keeping the successful first step?

## What To Do

1. Read the lesson carefully and make sure you can explain the warehouse case without looking back.
2. Work through the guided practice in order.
3. Check whether your answers name the integrity failure clearly instead of using vague language.
4. Complete the assignment for submission.
5. Revisit the transaction example and explain why the `COMMIT` point appears where it does.

## Assignments

### Assignment 1: Concurrency And Transaction Judgment

Write a short scenario response for one provided multi-user case, such as inventory allocation, scheduling, or payment posting. Your response must:

- identify the main concurrency risk
- name the likely integrity failure in concrete business terms
- state which actions belong in one transaction
- explain the purpose of `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK` for that case
- decide whether the case should end with commit or rollback as a unit
- explain how isolation helps protect the case at a basic conceptual level

## Deliverables

- one short written concurrency-and-transaction analysis
- one completed or annotated T-SQL transaction block
- one plain-language explanation of why the final action should be `COMMIT` or `ROLLBACK`

## Project Checkpoint Or Module Connection

For the Module 7 Operations Decision Memo, identify one multi-step operation in your project database or case scenario that should be wrapped in one transaction. Explain what false story the database could tell if only part of that work were saved. Connect your answer to trustworthy business practice by naming who would be harmed by the contradiction.

## Wrap-Up

Concurrency and transactions matter because real databases serve shared work, not isolated users. A concurrency problem happens when overlapping actions create inaccurate or contradictory data. A transaction protects one business event by grouping related changes so they succeed together or fail together. `BEGIN TRANSACTION` starts that unit, `COMMIT` keeps a successful unit, and `ROLLBACK` undoes a unit that should not be preserved.

These are not just technical commands. They are part of responsible database operation. When a database preserves only truthful, complete business events, it protects organizational trust, reduces avoidable correction work, and serves people more faithfully.
