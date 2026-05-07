# Lesson 2.4: Aggregates and Grouping

## Lesson overview

Lesson 2.3 taught you how to retrieve detail rows from one table. Lesson 2.4 changes the kind of question you ask. Instead of listing orders one by one, you will summarize orders into counts, totals, averages, and grouped reports.

This lesson stays on one table on purpose. You need to see what summarization does to result meaning before joins make the row structure more complicated.

## Lesson outcomes

By the end of this lesson, you should be able to:

- explain the difference between a detail-level question and a summary-level question
- use common aggregate functions to answer summary questions
- explain what one row means before grouping and after grouping
- use `GROUP BY` to make one row represent the intended reporting group
- decide whether a condition belongs in `WHERE` or `HAVING`
- diagnose and repair a grouped query that gives a misleading business report

## Key terms

- Aggregate function: a function that summarizes many rows into one value
- Detail row: a result row that still represents one original record
- Group: a set of rows collected together because they share the same grouped value
- Summary row: a result row that represents a whole group instead of one original record
- Reporting level: what one row in the result set means
- `GROUP BY`: the clause that defines the groups
- `HAVING`: the clause that filters groups after aggregation

## Readings and media

- Read this lesson from top to bottom.
- Read each SQL example slowly and state what one row means.
- If set-based thinking still feels weak, briefly review Lesson 2.2 before doing the practice.
- If you test the queries in SQL Server, compare the result meaning to the business question instead of checking only whether the query runs.

## Core content

### A recurring case for this lesson

Use this one-table reporting case throughout the lesson:

`sales.[Order]`

- `OrderID`
- `CustomerID`
- `SalesRepID`
- `OrderDate`
- `OrderStatus`
- `OrderTotal`

The table name is less important than the reporting logic. Keep asking one question: what does one row in this result represent?

### 1. Detail rows and summary rows answer different questions

Start with a detail query:

```sql
SELECT OrderID,
       CustomerID,
       OrderStatus,
       OrderTotal
FROM sales.[Order]
ORDER BY OrderID;
```

Each output row still represents one stored order. That makes this a detail-level result.

Now compare it to:

```sql
SELECT COUNT(*) AS OrderCount
FROM sales.[Order];
```

This result no longer lists one row per order. It returns one summary value for the whole table. The question changed from "Show me orders" to "How many orders are there?"

That is the first principle of this lesson:

- detail queries answer questions about original rows
- aggregate queries answer questions about sets of rows

If you forget that change, you can misread the report.

### 2. Aggregate functions summarize many rows into one value

Common aggregate functions include:

- `COUNT(*)`: how many rows
- `SUM(OrderTotal)`: how much in total
- `AVG(OrderTotal)`: average amount
- `MIN(OrderTotal)`: smallest amount
- `MAX(OrderTotal)`: largest amount

Example:

```sql
SELECT COUNT(*) AS ClosedOrderCount,
       SUM(OrderTotal) AS ClosedSales,
       AVG(OrderTotal) AS AverageClosedOrderTotal
FROM sales.[Order]
WHERE OrderStatus = 'Closed';
```

This query summarizes all closed orders into three values. The output is still one row because the question is about the whole filtered set.

Use aggregates when the business question asks for:

- how many
- how much
- what is the average
- what is the highest
- what is the lowest

Do not add an aggregate just because you can. Add it because the question requires summarization.

### 3. `GROUP BY` decides what one row means

Sometimes one summary row for the whole table is not enough. A manager might want one summary per customer or one summary per sales representative.

```sql
SELECT SalesRepID,
       COUNT(*) AS ClosedOrderCount,
       SUM(OrderTotal) AS ClosedSales
FROM sales.[Order]
WHERE OrderStatus = 'Closed'
GROUP BY SalesRepID
ORDER BY ClosedSales DESC;
```

Now each output row represents one sales representative's closed orders. The grouped column defines the reporting level.

Read one row aloud like this:

"This row represents all closed orders for SalesRepID 12, summarized into a count and a total."

That plain-language test matters. If you cannot say clearly what one row means, you do not yet understand the report.

### 4. Group meaning changes when grouping changes

Look at these two queries side by side.

One row per sales representative:

