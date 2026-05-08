# Lesson 2.5 Writing Instructions

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file for this lesson.

## Assigned lesson

- Lesson number: `2.5`
- Canonical title: `Joins`
- Canonical slug: `joins`
- Module: `Module 2: SQL Foundations`

## Output paths

- Instruction file: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-05-joins/authoring-instructions.md`
- Student draft: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-05-joins/lesson.md`
- Instructor draft: `textbook/v4/modules/module-02-sql-foundations/lessons/lesson-02-05-joins/instructor.md`

## Summary

Draft Lesson 2.5, `Joins`, as the lesson on retrieving related data across tables.

## Required source package

Read these files before drafting:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/02-module-2-sql-foundations.md`

## Lesson focus

Teach join purpose, join paths, and row meaning across related tables so students can interpret multi-table results accurately.

## Module context to preserve

- This lesson follows `Single-Table Queries` and `Aggregates and Grouping`.
- It should show that joins introduce a new risk: SQL can run and still produce plausible but incorrect multi-table output.
- It should prepare students for `Common Table Expressions`, where already-working joined queries are reorganized for clearer reasoning and verification.
- It should reinforce the Module 2 `Query Verification Lab` focus on reading, judging, and repairing queries instead of trusting execution alone.

## Primary strategy requirements

From `textbook/v4/02-instructional-strategies-for-lessons.md`:

- Primary learning type: `Principles`
- Secondary learning type: `Procedures`
- Strategy pattern:
  - relationship-based explanation
  - join-path reasoning
  - contrasting examples with row multiplication risks
  - business-meaning interpretation

## Lesson-specific requirements

- Explain why joins are needed when a business question depends on related tables.
- Teach students to identify the join path before writing SQL.
- Make the meaning of one joined row explicit more than once.
- Include at least one example or practice item where a wrong join still looks believable.
- Include at least one example or practice item where row duplication is the real reasoning problem.
- Keep the lesson aligned to the v4 AI-available model by emphasizing explanation, diagnosis, comparison, and verification in addition to query writing.

## Required emphasis

- explain what each joined row represents
- include a case where a wrong join still looks believable
- connect bad joins to false conclusions about people, inventory, service, or operations
- explicitly teach students how to verify that a join answers the intended business question

## Boundaries and non-goals

- Keep the focus on beginner join reasoning in SQL Server and T-SQL.
- Use `INNER JOIN` as the default teaching pattern and include `LEFT JOIN` only where it helps students reason about missing related rows.
- Do not turn the lesson into a coverage survey of every join type or advanced SQL optimization topic.
- Do not drift into window functions, recursive logic, or deep performance tuning.
- Keep grouped examples simple and subordinate to join interpretation.

## Suggested teaching moves

- Start with a business question that one table cannot answer by itself.
- Name the source table, target table, and connecting key path before showing the query.
- Require a plain-language reading of one row after every major example.
- Contrast a correct join with a wrong-but-believable join and make students explain why the wrong output could fool a manager.
- Include one row-multiplication example where joining to a detail table changes counting logic.
- Add a verification routine such as path check, row-meaning statement, duplicate-risk check, and spot-check against a known record.

## Suggested case shape

Use one recurring sales case and one short service-operations case.

Suggested sales tables:

- `sales.Customer(CustomerID, CustomerName, RegionCode)`
- `sales.[Order](OrderID, CustomerID, SalesRepID, OrderDate, OrderStatus)`
- `sales.OrderLine(OrderLineID, OrderID, ProductID, Quantity, UnitPrice)`
- `sales.Product(ProductID, ProductName, CategoryName)`
- `sales.SalesRep(SalesRepID, SalesRepName)`

Suggested service case:

- `service.ServiceTicket(TicketID, CustomerID, OpenedByEmployeeID, AssignedTechnicianID, TicketStatus)`
- `hr.Employee(EmployeeID, EmployeeName)`

## Christian integration guidance

- Keep integration brief and business-facing.
- Connect careless joins to truthful reporting, neighbor-serving information systems, and responsible decision support.
- Note that bad joins can misstate performance, workload, inventory demand, customer activity, or service responsibility.

## Acceptance criteria

- the lesson explains why joins are needed and how join paths affect result meaning
- at least one example or practice item surfaces row duplication or wrong-row matching as a reasoning problem
- the lesson explicitly teaches students how to verify that a join answers the intended business question
- the lesson includes a believable wrong join, not just a syntax error
- the lesson also meets the shared v4 lesson acceptance criteria

## Invocation note

Use `textbook/v4/03-lesson-prompt.md` as the standing instruction file, then write only Lesson `2.5` using the canonical title, slug, and output paths above.
