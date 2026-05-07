# Lesson 3.1: Entities, Attributes, and Identifiers

## Lesson Overview

This lesson starts Module 3 by teaching the first judgment in conceptual data modeling: what the organization is actually tracking. You will learn how to separate entities from attributes, how to compare stronger and weaker identifier choices, and how to explain those choices in business language instead of intuition alone.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- distinguish entities from attributes in a short business case
- use a repeatable method to justify one borderline classification decision
- compare stronger and weaker identifiers using uniqueness, stability, and business meaning
- explain why one identifier choice is stronger than another
- distinguish strong entities from weak entities at a conceptual level
- explain what or who may become invisible when requirements are read carelessly

## Key Terms

- `Entity`: something the organization tracks as its own subject over time
- `Attribute`: a recorded fact that describes an entity
- `Identifier`: the attribute or attribute set that distinguishes one instance from another
- `Instance`: one specific occurrence of an entity
- `Strong entity`: an entity that can be identified on its own
- `Weak entity`: an entity that depends on another entity for full identification
- `Descriptive property`: a fact that supports description but does not become a tracked object by itself

## Readings and Media

- Read [03-module-3-core-data-modeling.md](../../modules-plan/03-module-3-core-data-modeling.md).
- Read [06-design-object-naming-and-notation-conventions.md](../../06-design-object-naming-and-notation-conventions.md), especially the sections on entity names, attribute names, identifiers, and weak entities.
- Work through the examples and guided practice in this lesson. There is no required video for this lesson.

## Core Content

### A Repeatable Way To Tell Entities From Attributes

Use this three-question test whenever you read a scenario:

1. `Track`: Does the organization track this as its own thing over time?
2. `Describe`: Does this mainly tell us something about another tracked thing?
3. `Distinguish`: If we need to tell one instance apart from another, what would identify it?

This gives you a repeatable sequence:

1. highlight candidate nouns
2. ask whether each candidate is tracked independently
3. move descriptive facts under the entity they describe
4. test whether each remaining entity has a meaningful identifier

If the business tracks it independently, it is probably an entity. If it mainly describes something else, it is probably an attribute. If you cannot explain how one instance would be distinguished from another, your entity choice may still be weak.

### Entities Are Tracked Things

An entity is not just an important word. It is something the organization needs to keep track of as its own subject.

Examples:

- `Student` is usually an entity because the organization keeps a record for each student.
- `RepairOrder` is usually an entity because the shop tracks each order over time.
- `Volunteer` is usually an entity because the nonprofit keeps records about each person serving in that role.

Non-examples:

- `Status` is often an attribute because it describes the current condition of another tracked thing.
- `PhoneNumber` is often an attribute because it describes a person or organization already being tracked.
- `DeviceType` is often an attribute because it describes a repair order rather than standing alone as the tracked subject.

Important rule:

Importance does not automatically make something an entity. A detail can matter greatly to the business and still remain an attribute.

### Attributes Describe Tracked Things

An attribute records a fact about an entity. It helps the organization describe, search, sort, or operate on that entity.

Examples:

- `Student(StudentID, FirstName, LastName, GradeLevel, Email)`
- `RepairOrder(RepairOrderID, IntakeDate, DeviceType, ReportedProblem, Status)`

In these examples:

- `Student` and `RepairOrder` are entities
- `GradeLevel`, `Email`, `IntakeDate`, `DeviceType`, `ReportedProblem`, and `Status` are attributes

Borderline cases require judgment. `Address` may be an attribute in one case, but it may need entity status in another case if the organization tracks multiple addresses, shared locations, or address history independently. The correct question is not "Is this important?" The correct question is "Is this tracked on its own?"

### Identifier Choices Should Be Judged, Not Assumed

An identifier distinguishes one instance from another. Stronger and weaker identifier choices should be compared using three tests:

