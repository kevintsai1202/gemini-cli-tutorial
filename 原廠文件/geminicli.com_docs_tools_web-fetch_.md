---
url: "https://geminicli.com/docs/tools/web-fetch/"
title: "Web Fetch Tool (`web_fetch`) | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/tools/web-fetch/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Web Fetch Tool (\`web\_fetch\`)

Copy as MarkdownCopied!

This document describes the `web_fetch` tool for the Gemini CLI.

## Description

[Section titled “Description”](https://geminicli.com/docs/tools/web-fetch/#description)

Use `web_fetch` to summarize, compare, or extract information from web pages.
The `web_fetch` tool processes content from one or more URLs (up to 20) embedded
in a prompt. `web_fetch` takes a natural language prompt and returns a generated
response.

### Arguments

[Section titled “Arguments”](https://geminicli.com/docs/tools/web-fetch/#arguments)

`web_fetch` takes one argument:

- `prompt` (string, required): A comprehensive prompt that includes the URL(s)
(up to 20) to fetch and specific instructions on how to process their content.
For example:
`"Summarize https://example.com/article and extract key points from https://another.com/data"`.
The prompt must contain at least one URL starting with `http://` or
`https://`.

## How to use `web_fetch` with the Gemini CLI

[Section titled “How to use web\_fetch with the Gemini CLI”](https://geminicli.com/docs/tools/web-fetch/#how-to-use-web_fetch-with-the-gemini-cli)

To use `web_fetch` with the Gemini CLI, provide a natural language prompt that
contains URLs. The tool will ask for confirmation before fetching any URLs. Once
confirmed, the tool will process URLs through Gemini API’s `urlContext`.

If the Gemini API cannot access the URL, the tool will fall back to fetching
content directly from the local machine. The tool will format the response,
including source attribution and citations where possible. The tool will then
provide the response to the user.

Usage:

```
web_fetch(prompt="Your prompt, including a URL such as https://google.com.")
```

## `web_fetch` examples

[Section titled “web\_fetch examples”](https://geminicli.com/docs/tools/web-fetch/#web_fetch-examples)

Summarize a single article:

```
web_fetch(prompt="Can you summarize the main points of https://example.com/news/latest")
```

Compare two articles:

```
web_fetch(prompt="What are the differences in the conclusions of these two papers: https://arxiv.org/abs/2401.0001 and https://arxiv.org/abs/2401.0002?")
```

## Important notes

[Section titled “Important notes”](https://geminicli.com/docs/tools/web-fetch/#important-notes)

- **URL processing:**`web_fetch` relies on the Gemini API’s ability to access
and process the given URLs.
- **Output quality:** The quality of the output will depend on the clarity of
the instructions in the prompt.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.