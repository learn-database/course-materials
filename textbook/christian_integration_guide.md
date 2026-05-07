# ITM-2100 Christian Integration Guide For Authors

## Purpose

This guide defines how Christian worldview, vocation, stewardship, and business ethics should appear throughout ITM-2100. The goal is course-wide integration that strengthens database learning for Christian business majors instead of interrupting it with disconnected devotional content.

Use this guide with:

- `textbook/itm2100_textbook_plan.md`
- `textbook/chapters/textbook_revision_checklist.md`
- `plans/fall-2026-course-plan.md`

## Integration Model

Christian integration in this course should follow four operating rules:

1. Start with real business and database work.
2. Connect that work to Christian responsibility, not just private opinion.
3. Keep the reflection tied to a concrete data, design, reporting, or governance decision.
4. Ask students to justify choices in business terms and ethical terms together.

This means a chapter should not add a stand-alone faith sidebar and then return to normal content. Instead, Christian integration should appear inside the same examples, warnings, labs, and project checkpoints that already teach database reasoning.

## Key Biblical Anchors

Use Scripture as a grounding reference for the course themes, not as a replacement for technical instruction. In most cases, a verse reference or a short paraphrased connection is enough.

Recommended course-level anchors:

- truthfulness in words, records, and reporting: Proverbs 12:22; Ephesians 4:25
- justice, fairness, and honest business practice: Micah 6:8; Proverbs 11:1; Leviticus 19:35-36
- stewardship of resources and responsibilities: Luke 16:10; 1 Corinthians 4:2; Colossians 3:23-24
- wisdom, discernment, and careful judgment: Proverbs 2:6-11; James 1:5
- neighbor-serving work and human dignity: Mark 12:31; Genesis 1:26-27; Philippians 2:4
- work that protects and serves others well: Jeremiah 29:7; Matthew 5:16

Use these anchors selectively:

- prefer verses that naturally fit a concrete database, reporting, privacy, access, or stewardship decision
- use references and short framing statements rather than long quoted blocks
- avoid forcing a verse into every chapter section or every exercise

## Core Themes

### 1. Human dignity and neighbor-serving information systems

- Biblical anchors: Genesis 1:26-27; Mark 12:31; Philippians 2:4
- Treat data about people as more than raw inventory.
- Emphasize that database design affects customers, employees, patients, donors, students, and other stakeholders.
- Ask whether the system helps the organization serve people accurately, fairly, and responsibly.

### 2. Vocation and faithful business work

- Biblical anchors: Colossians 3:23-24; 1 Corinthians 10:31; Matthew 5:16
- Frame database work as part of competent, trustworthy service.
- Reinforce that analysts, designers, and developers carry responsibility for clarity, truthfulness, and follow-through.
- Show that ordinary business tasks such as requirements analysis, data cleaning, and rule enforcement are part of faithful work.

### 3. Stewardship of data, time, and organizational resources

- Biblical anchors: Luke 16:10; 1 Corinthians 4:2; Proverbs 21:5
- Connect good design to reduced waste, fewer rework cycles, and better decision support.
- Treat maintainability, data quality, and security-minded habits as stewardship concerns.
- Show that weak database design wastes money, attention, and trust.

### 4. Truthfulness, justice, and business ethics

- Biblical anchors: Proverbs 12:22; Ephesians 4:25; Micah 6:8; Proverbs 11:1
- Address honesty in reporting, responsible access, privacy, bias, and misuse of personal or operational data.
- Show how poor schema choices, misleading queries, or careless data entry can distort decisions.
- Ask students to consider who is harmed when business data is incomplete, duplicated, exposed, or misinterpreted.

## Core Vocabulary For Chapter Revision

Use this vocabulary where it naturally fits the learning outcome. Do not force every term into every chapter.

- worldview
- vocation
- stewardship
- integrity
- honesty
- justice
- wisdom
- neighbor-serving
- human dignity
- accountability
- trust
- discernment
- responsible data use
- privacy
- appropriate access
- transparency
- faithful service
- organizational responsibility

## Writing Rules For Authors

- Keep Christian integration subordinate to the chapter outcome, not separate from it.
- Use business-facing language that fits an undergraduate Christian business program.
- Use Scripture references to support the stated course themes, especially truthfulness, justice, stewardship, wisdom, vocation, and neighbor-serving work.
- Prefer brief verse references or short paraphrased connections over long quotations.
- Prefer short reflection prompts tied to a database decision over long devotional commentary.
- Show both capability and responsibility: students should learn how to build databases and why faithful practice matters.
- Avoid denominational claims, church policy debates, or unsupported moral generalities.
- Avoid proof-texting a technical point with a verse that does not naturally fit the actual business or database decision.
- Avoid replacing technical exercises with reflection-only work.

## Where Integration Should Appear In Each Chapter

Each chapter should include at least two of the following touchpoints:

- a purpose statement that frames database work as responsible business service
- a worked example that includes a stewardship or ethics implication
- a common mistake that names a real business or neighbor-impact risk
- a lab instruction that asks for a responsible design or data-use choice
- a project checkpoint that links the chapter artifact to trustworthy business practice

## Chapter And Project Integration Map

### Chapter 1. Why Databases Matter

