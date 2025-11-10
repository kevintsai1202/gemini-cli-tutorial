---
url: "https://geminicli.com/docs/tools/memory/"
title: "Memory Tool (`save_memory`) | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/tools/memory/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Memory Tool (\`save\_memory\`)

Copy as MarkdownCopied!

This document describes the `save_memory` tool for the Gemini CLI.

## Description

[Section titled “Description”](https://geminicli.com/docs/tools/memory/#description)

Use `save_memory` to save and recall information across your Gemini CLI
sessions. With `save_memory`, you can direct the CLI to remember key details
across sessions, providing personalized and directed assistance.

### Arguments

[Section titled “Arguments”](https://geminicli.com/docs/tools/memory/#arguments)

`save_memory` takes one argument:

- `fact` (string, required): The specific fact or piece of information to
remember. This should be a clear, self-contained statement written in natural
language.

## How to use `save_memory` with the Gemini CLI

[Section titled “How to use save\_memory with the Gemini CLI”](https://geminicli.com/docs/tools/memory/#how-to-use-save_memory-with-the-gemini-cli)

The tool appends the provided `fact` to a special `GEMINI.md` file located in
the user’s home directory (`~/.gemini/GEMINI.md`). This file can be configured
to have a different name.

Once added, the facts are stored under a `## Gemini Added Memories` section.
This file is loaded as context in subsequent sessions, allowing the CLI to
recall the saved information.

Usage:

```
save_memory(fact="Your fact here.")
```

### `save_memory` examples

[Section titled “save\_memory examples”](https://geminicli.com/docs/tools/memory/#save_memory-examples)

Remember a user preference:

```
save_memory(fact="My preferred programming language is Python.")
```

Store a project-specific detail:

```
save_memory(fact="The project I'm currently working on is called 'gemini-cli'.")
```

## Important notes

[Section titled “Important notes”](https://geminicli.com/docs/tools/memory/#important-notes)

- **General usage:** This tool should be used for concise, important facts. It
is not intended for storing large amounts of data or conversational history.
- **Memory file:** The memory file is a plain text Markdown file, so you can
view and edit it manually if needed.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.