```sql
SELECT SalesRepID,
       COUNT(*) AS ClosedOrderCount
FROM sales.[Order]
WHERE OrderStatus = 'Closed'
GROUP BY SalesRepID;
```

One row per sales representative per customer:

```sql
SELECT SalesRepID,
       CustomerID,
       COUNT(*) AS ClosedOrderCount
FROM sales.[Order]
WHERE OrderStatus = 'Closed'
GROUP BY SalesRepID, CustomerID;
```

Both queries are valid SQL. They answer different questions.

- The first report answers: "How many closed orders did each sales representative handle?"
- The second report answers: "How many closed orders did each sales representative handle for each customer?"

That difference is not a formatting detail. It changes what the result means.

### 5. A valid grouped query can still produce a misleading business report

Suppose a sales manager asks:

"Which sales representatives closed fewer than 5 orders in March?"

A student writes:

```sql
SELECT SalesRepID,
       CustomerID,
       COUNT(*) AS ClosedOrderCount
FROM sales.[Order]
WHERE OrderStatus = 'Closed'
  AND OrderDate >= '2026-03-01'
  AND OrderDate < '2026-04-01'
GROUP BY SalesRepID, CustomerID
HAVING COUNT(*) < 5
ORDER BY SalesRepID, CustomerID;
```

This query runs. The syntax is not the problem. The grouping is the problem.

Each row now represents one sales representative for one customer in March. That can make strong performance look weak because one representative with 14 March closings across 6 customers might appear only as several small counts such as 2, 3, 1, 4, 2, and 2. If a manager mistakes those rows for one-row-per-representative results, the report distorts the truth.

That is a business-integrity problem. Distorted summaries can affect staffing, coaching, compensation, or performance evaluation. Accurate reporting is part of faithful and honest business work because people make decisions from these summaries.

The correct grouping for the stated question is:

```sql
SELECT SalesRepID,
       COUNT(*) AS ClosedOrderCount
FROM sales.[Order]
WHERE OrderStatus = 'Closed'
  AND OrderDate >= '2026-03-01'
  AND OrderDate < '2026-04-01'
GROUP BY SalesRepID
HAVING COUNT(*) < 5
ORDER BY SalesRepID;
```

Now each row represents one sales representative's March closed-order count. The report meaning matches the question.

### 6. `WHERE` filters rows before grouping, and `HAVING` filters groups after grouping

This distinction becomes easier once you think about query logic in order.

```sql
SELECT SalesRepID,
       COUNT(*) AS ClosedOrderCount,
       SUM(OrderTotal) AS ClosedSales
FROM sales.[Order]
WHERE OrderStatus = 'Closed'
GROUP BY SalesRepID
HAVING SUM(OrderTotal) >= 10000
ORDER BY ClosedSales DESC;
```

Read the logic this way:

1. `WHERE OrderStatus = 'Closed'` keeps only closed-order rows.
2. `GROUP BY SalesRepID` forms one group per sales representative.
3. `COUNT(*)` and `SUM(OrderTotal)` summarize each group.
4. `HAVING SUM(OrderTotal) >= 10000` keeps only groups whose total sales reach the threshold.

Use this rule:

- `WHERE` decides which rows are included before summarization
- `HAVING` decides which summarized groups remain after summarization

If the condition refers to individual rows, it usually belongs in `WHERE`.

If the condition refers to an aggregate such as `COUNT(*)`, `SUM(...)`, or `AVG(...)`, it belongs in `HAVING`.

### 7. A repeatable process for honest summarized reporting

When you build a grouped query, use this process:

1. Read the business question carefully.
2. Decide whether the question asks for detail rows or summary rows.
3. Choose the aggregate that matches the question.
4. Decide what one output row should represent.
5. Put that non-aggregated column or column set in `SELECT`.
6. Put the same non-aggregated column or column set in `GROUP BY`.
7. Put row-level filters in `WHERE`.
8. Put group-level filters in `HAVING`.
9. Read one output row in plain language.
10. Ask whether that row meaning matches the business question.

This final check is the quality-control habit that matters most. A query that runs is not automatically a truthful report.

## Examples and case

### Example 1: one summary value for the whole filtered set

Business question: "What is the total dollar value of closed orders?"

