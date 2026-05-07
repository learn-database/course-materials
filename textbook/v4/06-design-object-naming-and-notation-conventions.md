# Design Object Naming and Notation Conventions

## Purpose

This document defines the naming conventions and representation conventions used across `v4` when the course refers to design objects. v4 uses the same convention set established in `v3` so students see the same object types represented consistently from early concept lessons through later artifact creation work.

The goal is not to create a rigid professional standards manual. The goal is to create a small, teachable convention set that:

- keeps examples readable
- reduces confusion between logical and implementation-ready artifacts
- gives writing agents a stable reference
- prepares students to create diagrams later in the course

## How to Use This Document

- Use these conventions from the beginning of the course when examples, visuals, cases, tables, and artifacts are introduced.
- Use them lightly in Modules 1 and 2 so students see consistent naming and object representation before formal modeling begins.
- Treat these conventions as reading conventions in Modules 3 and 4.
- Treat these conventions as creation conventions in Module 5 and later.
- Keep the distinction between ER Diagram conventions and Database Design Diagram conventions explicit.

## Scope

This document covers recurring design objects and related labels:

- entities
- weak entities
- attributes
- identifiers
- relationships
- cardinality and optionality
- intersection tables
- table names
- column names
- PK and FK notation
- ER Diagram versus Database Design Diagram boundaries

## General Rules

### Consistency First

Use one clear naming style consistently within a course example. Avoid switching styles within the same diagram, case, or lesson.

### Plain Business Language

Prefer names students can understand from the business case. Avoid unexplained abbreviations and unnecessary technical shorthand.

### Singular Object Names

Prefer singular names for entities and tables because they usually keep the naming pattern stable between logical and implementation-ready representations.

Plural names are acceptable if they are used consistently within the same course example, diagram, case, or database design.

Examples:

- `Student`
- `Course`
- `Enrollment`

Also acceptable if used consistently:

- `Students`
- `Courses`

### Avoid Decorative Naming

Do not use prefixes such as `tbl`, `obj`, or `ent`. Do not add words that do not help meaning.

Avoid:

- `tblStudent`
- `Entity_Course`
- `StudentTable`

Prefer:

- `Student`
- `Course`

## Logical Model Naming Conventions

### Entity Names

Entity names should:

- preferably be singular nouns
- name a thing the system tracks independently
- reflect the business process rather than the software interface

Good examples:

- `Student`
- `Tutor`
- `Session`
- `Invoice`

Avoid:

- `ManageStudentScreen`
- `Information`

Plural names such as `Students` are acceptable if the naming style is kept consistent throughout the same case or artifact set.

### Weak Entity Names

Weak entity names should:

- preferably still use singular nouns
- name the dependent object directly
- make the dependency clear through the case, relationship, and identifier explanation rather than through awkward naming

Good examples:

- `LineItem`
- `Dependent`
- `SessionNote`

Do not force dependency into the name unless it improves meaning.

Avoid:

- `WeakStudentPhone`
- `DependentOfEmployeeEntity`

### Attribute Names

Attribute names in logical models should:

- use plain business language
- be written as one readable word, using PascalCase when a business term has multiple parts
- describe what is being recorded
- avoid implementation-specific datatype language

Good examples:

- `LastName`
- `HireDate`
- `CreditHours`
- `PaymentStatus`

Avoid:

- `varchar_last_name`
- `student_name_field`
- `IsNullableStatus`
- `Last Name`
- `Payment Status`

### Identifier Naming in Logical Models

In logical models, treat the identifier as the attribute or attribute set that distinguishes one instance from another.

Use names that reflect business meaning and follow the one-word attribute rule:

- `StudentID`
- `CourseCode`
- `InvoiceNumber`

When the identifier is composite, make the parts explicit in the explanation rather than hiding that fact.

## Implementation-Level Naming Conventions

### Table Names

Prefer singular PascalCase names for tables.

Examples:

- `Student`
- `Course`
- `Enrollment`
- `InvoiceLine`

Plural PascalCase table names are acceptable if they are used consistently in the same database design.

Examples:

- `Students`
- `Courses`
- `Enrollments`

If a strong business term exists for an intersection table, prefer it.

Prefer:

- `Enrollment`

If no strong business term exists, combine the entity names clearly and consistently.

Possible fallback:

