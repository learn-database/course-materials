# Lesson 1.1: Why Databases Matter

## Instructor-Facing Content

### Module

Module 1: `The Whole Database Workflow`

### Lesson Purpose

Introduce the course from the business side of database work. Students should learn the language needed to describe why organizations keep structured records, compare spreadsheet versus disconnected-file versus database approaches, and judge when a database is warranted.

### Module Context

This is the opening lesson for Module 1 and for the course as a whole. No earlier lesson in the module prepares for it; instead, it establishes the business framing and terminology that Lesson `1.2` will build on when students move into the end-to-end workflow and artifact boundaries. It also sets the module's central theme that a polished deliverable is not the same thing as justified database reasoning.

### Primary Learning Type(s)

Facts / declarative knowledge

### Secondary Learning Type(s), If Any

Concepts

### Estimated Time

50 to 65 minutes

### Lesson Outcomes

By the end of the lesson, students should be able to:

- distinguish `business process`, `data`, `information`, and `database`
- compare spreadsheet, disconnected-file, and database approaches
- explain when a database is warranted and when a simpler tool is enough
- identify `table`, `row`, and `column` in a simple example
- justify a tool recommendation with business reasoning about updates, relationships, reporting, and trust

### Module Alignment

- supports the Module 1 objective of giving students a whole-system view by starting with the business need for organized records
- supports the Module 1 objective of judging when a scenario calls for a database versus a simpler tool
- prepares students for the module's case-framing check by building terminology accuracy and scenario-classification skill

### Course Objective Alignment

- Objective 1: know basic database terminology
- Objective 2: evaluate a business process and determine what data must be stored

### Lesson Sequence Role

Introduces module knowledge and establishes the module's judgment frame.

### Required Prior Knowledge

- ability to read a short business scenario carefully
- everyday familiarity with organizational records such as customers, appointments, payments, or schedules
- no prior SQL, modeling, or systems-analysis knowledge required

### Lesson Opening Guidance

Open with a simple contrast that reveals the tool-fit problem quickly. For example, compare a one-time event roster with a tutoring center that must coordinate students, tutors, sessions, and payment status across recurring updates. Ask what goes wrong when the same facts are stored in several places and the director asks for a report that staff cannot fully trust.

Keep the opening focused on business reliability and truthful reporting, not on software enthusiasm.

### Teaching Notes

- Keep the lesson business-facing and beginner-friendly. Students do not need implementation detail yet.
- Treat `table`, `row`, and `column` as recognition vocabulary only.
- Make the contrast among spreadsheet, disconnected-file, and database approaches explicit. Students should leave knowing that the comparison is about fit, not prestige.
- Stress that "database warranted" depends on multiple factors together: related records, repeated updates, reporting needs, shared usage, and business risk.
- Use the tutoring-center case consistently so students can focus on reasoning instead of relearning new scenario details.
- Reinforce that AI can generate vague recommendations quickly, so students must still verify the fit and the reasoning.

### Online Activities

- complete the guided classification prompts
- complete the tool-fit comparison exercise
- respond to the harm-oriented trust question
- critique the sample AI-style recommendation before submitting the graded work

### Homework / Graded Assignments

`Assignment 1: Tool-Fit Case Check`

- students classify three short scenarios by best current fit: spreadsheet, disconnected files, or database
- students provide a short justification for each choice

`Assignment 2: Recommendation Critique`

- students critique and improve a weak recommendation about whether a database is warranted
- students connect the reasoning to business process, trustworthy reporting, and potential harm from poor structure

### Deliverables

- one completed tool-fit case check
- one 150 to 250 word recommendation critique

### Assessment Plan

Formative evidence:

- accurate term classification
- correct identification of tool-fit factors in short scenarios
- clear explanation of who could be harmed when poor structure distorts reporting or service
- critique of a weak AI-generated-style recommendation

Graded evidence:

- `Assignment 1` checks scenario classification and brief business justification
- `Assignment 2` checks whether students can evaluate reasoning quality rather than merely produce polished prose

This lesson avoids over-relying on an AI-generable artifact by asking students to classify cases, critique weak reasoning, and justify why a database is or is not warranted in specific contexts.

Stronger performance looks like:

- precise use of terms without mixing `data` and `information`
- clear recognition that disconnected files can fail even when each individual file looks reasonable
- explicit explanation of why a spreadsheet may still be the correct tool in a simple case
- direct connection between structure problems and trust, stewardship, service, or reporting consequences

### Suggested Rubric Focus

`Assignment 1: Tool-Fit Case Check`

- the selected approach fits the scenario described
- the justification names relevant factors such as repeated updates, related records, reporting needs, or shared-source requirements
- the response avoids assuming a database is always better
- the response uses business-facing language rather than technical jargon

`Assignment 2: Recommendation Critique`

- the student judges whether the original recommendation is adequate
- the revised reasoning explains the business process clearly
- the student makes a defensible decision about whether a database is warranted
- the response names at least one plausible harm tied to distorted reporting or weak service
- the response improves the logic, not only the wording

### Common Misconceptions

- students may assume a database is always the most professional answer
- students may confuse `business process` with the files or reports used to support it
- students may treat `data` and `information` as identical
- students may think the problem is file quantity alone rather than coordination and trustworthiness
- students may jump into implementation details before they can explain why the organization needs structured support

### Christian Integration Notes

Keep integration inside normal teaching elements. The strongest touchpoint in this lesson is the harm question tied to distorted reporting or service. Frame poor structure as a stewardship and truthfulness problem: weak recordkeeping wastes time, creates avoidable rework, and can misrepresent what the organization owes, delivered, or completed. Ask who is affected when reports are not trustworthy, but keep the discussion connected to the case and the tool decision.

### Workflow Connection

This lesson occupies the first step of the larger workflow: understanding the business process and judging whether structured data support is needed. Lesson `1.2` then extends that reasoning into the full database workflow from business process to implementation-ready work.
