# Lesson 2.5: Joins

## Lesson overview

Lesson 2.3 taught you how to retrieve rows from one table. Lesson 2.4 taught you how grouping changes result meaning. Lesson 2.5 adds the next major idea: many business questions depend on facts stored in related tables, so you must combine rows correctly before you can interpret the result.

This lesson is not only about making `JOIN` syntax run. It is about understanding why the join is needed, which path connects the tables, and what one joined row actually represents.

## Lesson outcomes

By the end of this lesson, you should be able to:

- explain why a join is needed for a multi-table business question
- identify the join path that connects the needed tables
- write readable beginner joins with `INNER JOIN` and basic `LEFT JOIN` use
- explain what one joined row represents
- diagnose a wrong join that still looks believable
- detect row duplication caused by joining to a detail table
- verify that a join answers the intended business question before trusting the output

## Key terms

- `join`: a way to combine related rows from multiple tables
- `join predicate`: the condition that states how rows match
- `join path`: the relationship route used to move from one needed table to another
- `joined row`: one result row created after matching rows across tables
- `inner join`: returns only rows that find a match on both sides of the join
- `left join`: keeps all rows from the left table even when no matching row exists on the right
- `row duplication`: repeated appearance of one business fact because it matches multiple detail rows
- `row meaning`: the plain-language explanation of what one result row represents

## Readings and media

- Read this lesson from beginning to end.
- Study each worked example and say what one row means before moving on.
- If grouping logic still feels weak, briefly review Lesson 2.4 because duplicate rows often become visible only when you count or summarize.
- If you test the queries in SQL Server, do not stop at "it ran." Check whether the join path and the row meaning answer the business question.

## Core content

### A recurring case for this lesson

Use these tables through most of the lesson:

- `sales.Customer(CustomerID, CustomerName, RegionCode)`
- `sales.[Order](OrderID, CustomerID, SalesRepID, OrderDate, OrderStatus)`
- `sales.OrderLine(OrderLineID, OrderID, ProductID, Quantity, UnitPrice)`
- `sales.Product(ProductID, ProductName, CategoryName)`
- `sales.SalesRep(SalesRepID, SalesRepName)`

Later, one short service case will add:

- `service.ServiceTicket(TicketID, CustomerID, OpenedByEmployeeID, AssignedTechnicianID, TicketStatus)`
- `hr.Employee(EmployeeID, EmployeeName)`

Keep asking one question: what does one output row represent after these tables are joined?

### Why joins are needed

Suppose the business question is:

"List each order with the customer name."

The `sales.[Order]` table may have `OrderID`, `CustomerID`, `SalesRepID`, and `OrderDate`, but not `CustomerName`. The `sales.Customer` table has `CustomerName`, but not the order facts.

No single table answers the question by itself. You need related facts from more than one table, so you need a join.

That gives you the first rule of this lesson:

- use a join when the business question needs columns from related tables
- do not add a join unless the question actually needs it

Unneeded joins create extra risk. A query can become more complex and may even change row counts for no business reason.

### Start with the relationship path, not the SQL

Before you type `INNER JOIN`, identify three things:

1. the starting table
2. the needed destination table
3. the path that connects them

For "List each order with the customer name":

- start table: `sales.[Order]`
- destination table: `sales.Customer`
- path: `sales.[Order].CustomerID -> sales.Customer.CustomerID`

Then write the query:

```sql
SELECT o.OrderID,
       o.OrderDate,
       c.CustomerName
FROM sales.[Order] AS o
INNER JOIN sales.Customer AS c
    ON o.CustomerID = c.CustomerID
ORDER BY o.OrderID;
```

Plain-language row meaning:

"One row represents one order, along with the name of the customer who placed that order."

That row meaning matters as much as the syntax. If you cannot explain the joined row clearly, you should not trust the result yet.

### The joined row takes its meaning from the path and the relationship

Now use a different question:

"List each order with the sales representative who handled it."

