# Module 8 Overview: Procedural Logic and Final Project Revision

## Instructor-Facing Content

### Module Purpose

Module 8 is the bounded-automation and final-revision module. Students should learn to justify procedural choices, test procedural behavior, and revise the full project package when a late rule or constraint changes the system.

### Implementation Emphasis

- keep stored procedures and triggers narrow, purposeful, and testable
- teach the lesson sequence as a progression from reusable operations to event-driven logic to full-project revision
- require students to compare procedures, triggers, constraints, queries, permissions, and human review rather than treating automation as the default
- keep final-project revision focused on cross-artifact coherence, not cosmetic cleanup
- embed Christian integration inside ordinary checkpoints about trustworthy automation, faithful follow-through, and honest limitation statements

### Alignment

- Module 8 should align to the v4 assessment shift away from polished artifacts alone and toward explanation, diagnosis, adaptation, and verification
- Lesson 8.1 introduces stored-procedure judgment and testing
- Lesson 8.2 deepens trigger judgment and automation boundaries
- Lesson 8.3 makes change-request revision the capstone performance
- The module should stay inside introductory procedural logic and full-project revision, not drift into advanced procedural patterns, performance tuning, or broader software-engineering automation topics

### Grading Focus

Grade the reasoning as seriously as the SQL artifact.

- whether the procedural choice is justified against at least one stronger or weaker alternative
- whether expected and unexpected behavior are defined and tested clearly
- whether the student identifies the right affected artifacts after a late change
- whether the revision path starts at the earliest affected artifact and stays coherent downstream
- whether the student explains limits, access implications, and trustworthiness honestly

### Likely Misconceptions

- "If SQL Server can automate it, it should."
- "A procedure or trigger that compiles is finished."
- "A trigger is the advanced answer to every business rule."
- "Final revision means polishing files instead of tracing cross-artifact consequences."
- "If the SQL works, permissions, views, diagrams, and tests do not need review."

### Boundary And Risk Notes

- do not let students treat triggers as invisible business policy engines
- do not let final revision collapse the ERD, DBDD, and implementation into one blurred artifact
- do not accept "changed everything" or "only changed SQL" responses without case-based justification
- do not grade artifact polish as stronger evidence than adaptation, verification, and explanation
- keep automation warnings concrete: fairness-sensitive, access-sensitive, or judgment-heavy decisions may require human review instead of full database automation
