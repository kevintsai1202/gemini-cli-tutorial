---
url: "https://geminicli.com/docs/cli/token-caching/"
title: "Token Caching and Cost Optimization | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/cli/token-caching/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Token Caching and Cost Optimization

Copy as MarkdownCopied!

Gemini CLI automatically optimizes API costs through token caching when using
API key authentication (Gemini API key or Vertex AI). This feature reuses
previous system instructions and context to reduce the number of tokens
processed in subsequent requests.

**Token caching is available for:**

- API key users (Gemini API key)
- Vertex AI users (with project and location setup)

**Token caching is not available for:**

- OAuth users (Google Personal/Enterprise accounts) - the Code Assist API does
not support cached content creation at this time

You can view your token usage and cached token savings using the `/stats`
command. When cached tokens are available, they will be displayed in the stats
output.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.