# Lesson 2.6: Common Table Expressions

## Lesson overview

In Lesson 2.4, you learned to summarize rows with aggregates and grouping. In Lesson 2.5, you learned to combine related tables with joins. This lesson builds on both skills by showing how to organize a longer query into readable stages.

A common table expression, or CTE, is useful when a query has a meaningful intermediate result that deserves its own name. The point is not to make SQL look advanced. The point is to make business logic easier to read, verify, and revise.

## Lesson outcomes

By the end of this lesson, you should be able to:

- explain what problem a nonrecursive CTE solves in readable query design
- rewrite a longer working query using a nonrecursive CTE
- explain what rows the intermediate result contains before interpreting the final result
- compare an original query and a CTE rewrite and judge whether readability improved
- verify that a CTE rewrite still answers the original business question

## Key terms

- **common table expression (CTE):** a named temporary result set defined for the next statement
- **nonrecursive CTE:** a CTE that does not refer to itself
- **intermediate result:** a meaningful set of rows produced before the final result
- **scope:** where a named query object can be used
- **readability:** how easy it is to follow and verify a query
- **verification:** checking whether the query logic and output truly match the business question

## Readings and media

- Read this lesson from beginning to end.
- Study the worked SQL examples and the explanations of what each intermediate result contains.
- If result-set thinking still feels abstract, briefly review your notes from Lesson 2.2.
- If grouped summaries or joins feel shaky, review Lessons 2.4 and 2.5 before starting the guided practice.

## Core content

### The problem a CTE solves

Sometimes a SQL query works, but the logic is packed into one dense statement. When that happens, it becomes harder to answer questions such as these:

- What is the first meaningful result set in this query?
- What does one row in that intermediate step represent?
- Where is the final threshold or business rule actually applied?
- If the report is wrong, which part of the logic should I inspect first?

A CTE helps when there is a natural first step that can stand on its own. The CTE gives that step a name, then the next statement uses it to finish the report.

Basic pattern:

```sql
WITH CteName AS (
    SELECT ...
    FROM ...
    WHERE ...
)
SELECT ...
FROM CteName;
```

Read this pattern in two moves:

1. Build the named intermediate result.
2. Use that intermediate result in the next statement.

That is why a CTE is mainly a readability tool in this lesson. It helps you reason through multi-step retrieval without changing the business question.

### Start with a working query

Do not begin with `WITH` just because the syntax exists. Start with a query that already answers the business question. Then ask whether part of the query deserves a clear name.

Suppose a sales manager asks:

"Which customers generated at least `1000` in closed-order sales, and how many closed orders did each customer place?"

One working version is:

```sql
SELECT c.CustomerName,
       s.ClosedOrderCount,
       s.ClosedOrderSales
FROM (
    SELECT o.CustomerID,
           COUNT(*) AS ClosedOrderCount,
           SUM(o.OrderTotal) AS ClosedOrderSales
    FROM sales.[Order] AS o
    WHERE o.OrderStatus = 'Closed'
    GROUP BY o.CustomerID
) AS s
INNER JOIN sales.Customer AS c
    ON s.CustomerID = c.CustomerID
WHERE s.ClosedOrderSales >= 1000
ORDER BY s.ClosedOrderSales DESC;
```

This query may already be correct. The question is not "Can it run?" The question is "Can another reader explain the logic confidently?"

### Identify the intermediate result before the final result

Look at the inner query by itself:

```sql
SELECT o.CustomerID,
       COUNT(*) AS ClosedOrderCount,
       SUM(o.OrderTotal) AS ClosedOrderSales
FROM sales.[Order] AS o
WHERE o.OrderStatus = 'Closed'
GROUP BY o.CustomerID;
```

Before you talk about the final report, explain what this intermediate result contains.

Each row represents:

- one customer
- only closed orders for that customer
- the number of closed orders for that customer
- the total sales amount from those closed orders

That explanation matters. If you cannot describe the intermediate result accurately, you cannot verify the final result confidently. This is also where CTEs become useful: the summary step is meaningful enough to deserve a name.

### Rewrite the query with a CTE

