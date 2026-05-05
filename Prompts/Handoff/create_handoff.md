---
description: Create handoff document for transferring work to another session
---

# Create Handoff

You are tasked with writing a handoff document to hand off your work to another agent in a new session. You will create a handoff document that is thorough, but also **concise**. The goal is to compact and summarize your context without losing any of the key details of what you're working on.

## Process

### 1. Filepath & Metadata

Use the following information to understand how to create your document:
- **Location**: Create your file in a `sessions` subfolder within the SAME folder where the master plan or feature documentation exists.
- **Filepath format**: `{feature-folder}/sessions/YYYY-MM-DD_HH-MM-SS_description.md`, where:
  - `{feature-folder}` is the folder containing the plan or feature document(s) you are implementing
  - `YYYY-MM-DD` is today's date
  - `HH-MM-SS` is the hours, minutes and seconds based on the current time, in 24-hour format (i.e. use `13:00` for `1:00 pm`)
  - `description` is a brief kebab-case description of the work
- **Note**: Create the `sessions` folder if it doesn't already exist

### 2. Handoff writing.

using the above conventions, write your document. use the defined filepath, and the following YAML frontmatter pattern. Use the metadata gathered in step 1, Structure the document with YAML frontmatter followed by content:

Use the following template structure:

```markdown
---
date: [Current date and time with timezone in ISO format]
author: [Author or agent name]
git_commit: [Current commit hash]
branch: [Current branch name]
repository: [Repository name]
topic: "[Feature/Task Name] Implementation Strategy"
tags: [implementation, strategy, relevant-component-names]
status: complete
last_updated: [Current date in YYYY-MM-DD format]
last_updated_by: [Author name]
type: implementation_strategy
---

# Handoff: {Master Plan Name} - {Session Description}

## Master Plan Reference

{Full path to the master plan document being implemented}

## Task(s)

{description of the task(s) that you were working on, along with the status of each (completed, work in progress, planned/discussed). If you are working on an implementation plan, make sure to call out which phase/section of the master plan you are implementing. Reference specific sections or chapters from the master plan document.}

## Critical References

{List any critical specification documents, architectural decisions, or design docs that must be followed. Include only 2-3 most important file paths. Leave blank if none.}

## Recent changes

{describe recent changes made to the codebase that you made in line:file syntax}

## Learnings

{describe important things that you learned - e.g. patterns, root causes of bugs, or other important pieces of information someone that is picking up your work after you should know. consider listing explicit file paths.}

## Artifacts

{ an exhaustive list of artifacts you produced or updated as filepaths and/or file:line references - e.g. paths to feature documents, implementation plans, etc that should be read in order to resume your work.}

## Action Items & Next Steps

{ a list of action items and next steps for the next agent to accomplish based on your tasks and their statuses}

## Other Notes

{ other notes, references, or useful information - e.g. where relevant sections of the codebase are, where relevant documents are, or other important things you leanrned that you want to pass on but that don't fall into the above categories}
```

---

### 3. Finalize

Once completed, respond to the user confirming the handoff was created, including the full path to the handoff file so they can provide it when resuming work in a new session.

---

## Additional Notes & Instructions

- **more information, not less**. This is a guideline that defines the minimum of what a handoff should be. Always feel free to include more information if necessary.
- **be thorough and precise**. include both top-level objectives, and lower-level details as necessary.
- **avoid excessive code snippets**. While a brief snippet to describe some key change is important, avoid large code blocks or diffs; do not include one unless it's necessary (e.g. pertains to an error you're debugging). Prefer using `path/to/file.ext:line` references that an agent can follow later when it's ready.
