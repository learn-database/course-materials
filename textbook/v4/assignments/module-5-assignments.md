# Module 5 Assignments

## Lesson 5.1: Clean the Conceptual ERD

### Flawed ERD Description

A conceptual ERD for a tutoring system includes these elements:

- `Student(StudentID, FirstName, LastName, Email, varchar(50), NOT NULL)`
- `Tutor(TutorID, FirstName, LastName, HourlyRate decimal(8,2))`
- `Session(SessionID, StudentID FK, TutorID FK, SessionDate datetime, Minutes int)`
- relationship labels are missing
- a many-to-many relationship between `Student` and `Tutor` is shown directly, even though the case records individual sessions

### Tasks

1. List the implementation details that should be removed from the conceptual ERD.
2. Rewrite the entities and key attributes in conceptual form.
3. Describe the corrected relationships in Crow's Foot terms.
4. Explain why one removed detail belongs in the DBDD instead.

### Submission

Submit a corrected ERD or text equivalent plus explanations.

### Grading Criteria

- conceptual ERD boundary control
- corrected notation and relationship meaning
- accurate ERD versus DBDD explanation

## Lesson 5.2: Build the DBDD Slice

### Conceptual Model Slice

Entities:

- `Student` with identifier `StudentID`
- `Tutor` with identifier `TutorID`
- `Session` with identifier `SessionID`

Relationships:

- one student may have many sessions
- one tutor may lead many sessions
- each session has exactly one student and one tutor

### Tasks

1. Convert this slice into a DBDD.
2. Include table names, columns, PKs, FKs, data types, and nullability.
3. Explain one PK or FK decision.
4. Explain one data type or nullability decision.

### Submission

Submit a DBDD table list or diagram and the two explanations.

### Grading Criteria

- correct table and key structure
- reasonable data types and nullability
- clear mapping from conceptual model to implementation-ready design

## Lesson 5.3: ERD to DBDD Alignment Review

### ERD Statement

Each `Order` is placed by exactly one `Customer`. Each `Order` contains one or more `OrderLine` records. Each `OrderLine` refers to exactly one `Product`.

### Proposed DBDD

- `Customer(CustomerID PK, CustomerName)`
- `Order(OrderID PK, OrderDate)`
- `OrderLine(OrderLineID PK, OrderID FK, Quantity)`
- `Product(ProductID PK, ProductName)`

### Tasks

1. Identify what relationship meaning is missing from the proposed DBDD.
2. Correct one DBDD element.
3. Explain why the correction preserves the ERD meaning.
4. Identify one implementation detail that should not be pushed backward into the conceptual ERD.

### Submission

Submit an alignment checklist and corrected DBDD excerpt.

### Grading Criteria

- accurate mapping diagnosis
- corrected FK or table structure
- clear artifact-boundary reasoning