```sql
WITH ClosedOrderSummary AS (
    SELECT o.CustomerID,
           COUNT(*) AS ClosedOrderCount,
           SUM(o.OrderTotal) AS ClosedOrderSales
    FROM sales.[Order] AS o
    WHERE o.OrderStatus = 'Closed'
    GROUP BY o.CustomerID
)
SELECT c.CustomerName,
       s.ClosedOrderCount,
       s.ClosedOrderSales
FROM ClosedOrderSummary AS s
INNER JOIN sales.Customer AS c
    ON s.CustomerID = c.CustomerID
WHERE s.ClosedOrderSales >= 1000
ORDER BY s.ClosedOrderSales DESC;
```

Now the logic is easier to read in order:

1. `ClosedOrderSummary` creates one summary row per customer for closed orders.
2. The outer query joins those summary rows to customer names.
3. The outer query keeps only customers whose closed-order sales are at least `1000`.
4. The outer query sorts the report from highest to lowest closed-order sales.

The CTE did not change the business question. It changed the organization.

### Why naming matters

A CTE only helps if the name tells the reader what the rows mean.

Stronger:

- `ClosedOrderSummary`
- `OpenInvoiceBalance`
- `RepQuarterSales`

Weaker:

- `Temp1`
- `StepA`
- `DataSet`

Weak names force the reader to reopen the SQL and rediscover the logic. Strong names shorten that work.

### Verification habits for CTEs

In this course, a readable query is also a more verifiable query. Use these habits after you write a CTE:

1. Say what one row in the CTE represents.
2. Confirm that the CTE includes the right filters and grouping logic.
3. Confirm that the outer query applies the final business rule in the right place.
4. Compare the CTE rewrite to the original business question.
5. If possible, inspect the intermediate result separately while testing.

For the sales example, the verification check sounds like this:

- The CTE should include only closed orders.
- The CTE should produce one row per customer.
- The outer query should apply the `1000` sales threshold after the summary is available.
- The final query should show customer names, closed-order count, and closed-order sales for only the qualifying customers.

### When a CTE helps and when it does not

A CTE helps when:

- the query has a real intermediate result worth naming
- the named step makes the final query easier to explain
- separating the stages makes verification easier

A CTE does not help much when:

- the original query is already short and clear
- the CTE name hides the meaning
- the rewrite adds lines without clarifying the logic

This is why you should compare readability, not just syntax. "It uses `WITH`" is not a strong reason. "It isolates the grouped summary so I can verify it before the customer join" is a strong reason.

### Scope and lesson boundary

A nonrecursive CTE exists only for the next statement. It does not become a permanent database object, and it cannot be reused by later independent statements.

This lesson stays with nonrecursive CTEs used for readable `SELECT` queries. Recursive CTEs are a different topic and are outside the scope of Lesson 2.6.

## Examples and case

### Case 1: customer sales threshold report

Business question:

"Which customers generated at least `1000` in closed-order sales, and how many closed orders did each customer place?"

Available tables:

- `sales.Customer(CustomerID, CustomerName, RegionCode)`
- `sales.[Order](OrderID, CustomerID, OrderStatus, OrderTotal, OrderDate)`

Best intermediate result:

- one row per customer
- closed orders only
- count of closed orders
- total sales from closed orders

Why this is a good CTE case:

- the summary step has clear business meaning
- the final query has a distinct second step
- you can verify the summary before attaching customer names and the sales threshold

### Case 2: open invoice follow-up list

Business question:

"Which customers currently have more than `5000` in unpaid invoices, and what is the oldest unpaid invoice date for each one?"

A readable CTE version might look like this:

```sql
WITH OpenInvoiceSummary AS (
    SELECT i.CustomerID,
           SUM(i.InvoiceBalance) AS TotalOpenBalance,
           MIN(i.InvoiceDate) AS OldestOpenInvoiceDate
    FROM accounting.Invoice AS i
    WHERE i.InvoiceStatus = 'Open'
    GROUP BY i.CustomerID
)
SELECT c.CustomerName,
       s.TotalOpenBalance,
       s.OldestOpenInvoiceDate
FROM OpenInvoiceSummary AS s
INNER JOIN sales.Customer AS c
    ON s.CustomerID = c.CustomerID
WHERE s.TotalOpenBalance > 5000
ORDER BY s.TotalOpenBalance DESC;
```

Explain the intermediate result before the final result:

- one row per customer
- open invoices only
- total unpaid balance per customer
- oldest open invoice date per customer

This kind of report affects who receives collection follow-up or account review. Clear structure matters because hidden logic can misstate who needs action.