- `Uniqueness`: Does this choice reliably separate one instance from another?
- `Stability`: Is it likely to remain usable over time without frequent change?
- `Business meaning`: Does the choice make sense in the organization’s actual work, or is it only convenient at first glance?

Consider `Customer`:

- `CustomerID` is usually strong because it is intended to distinguish one customer from another.
- `Email` may be useful, but it can change and may not be present in every case.
- `LastName` is weak because many customers can share it.

Consider `RepairOrder`:

- `RepairOrderID` is usually stronger than `IntakeDate`.
- `IntakeDate` has business meaning, but it is not unique enough to distinguish one order from another.

You should be able to say why a stronger choice is stronger. "It looks official" is not enough. A defensible answer names uniqueness, stability, and business meaning directly.

### Tracked Objects Versus Descriptive Facts

When you classify scenario elements, do not promote every repeated detail into a new entity.

Suppose a service center records this:

- `Client(ClientID, ClientName, PreferredLanguage, PhoneNumber)`
- `Appointment(AppointmentID, AppointmentDate, AppointmentTime, ServiceType)`

`PreferredLanguage` matters. `PhoneNumber` matters. `ServiceType` matters. But those facts still describe tracked things. They do not automatically become separate entities just because staff care about them.

The stronger question is whether the organization keeps its own ongoing record for that thing. If the answer is no, it probably stays an attribute at this stage.

### Strong Entities And Weak Entities

A strong entity can be identified on its own. A weak entity depends on another entity for full identification.

Use this example:

- `ServiceVisit(ServiceVisitID, VisitDate, VisitTime, ServiceType)`
- `VisitNote(NoteNumber, NoteText, EnteredAt)`

If `NoteNumber` repeats across different visits, then `VisitNote` is not fully identified by `NoteNumber` alone. It depends on a specific `ServiceVisit` context. That makes it a weak entity conceptually.

This does not make the note less important. It means its identity is incomplete without the parent entity.

That distinction matters because Lesson `3.2` will build on it when you study relationships and identifying relationships. Cleaner strong-versus-weak thinking now usually leads to cleaner conceptual models later.

### Visibility And Careful Requirements Reading

Requirements reading is not only a technical exercise. It affects whose work and needs remain visible in the model.

If a food pantry case mentions `Household`, `Volunteer`, `DistributionVisit`, and `DietaryAccommodation`, but a rushed reader keeps only `DistributionVisit` and a few dates, several things disappear:

- the people being served
- the volunteers doing the work
- the accommodations needed for responsible service

That is a modeling failure before it is a diagram failure. A careless model can make important stakeholders invisible and can lead to incomplete reporting, poor service, or misleading summaries. Careful modeling supports truthful representation of the organization’s real work.

## Examples and Case

Use this running case throughout the lesson:

`HopeBridge Community Resource Center` schedules service visits for clients. The center keeps a record for each client and case manager. A service visit has a date, time, service type, and status. After each visit, the center records one or more visit notes written by the case manager. A note number repeats across different visits, so note number alone does not fully identify a note. The center also records each client's preferred language, phone number, and transportation need.`

First-pass classification:

- likely entities: `Client`, `CaseManager`, `ServiceVisit`, `VisitNote`
- likely attributes: `PreferredLanguage`, `PhoneNumber`, `TransportationNeed`, `VisitDate`, `VisitTime`, `ServiceType`, `Status`, `NoteText`, `EnteredAt`
- identifier candidates: `ClientID`, `CaseManagerID`, `ServiceVisitID`, `NoteNumber`

Borderline judgments:

- `TransportationNeed` matters for responsible service, but in this case it still describes `Client`.
- `ServiceType` matters operationally, but here it still describes `ServiceVisit` rather than standing alone as a separately tracked object.
- `VisitNote` is stronger as an entity than `Status` because the center records multiple notes over time and treats each note as a separate recorded item within a visit.

Identifier comparison from the case:

