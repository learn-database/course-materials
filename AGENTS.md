# Agent Instructions

This is a public repository. Treat every committed file as visible to students, the public internet, and future contributors.

## Public Repository Safety

Never commit sensitive information, including:

- API keys, access tokens, OAuth secrets, LTI client secrets, private keys, certificates, passwords, or session cookies
- `.env` files or machine-specific configuration files
- real student names, emails, IDs, grades, submissions, accommodations, advising notes, or analytics exports
- Canvas course exports that include users, enrollments, submissions, gradebook data, or unpublished institutional data
- private institutional URLs, internal-only credentials, or vendor account details

Use placeholders instead:

```text
CANVAS_CLIENT_ID=<replace-with-client-id>
LTI_PRIVATE_KEY=<store-outside-repo>
STUDENT_NAME=Example Student
CANVAS_COURSE_ID=000000
```

If a task requires real credentials, rosters, submissions, or grade data, keep that material outside this repository and document only the public-safe setup steps.

## Before Committing

Before staging or committing, inspect the diff for secrets and private data:

```text
git status --short
git diff
git diff --cached
```

If sensitive content appears in the diff, stop and remove it before committing. Do not assume that `.gitignore` is enough; inspect the actual staged changes.

## Course Content Rules

- Use only public-safe examples, fictional students, and fictional organizations unless the source is already approved for public use.
- Keep Lakeside Tutoring Center as the primary running case and Cedar Valley Community Clinic as the alternative case unless the course design changes.
- Do not invent official course objectives, policies, rubrics, or institutional requirements.
- Preserve Christian integration guidance from `textbook/christian_integration_guide.md` when authoring course content.

## AI Agent Handoff

When asking another AI agent to work in this repo, include this instruction:

```text
This is a public repository. Do not write or commit secrets, credentials, real student data, Canvas exports with user data, or institution-private information. Use placeholders and public-safe fictional examples only.
```