## Guided practice

### Guided Practice A: explain the intermediate result

Read this CTE and answer the question that follows.

```sql
WITH RepQuarterSales AS (
    SELECT o.SalesRepID,
           COUNT(*) AS ClosedOrderCount,
           SUM(o.OrderTotal) AS ClosedQuarterSales
    FROM sales.[Order] AS o
    WHERE o.OrderStatus = 'Closed'
      AND o.OrderDate >= '2026-01-01'
      AND o.OrderDate < '2026-04-01'
    GROUP BY o.SalesRepID
)
SELECT r.SalesRepName,
       q.ClosedOrderCount,
       q.ClosedQuarterSales
FROM RepQuarterSales AS q
INNER JOIN sales.SalesRep AS r
    ON q.SalesRepID = r.SalesRepID
WHERE q.ClosedQuarterSales >= 25000
ORDER BY q.ClosedQuarterSales DESC;
```

Before you explain the final report, answer this:

1. What does one row in `RepQuarterSales` represent?
2. Which rows from `sales.[Order]` are included in that result?
3. Which part of the final business rule is still left for the outer query?

### Guided Practice B: complete the rewrite

Rewrite the following dense query as a CTE by filling in the blanks.

```sql
WITH ____________________ AS (
    SELECT i.CustomerID,
           SUM(i.InvoiceBalance) AS TotalOpenBalance,
           MIN(i.InvoiceDate) AS OldestOpenInvoiceDate
    FROM accounting.Invoice AS i
    WHERE ____________________
    GROUP BY ____________________
)
SELECT c.CustomerName,
       s.TotalOpenBalance,
       s.OldestOpenInvoiceDate
FROM ____________________ AS s
INNER JOIN sales.Customer AS c
    ON s.CustomerID = c.CustomerID
WHERE ____________________
ORDER BY s.TotalOpenBalance DESC;
```

Check yourself against this standard:

- the CTE name should describe the rows it returns
- the filter inside the CTE should match the unpaid-invoice logic
- the grouping should produce one row per customer
- the outer query should apply the final threshold

### Guided Practice C: judge readability claims

For each statement, decide whether it is a strong reason or a weak reason for using a CTE.

1. "The rewrite is better because `OpenInvoiceSummary` tells me what the intermediate rows contain."
2. "The rewrite is better because CTEs are more advanced than subqueries."
3. "The rewrite is clearer because I can verify the summary logic before I inspect the customer join."
4. "The rewrite is better because it has more lines and more whitespace."

### Guided Practice D: correct the misconception

Correct this statement in one or two sentences:

"After I define a CTE once, I can reuse it in the next several `SELECT` statements because it acts like a temporary table in the database."

Your correction should mention one-statement scope.

## What to do

1. Read the worked examples and the explanation of each intermediate result.
2. Complete Guided Practice A through D.
3. Take one grouped or joined query from earlier Module 2 work and rewrite it with a nonrecursive CTE.
4. Write a brief explanation of what the CTE returns before you explain the final result.
5. Compare your original query and revised query and decide whether readability actually improved.

## Assignments

Submit one SQL worksheet or Markdown response that includes:

- the original working query
- the nonrecursive CTE rewrite
- a two- to four-sentence explanation of the intermediate result
- a short verification note explaining how you know the rewrite still answers the business question
- a short readability comparison explaining whether the CTE improved the query

## Deliverables

- one correct nonrecursive CTE rewrite
- one explanation of the intermediate result before the final result
- one verification note tied to the business question
- one readability comparison using specific reasons

## Project checkpoint or module connection

The Module 2 assessment pattern asks you to verify query meaning, not just produce SQL that runs. If you are building queries for your project case, identify one report where naming an intermediate result would help another reviewer inspect the logic. Keep that example for the module's query-verification work.

Also ask yourself which fields in your report deserve extra care because they affect follow-up actions, fairness, privacy, or customer treatment. Clear query structure helps you tell the truth about those results.

## Wrap-up

A nonrecursive CTE is a readability and reasoning tool. It is useful when a query has a meaningful intermediate result that should be named before the final step is applied. In this lesson, the goal is not advanced syntax. The goal is clearer business logic.

As you move into later query verification work, keep asking two questions:

- What does the intermediate result actually contain?
- Does naming that result make the final query easier to verify against the business question?
