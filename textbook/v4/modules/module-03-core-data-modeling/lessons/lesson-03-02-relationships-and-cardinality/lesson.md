# Lesson 3.2: Relationships and Cardinality

## Before You Start

### Lesson Overview

In Lesson 3.1, you learned how to identify entities, attributes, identifiers, and weak entities. This lesson adds the next judgment: once you know what the business must track, how do those tracked things connect?

Relationships are not just diagram lines. A relationship states how the business works. Cardinality and participation explain what the organization allows, what it requires, and what would be false if the model showed the wrong pattern.

### Lesson Outcomes

By the end of this lesson, you should be able to:

- explain a relationship in plain business language
- distinguish `one-to-many` from `many-to-many` patterns
- recognize recursive hierarchy and recursive network patterns at a conceptual level
- explain `cardinality`, `optionality`, and `participation`
- justify minimum and maximum participation from a business rule
- explain how a wrong cardinality choice misrepresents real work
- critique a relationship choice by using the scenario, not surface wording alone

### Key Terms

- `relationship`: a meaningful business connection between entities
- `cardinality`: the maximum number of related instances allowed in a relationship
- `optionality`: whether participation on one side is optional or required
- `participation`: the minimum involvement required for an instance to take part in the relationship
- `one-to-many`: one instance on one side can relate to many instances on the other side
- `many-to-many`: many instances on each side can relate to many instances on the other side
- `recursive relationship`: a relationship where an entity relates to another instance of the same entity
- `recursive hierarchy`: a self-referencing `1:N` pattern where one parent may have many children, but each child has at most one parent
- `recursive network`: a self-referencing `M:N` pattern, also written `N:M`, where many instances can relate to many other instances of the same entity
- `business rule`: a statement that tells you what the organization allows, requires, or records

### Readings and Media

- Read this lesson carefully from start to finish.
- Review [03-module-3-core-data-modeling.md](../../modules-plan/03-module-3-core-data-modeling.md) to keep the module purpose in view.
- Review [06-design-object-naming-and-notation-conventions.md](../../06-design-object-naming-and-notation-conventions.md), especially the sections on relationships, cardinality, optionality, and conceptual ERD boundaries.

## Relationships Begin With Business Meaning

### 1. Relationships begin with business meaning

A relationship exists because the business connects two entities through work, responsibility, or dependency. The line in the ERD is only useful if you can translate it into a business sentence.

Examples:

- `Advisor` advises `Student`
- `Customer` places `Order`
- `Order` contains `OrderLine`
- `Student` enrolls in `Course`

If you cannot explain the relationship in words, do not trust the diagram yet.

Ask these questions first:

1. What business action or rule connects the entities?
2. How many related instances can exist on each side at most?
3. Is participation on each side required or optional?
4. What false story would the model tell if the pattern were drawn incorrectly?

### 2. Cardinality and participation answer different questions

Students often blend these ideas together. Keep them separate.

`Cardinality` asks about the maximum participation allowed.

- Can one advisor advise only one student?
- Can one advisor advise many students?
- Can students and courses each connect to many on the other side?

`Participation` asks about the minimum participation required.

- Must every `Student` have an `Advisor`?
- Can an `Advisor` exist before any students are assigned?
- Must every `Order` belong to a `Customer`?

`Optionality` is the plain-language result of that minimum-participation judgment: optional or required.

Use this case:

- one `Advisor` may advise many `Student` instances
- each `Student` must be assigned to one `Advisor`

From that rule, you can say:

- maximum participation is one-to-many
- `Student` participation is required
- `Advisor` participation may be optional if the school records advisors before assignments are made

### Practice 2: Separate maximum from minimum

Case:

`A college tracks Program and Student. A program may have many students. Each student must belong to one program.`

Answer:

1. What is the maximum participation pattern?
2. Which side is required?
3. Which side may be optional?
4. What words in the case support your answer?

## Relationship Patterns

### 1. One-to-many and many-to-many do not mean the same thing

These two patterns tell very different business stories.

#### One-to-many

Business rule:

- one `Customer` may place many `Order` instances
- each `Order` belongs to one `Customer`

This means one customer can be related to multiple orders, but each order is tied back to one customer.

