# v4 Modules

This folder uses the lesson-first v4 authoring structure.

Each module folder follows this pattern:

```text
module-03-core-data-modeling/
  overview.md
  module.md
  instructor.md
  lessons/
    lesson-03-02-relationships-and-cardinality/
      lesson.md
      instructor.md
      authoring-instructions.md
      import.yml
```

File roles:

- `overview.md`: concise module overview.
- `module.md`: student-facing module-level content.
- `instructor.md`: module-level instructor guidance.
- `lesson.md`: student-facing lesson source.
- `instructor.md` inside a lesson folder: lesson-specific instructor guidance.
- `authoring-instructions.md`: AI/content-agent drafting prompt and constraints for that lesson.
- `import.yml`: workbook-player mapping for lesson segments, source sections, interactions, scoring mode, and ordering.

Reserved future lesson files:

- `assets/`: lesson-specific images, diagrams, SQL files, data files, or other supporting resources.

Keep lesson-specific material inside the lesson folder. Keep course-wide, module-wide, case, assignment, and assessment planning files in their existing v4 folders until they are intentionally decomposed into lesson-level artifacts.
