# Module 3 Assignments

## Shared Case: Cedarville Community Market

Cedarville Community Market operates a small grocery pickup program. Customers place orders online. Each order contains one or more products. Employees prepare orders and record when each order is picked up. The market also tracks suppliers for products, but it does not track supplier payments in this system.

## Lesson 3.1: Entity or Attribute?

### Candidate Terms

Classify each as `entity`, `attribute`, `identifier`, `background detail`, or `unclear`.

1. Customer
2. CustomerEmail
3. Order
4. OrderNumber
5. Product
6. ProductName
7. Supplier
8. PickupTime
9. Employee
10. SupplierPayment
11. ShoppingCartColor
12. QuantityOrdered

### Tasks

1. Complete the classification table.
2. Justify three classifications.
3. Recommend a stronger identifier for one weak or unclear identifier choice.

### Submission

Submit the table and short explanations.

### Grading Criteria

- accurate entity and attribute distinction
- identifier reasoning
- appropriate scope control

## Lesson 3.2: Cardinality Defense

### Relationship Claims

Evaluate these claims for the market case:

1. One customer may place many orders.
2. One order may include many products, and one product may appear on many orders.
3. One supplier may supply many products.
4. One employee may prepare many orders.

### Tasks

1. For each claim, identify the relationship type: `1:1`, `1:M`, or `M:N`.
2. Identify optionality where the case supports it.
3. Choose one claim and write a 3-4 sentence defense from the business rules.
4. Critique this incorrect claim: "Each order has exactly one product."

### Submission

Submit a relationship table and the written defense.

### Grading Criteria

- correct relationship type
- justified optionality
- clear critique of weak relationship logic

## Lesson 3.3: Requirements to First ERD

### Case Extension

The market wants a conceptual ERD for pickup orders. The system must track customers, orders, products, order lines, employees who prepare orders, and suppliers. Each order has one customer. Each order has one or more order lines. Each order line records a product and quantity. Employees can prepare many orders, but a new employee may not have prepared any orders yet. A product has one supplier in this system.

### Tasks

1. List the must-track entities.
2. List the relationships and cardinalities.
3. Draft a conceptual ERD.
4. Annotate two modeling choices.
5. Identify one detail excluded from the model and explain why.

### Submission

Submit the entity list, relationship list, ERD image or text diagram, and annotations.

### Grading Criteria

- correct extraction of required entities
- accurate relationship and cardinality reasoning
- conceptual ERD avoids implementation details
- clear defense of modeling choices
