---
url: "https://geminicli.com/docs/cli/"
title: "Gemini CLI | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/cli/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Gemini CLI

Copy as MarkdownCopied!

Within Gemini CLI, `packages/cli` is the frontend for users to send and receive
prompts with the Gemini AI model and its associated tools. For a general
overview of Gemini CLI, see the [main documentation page](https://geminicli.com/docs).

## Basic features

[Section titled “Basic features”](https://geminicli.com/docs/cli/#basic-features)

- **[Commands](https://geminicli.com/docs/cli/commands):** A reference for all built-in slash commands
(e.g., `/help`, `/chat`, `/tools`).
- **[Custom Commands](https://geminicli.com/docs/cli/custom-commands):** Create your own commands and
shortcuts for frequently used prompts.
- **[Headless Mode](https://geminicli.com/docs/cli/headless):** Use Gemini CLI programmatically for
scripting and automation.
- **[Themes](https://geminicli.com/docs/cli/themes):** Customizing the CLI’s appearance with different
themes.
- **[Keyboard Shortcuts](https://geminicli.com/docs/cli/keyboard-shortcuts):** A reference for all
keyboard shortcuts to improve your workflow.
- **[Tutorials](https://geminicli.com/docs/cli/tutorials):** Step-by-step guides for common tasks.

## Advanced features

[Section titled “Advanced features”](https://geminicli.com/docs/cli/#advanced-features)

- **[Checkpointing](https://geminicli.com/docs/cli/checkpointing):** Automatically save and restore
snapshots of your session and files.
- **[Enterprise Configuration](https://geminicli.com/docs/cli/enterprise):** Deploying and manage Gemini
CLI in an enterprise environment.
- **[Sandboxing](https://geminicli.com/docs/cli/sandbox):** Isolate tool execution in a secure,
containerized environment.
- **[Telemetry](https://geminicli.com/docs/cli/telemetry):** Configure observability to monitor usage and
performance.
- **[Token Caching](https://geminicli.com/docs/cli/token-caching):** Optimize API costs by caching tokens.
- **[Trusted Folders](https://geminicli.com/docs/cli/trusted-folders):** A security feature to control
which projects can use the full capabilities of the CLI.
- **[Ignoring Files (.geminiignore)](https://geminicli.com/docs/cli/gemini-ignore):** Exclude specific
files and directories from being accessed by tools.
- **[Context Files (GEMINI.md)](https://geminicli.com/docs/cli/gemini-md):** Provide persistent,
hierarchical context to the model.

## Non-interactive mode

[Section titled “Non-interactive mode”](https://geminicli.com/docs/cli/#non-interactive-mode)

Gemini CLI can be run in a non-interactive mode, which is useful for scripting
and automation. In this mode, you pipe input to the CLI, it executes the
command, and then it exits.

The following example pipes a command to Gemini CLI from your terminal:

```
echo "What is fine tuning?" | gemini
```

You can also use the `--prompt` or `-p` flag:

```
gemini -p "What is fine tuning?"
```

For comprehensive documentation on headless usage, scripting, automation, and
advanced examples, see the **[Headless Mode](https://geminicli.com/docs/cli/headless)** guide.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.