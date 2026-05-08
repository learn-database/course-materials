# Module 5: Design Artifacts

## Student-Facing Content

### Module overview

Module 5 is where the course makes one of its most important design boundaries explicit: the conceptual `ERD` is not the same artifact as the implementation-ready `DBDD`.

Earlier modules helped you identify entities, attributes, relationships, keys, and normalization logic. This module uses that earlier work to do two connected jobs:

- refine the conceptual `ERD` so it communicates the business structure clearly and correctly
- build a separate `DBDD` that turns that meaning into tables, keys, data types, nullability, and other implementation-ready detail

The main challenge in this module is not drawing a more technical-looking diagram. The challenge is learning what belongs in each artifact, why that boundary matters, and how to move from one artifact to the other without changing the business meaning.

### Why this module matters

A database design can fail even when the diagrams look polished. One common reason is artifact confusion.

When implementation detail gets pushed into the conceptual `ERD`, the model becomes harder to read as a business-facing design. When the `DBDD` stays vague, key decisions about `PK`, `FK`, data type, nullability, and many-to-many resolution remain hidden until later, when they are harder to repair.

This module matters because good database work depends on both clarity and follow-through:

- the `ERD` should help another person understand the business structure without guesswork
- the `DBDD` should help another person implement that structure without inventing missing rules

That is also why this module treats artifact clarity as a professional responsibility. Clear design supports trustworthy communication. Careful translation from concept to implementation-ready structure is part of accountable follow-through. In a Christian business context, that kind of clarity serves neighbors and organizations by reducing avoidable confusion, hidden errors, and wasted rework.

### What this module is for

By the end of Module 5, you should be able to:

- explain the difference between a conceptual `ERD` and a `DBDD` without blurring their purposes
- refine a conceptual `ERD` in Crow's Foot notation without adding implementation clutter
- convert conceptual entities and relationships into implementation-ready tables and keys
- justify `PK`, `FK`, data type, and nullability choices from business meaning
- detect boundary violations when a detail belongs in the wrong artifact
- explain how design precision protects records, people, and operations from misunderstanding or loss

### The central boundary: `ERD` versus `DBDD`

This module will keep returning to one distinction.

The conceptual `ERD` answers questions such as:

- What business objects does the organization track?
- How are those objects related?
- Which attributes matter conceptually?
- What are the cardinality and optionality rules?

The `DBDD` answers different questions:

- What tables need to be built?
- Which columns identify each row?
- Where do foreign keys belong?
- What data type fits each column?
- Which values are required and which may be absent?

Keep this rule in view throughout the module:

- if a detail helps explain business structure, it likely belongs in the `ERD`
- if a detail makes the design build-ready, it likely belongs in the `DBDD`

Examples:

- entities, significant attributes, relationships, cardinality, and optionality belong in the conceptual `ERD`
- `PK`, `FK`, SQL Server data types, and `NULL` versus `NOT NULL` belong in the `DBDD`

The goal is not to declare one artifact better than the other. The goal is to use each artifact for its proper job.

### How the lessons fit together

The three lessons in Module 5 form a sequence.

#### Lesson 5.1: Refining Conceptual ERDs in Crow's Foot Notation

You will improve the conceptual `ERD` without turning it into a technical implementation document. The focus is notation accuracy, conceptual clarity, readable identifiers and attributes, and removal of implementation clutter.

#### Lesson 5.2: Database Design Diagrams

You will build the separate implementation-ready artifact. This is the first place in the module where `PK`, `FK`, data types, nullability, and intersection tables belong in the artifact itself.

#### Lesson 5.3: From Logical Model to Implementation-Ready Design

You will make the handoff logic explicit. The focus is not only on producing a `DBDD`, but on defending how conceptual meaning becomes implementation-ready structure and diagnosing weak mapping decisions.

Taken together, the lessons move from conceptual refinement to implementation-ready design in a controlled way:

1. clean up the conceptual model
2. create the separate implementation-ready artifact
3. justify and critique the conversion choices

### How this module fits the larger course workflow

Module 5 sits between earlier design reasoning and later SQL Server implementation.

The larger workflow now looks like this:

1. understand the business process
2. identify data requirements and business rules
3. identify entities, attributes, and relationships
4. create a conceptual `ERD`
5. refine the conceptual `ERD`
6. convert the design into a `DBDD`
7. implement the approved design in SQL Server later

This module completes steps 5 and 6. It does not ask you to start building `CREATE TABLE` statements yet. That later implementation work belongs to Module 6.

### The judgment you are expected to develop

This module is not only about following a procedure. It is about developing design judgment.

By the end of the module, you should be able to judge:

- whether a diagram element belongs in the `ERD`, the `DBDD`, both, or neither
- whether a refined `ERD` still communicates the business structure clearly
- whether a `DBDD` preserves the original conceptual meaning
- whether a many-to-many relationship has been resolved correctly
- whether a `PK`, `FK`, data type, or nullability choice is defensible
- whether an AI-generated diagram is trustworthy or only polished-looking

That judgment matters because strong AI tools can draft both kinds of artifacts quickly. The harder and more valuable skill is knowing whether the right information is in the right artifact and whether the translation from concept to implementation actually makes sense.

### Common boundary mistakes to watch for

Students often make the same mistakes in this part of the workflow:

- treating the `DBDD` as the `ERD` with extra labels
- adding `PK`, `FK`, data types, or nullability directly to the conceptual `ERD`
- assuming every optional relationship means a nullable foreign key
- choosing data types by appearance instead of by business meaning
- using a technical-looking diagram as proof that the design is correct

If you notice one of these mistakes, stop and ask two questions:

1. What is this artifact trying to communicate?
2. Does this detail support that purpose, or does it belong in the other artifact?

### What success looks like

By the end of Module 5, a strong student should be able to do more than submit two clean diagrams.

A strong performance means you can:

- explain why a detail belongs in one artifact and not the other
- repair a mixed-up design that blurs conceptual and implementation-ready information
- trace one relationship from business meaning to table structure
- identify at least one place where design precision protects users, customers, staff, or records from confusion or loss
- show that another reviewer could understand the model and the handoff without guesswork

### A module checkpoint

As you work through the lessons, use this checkpoint question:

`If another person inherited both artifacts today, could they tell what the business structure is, what the implementation-ready structure is, and why the boundary between them was kept clear?`

If the answer is no, keep refining.