#### Many-to-many

Business rule:

- one `Student` may take many `Course` instances
- one `Course` may include many `Student` instances

This means many are allowed on both sides. At the conceptual level, that may be exactly the right story. Later modules will discuss how implementation-ready designs handle that pattern, but this lesson is about telling the truth about the business first.

#### Recursive hierarchy

Business rule:

- one `Employee` may supervise many other `Employee` instances
- each `Employee` has zero or one current supervising `Employee`

This is a recursive hierarchy. It is recursive because `Employee` relates back to `Employee`. It is a `1:N` pattern because one supervisor may have many direct reports, but each direct report has at most one current supervisor.

#### Recursive network

Business rule:

- one `Provider` may collaborate with many other `Provider` instances
- one `Provider` may be collaborated with by many other `Provider` instances

This is a recursive network. It is recursive because `Provider` relates back to `Provider`. It is an `M:N` or `N:M` pattern because many providers can connect to many other providers. Later implementation work normally resolves this with an intersection table that points twice to the same entity.

### Example 1: Advisor and Student

Business rule:

- one `Advisor` may advise many `Student` instances
- each `Student` must be assigned to one `Advisor`

What this means:

- pattern: one-to-many
- `Student` participation: required
- `Advisor` participation: optional or required depending on whether unassigned advisors are tracked

### Example 2: Student and Course

Business rule:

- one `Student` may take many `Course` instances
- one `Course` may include many `Student` instances

What this means:

- pattern: many-to-many
- the conceptual model should represent that many-to-many meaning honestly

### Example 5: Provider and Provider

Business rule:

- one `Provider` may supervise many other `Provider` instances
- each `Provider` may have zero or one current supervising `Provider`

What this means:

- pattern: recursive hierarchy
- cardinality label: self-referencing `1:N`
- supervisor participation is optional for providers who are not supervised

### Example 6: User and User

Business rule:

- one `User` may be connected to many other `User` instances
- one `User` may be connected from many other `User` instances
- the relationship itself records the connection type

What this means:

- pattern: recursive network
- cardinality label: self-referencing `M:N` / `N:M`
- later implementation usually needs an intersection table such as `UserRelationship`

### Practice 1: Classify the pattern

Case:

`A nonprofit tracks Volunteer and Event. A volunteer may serve at many events. Each event includes many volunteers.`

Answer:

1. What business action connects the entities?
2. Is the pattern one-to-many or many-to-many?
3. Which part of the scenario proves your answer?

### Practice 5: Label the recursive pattern

Case:

`A clinic tracks Provider. A provider may supervise many other providers. Each provider may have zero or one current supervising provider.`

Answer:

1. Why is this recursive?
2. Is it a recursive hierarchy or a recursive network?
3. Is the cardinality label self-referencing `1:N` or self-referencing `M:N` / `N:M`?

## Avoid False Business Stories

### 1. Wrong cardinality choices misrepresent real work

A wrong relationship does more than break notation. It changes the meaning of the system.

Case 1: `Customer` and `Order`

If you model this as one-to-one, you falsely claim that each customer can place only one order. That would hide repeat business and distort sales history.

Case 2: `Technician` and `WorkOrder`

Suppose the repair shop states:

- one `Technician` may handle many `WorkOrder` instances over time
- each `WorkOrder` is assigned to one lead `Technician`

If you model this as many-to-many without evidence, you imply shared assignment and blurred accountability that the business never described.

Case 3: `Employee` and `ParkingPermit`

Suppose the business states:

- an employee may not have a parking permit
- each parking permit must belong to one employee

If you model employee participation as required, you falsely claim the business must issue every employee a permit.

The question is not "Which label sounds familiar?" The question is "Which pattern tells the true story of the work?"

### 2. Read both sides of the relationship

A relationship is easier to justify when you read it from both directions.

Weak answer:

- `Advisor` to `Student` is one-to-many.

Stronger answer:

- one `Advisor` may advise many `Student` instances
- each `Student` must be assigned to one `Advisor`

Those two sentences tell you:

- the maximum on one side is many
- the maximum on the other side is one
- student participation is required
- advisor participation may be optional

When you read a relationship from both sides, the model becomes defensible instead of memorized.

