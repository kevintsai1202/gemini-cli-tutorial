---
url: "https://geminicli.com/docs/tools/todos/"
title: "Todo Tool (`write_todos`) | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/tools/todos/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Todo Tool (\`write\_todos\`)

Copy as MarkdownCopied!

This document describes the `write_todos` tool for the Gemini CLI.

## Description

[Section titled “Description”](https://geminicli.com/docs/tools/todos/#description)

The `write_todos` tool allows the Gemini agent to create and manage a list of
subtasks for complex user requests. This provides you, the user, with greater
visibility into the agent’s plan and its current progress.

### Arguments

[Section titled “Arguments”](https://geminicli.com/docs/tools/todos/#arguments)

`write_todos` takes one argument:

- `todos` (array of objects, required): The complete list of todo items. This
replaces the existing list. Each item includes:

  - `description` (string): The task description.
  - `status` (string): The current status (`pending`, `in_progress`,
    `completed`, or `cancelled`).

## Behavior

[Section titled “Behavior”](https://geminicli.com/docs/tools/todos/#behavior)

The agent uses this tool to break down complex multi-step requests into a clear
plan.

- **Progress Tracking:** The agent updates this list as it works, marking tasks
as `completed` when done.
- **Single Focus:** Only one task will be marked `in_progress` at a time,
indicating exactly what the agent is currently working on.
- **Dynamic Updates:** The plan may evolve as the agent discovers new
information, leading to new tasks being added or unnecessary ones being
cancelled.

When active, the current `in_progress` task is displayed above the input box,
keeping you informed of the immediate action. You can toggle the full view of
the todo list at any time by pressing `Ctrl+T`.

Usage example (internal representation):

```
write_todos({

  todos: [\
\
    { description: 'Initialize new React project', status: 'completed' },\
\
    { description: 'Implement state management', status: 'in_progress' },\
\
    { description: 'Create API service', status: 'pending' },\
\
  ],

});
```

## Important notes

[Section titled “Important notes”](https://geminicli.com/docs/tools/todos/#important-notes)

- **Enabling:** This tool is disabled by default. To use it, you must enable it
in your `settings.json` file by setting `"useWriteTodos": true`.

- **Intended Use:** This tool is primarily used by the agent for complex,
multi-turn tasks. It is generally not used for simple, single-turn questions.


This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.