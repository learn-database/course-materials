# Lesson 4.1: Functional Dependencies

## Lesson Overview

Functional dependencies are design claims about which business facts belong to
which business things. In this lesson, you will learn to read a dependency
statement, test whether it is supported by business rules, and reject claims
that only look true because of a small sample.

This lesson starts Module 4. That matters because the rest of the module
depends on sound dependency reasoning. If the dependencies are weak, later key
logic and normalization work will be weak too.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain a functional dependency in plain business language
- identify the determinant in a dependency statement
- defend a dependency claim with a stated business rule
- reject a claim that is supported only by accidental sample patterns
- distinguish trivial structural dependencies from meaningful business
  dependencies
- split and combine equivalent dependency statements correctly

## Key Terms

- `functional dependency (FD)`: a claim that one attribute set determines one
  or more other attributes in the relation being analyzed
- `determinant`: the attribute or attribute set on the left side of an FD
- `dependent attribute`: an attribute whose value is determined by the
  determinant in the stated relation
- `business rule`: a statement about how the organization actually operates
  that justifies a dependency claim
- `sample-data regularity`: a pattern that appears in a small sample but is not
  guaranteed by the business
- `trivial dependency`: a structurally true dependency whose right side is
  already contained in the left side
- `relation`: the set of attributes being analyzed together

## Readings and Media

- Read this lesson carefully before attempting the practice or assignments.
- Review `textbook/v4/06-design-object-naming-and-notation-conventions.md` if
  you want a refresher on compact relation-schema notation.
- No separate video is required for this lesson.

## Core Content

### Start With Row Meaning

Before you write or judge any functional dependency, state what one row means.

That step matters because a dependency claim is always about a specific
relation. If one row means "one scheduled service appointment," then the facts
in that row must be judged at the appointment level, not at the customer level,
not at the technician level, and not at the service-type level unless the
business rules say so.

You used this same question in Module 3 to decide whether something should be an entity or an attribute. Here it anchors functional dependency reasoning: until you know what one row represents, you cannot say what determines what.

If you skip row meaning, the notation can become misleading. A dependency that
looks neat in symbols may still be wrong because it assigns a fact to the wrong
business thing.

### What `X -> Y` Means

`X -> Y` means that once the value of `X` is fixed, the value of `Y` is fixed
for every valid row in the relation.

Read that as a business claim, not as a pattern trick.

It does not mean:

- `X` causes `Y`
- `X` comes before `Y`
- `X` is automatically a foreign key

It means that the business rules guarantee exactly one `Y` value for each valid
`X` value in this relation.

Example:

`ServiceCode -> ServiceDescription`

Plain-language reading:

"If you know the service code, the service description is fixed."

That claim is reasonable only if the business rules say each service code names
one service.

### The Determinant Is the Source of Authority

The determinant is the left side of the dependency statement. It tells you
which business thing owns the fact on the right side.

In `CustomerID -> CustomerName`, the determinant is `CustomerID`. That means
the customer record is the source of authority for the customer name on file.

In `ServiceCode -> StandardFee`, the determinant is `ServiceCode`. That means
the fee belongs to the service definition, not to a particular customer, not to
the technician, and not to a random sample row.

This is the practical question to ask:

- What business thing determines this fact?

If you can answer that question clearly, the dependency claim becomes easier to
defend or reject.

### Defend Dependencies With Business Rules

A defensible FD needs more than a tidy sample. It needs a business rule.

Use this test when you evaluate a claim:

1. What does one row represent?
2. What business thing does the determinant identify?
3. What rule says that determinant fixes the value on the right side?
4. Would the claim still hold if the organization added more valid rows next
   month?

If you cannot name the business rule, the claim is weak.

### Sample Patterns Can Mislead You

Sample data can suggest a dependency, but sample data alone cannot prove one.

Suppose you inspect three rows and see that each technician appears with only
one van. It may be tempting to claim:

`TechnicianID -> VanID`

That claim is not defensible unless the business rules explicitly say each
technician is permanently assigned exactly one van. If technicians rotate vans,
share vehicles, or use different vans on different days, then the sample pattern
is accidental.

This distinction matters because accidental patterns can look convincing. They
often survive in a short classroom sample even though they would fail in real
operations.

### Structural Truth Is Not the Same as Business Meaning

Some dependencies are true by structure alone.

Example:

`AppointmentID, ServiceCode -> ServiceCode`

That statement is true because `ServiceCode` is already on the left side. It is
a `trivial dependency`.

Trivial dependencies are structurally true, but they usually do not help much
with design judgment. They do not tell you where a copied fact belongs. They do
not reveal whether a fact is being stored under the wrong determinant. They are
different from accidental sample-data regularity:

- a trivial dependency is always true because of the notation structure
- a sample-only pattern may look true in a short table but can fail as soon as
  more valid rows appear

Keep those two ideas separate.

### Splitting and Combining Equivalent Dependencies

When the determinant is the same, you can rewrite a dependency without changing
its meaning.

Example:

`ServiceCode -> ServiceDescription, StandardFee`

You can split that into:

- `ServiceCode -> ServiceDescription`
- `ServiceCode -> StandardFee`

You can also combine those two statements back into the compact form:

`ServiceCode -> ServiceDescription, StandardFee`

This rewrite is safe because the determinant stays the same.

Be careful with false combining. If you start with:

- `CustomerID -> CustomerName`
- `TechnicianID -> TechnicianName`

you should not treat this as an equivalent rewrite:

`CustomerID, TechnicianID -> CustomerName, TechnicianName`

That larger statement may be true, but it hides the fact that two different
determinants are involved. For design reasoning, that weakens the analysis.

## Examples and Case

### Main Case: Home Service Scheduling

Consider this relation:

`ServiceAppointment(AppointmentID, CustomerID, CustomerName, ServiceCode,`
`ServiceDescription, StandardFee, TechnicianID, TechnicianName, VanID,`
`AppointmentDate, TimeSlot)`

Assume one row means one scheduled service appointment for one customer.

Use these business rules:

- each `AppointmentID` identifies one scheduled appointment
- each `CustomerID` identifies one customer and one billing name on file
- each `ServiceCode` identifies one service and one standard fee
- each `TechnicianID` identifies one technician and one technician name
- a technician may use different vans on different days
- the same van may be used by different technicians over time
- the same customer may schedule many appointments

### Defensible Dependency Claims

These claims are supported by the business rules:

- `AppointmentID -> CustomerID, ServiceCode, TechnicianID, VanID,`
  `AppointmentDate, TimeSlot`
- `CustomerID -> CustomerName`
- `ServiceCode -> ServiceDescription, StandardFee`
- `TechnicianID -> TechnicianName`

Why are these defensible?

- `AppointmentID` identifies the appointment record itself.
- `CustomerID` identifies the customer record.
- `ServiceCode` identifies the defined service.
- `TechnicianID` identifies the technician.

Each accepted claim points to a business thing and a stated business rule.

### A Sample Pattern That Looks Like an FD but Is Not Justified

Now look at this short sample:

| AppointmentID | TechnicianID | TechnicianName | VanID |
| --- | --- | --- | --- |
| A1001 | T17 | Elena Ruiz | V3 |
| A1002 | T22 | Marcus Green | V5 |
| A1003 | T31 | Priya Patel | V9 |

In this sample, each technician appears with one van. A careless reader might
claim:

`TechnicianID -> VanID`

Reject that claim. The business rules say technicians may use different vans on
different days. The sample is too small to prove a permanent technician-to-van
dependency.

This is the key judgment:

- the sample suggests a pattern
- the business rules do not guarantee the pattern
- therefore the FD claim is not defensible

### Why Inconsistency Causes Business Harm

Suppose the table stores `ServiceDescription` and `StandardFee` on every
appointment row even though those facts belong to `ServiceCode`. If one row is
updated and another is missed, the same service can appear with conflicting
descriptions or prices.

That inconsistency creates real problems:

- invoices may charge the wrong amount
- managers may review untrustworthy revenue reports
- staff may promise customers the wrong service details
- time is wasted correcting repeated copied facts

The point of dependency analysis is not only correctness on paper. It is also
to protect operations, trust, and people from avoidable error.

### Structural Dependency Example

This claim is trivial:

`AppointmentID, ServiceCode -> AppointmentID`

It is true because `AppointmentID` already appears on the left side.

Do not confuse that with a meaningful design claim such as:

`ServiceCode -> StandardFee`

The second statement tells you where the fee belongs in business terms. The
trivial statement does not.

## Guided Practice

Use the Home Service Scheduling case.

1. Translate each dependency into plain language:
   - `CustomerID -> CustomerName`
   - `ServiceCode -> StandardFee`
   - `AppointmentID -> TechnicianID`
2. Label each claim as `defensible`, `sample-only`, or `trivial`:
   - `TechnicianID -> VanID`
   - `ServiceCode -> ServiceDescription`
   - `AppointmentID, TimeSlot -> TimeSlot`
3. For each accepted claim, name the business rule that supports it.
4. Split this dependency into equivalent statements:
   - `ServiceCode -> ServiceDescription, StandardFee`
5. Combine these equivalent statements into one compact dependency:
   - `CustomerID -> CustomerName`
   - `CustomerID -> CustomerPhone`

## What to Do

Work through the case in this order:

1. Write one sentence explaining what one row represents.
2. List the business rules that matter for dependency reasoning.
3. Evaluate each proposed FD by asking what business rule defends it.
4. Reject any claim that depends only on the short sample.
5. Identify one trivial dependency and explain why it is structurally true.
6. Practice splitting and combining equivalent statements.

## Assignments

### Assignment 1: Dependency Judgment Check

For the `ServiceAppointment` relation:

- identify at least four defensible FDs
- reject at least two weak claims
- explain one rejected claim as a sample-only pattern
- identify one trivial dependency

### Assignment 2: Short Written Defense

Write `200` to `300` words that do both of the following:

- defend one accepted dependency with a specific business rule
- reject one weak dependency by explaining why the sample does not justify it

Your explanation should stay in business language, not just notation.

## Deliverables

- one completed dependency-judgment submission
- one short written defense paragraph

## Project Checkpoint or Module Connection

The main graded task in Module 4 asks you to compare decompositions and defend
which one preserves business meaning better. You cannot do that well unless you
can first identify which dependencies are valid.

As a checkpoint, ask yourself:

- Which copied fact in your project case would do the most damage if it became
  inconsistent across rows?
- What determinant should own that fact instead?

That question connects sound design to stewardship, truthful reporting, and
reduced rework.

## Wrap-Up

Functional dependencies are not guesses based on a neat-looking sample. They
are claims that must be defended by business meaning. In this lesson, the key
habit is simple: do not ask only whether a pattern appears in the data. Ask
what the organization guarantees.

That habit prepares you for the next step in Module 4, where you will use valid
dependencies to reason about candidate keys.