```sql
SELECT o.OrderID,
       o.OrderDate,
       r.SalesRepName
FROM sales.[Order] AS o
INNER JOIN sales.SalesRep AS r
    ON o.SalesRepID = r.SalesRepID
ORDER BY o.OrderID;
```

One row now means:

"One row represents one order, along with the sales representative assigned to that order."

Notice what changed:

- the starting table stayed the same
- the destination table changed
- the join path changed
- the business meaning changed

Join syntax is not enough. The path determines what business fact you are attaching to the row.

### Multi-table joins create a more specific row

Suppose the business question is:

"Which products appeared on each order?"

That answer is not stored directly in one place. You need the path:

`sales.[Order] -> sales.OrderLine -> sales.Product`

```sql
SELECT o.OrderID,
       p.ProductName,
       ol.Quantity,
       ol.UnitPrice
FROM sales.[Order] AS o
INNER JOIN sales.OrderLine AS ol
    ON o.OrderID = ol.OrderID
INNER JOIN sales.Product AS p
    ON ol.ProductID = p.ProductID
ORDER BY o.OrderID,
         p.ProductName;
```

Read one row carefully:

"One row represents one order line on one order, including the product on that line and the quantity sold."

That is not the same as "one row per order." Joining to a detail table changed the reporting level.

This is one of the biggest join habits in Module 2:

- joining to a detail table often makes the row more specific
- the more specific row may be correct, but only if it matches the business question

### `LEFT JOIN` helps when missing related rows still matter

Sometimes the business question says, in effect, "Show me all rows from the main table, even if a related row is missing."

Example:

"List all customers and any orders they have placed."

```sql
SELECT c.CustomerID,
       c.CustomerName,
       o.OrderID,
       o.OrderDate
FROM sales.Customer AS c
LEFT JOIN sales.[Order] AS o
    ON c.CustomerID = o.CustomerID
ORDER BY c.CustomerID,
         o.OrderID;
```

This result may include customers whose order columns are `NULL`.

One row means:

"One row represents one customer and one matching order if an order exists; otherwise it represents a customer with no matching order yet."

Use `LEFT JOIN` when unmatched rows on the left side still matter to the question. If the goal is "customers with or without orders," an `INNER JOIN` would silently remove customers who have not ordered yet.

### A wrong join can still look believable

Now consider a service-operations question:

"Which technician is assigned to each open service ticket?"

Available tables:

- `service.ServiceTicket(TicketID, CustomerID, OpenedByEmployeeID, AssignedTechnicianID, TicketStatus)`
- `hr.Employee(EmployeeID, EmployeeName)`

Correct version:

```sql
SELECT t.TicketID,
       e.EmployeeName AS AssignedTechnician,
       t.TicketStatus
FROM service.ServiceTicket AS t
INNER JOIN hr.Employee AS e
    ON t.AssignedTechnicianID = e.EmployeeID
WHERE t.TicketStatus = 'Open'
ORDER BY t.TicketID;
```

Misleading version:

```sql
SELECT t.TicketID,
       e.EmployeeName AS AssignedTechnician,
       t.TicketStatus
FROM service.ServiceTicket AS t
INNER JOIN hr.Employee AS e
    ON t.OpenedByEmployeeID = e.EmployeeID
WHERE t.TicketStatus = 'Open'
ORDER BY t.TicketID;
```

Why the wrong query can fool someone:

- it runs without syntax errors
- it returns real ticket IDs
- it returns real employee names
- the alias `AssignedTechnician` makes the output look polished

But the path is wrong. The bad query answers "Who opened each open ticket?" not "Who is assigned to each open ticket?"

That matters because false join logic can distort workload reporting, delay follow-up, and unfairly judge staff performance. In a business setting, this is not a minor formatting issue. It is a truthfulness problem about service operations and people.

### Row duplication is a reasoning problem, not just an extra-row problem

Suppose the business question is:

"How many orders were closed in March?"

