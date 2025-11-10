---
url: "https://geminicli.com/docs/tools/web-search/"
title: "Web Search Tool (`google_web_search`) | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/tools/web-search/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Web Search Tool (\`google\_web\_search\`)

Copy as MarkdownCopied!

This document describes the `google_web_search` tool.

## Description

[Section titled “Description”](https://geminicli.com/docs/tools/web-search/#description)

Use `google_web_search` to perform a web search using Google Search via the
Gemini API. The `google_web_search` tool returns a summary of web results with
sources.

### Arguments

[Section titled “Arguments”](https://geminicli.com/docs/tools/web-search/#arguments)

`google_web_search` takes one argument:

- `query` (string, required): The search query.

## How to use `google_web_search` with the Gemini CLI

[Section titled “How to use google\_web\_search with the Gemini CLI”](https://geminicli.com/docs/tools/web-search/#how-to-use-google_web_search-with-the-gemini-cli)

The `google_web_search` tool sends a query to the Gemini API, which then
performs a web search. `google_web_search` will return a generated response
based on the search results, including citations and sources.

Usage:

```
google_web_search(query="Your query goes here.")
```

## `google_web_search` examples

[Section titled “google\_web\_search examples”](https://geminicli.com/docs/tools/web-search/#google_web_search-examples)

Get information on a topic:

```
google_web_search(query="latest advancements in AI-powered code generation")
```

## Important notes

[Section titled “Important notes”](https://geminicli.com/docs/tools/web-search/#important-notes)

- **Response returned:** The `google_web_search` tool returns a processed
summary, not a raw list of search results.
- **Citations:** The response includes citations to the sources used to generate
the summary.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.