- `StudentCourse`

### Column Names

Use PascalCase names for columns.

Examples:

- `StudentID`
- `FirstName`
- `LastName`
- `HireDate`
- `CreditHours`

Column names should:

- remain readable
- avoid spaces
- avoid unnecessary abbreviations
- reflect business meaning first

### Primary Key Naming

Use the pattern:

- `<EntityName>ID`

Examples:

- `StudentID`
- `CourseID`
- `InvoiceID`

If a business key is used instead, its meaning should remain explicit.

Examples:

- `CourseCode`
- `InvoiceNumber`

### Foreign Key Naming

Name foreign keys after the referenced entity key when possible.

Examples:

- `StudentID`
- `CourseID`
- `InvoiceID`

This helps students see how relationships are carried into implementation.

### Intersection Table Naming

Use one of two patterns:

- a meaningful business term if one exists
- a clear combined name if no business term exists

Examples:

- `Enrollment`
- `OrderLine`
- `StudentCourse`

The intersection table should not be named casually or inconsistently across examples.

## Relational Schema Notation Convention

### Purpose

Use relational schema notation when the course needs a compact text form for the structure of a relation.

This notation is useful in:

- relation examples
- dependency analysis
- key reasoning
- normalization work
- quick structural comparisons in lessons

### Core Pattern

Use the pattern:

- `RelationName(AttributeName Role, AttributeName, AttributeName Role)`

Examples:

```text
Student(StudentID PK, Name)
Course(CourseID PK, Title)
Enrollment(StudentID PK FK, CourseID PK FK)
```

### Role Labels

Use explicit role labels after attribute names:

- `PK` for primary key
- `FK` for foreign key

If an attribute is both part of the primary key and a foreign key, mark both:

- `StudentID PK FK`
- `CourseID PK FK`

### Reading Rule

Teach students to read this notation as structure, not data.

Example:

```text
Order(OrderID PK, OrderDate, CustomerID FK)
```

means:

- the relation is `Order`
- `OrderID` is the primary key
- `CustomerID` is a foreign key
- the notation describes structure, not stored rows

### Referential Constraint Notation

When presenting a set of relations, list referential constraints in a separate block after the relation schemas.

Use the pattern:

- `AttributeName REFERENCES RelationName(AttributeName)`

Example:

```text
Student(StudentID PK, Name)
Course(CourseID PK, Title)
Enrollment(StudentID PK FK, CourseID PK FK)

Referential constraints:
- StudentID REFERENCES Student(StudentID)
- CourseID REFERENCES Course(CourseID)
```

When the source relation needs to be explicit for clarity, use:

- `RelationName.AttributeName REFERENCES RelationName(AttributeName)`

Example:

```text
Enrollment.StudentID REFERENCES Student(StudentID)
Enrollment.CourseID REFERENCES Course(CourseID)
```

### Referential Constraint Rule

Prefer the keyword `REFERENCES` rather than arrow notation when presenting referential constraints in the course.

Reason:

- `REFERENCES` matches T-SQL language
- it is clearer for students
- it does not conflict with functional dependency notation such as `X -> Y`

### Schema-Term Difference Note

When this notation is used in the course, call it **relational schema notation** or **relation schema notation**.

Make clear that this meaning of schema is different from **SQL Server schema**:

- relational schema = structure of a relation
- SQL Server schema = named container or namespace such as `dbo`

### Formatting Rule

Keep the notation simple and text-friendly:

- relation name first
- attributes inside parentheses
- comma-separated attributes
- explicit `PK` and `FK` labels

Do not rely on underlining, color, or tool-specific formatting for key meaning when this compact notation is used.

## ER Diagram Representation Conventions

### Core Rule

The ER Diagram is a logical artifact. It represents business structure, not SQL implementation detail.

### Entity Representation

Represent each entity with a clear entity box and list the meaningful attributes needed for the logical model.

### Entity Notation Convention

Use a simple, consistent entity notation in ERD examples and student work:

- represent each entity as one named box or container
- place the entity name at the top of the box
- use the chosen naming style consistently, with singular preferred
- list attributes inside the entity box under the name
- place the identifier first when the notation allows it
- include only meaningful logical attributes needed for the model

Recommended reading pattern:

1. entity name
2. identifier
3. significant non-identifier attributes

