# Lesson 4.2: Keys of Relations

## Lesson Overview

Lesson 4.1 taught you to defend functional dependencies from business meaning. Lesson 4.2 uses that same logic to answer a sharper question: which attribute set actually makes a relation structurally unique?

This is not a lesson about guessing which values happen to look unique in a sample. It is a lesson about defending a candidate key. You will compare strong and weak key proposals, test whether a proposal determines the whole relation, and check whether any attribute in that proposal is unnecessary.

## Lesson Outcomes

By the end of this lesson, you should be able to:

- explain what makes a key candidate strong or weak in business terms
- distinguish a superkey from a candidate key
- test whether a proposed attribute set determines the whole relation
- test minimality by checking whether any attribute can be removed
- identify the prime attributes in a relation and explain why that label matters later
- reject a plausible but weak key candidate with a structural explanation

## Key Terms

- `superkey`: an attribute set that determines every attribute in the relation
- `candidate key`: a minimal superkey
- `minimality`: the condition that no attribute in the candidate key is unnecessary
- `attribute closure`: the set of attributes you can reach from a starting set by applying the known dependencies
- `structural uniqueness`: the idea that the row is made distinct by the actual logic of the relation, not by a temporary data pattern
- `prime attribute`: an attribute that belongs to at least one candidate key
- `nonprime attribute`: an attribute that does not belong to any candidate key

## Readings And Media

- Read this full lesson before attempting the assignment.
- Review Lesson 4.1 notes on defensible functional dependencies if you need a refresher on business-meaning-based reasoning.
- Keep `textbook/v4/06-design-object-naming-and-notation-conventions.md` available if you want a reminder about compact relation notation.
- No separate video or outside reading is required for this lesson.

## Core Content

In Lesson 3.1 you compared identifier choices using three tests: uniqueness, stability, and business meaning. This lesson formalizes that same judgment using relational key theory. The intuition is identical — you are still asking what minimally distinguishes one row from every other — but the tools are now precise enough to test formally and defend under scrutiny.

### 1. Start With What One Row Means

Before you test any key candidate, ask what one row represents.

That question controls everything that follows. If one row means "one student registered in one specific section," then a good key candidate must distinguish one student's registration in one specific section. A proposal that identifies only the student, or only the course, is already too weak because it misses the row's grain.

This is the same question that opened Module 3's entity work. There, it helped you distinguish entities from attributes. Here, it is the starting condition for key analysis: the key must uniquely identify the thing the row is supposed to represent.

This is why key reasoning starts with meaning, not with notation.

### 2. Strong And Weak Key Candidates In Business Terms

A strong key candidate usually has these traits:

- it matches the grain of the row
- it can be defended from business rules and dependencies
- it does not depend on descriptive data that may change
- it does not include extra attributes just because they are available

A weak key candidate often has one or more of these problems:

- it only looks unique in a small sample
- it borrows descriptive or contact data instead of structural identifiers
- it ignores part of the row grain
- it includes unnecessary attributes that do not help determine the relation

You should learn to say more than "this looks unique." A better explanation is, "this candidate is strong because it matches the business meaning of one row and determines the rest of the relation without extra attributes."

### 3. Superkey Versus Candidate Key

A `superkey` is any attribute set that determines the entire relation.

A `candidate key` is stricter. It must:

- determine the whole relation
- stay minimal

That distinction matters because a large attribute set can still be sufficient while being weak as a final key choice.

If `StudentID, SectionID` determines the whole relation, then `StudentID, SectionID, StudentEmail` also determines the whole relation. But the larger set is weaker as a final answer because `StudentEmail` is unnecessary. It is a superkey, not a candidate key.

### 4. A Repeatable Test For Candidate Keys

Use the same two-step process every time:

1. Test sufficiency.
2. Test minimality.

Sufficiency asks: does this set determine the whole relation?

Minimality asks: if I remove one attribute, does the reduced set still determine the whole relation?

Keep those questions separate. Many mistakes happen because students prove sufficiency and then stop too early.

### 5. Attribute Closure Helps Test Sufficiency

Attribute closure is a practical way to test sufficiency.

For an attribute set `X`, `X+` means the attributes you can reach from `X` by applying the known functional dependencies.

Use closure like this:

1. start with the attributes already in the set
2. scan the dependency list
3. when the left side of a dependency is already available, add the right side
4. repeat until nothing new can be added

If the final closure contains every attribute in the relation, the set is sufficient. At that point, the set is a superkey.