A student writes:

```sql
SELECT COUNT(*) AS ClosedMarchOrderCount
FROM sales.[Order] AS o
INNER JOIN sales.OrderLine AS ol
    ON o.OrderID = ol.OrderID
WHERE o.OrderStatus = 'Closed'
  AND o.OrderDate >= '2026-03-01'
  AND o.OrderDate < '2026-04-01';
```

This query runs, but it is risky. Why?

After joining to `sales.OrderLine`, one order with three line items appears in three joined rows. `COUNT(*)` now counts joined rows, not necessarily orders.

If the question is about orders, the result can be inflated by row duplication.

Safer correction if the join is not needed:

```sql
SELECT COUNT(*) AS ClosedMarchOrderCount
FROM sales.[Order] AS o
WHERE o.OrderStatus = 'Closed'
  AND o.OrderDate >= '2026-03-01'
  AND o.OrderDate < '2026-04-01';
```

If the product table is needed for a later filter, then the repair may be:

```sql
SELECT COUNT(DISTINCT o.OrderID) AS ClosedMarchOrderCount
FROM sales.[Order] AS o
INNER JOIN sales.OrderLine AS ol
    ON o.OrderID = ol.OrderID
WHERE o.OrderStatus = 'Closed'
  AND o.OrderDate >= '2026-03-01'
  AND o.OrderDate < '2026-04-01';
```

The important idea is not the exact fix. The important idea is this:

- after a join, verify what is being counted
- make sure the row meaning still matches the business question

### A join verification routine

Use this routine before you trust a multi-table result:

1. Restate the business question in plain language.
2. Name the starting table and each additional table needed.
3. State the join path column by column.
4. Read one result row aloud in plain language.
5. Ask whether the join made the row more detailed than the question intended.
6. Check whether `INNER JOIN` is wrongly removing needed unmatched rows.
7. If counting or summarizing, ask what the query is actually counting after the join.
8. Spot-check one known record or one small set of IDs to confirm the path.

For example, for the ticket-assignment report, your check might sound like this:

- The question is about assigned technicians, not ticket creators.
- The path must therefore use `AssignedTechnicianID`.
- One row should represent one open ticket and the employee assigned to work it.
- A quick spot-check on one known ticket should confirm the employee matches the operational record.

That routine is what protects you from believable but wrong output.

## Examples and case

### Example 1: one row per order with customer name

Business question: "List each order with the customer name."

```sql
SELECT o.OrderID,
       c.CustomerName
FROM sales.[Order] AS o
INNER JOIN sales.Customer AS c
    ON o.CustomerID = c.CustomerID
ORDER BY o.OrderID;
```

Meaning:

- one row represents one order and its customer

### Example 2: one row per order line with product details

Business question: "Which products appeared on each order?"

```sql
SELECT o.OrderID,
       p.ProductName,
       ol.Quantity
FROM sales.[Order] AS o
INNER JOIN sales.OrderLine AS ol
    ON o.OrderID = ol.OrderID
INNER JOIN sales.Product AS p
    ON ol.ProductID = p.ProductID
ORDER BY o.OrderID,
         p.ProductName;
```

Meaning:

- one row represents one product line on one order

### Example 3: believable wrong join in service reporting

Business question: "Which technician is assigned to each open ticket?"

Misleading version joins `OpenedByEmployeeID` to `hr.Employee`.

Why it is misleading:

- it returns real names
- it still looks like a clean report
- it uses the wrong relationship path, so it answers a different question

Correct version joins `AssignedTechnicianID` to `hr.Employee`.

## Guided practice

### Guided Practice A: explain why the join is needed

Business question:

"Show each closed order with the customer name and the sales representative name."

Answer these before writing SQL:

1. Which table should you start from?
2. Which other tables are needed?
3. What is the join path to each one?
4. What should one row represent in the final result?

### Guided Practice B: choose the correct join path

You need a report that answers:

"Which products did each customer order?"