- Connect database purpose to serving organizations and people truthfully.
- Name spreadsheet failure not only as inefficiency but as a stewardship and trust problem.
- Project checkpoint prompt: ask where poor data structure could harm customers, staff, or reporting integrity.

### Chapter 2. SQL Server and the Working Environment

- Frame safe workflow, naming, and verification as habits of accountable work.
- Ethical guidance: least-necessary changes, careful script execution, and respect for shared systems.
- Project checkpoint prompt: ask what operational risks follow from careless execution in a live business environment.

### Chapter 3. Querying a Single Table

- Use examples about fair, accurate retrieval rather than only syntax drills.
- Ethical guidance: avoid careless filtering that hides needed records or misstates business reality.
- Project checkpoint prompt: ask which fields in the project case require especially careful handling because they affect people or sensitive decisions.

### Chapter 4. Joining Tables and Summarizing Results

- Show that joins and summaries influence managerial judgment and resource allocation.
- Ethical guidance: warn against misleading aggregation, missing context, or false confidence in partial data.
- Project checkpoint prompt: ask what business question should be answered honestly and clearly by a future project view.

### Chapter 5. Keys, Attributes, and Data Type Decisions

- Frame key and data-type choices as stewardship of future accuracy and maintainability.
- Ethical guidance: ask whether identifiers, nullability, and field sizes protect clarity or invite confusion.
- Project checkpoint prompt: ask students to justify one design choice as both technically sound and responsibly maintainable.

### Chapter 6. Functional Dependencies

- Show that dependency reasoning protects truthfulness by keeping facts in the right place.
- Ethical guidance: connect misplaced dependencies to inconsistent reporting and avoidable errors.
- Project checkpoint prompt: ask which dependency mistake would most damage trust in the project database.

### Chapter 7. Normalization and Design Repair

- Present normalization as repair that reduces waste, confusion, and repeated correction work.
- Ethical guidance: connect anomalies to downstream harm for billing, inventory, scheduling, or service quality.
- Project checkpoint prompt: ask where decomposition improves stewardship of organizational resources.

### Chapter 8. Discovering Entities from Requirements

- Frame requirements reading as careful listening to what the organization is actually responsible to track.
- Ethical guidance: ask which stakeholders become invisible if the requirements are read carelessly.
- Project checkpoint prompt: ask whether the proposed entities reflect the true work and people involved in the case.

### Chapter 9. Building High-Quality ER Diagrams

- Connect diagram clarity to trustworthy communication with clients, instructors, and teammates.
- Ethical guidance: poor diagram clarity should be treated as a responsibility issue, not only a style issue.
- Project checkpoint prompt: ask whether another reviewer could understand the model without guesswork.

### Chapter 10. From ERD to Database Design Diagram

- Frame PK/FK, nullability, and table structure as commitments to accurate implementation.
- Ethical guidance: ask what weak mapping choices could create hidden business errors later.
- Project checkpoint prompt: ask students to identify one place where design precision protects people from confusion or loss.

### Chapter 11. Creating Tables and Constraints in SQL Server

- Present constraints as practical expressions of accountability and business rule fidelity.
- Ethical guidance: explain that failing to enforce rules invites inaccurate or unjust outcomes.
- Project checkpoint prompt: ask which constraints are most important for trustworthy operations in the project case.

### Chapter 12. Populating Data and Building Views

- Treat sample data and views as stewardship exercises, not filler work.
- Ethical guidance: use realistic but appropriate data, avoid exposing unnecessary personal details, and build views that answer honest business questions.
- Project checkpoint prompt: ask which project views support transparent decision-making without oversharing data.

### Chapter 13. Triggers and Stored Procedures

- Frame automation as delegated authority that must be carefully bounded and tested.
- Ethical guidance: ask what should and should not be automated in order to preserve accurate business judgment.
- Project checkpoint prompt: ask whether a trigger or procedure enforces a rule fairly, clearly, and predictably.

### Chapter 14. The Semester Project Playbook

- Present revision, consistency, and packaging as marks of faithful, professional follow-through.
- Ethical guidance: name the responsibility to submit work that is coherent, defensible, and honest about limitations.
- Project checkpoint prompt: ask students to evaluate whether the final package demonstrates trustworthy stewardship of the case data and design decisions.

## Project-Wide Reflection Prompts

Use short prompts like these at milestone checkpoints:

- What part of this artifact most directly serves people or organizational trust?
- Where could poor data design in this milestone create waste, confusion, or unfair treatment?
- Which design decision in this milestone is an act of stewardship, and why?
- What data in this case should be handled with extra care, and how will the design reflect that?
- How does this deliverable help the business tell the truth about its operations?

## Ethical Data-Use Guidance For Business Settings

Use these themes repeatedly in examples, labs, and project reviews:

- collect and store data because it serves a defined business purpose, not merely because it is available
- limit access and visibility to what is appropriate for the business task
- protect data quality because inaccurate data can harm people and decisions
- design reports and views so they clarify reality instead of distorting it
- document assumptions when the data model simplifies reality
- test procedural logic carefully before trusting automation with consequential actions

## Revision Checklist For Authors

Before finalizing a chapter, confirm:

- the Christian integration point supports the technical learning goal
- the integration appears in a chapter element students already use
- the example or prompt names a real business implication
- the vocabulary fits the course tone and does not sound pasted in
- the chapter still teaches database reasoning first and clearly
