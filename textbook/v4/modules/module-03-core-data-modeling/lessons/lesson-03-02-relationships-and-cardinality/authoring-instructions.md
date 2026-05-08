# Lesson 3.2 Writing Instructions: Relationships and Cardinality

## Canonical lesson identity

- Lesson number: `3.2`
- Canonical title: `Relationships and Cardinality`
- Canonical slug: `relationships-and-cardinality`

## Output paths

- Student draft: `textbook/v4/drafts/module-3-core-data-modeling/lesson-3.2-relationships-and-cardinality.md`
- Instructor draft: `textbook/v4/drafts/module-3-core-data-modeling/lesson-3.2-relationships-and-cardinality-instructor.md`

## Summary

Draft Lesson 3.2 as the Module 3 lesson that teaches students how relationships express business meaning in a conceptual ERD. The lesson should move beyond notation recall and teach students to justify relationship choices from the business scenario.

## Source package

Read and apply these files:

1. `textbook/v4/00-course-design-spec.md`
2. `textbook/v4/01-module-content.md`
3. `textbook/v4/02-instructional-strategies-for-lessons.md`
4. `textbook/v4/05-lesson-writing-agent-index.md`
5. `textbook/v4/06-design-object-naming-and-notation-conventions.md`
6. `textbook/christian_integration_guide.md`
7. `textbook/v4/modules-plan/03-module-3-core-data-modeling.md`

## Module context to preserve

- Lesson 3.1 prepared students to identify entities, attributes, identifiers, and weak entities.
- Lesson 3.2 should teach how those entities connect through business rules, maximum participation, and minimum participation.
- Lesson 3.3 will ask students to draft and critique a first conceptual ERD from a case.
- Module 3 grades critique and defense of conceptual choices, not diagram polish alone.

## Required lesson emphasis

- Keep the lesson grounded in business meaning rather than notation memorization alone.
- Clearly distinguish `one-to-many` and `many-to-many` patterns.
- Label recursive hierarchy as self-referencing `1:N` and recursive network as
  self-referencing `M:N` / `N:M` when recursive examples are used.
- Teach optionality and participation with concrete case reasoning.
- Include at least one example where the wrong cardinality choice misrepresents real work.
- Include at least one practice or critique item that requires justification from the business scenario, not from surface wording alone.
- Preserve the conceptual ERD boundary and avoid `PK`, `FK`, data types, nullability, or implementation repair procedures.

## Strategy alignment

Use the v4 strategy for Lesson 3.2:

- Primary learning type: `Principles`
- Secondary learning type: `Concepts`
- Strategy pattern:
  - rule explanation
  - diagram reading
  - contrasting cases
  - cardinality and optionality judgment
- Practice type:
  - identify one-to-many and many-to-many patterns
  - justify optionality from business rules
  - critique a weak relationship choice
- Assessment evidence:
  - students match relationship patterns to business rules
  - students justify cardinality and optionality decisions
  - students detect relationship errors in a model

## Content requirements

The student lesson should:

- explain that a relationship line is a claim about how the business works
- define `relationship`, `cardinality`, `optionality`, and `participation` clearly
- show how to read both sides of a relationship in plain language
- distinguish maximum participation from minimum participation
- contrast one-to-many and many-to-many with realistic business cases
- define recursive hierarchy and recursive network as relationship patterns if
  the lesson uses recursive examples
- show why a wrong cardinality can hide work, create false limits, or misrepresent accountability
- include a short critique activity tied to the module's later model critique and defense assessment

The instructor lesson should:

- connect Lesson 3.2 explicitly to Lessons 3.1 and 3.3
- align activities to principle learning and judgment evidence
- emphasize explanation and critique over diagram production alone
- include common misconceptions about optionality, participation, and many-to-many relationships
- embed Christian integration inside normal modeling judgment, especially truthful representation and keeping stakeholders visible

## Suggested case direction

Use small business-facing cases such as `Advisor` and `Student`, `Student` and `Course`, `Customer` and `Order`, `Order` and `OrderLine`, `Technician` and `WorkOrder`, or similar plain-language examples that support conceptual modeling.

At least one case should show:

- a relationship that is truly many-to-many at the conceptual level
- a relationship where minimum participation matters
- a flawed relationship choice that students must critique and correct

## Acceptance checks

Confirm before finalizing:

- The lesson clearly distinguishes one-to-many and many-to-many patterns.
- Recursive examples, if present, use the labels `recursive hierarchy` for
  self-referencing `1:N` and `recursive network` for self-referencing `M:N` /
  `N:M`.
- Optionality and participation are taught with concrete case reasoning.
- At least one practice or critique item asks students to justify cardinality from the business scenario, not from surface wording alone.
- The lesson stays within conceptual ERD scope.
- The lesson fits Module 3's critique-and-defense assessment logic.
- The lesson follows the canonical title, slug, and output paths.