- `ClientID` is stronger than `PhoneNumber` because phone numbers can change and are not reliable enough as a long-term identifier.
- `ServiceVisitID` is stronger than `VisitDate` because many visits can happen on the same day.
- `NoteNumber` is weak by itself because it only becomes meaningful within a specific `ServiceVisit`.

Visibility prompt:

If a modeler keeps only `Visit`, `Date`, and `Status` from this case, who becomes less visible? A strong answer should notice that clients, case managers, and transportation needs all disappear from the model, even though they affect how service is delivered.

## Guided Practice

### Practice 1: Sort The Scenario Elements

Classify each item from the HopeBridge case as `Entity`, `Attribute`, or `Borderline`:

- `Client`
- `PreferredLanguage`
- `CaseManager`
- `TransportationNeed`
- `ServiceVisit`
- `ServiceType`
- `VisitNote`
- `Status`

After you sort them, explain one borderline decision using the `Track, Describe, Distinguish` test.

### Practice 2: Compare Identifier Choices

For each pair, choose the stronger identifier and explain why using uniqueness, stability, and business meaning:

1. `ClientID` or `PhoneNumber`
2. `ServiceVisitID` or `VisitDate`
3. `CaseManagerID` or `LastName`

Then answer this question:

4. Is `NoteNumber` enough by itself for `VisitNote`? Explain why or why not.

### Practice 3: Strong Or Weak

Classify these as conceptually strong or weak:

- `Client`
- `CaseManager`
- `ServiceVisit`
- `VisitNote`

Then explain this sentence in your own words:

`VisitNote` depends on `ServiceVisit` for full identification.

### Practice 4: Visibility Check

Answer this prompt in two or three sentences:

If someone reads the HopeBridge requirements carelessly, what or who is most likely to become invisible in the model, and why would that harm responsible service or truthful reporting?

## What to Do

1. Read the assigned Module 3 plan section and the naming-and-notation guidance.
2. Study the `Track, Describe, Distinguish` method and the HopeBridge example.
3. Complete the guided practice before starting the assignment.
4. Finish the lesson worksheet for the new case below.
5. Review your answers to make sure they stay conceptual and do not drift into implementation detail.

## Assignments

Complete the conceptual modeling worksheet for this case:

`North Harbor Repair Shop` keeps records about customers, repair orders, and technicians. Each repair order records the intake date, device type, reported problem, and current status. Each repair order may have several diagnostic notes recorded over time. A diagnostic note number repeats across different repair orders, so note number alone is not enough to distinguish one note from another. The shop also records each customer's phone number and preferred contact method.`

Required work:

- classify scenario elements into entities, attributes, and identifier candidates
- explain one borderline entity-versus-attribute decision with the `Track, Describe, Distinguish` method
- compare stronger and weaker identifiers for `Customer`, `RepairOrder`, and `DiagnosticNote`
- evaluate identifier choices using uniqueness, stability, and business meaning
- identify which entities are strong and which are weak
- explain what or who could become invisible if the requirements are read carelessly

## Deliverables

Submit one completed worksheet or short written response that includes:

- your classifications
- your identifier comparisons
- your strong-versus-weak entity decisions
- one plain-language explanation of a borderline case
- one short visibility reflection tied to the case

## Project Checkpoint or Module Connection

Start a first-pass list of likely entities and attributes for your semester project case. Then ask two questions:

- Which items are truly being tracked as their own subjects?
- Who or what would disappear from the model if I reduced the case to only the most obvious transactions?

This checkpoint prepares you for the Module 3 critique-and-defense assessment. A polished diagram is not enough in this module. You will need to defend why your entity, attribute, and identifier choices represent the business truthfully.

## Wrap-Up

This lesson gave you the first conceptual tools for deciding what the system tracks, what only describes those tracked things, and how one instance differs from another. If you can classify a scenario element with a clear reason, reject a weak identifier with specific evidence, and notice who becomes invisible when requirements are read carelessly, you are building the kind of judgment this module is designed to assess.
