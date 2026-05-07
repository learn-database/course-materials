# Module 4 Assignments

## Lesson 4.1: Defensible or Accidental?

### Relation

`Registration(StudentID, StudentName, Major, AdvisorID, AdvisorName, CourseCode, CourseTitle, InstructorName)`

### Business Rules

- Each student has one declared major.
- Each student has one assigned advisor.
- Each advisor has one advisor name.
- Each course code identifies one course title.
- A course may be taught by different instructors in different terms, but term is not included in this relation.

### Proposed Functional Dependencies

1. `StudentID -> StudentName`
2. `StudentID -> Major`
3. `StudentID -> AdvisorID`
4. `AdvisorID -> AdvisorName`
5. `CourseCode -> CourseTitle`
6. `CourseCode -> InstructorName`
7. `InstructorName -> CourseCode`

### Tasks

1. Classify each FD as `defensible`, `unsupported`, or `false`.
2. Explain two defensible FDs.
3. Reject one sample-only or unsupported pattern.

### Submission

Submit the FD table and explanations.

### Grading Criteria

- correct FD classification
- business-rule-based reasoning
- rejection of unsupported dependency claims

## Lesson 4.2: Candidate Key Check

### Relation

`Registration(StudentID, CourseCode, Term, StudentName, CourseTitle, Grade)`

### Business Rules

- A student may take many courses.
- A course may have many students.
- A student may take the same course in different terms.
- A student may have only one grade for a course in a given term.

### Candidate Key Options

1. `StudentID`
2. `CourseCode`
3. `StudentID, CourseCode`
4. `StudentID, CourseCode, Term`
5. `StudentID, CourseCode, Term, StudentName`

### Tasks

1. Classify each option as `candidate key`, `superkey`, or `non-key`.
2. Explain why the correct candidate key is minimal.
3. Reject one weak key candidate.

### Submission

Submit the classification table and explanations.

### Grading Criteria

- accurate key classification
- correct minimality reasoning
- clear explanation of structural uniqueness

## Lesson 4.3: Repair the Weak Relation

### Problem Relation

`OrderLine(OrderID, CustomerName, CustomerEmail, ProductID, ProductName, SupplierName, Quantity)`

### Business Rules

- One order belongs to one customer.
- One customer email identifies one customer name.
- One product ID identifies one product name and one supplier.
- One order may include many products.

### Proposed Repairs

Repair A:

- `Order(OrderID, CustomerEmail, CustomerName)`
- `OrderLine(OrderID, ProductID, Quantity)`
- `Product(ProductID, ProductName, SupplierName)`

Repair B:

- `Order(OrderID, CustomerEmail)`
- `Customer(CustomerEmail, CustomerName)`
- `OrderLine(OrderID, ProductID, Quantity)`
- `Product(ProductID, ProductName, SupplierName)`

### Tasks

1. Identify one update, insertion, or deletion anomaly in the original relation.
2. Choose the stronger repair.
3. Explain why the weaker repair still leaves a design problem or weaker dependency placement.
4. Name one business risk of leaving the original design unchanged.
5. Explain whether a denormalized reporting table could be justified for read-only sales reports, and why that reporting table should remain separate from the operational order-entry database.

### Submission

Submit a short design memo, 300-500 words.

### Grading Criteria

- accurate anomaly diagnosis
- defensible repair choice
- clear explanation of dependency placement
- realistic business risk
- correct distinction between operational normalization and reporting denormalization
