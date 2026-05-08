# ITM-2100 Course Design Spec v4

## Purpose

This document defines the course-level design decisions for ITM-2100 Database Management in the v4 planning cycle. It is the authority for course structure, scope, artifact boundaries, async delivery assumptions, AI-use assumptions, assessment philosophy, and module-planning rules.

This version assumes a fully asynchronous online course in which students have practical access to strong AI tools that can generate, test, debug, and verify many database artifacts. As a result, v4 does not treat standalone artifacts as strong evidence of student learning.

Detailed module planning lives in companion documents:

- [01-module-content.md](01-module-content.md) for the module index
- [02-instructional-strategies-for-lessons.md](02-instructional-strategies-for-lessons.md) for lesson-level strategy rules
- [assessments/](assessments/) for the lesson-, module-, and course-level assessment artifacts
- [activities/](activities/) for lesson-level assignment and activity patterns
- [assignments/](assignments/) for student-facing lesson assignment drafts
- [cases/](cases/) for the primary tutoring case, alternative clinic case, and late-course redesign progression
- [05-lesson-writing-agent-index.md](05-lesson-writing-agent-index.md) for canonical lesson slugs, filenames, and agent output paths
- [modules-plan/](modules-plan/) for detailed module blueprints
- [06-design-object-naming-and-notation-conventions.md](06-design-object-naming-and-notation-conventions.md) for the shared v4 naming and notation conventions
- [../christian_integration_guide.md](../christian_integration_guide.md) for the course-wide Christian integration standard

## Course Identity

### Title

ITM-2100 Database Management

### Delivery Format

The course is designed for fully asynchronous online delivery. Student-facing material must teach directly, function cleanly in an LMS, and remain understandable without live lecture support.

### Primary Course Promise

Students move from a business process to a working SQL Server relational database through analysis, modeling, normalization, implementation, querying, operational control, and project revision.

### Technical Environment

The default technical environment remains SQL Server using T-SQL and SQL Server tooling such as SSMS, VS Code with the `mssql` extension, and `sqlcmd` where appropriate.

### Student Context

The course serves Christian business majors. Christian integration should therefore remain part of the course design, but it must stay subordinate to the technical learning goals and appear inside normal instruction, examples, warnings, labs, and project checkpoints rather than as detached devotional material.

## Core Design Shift in v4

v3 treated authentic artifact production as major assessment evidence. v4 keeps the workflow and artifacts, but changes what counts as credible proof of learning.

In v4:

- AI may help students generate ERDs, DBDDs, SQL, procedures, triggers, tests, and revisions.
- AI may also help students execute code, inspect outputs, debug errors, and verify results.
- Therefore, the course should not rely on polished artifacts alone as proof of understanding.
- Major assessments must instead emphasize explanation, diagnosis, comparison, adaptation, and verification against requirements.

## Course Objectives

The course is designed so that students can:

1. know basic database terminology
2. evaluate a business process and determine what data must be stored
3. create ER Diagrams and Database Design Diagrams that reflect a given business process
4. normalize a database design appropriately
5. create and use SQL statements for querying and data manipulation
6. administer introductory backup, recovery, security, and concurrency control work

## Design Commitments

### Whole-System First

Students should still see the overall database workflow early, then revisit the same workflow with increasing depth.

### Running Cases

Lakeside Tutoring Center is the primary running case for v4. Cedar Valley Community Clinic is the alternative case for further discussion, comparison, and extension resources. Use the simple initial case designs early in the course, then revisit the same cases later for redesign work involving shared `User`, `Role`, and role-specific profile tables.

### Module-and-Lesson Structure

Modules are the main instructional units. Lessons divide the module into teachable parts. Weeks are pacing labels only.

### Independent Online Learning

Student-facing content must teach directly, include realistic examples, and support independent study.

### Christian Integration Continuity

v4 does not replace the existing Christian integration standard. Use [textbook/christian_integration_guide.md](../christian_integration_guide.md) as the governing authoring guide for worldview, vocation, stewardship, privacy, justice, trust, and responsible business-data use.

### Naming and Notation Continuity

v4 uses the same naming and notation convention set established in v3. Use [06-design-object-naming-and-notation-conventions.md](06-design-object-naming-and-notation-conventions.md) as the local v4 reference for entity names, attribute names, table names, column names, PK and FK notation, relational schema notation, and ERD versus DBDD boundaries.