Choose the correct path and explain why:

1. `sales.Customer -> sales.[Order] -> sales.OrderLine -> sales.Product`
2. `sales.Customer -> sales.SalesRep -> sales.Product`
3. `sales.Customer -> sales.OrderLine -> sales.Product`

Your explanation should name the missing or incorrect relationship in the wrong options.

### Guided Practice C: diagnose the believable wrong join

Read this query:

```sql
SELECT t.TicketID,
       e.EmployeeName,
       t.TicketStatus
FROM service.ServiceTicket AS t
INNER JOIN hr.Employee AS e
    ON t.OpenedByEmployeeID = e.EmployeeID
WHERE t.TicketStatus = 'Open';
```

The business question is "Which technician is assigned to each open ticket?"

Answer these:

1. What does one row in this query actually represent?
2. Why might the output still look believable?
3. Which column should be used instead?
4. What false conclusion could a manager make from this bad join?

### Guided Practice D: detect row duplication

Read this query:

```sql
SELECT o.CustomerID,
       COUNT(*) AS ClosedOrderCount
FROM sales.[Order] AS o
INNER JOIN sales.OrderLine AS ol
    ON o.OrderID = ol.OrderID
WHERE o.OrderStatus = 'Closed'
GROUP BY o.CustomerID;
```

The business question is "How many closed orders has each customer placed?"

Answer these:

1. What does one joined row represent before the `GROUP BY` happens?
2. Why can `COUNT(*)` overstate the number of orders?
3. What repair would you make?
4. How would you explain the problem to a business reader in plain language?

### Guided Practice E: decide between `INNER JOIN` and `LEFT JOIN`

Business question:

"List all customers and any orders they have placed so the sales team can see both active buyers and customers with no orders yet."

Answer:

1. Should the query use `INNER JOIN` or `LEFT JOIN`?
2. Why would the other choice misstate the business situation?
3. What should one row mean in the correct result?

## What to do

1. Read each example slowly and say what one row means.
2. Complete Guided Practice A through E.
3. Draft one multi-table query of your own for a business question.
4. Write the join path in plain language before or beside the SQL.
5. Run the query if you have SQL Server access.
6. Check whether the joined row meaning matches the business question.
7. If the query includes counting or summarizing, verify that the join did not change what is being counted.
8. If you use AI to draft the join, verify the path and row meaning yourself.

## Assignments

Submit one short SQL worksheet or Markdown response for Lesson 2.5 that includes:

- one correct `INNER JOIN` query with a plain-language explanation of what one row represents
- one join-path explanation for a multi-table business question
- one diagnosis of a believable wrong join
- one row-duplication diagnosis and repair
- one short explanation of when `LEFT JOIN` is needed instead of `INNER JOIN`

## Deliverables

- one correct join query
- one plain-language row-meaning explanation
- one critique of a wrong-but-believable join
- one repair of a row-duplication problem
- one brief verification note showing how the student knows the join answers the intended business question

## Project checkpoint or module connection

The Module 2 `Query Verification Lab` will not reward a query only because it runs. It will reward your ability to explain whether the join path is correct, whether one row means what the business reader thinks it means, and whether duplicate or missing rows have changed the answer.

If you are working with a project case, identify one future report that will need multiple tables. Write down the path now, then ask which wrong join would still look believable to a hurried manager. That question is part of trustworthy reporting.

## Wrap-up

Joins are how SQL retrieves related facts across tables, but the real skill is not typing `INNER JOIN`. The real skill is choosing the right path and interpreting the meaning of the rows that come back.

A correct join answers the intended business question. A bad join can still look believable, especially when it returns real names, real products, or real ticket numbers. Keep asking:

- Why is this join needed?
- What path connects these tables?
- What does one joined row represent?
- How do I know this output answers the real question instead of a different one?

Those habits will keep mattering in Lesson 2.6, where you will reorganize joined logic into clearer steps with common table expressions.
