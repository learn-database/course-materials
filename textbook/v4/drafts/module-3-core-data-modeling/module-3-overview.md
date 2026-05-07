# Module 3 Overview: Core Data Modeling

## Devotion

> *"Love your neighbor as yourself."*
> — Mark 12:31

Data modeling is abstract work: entities, attributes, identifiers, cardinality. But the things being modeled are rarely abstract. A tutoring center tracks students. A hospital tracks patients. A nonprofit tracks donors. A company tracks employees. When we decide what to model — what the organization will track, how it will identify people, and what relationships it will record — we are making decisions about how the system will see and represent other human beings.

A model that omits a category of person makes them invisible to every report the system produces. A weak identifier creates confusion that eventually attaches the wrong record to the wrong person. A missing relationship means a dependency that affects someone's service, pay, or standing goes unrecorded. These are not only design flaws. They are ways of failing the people the system was built to serve.

This module begins the most important work in the database workflow: deciding what to track and why. The technical skill it builds — entity classification, relationship reasoning, identifier comparison — rests on a prior discipline: reading requirements carefully enough to see all the people and work the system must represent fairly and accurately.

Modeling a data structure is, in some sense, a form of neighbor care. Do it thoughtfully.

## What This Module Is About

Module 3 is where the design work begins. Before any SQL is written or any table is created, you need a conceptual model of what the organization tracks, how those things relate to each other, and how each record can be uniquely identified. That is what data modeling produces.

This module teaches you to build and evaluate that conceptual model — not to produce a diagram quickly, but to justify the choices in it.

Three lessons. Each one focuses on a different modeling judgment:

- **Lesson 3.1** asks: What does this organization actually track, and how should each record be identified?
- **Lesson 3.2** asks: How are those things related to each other, and what do those relationships mean as business rules?
- **Lesson 3.3** asks: Starting from a business narrative, how do you discover requirements and draft a first-pass conceptual ERD?

## Why This Module Matters

A conceptual model is a claim about how an organization works. If the model is wrong, everything built on it will also be wrong — the implementation will not match the business, the queries will not match expectations, and the reports will not tell the truth.

The most common modeling failures are not technical. They are judgment failures: treating a property as an entity when it should be an attribute, assigning the wrong cardinality because it seems convenient, or including things the organization does not actually track. This module teaches you to catch those failures in your own work and in models you are asked to evaluate.

Data modeling also has ethical dimensions. If a model leaves out people, obscures workloads, or misrepresents service delivery, those omissions affect real people who depend on accurate records.

## How The Lessons Connect

| Lesson | Core Question | What You Will Do |
|--------|---------------|-----------------|
| 3.1: Entities, Attributes, and Identifiers | What does the organization track? | Use the three-question test to classify things; compare identifier choices by strength |
| 3.2: Relationships and Cardinality | How are tracked things connected? | Justify cardinality and participation/optionality from business rules, not assumptions |
| 3.3: Discovering Requirements and Drafting a Conceptual ERD | How does a model come from a narrative? | Read a business case, discover requirements, and produce a first-pass conceptual ERD |

Lessons 3.1 and 3.2 give you the vocabulary and reasoning for individual modeling decisions. Lesson 3.3 puts those decisions together in a complete drafting task.

## Where This Module Fits The Workflow

This module covers **stages 3 and 4** of the course workflow:

3. **Identify entities, attributes, and relationships** — determine what the organization tracks and how those things connect
4. **Create the conceptual ER Diagram** — represent that understanding in a Crow's Foot diagram

Module 1 told you what the workflow is for. Module 3 begins the real design work. The conceptual ERD you build here becomes the starting point for Module 5, where it will be refined and then converted into an implementation-ready design.

## What The Assessment Will Ask

The module assessment is a **Model Critique and Defense**. You will be given a flawed conceptual ERD built from a business narrative and asked to:

- identify specific errors in entity classification, identifier choice, cardinality, or optionality
- explain why each error is a problem — not just that it is wrong, but what it misrepresents
- revise the model to correct the errors
- defend your revisions with reasoning from the business narrative

You will not only be asked to produce your own model. You will be asked to evaluate and repair one.

## Key Terms To Watch For

- `entity` — a distinct kind of thing the organization tracks, with multiple instances
- `attribute` — a property stored about an entity
- `identifier` — an attribute or set of attributes that uniquely distinguishes one instance from another
- `instance` — one specific occurrence of an entity, such as one particular student or one particular session
- `strong entity` — an entity whose instances can be identified independently
- `weak entity` — an entity whose instances can only be identified in the context of another entity
- `relationship` — a connection between two entities that reflects a business rule
- `cardinality` — the maximum number of instances of one entity that can be associated with one instance of another
- `participation` — whether every instance of an entity must participate in a relationship (mandatory) or may not (optional)
- `one-to-many` — one instance on one side connects to many instances on the other
- `many-to-many` — many instances on both sides can connect to each other

## A Note On Scope Control

A common mistake at this stage is modeling everything you can imagine instead of what the organization actually needs to track for its business process. More entities and relationships do not make a model better. A focused model that accurately represents the stated requirements is stronger than an expansive model that includes guesses.

Lesson 3.3 gives you practice starting from a business narrative and making careful scope decisions. That discipline is one of the most important things this module teaches.