### Lesson Naming Continuity

v4 should use one canonical lesson identity system for AI-generated content. Use [05-lesson-writing-agent-index.md](05-lesson-writing-agent-index.md) as the authority for lesson numbers, lesson slugs, and file-output paths. Agents should not invent alternate slugs or filenames.

### AI-Available Reality

The course design must assume students can use AI unless the LMS technically restricts it. Assessment should be valid under that assumption rather than built around unrealistic policing.

### Constructive Alignment

Outcomes, activities, and assessments must align. If the graded evidence does not actually demonstrate the claimed performance, the design is not finished.

## Workflow Spine

The course should repeatedly connect lessons to the same larger workflow:

1. understand the business process
2. identify data requirements and business rules
3. identify entities, attributes, and relationships
4. create the conceptual ER Diagram
5. convert the logical model into an implementation-ready Database Design Diagram
6. implement the design in SQL Server
7. query and manipulate data
8. manage introductory operational concerns
9. revise the solution when constraints or requirements change

## Course-Wide Christian Integration Model

Christian integration in ITM-2100 should follow these rules:

1. Start with real business and database work.
2. Connect that work to Christian responsibility rather than private opinion alone.
3. Keep the reflection tied to a concrete data, design, reporting, access, automation, or governance choice.
4. Ask students to justify technical choices in business terms and ethical terms together where that fit is natural.

This means modules and lessons should not insert isolated faith sidebars and then return to normal content. Integration should appear inside the same examples, common mistakes, project checkpoints, revision prompts, and scenario judgments that already teach database reasoning.

Core themes carried across the course:

- human dignity and neighbor-serving information systems
- vocation and faithful business work
- stewardship of data, time, and organizational resources
- truthfulness, justice, privacy, and accountable reporting

Minimum design expectation:

- each module should include at least two integration touchpoints in normal teaching elements
- at least one touchpoint in each module should connect directly to a project or case decision
- integration language should stay business-facing and technically grounded

## Module Map

The course uses an eight-module structure:

1. The Whole Database Workflow
2. SQL Foundations
3. Core Data Modeling
4. Design Logic
5. Design Artifacts
6. SQL Server Implementation
7. Database Operation and Control
8. Procedural Logic and Final Project Revision

## Artifact Boundaries

### ER Diagram

The ER Diagram is a conceptual model. It shows entities, identifiers, significant attributes, relationships, cardinality, and optionality. It does not include SQL data types, nullability, or implementation-level foreign-key notation.

### Database Design Diagram

The Database Design Diagram is a separate implementation-ready artifact. It shows tables, columns, primary keys, foreign keys, data types, nullability, and other build-ready structural details.

### Separation Rule

The ER Diagram and the Database Design Diagram must remain distinct in instruction, examples, assignments, and assessment.

## Knowledge Model

### Concepts

Concepts answer the question "What is it?"

### Principles

Principles answer the question "What rule or relationship should guide the decision?"

### Procedures

Procedures answer the question "How do I do it?"

### Judgments

Judgments answer the question "How do I know this is the right choice, diagnosis, or revision for this case?"

### Course Rule

Modules and lessons should separate concepts, principles, procedures, and judgments clearly enough that instruction and assessment can target them intentionally.

## Assessment Philosophy

### Assessment Reality

In a fully asynchronous AI-available course, a take-home artifact alone is weak evidence of independent reasoning. v4 therefore treats generated artifacts as useful work products, but not as the sole basis for major grading decisions.

### Assessment Rule

Every major artifact-based assignment must be paired with a second evidence type. Acceptable second evidence includes:

- timed case checks
- critique-and-repair tasks
- annotated walkthroughs
- short screencast defenses
- comparison of alternatives
- output-verification tasks
- change-request revisions
- scenario-based decision memos

### Graded Evidence Priorities

The strongest evidence should come from:

- explanation of why a choice is correct
- diagnosis of flaws, risks, or inconsistencies
- adaptation when business rules change
- verification that outputs satisfy stated requirements
- judgment about whether AI-generated work is trustworthy
- justification of responsible data, design, access, reporting, or automation choices when the module naturally calls for it

### AI Use Policy

The course may allow AI assistance for drafting, coding, querying, testing, debugging, and formatting. Students should still be accountable for:

- framing the problem correctly
- verifying the output
- explaining the logic
- defending final choices
- documenting meaningful AI use when required