```sql
SELECT SUM(OrderTotal) AS ClosedSales
FROM sales.[Order]
WHERE OrderStatus = 'Closed';
```

Meaning:

- one row represents the whole set of closed orders

### Example 2: one row per customer

Business question: "How many orders has each customer placed?"

```sql
SELECT CustomerID,
       COUNT(*) AS OrderCount
FROM sales.[Order]
GROUP BY CustomerID
ORDER BY CustomerID;
```

Meaning:

- one row represents one customer

### Example 3: a misleading grouping choice

Business question: "How many orders has each customer placed?"

Misleading version:

```sql
SELECT CustomerID,
       OrderDate,
       COUNT(*) AS OrderCount
FROM sales.[Order]
GROUP BY CustomerID, OrderDate
ORDER BY CustomerID, OrderDate;
```

Why it is misleading:

- each row represents one customer on one date, not one customer overall
- the report may look reasonable, but it answers a narrower question than the business asked

Corrected version:

```sql
SELECT CustomerID,
       COUNT(*) AS OrderCount
FROM sales.[Order]
GROUP BY CustomerID
ORDER BY CustomerID;
```

## Guided practice

Work these in order. Write the answer and then explain what one output row means.

1. Classify each question as detail-level or summary-level:
   - "List every closed order from March."
   - "How many closed orders were there in March?"
   - "What was the average order total for each customer?"

2. Choose the better query for the question "How many orders did each sales representative handle?"
   - Query A groups by `SalesRepID`
   - Query B groups by `SalesRepID, CustomerID`
   Explain why one query matches the report and the other distorts it.

3. Diagnose this query:

```sql
SELECT SalesRepID,
       OrderStatus,
       COUNT(*) AS OrderCount
FROM sales.[Order]
GROUP BY SalesRepID, OrderStatus;
```

The business question is "How many orders did each sales representative handle?" State what one row really means and explain why the grouping changes the business interpretation.

4. Decide whether each condition belongs in `WHERE` or `HAVING`:
   - keep only rows where `OrderStatus = 'Closed'`
   - keep only sales representatives with `COUNT(*) >= 5`
   - keep only rows where `OrderDate >= '2026-03-01'`
   - keep only customers with `AVG(OrderTotal) > 500`

5. Repair this report:

```sql
SELECT CustomerID,
       OrderDate,
       SUM(OrderTotal) AS TotalSales
FROM sales.[Order]
WHERE OrderStatus = 'Closed'
GROUP BY CustomerID, OrderDate;
```

The business question is "What is each customer's total closed-order sales?" Rewrite the query and explain the repair.

## What to do

1. Read the business question before writing SQL.
2. Decide what one row should represent.
3. Draft the query.
4. Run it if you have SQL Server access.
5. Read one row in plain language.
6. Revise the grouping or filter placement if the row meaning does not match the question.
7. If you use AI to draft a query, verify the grouping logic yourself. AI can produce valid SQL that still answers the wrong question.

## Assignments

Complete a short query-verification worksheet for Lesson 2.4.

- Write one aggregate query that returns a single summary value.
- Write one grouped query that returns one row per `CustomerID`.
- Write one grouped query that uses both `WHERE` and `HAVING`.
- Diagnose one misleading grouped query and explain why its reporting level is wrong.
- Revise that misleading query so it answers the stated business question honestly.
- For one grouped result, write two or three sentences explaining what one row does and does not mean.

## Deliverables

- one SQL worksheet or text submission with the required queries
- one short plain-language explanation of grouped row meaning and filter placement

## Project checkpoint or module connection

The Module 2 `Query Verification Lab` will ask you to judge whether a query actually answers a business question. This lesson gives you one of the main habits you will need there: do not trust a query only because it runs. Check what one row means, check whether the grouping level matches the report, and check whether the summary would be honest enough to support a real business decision.

## Wrap-up

Aggregates and grouping are about more than counting and totaling. They change the meaning of the result set. A detail query returns original rows. A grouped query returns summary rows. The grouped columns decide what one row represents, and that decision can either clarify the business question or distort it.

If you keep asking "What does one row mean?" you will make better choices about `GROUP BY`, `WHERE`, and `HAVING`. That habit will matter even more in Lesson 2.5, where joins can change the row set before you summarize it.