Closure answers the sufficiency question. It does not answer the minimality question by itself.

### 6. Main Worked Case: Course Registration

Use this relation:

`CourseRegistration(StudentID, SectionID, StudentEmail, CourseID, Term, InstructorID, InstructorName, FinalGrade)`

Treat one row as one student's registration in one specific section.

Business rules:

- each `StudentID` identifies one student and that student's current institutional email
- each `SectionID` identifies one section, one course, one term, and one assigned instructor
- each `InstructorID` identifies one instructor and one instructor name
- `FinalGrade` belongs to one student's registration in one section

Defensible dependencies:

- `StudentID -> StudentEmail`
- `SectionID -> CourseID, Term, InstructorID`
- `InstructorID -> InstructorName`
- `StudentID, SectionID -> FinalGrade`

Now test the proposal `StudentID, SectionID`.

Start the closure:

`(StudentID, SectionID)+ = {StudentID, SectionID}`

Apply the dependencies:

- from `StudentID -> StudentEmail`, add `StudentEmail`
- from `SectionID -> CourseID, Term, InstructorID`, add `CourseID`, `Term`, and `InstructorID`
- from `InstructorID -> InstructorName`, add `InstructorName`
- from `StudentID, SectionID -> FinalGrade`, add `FinalGrade`

Now the closure is:

`{StudentID, SectionID, StudentEmail, CourseID, Term, InstructorID, InstructorName, FinalGrade}`

That is the full relation, so `StudentID, SectionID` is sufficient. It is a superkey.

Now test minimality.

If you remove `StudentID`, then `SectionID+` gives you section-level facts but not the student's email or final grade for a specific student. So `SectionID` alone is too weak.

If you remove `SectionID`, then `StudentID+` gives you the student's email but not the section, course, instructor, term, or final grade for a specific registration. So `StudentID` alone is too weak.

Neither attribute is removable. Therefore:

- `StudentID, SectionID` is sufficient
- `StudentID, SectionID` is minimal
- `StudentID, SectionID` is a candidate key

### 7. Comparing Strong And Weak Candidates

Now compare several proposals for the same relation.

| Proposal | Why it may look plausible | Why it is strong or weak |
| --- | --- | --- |
| `StudentID, SectionID` | It matches one student's registration in one section. | Strong. It matches the row grain, determines the full relation, and no attribute is removable. |
| `StudentEmail, SectionID` | Email may look unique for each student right now. | Weak. The dependencies do not show that `StudentEmail` determines `StudentID`, and email is contact data that can change. |
| `StudentID, CourseID` | A student and a course sound close to an enrollment. | Weak. One course can have multiple sections or repeated offerings, so this ignores the row grain. |
| `StudentID, SectionID, StudentEmail` | It certainly contains enough information. | Weak as a final key choice. It is a superkey, but `StudentEmail` is extra and unnecessary. |

Notice that weak candidates fail for different reasons.

- some fail because they do not determine the whole relation
- some fail because they ignore the true business grain
- some fail because they add unnecessary attributes

All three are important forms of weak reasoning.

### 8. Rejecting A Plausible But Weak Candidate

Consider `StudentEmail, SectionID`.

This proposal feels plausible because many organizations treat email as a practical way to identify a student. But the relation is not about convenience alone. It is about structural uniqueness.

The problem is not that email is always useless. The problem is that the given dependency set does not justify `StudentEmail -> StudentID`. If the business changes an email address, merges accounts, or allows alternate contact addresses, the row logic should not collapse.

A good rejection sounds like this:

`StudentEmail, SectionID` is a weak candidate because it relies on contact data that may look unique now but is not the structural basis of the row. The dependency set supports `StudentID -> StudentEmail`, not the reverse.

That explanation is better than saying only, "email can change." It connects the business fact and the dependency logic.

### 9. Prime Attributes, Only As Far As You Need Them

A `prime attribute` is an attribute that belongs to at least one candidate key.

In the `CourseRegistration` relation, the prime attributes are:

- `StudentID`
- `SectionID`

The nonprime attributes are:

- `StudentEmail`
- `CourseID`
- `Term`
- `InstructorID`
- `InstructorName`
- `FinalGrade`

Why do you need that label?

Mostly because later normalization reasoning asks whether a nonprime attribute depends on part of a candidate key. That helps you spot partial dependency problems. You do not need to memorize prime-attribute jargon for its own sake. You need it because it supports later structural reasoning.

### 10. How Weak Key Logic Creates Structural Confusion Later