## Async Assessment Architecture

The course should favor a repeating pattern:

1. instructional content and guided practice
2. AI-allowed production work or artifact drafting
3. second evidence task that tests explanation, diagnosis, or adaptation
4. revision based on new constraints or detected flaws

Typical course-level weighting target:

- 30 to 40 percent timed quizzes and short case checks
- 25 to 35 percent critique, diagnosis, and repair tasks
- 15 to 25 percent annotated or recorded explanations
- 15 to 25 percent revision and change-request work

## Module Planning Rule

### Planning Logic

Module planning should follow this sequence:

1. determine the module's instructional role in the course sequence
2. identify which knowledge types are dominant in each lesson
3. identify what AI can plausibly generate or verify in that lesson
4. decide what evidence students must still provide themselves
5. pair each major artifact with a second evidence type
6. align module assessment to the actual performance students must demonstrate

### Lesson Strategy Rule

Lesson strategy should still follow the dominant learning type:

- facts: explanation, organization, recall, recognition
- concepts: definition, attributes, examples, non-examples, classification
- principles: rule explanation, judgment, application, diagnosis
- procedures: demonstration, guided practice, execution, error checking
- problem solving: case walkthrough, comparison, revision, verification

## Writing Standards

### Style

The tone should be plain, precise, neutral, and usable. Prefer realistic cases and concrete explanations.

### Depth

Student-facing content must still function as textbook-level instructional material.

### Online Suitability

Instructions, examples, and activity setup must be self-contained for independent use in an LMS.

### AI-Aware Framing

Where appropriate, lessons should explicitly distinguish:

- what students may reasonably ask AI to do
- what students still need to understand
- what common AI-generated mistakes need verification

### Christian Integration Framing

Where appropriate, lessons should also distinguish:

- what business decision carries an ethical or stewardship implication
- who could be harmed by careless data, reporting, access, or automation choices
- how faithful business practice supports the technical goal instead of replacing it

## Quality Rules

### Alignment Rule

Outcomes must align with activities and assessments.

### Evidence Rule

If the only graded evidence is an artifact that AI can plausibly generate well, the assessment design is incomplete.

### Verification Rule

Tasks should require students to verify outputs against stated business rules, not just show that code runs.

### Adaptation Rule

Major modules should include at least one task where a new rule or changed condition forces revision.

### Terminology Rule

Terminology must remain consistent across modules.

### Artifact Rule

Logical and implementation artifacts must remain distinct across instruction and assessment.

### Naming Rule

Naming and notation should remain consistent across modules. Use the shared v4 design-object naming convention file rather than inventing per-module naming patterns.

### Lesson File Rule

Lesson numbers are the primary identifiers. Lesson titles are display text. Lesson slugs are stable filename keys. Once a lesson slug is assigned in the v4 lesson-writing index, do not silently rename it from title drift alone.

### Integration Rule

Christian integration must be embedded consistently and naturally across the course. It should support the technical objective, appear inside ordinary instructional elements, and avoid stand-alone devotional detours.

## Completion Standard

A module is considered planned for v4 when it:

- defines clear instructional scope
- specifies lesson roles
- states what students must know versus what AI may assist with
- includes AI-resilient assessment architecture
- identifies concrete evidence types
- remains consistent with the course workflow and artifact boundaries

## Companion Documents

### [01-module-content.md](01-module-content.md)

Use this file as the index to the v4 module blueprints.

### [modules-plan/](modules-plan/)

Use the relevant module file in this directory for module purposes, lesson breakdowns, human-versus-AI boundaries, and assessment design.

### [02-instructional-strategies-for-lessons.md](02-instructional-strategies-for-lessons.md)

Use this file for v4 lesson-strategy patterns, dominant learning-type guidance, and AI-aware assessment moves.

### [05-lesson-writing-agent-index.md](05-lesson-writing-agent-index.md)

Use this file as the canonical lesson manifest for writing agents. It defines lesson slugs, filename patterns, and the expected output paths for lesson instruction files and draft lesson files.

### [06-design-object-naming-and-notation-conventions.md](06-design-object-naming-and-notation-conventions.md)

Use this file as the shared v4 reference for naming conventions and design-object notation.

### [../christian_integration_guide.md](../christian_integration_guide.md)

Use this file as the course-wide standard for Christian integration themes, writing rules, and touchpoint patterns.