Note for later: optional participation at the conceptual level does not automatically translate to a nullable column in the implementation. Lesson 5.2 will explain exactly where the two diverge and why.

### 3. Surface wording can mislead you

Students often rely on sentence clues such as "has many" or on the presence of plural nouns. That is not enough.

Look at this scenario:

`A clinic keeps records about Physician and Patient. A physician can see many patients. A patient may see different physicians across the year.`

A quick reader might lock onto "a physician can see many patients" and call it one-to-many. But the second sentence matters. Because patients may also see different physicians, the conceptual relationship is many-to-many.

This is why good modelers read the full scenario instead of copying the first pattern-looking phrase they notice.

### Example 3: Customer and Order

Business rule:

- one `Customer` may place many `Order` instances
- each `Order` must belong to one `Customer`

What this means:

- pattern: one-to-many
- customer participation may be optional if a customer record can exist before the first order
- order participation is required
- modeling this as one-to-one would misrepresent repeat purchases

### Example 4: Employee and ParkingPermit

Business rule:

- an `Employee` may have zero or one `ParkingPermit`
- each `ParkingPermit` must belong to one `Employee`

What this means:

- maximum participation is one-to-one
- employee participation is optional
- parking-permit participation is required

### Practice 3: Critique the relationship choice

Case:

`A repair shop tracks Technician and WorkOrder. One technician may handle many work orders over time. Each work order is assigned to one lead technician.`

A classmate models the relationship as many-to-many.

Answer:

1. What is wrong with that choice?
2. What false business story would the model tell?
3. What relationship pattern should replace it, and why?

### Practice 4: Do not trust surface wording alone

Case:

`A clinic tracks Physician and Patient. A physician can see many patients. A patient may see different physicians across the year.`

Answer:

1. Why is this not one-to-many?
2. Which sentence changes the conclusion?
3. What relationship pattern best represents the case?

## Model People Truthfully

### 1. Relationship choices can keep people visible

Conceptual modeling is part of truthful and responsible business work. If you flatten a many-to-many relationship into a one-to-many relationship without evidence, you may hide who was involved, who received service, or who carried responsibility.

That matters in ordinary business settings. A weak relationship choice can make stakeholders invisible, obscure follow-up responsibility, or support inaccurate reporting. Careful relationship judgment is one small way database work serves people faithfully and truthfully.

### What To Do

1. Read each case completely before deciding on a pattern.
2. Write the relationship in two plain-language sentences, one from each side.
3. Identify maximum participation first, then minimum participation.
4. Explain whether participation on each side is optional or required.
5. For at least one case, state what would become false if the model used the wrong cardinality.

### Assignment: Relationship Critique

Complete the short relationship critique for this scenario:

`North Harbor Equipment Rental` tracks `Customer`, `RentalAgreement`, and `Item`. A customer may sign many rental agreements over time. Each rental agreement belongs to one customer. A rental agreement may include many items, and an item may appear on many rental agreements over time. Some customers create accounts before renting anything.`

Required work:

- identify the relationship pattern between `Customer` and `RentalAgreement`
- identify the relationship pattern between `RentalAgreement` and `Item`
- explain optionality and participation on each side
- critique this flawed claim: "`Customer` and `RentalAgreement` should be many-to-many because both nouns can appear many times in the business"
- justify each answer from the scenario, not from the nouns alone

### Deliverable

Submit one short written response that includes:

- your relationship classifications
- your optionality and participation explanations
- one critique of a flawed cardinality choice
- one sentence explaining what business reality the flawed model would misrepresent

### Project Checkpoint: Relationship Rules

Before starting Lesson 3.3, review your project case and write two or three relationship rules in plain language. Ask yourself:

- What is the real business action or responsibility here?
- What is the maximum participation on each side?
- What is the minimum participation on each side?
- Who becomes invisible or misrepresented if the relationship is modeled carelessly?

That preparation will make your first conceptual ERD easier to defend.

### Wrap-Up

This lesson teaches a simple but important modeling habit: read the business rule first, then draw the relationship. If you can explain one-to-many, many-to-many, optionality, and participation from the scenario itself, you are building the judgment needed for Lesson 3.3 and for the Module 3 critique-and-defense work that follows.