Suppose you incorrectly treat `StudentID, CourseID` as the candidate key.

That mistake makes the relation look as if one student can appear only once per course. But the real business may allow multiple sections of the same course or retakes in different terms. Once you force the wrong key into the design, later reasoning becomes distorted:

- you may think section-level facts belong to the whole row when they really depend on `SectionID`
- you may miss why repeating `InstructorName` across rows is a design warning
- you may normalize around the wrong determinant and create a decomposition that sounds tidy but does not reflect the business

Weak key logic does not stay isolated in one homework problem. It changes the structure you think you are defending.

## Examples And Case

### Main Case Summary

Relation:

`CourseRegistration(StudentID, SectionID, StudentEmail, CourseID, Term, InstructorID, InstructorName, FinalGrade)`

Defensible dependencies:

- `StudentID -> StudentEmail`
- `SectionID -> CourseID, Term, InstructorID`
- `InstructorID -> InstructorName`
- `StudentID, SectionID -> FinalGrade`

Candidate-key conclusion:

- `StudentID, SectionID` is a candidate key
- `StudentEmail, SectionID` is a plausible but weak proposal
- `StudentID, CourseID` is a plausible but weak proposal
- `StudentID, SectionID, StudentEmail` is a superkey but not a candidate key

### Short Contrast Case

A clinic stores appointment data in:

`AppointmentRecord(PatientID, AppointmentSlot, PatientPhone, ProviderID, ProviderName, RoomCode, VisitOutcome)`

If one row means one patient's appointment in one appointment slot, then `PatientID, AppointmentSlot` is worth testing. `PatientPhone, AppointmentSlot` may look plausible, but it borrows contact data instead of the patient identifier. The same pattern appears again: descriptive data can seem helpful without being structurally strong.

## Guided Practice

### Practice 1: Classify The Proposals

Using the `CourseRegistration` relation, classify each proposal as:

- not a superkey
- superkey only
- candidate key

Proposals:

- `StudentID`
- `SectionID`
- `StudentID, SectionID`
- `StudentEmail, SectionID`
- `StudentID, SectionID, StudentEmail`

Write one sentence of reasoning for each answer.

### Practice 2: Reject A Plausible Weak Candidate

A classmate says, "I think `StudentEmail, SectionID` should count as the key because email identifies the student anyway."

Write a short response that rejects that claim. Your answer must mention:

- row meaning
- dependency direction
- one business reason the proposal is structurally weaker than `StudentID, SectionID`

### Practice 3: Prime Or Nonprime

For the main case, label each attribute as prime or nonprime:

- `StudentID`
- `SectionID`
- `StudentEmail`
- `CourseID`
- `FinalGrade`

Then answer this question in one sentence:

Why are you learning the prime/nonprime distinction in this module?

## What To Do

1. Read the lesson once for the big idea: strong versus weak key reasoning.
2. Read the worked case a second time and compute the closure yourself.
3. Complete the guided practice without looking back at the finished classifications.
4. Do the assignment and make your reasoning explicit.
5. Before submitting, check that you defended the final key in business and structural terms.

## Assignments

### Assignment 1: Key Reasoning Worksheet

Given a relation and dependency set supplied in your LMS:

- test at least two proposed key candidates
- show closure or equivalent dependency-based reasoning for sufficiency
- test minimality explicitly for the strongest proposal
- identify the candidate key or keys
- reject at least one plausible but weak candidate in business terms

### Assignment 2: Short Defense Paragraph

Write 200 to 300 words answering this prompt:

Why is `looks unique right now` weaker than `is structurally defensible from the dependency set` when you choose a key for a relation?

Your answer should refer to:

- one strong candidate
- one weak candidate
- one way weak key logic could damage later normalization reasoning

## Deliverables

- one completed key reasoning worksheet
- one short defense paragraph

## Project Checkpoint Or Module Connection

Before Lesson 4.3, ask yourself:

If I pick the wrong candidate key for this relation, which later normalization judgment becomes less trustworthy?

Use this checkpoint to connect key reasoning to stewardship and truthfulness in business reporting. A weak key can make the structure look cleaner than it really is, which wastes time and damages trust when the data must support registration, billing, scheduling, or advising decisions.

## Wrap-Up

Keys are not just labels. They are arguments about structure.

A strong candidate key matches the grain of the row, determines the relation, and avoids unnecessary attributes. A weak candidate either misses the real row meaning, leans on descriptive data, or carries extra baggage. That distinction matters now, and it matters even more in the next lesson when you decide whether a relation needs repair.