Example pattern:

```text
Student
StudentID
FirstName
LastName
EmailAddress
```

The purpose of this pattern is readability. Students should be able to recognize immediately:

- what object is being represented
- how that object is identified
- what descriptive data belongs to it

Do not overload the entity box with implementation detail such as SQL datatypes, nullability, or FK clutter in the ER Diagram.

### Identifier Representation

Represent the identifier clearly and consistently in ERD examples. In course materials, the identifier should:

- appear first when appropriate
- be visually distinguished or explicitly labeled as the identifier
- be treated as a logical identifier, not automatically as a SQL implementation choice

### Relationship Representation

Represent relationships with Crow's Foot notation in course examples once relationship reading begins.

The relationship should be explained in plain language, not left as line symbolism only.

In this course, the relationship line does not need to terminate on a key attribute. For ERDs, relationship lines may connect at the entity level as long as the conceptual meaning is clear. For DBDDs, relationship lines also do not need to attach directly to the PK or FK text label as long as the table structure and PK/FK markings make the implementation-ready relationship clear.

### Cardinality and Optionality

Represent cardinality and optionality using the standard Crow's Foot marks used in the course. Always explain them in words when students are still learning to read the notation.

### Weak Entity Representation

When a weak entity appears:

- make its dependency explicit in the surrounding explanation
- make the identifying relationship clear
- do not assume students will infer the dependency from naming alone
- teach the conceptual meaning first: a weak entity depends on another entity for full identification

### Identifying and Non-Identifying Relationship Representation

In this course, explain the concept first and then use the Lucidchart visual cue consistently.

- An identifying relationship is the relationship that supports the full identification of a weak entity.
- A non-identifying relationship connects entities without serving that identification role.

When Lucidchart is used in the course:

- use the standard strong-entity rectangle for strong entities
- use the Lucidchart weak-entity shape for weak entities when it is available in the chosen library
- use the Lucidchart non-identifying relationship line style for non-identifying relationships
- use the Lucidchart identifying relationship line style for identifying relationships

Always explain the meaning in words when the notation first appears. Students should not be expected to infer dependency or identifying status from shape or line style alone.

If the chosen Lucidchart library or shape set behaves inconsistently, keep the conceptual explanation and add a clear label or note in the lesson rather than forcing a weak visual cue.

### Many-to-Many Representation

Many-to-many relationships may appear in conceptual modeling examples when the business meaning requires them. In early conceptual work, represent them honestly rather than prematurely hiding them.

Later modules may resolve them for implementation.

## Database Design Diagram Representation Conventions

### Core Rule

The Database Design Diagram is an implementation-ready artifact. It represents what is needed to build the structure in SQL Server.

### Table Representation

Represent each table with:

- table name
- columns
- PK marker
- FK marker when applicable
- datatype
- nullability when included in the course example

### Key Representation

Show PKs and FKs explicitly and consistently.

Examples:

- `PK StudentID`
- `FK StudentID`

The exact visual style can vary by tool, but the meaning must remain clear.

### Data Type and Nullability Representation

Show datatypes and nullability in the Database Design Diagram, not in the ER Diagram.

Examples:

- `StudentID int not null`
- `MiddleName varchar(50) null`

### Relationship Carryover

In the Database Design Diagram, the relationship is no longer shown only as a business-level line. It is also represented through FK structure and table design.

The line itself does not need to attach directly to the key label. The important rule is that the DBDD must show the correct table structure, PK/FK markings, and relationship meaning clearly and consistently.

## ER Diagram and Database Design Diagram Boundary Rules

### What Belongs in the ER Diagram

Include:

- entity names
- logical attributes
- logical identifiers
- relationships
- cardinality
- optionality

Do not include:

- SQL datatypes
- nullability markers intended for SQL implementation
- `PK` or `FK` implementation clutter unless a tool forces a representation and the lesson explicitly explains the boundary

### What Belongs in the Database Design Diagram

Include:

- table names
- column names
- PK markers
- FK markers
- datatypes
- nullability when taught in the lesson
- implementation-ready relationship structure

## Final Teaching Rule

The naming convention is only useful if students see it repeatedly and consistently.

When the course introduces a new object type:

1. name it consistently
2. represent it consistently
3. explain what the notation means
4. keep the logical-versus-implementation boundary visible
