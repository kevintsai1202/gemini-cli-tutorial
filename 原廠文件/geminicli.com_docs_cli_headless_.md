---
url: "https://geminicli.com/docs/cli/headless/"
title: "Headless Mode | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/cli/headless/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Headless Mode

Copy as MarkdownCopied!

Headless mode allows you to run Gemini CLI programmatically from command line
scripts and automation tools without any interactive UI. This is ideal for
scripting, automation, CI/CD pipelines, and building AI-powered tools.

- [Headless Mode](https://geminicli.com/docs/cli/headless/#headless-mode)
  - [Overview](https://geminicli.com/docs/cli/headless/#overview)
  - [Basic Usage](https://geminicli.com/docs/cli/headless/#basic-usage)
    - [Direct Prompts](https://geminicli.com/docs/cli/headless/#direct-prompts)
    - [Stdin Input](https://geminicli.com/docs/cli/headless/#stdin-input)
    - [Combining with File Input](https://geminicli.com/docs/cli/headless/#combining-with-file-input)
  - [Output Formats](https://geminicli.com/docs/cli/headless/#output-formats)
    - [Text Output (Default)](https://geminicli.com/docs/cli/headless/#text-output-default)
    - [JSON Output](https://geminicli.com/docs/cli/headless/#json-output)
      - [Response Schema](https://geminicli.com/docs/cli/headless/#response-schema)
      - [Example Usage](https://geminicli.com/docs/cli/headless/#example-usage)
    - [Streaming JSON Output](https://geminicli.com/docs/cli/headless/#streaming-json-output)
      - [When to Use Streaming JSON](https://geminicli.com/docs/cli/headless/#when-to-use-streaming-json)
      - [Event Types](https://geminicli.com/docs/cli/headless/#event-types)
      - [Basic Usage](https://geminicli.com/docs/cli/headless/#basic-usage)
      - [Example Output](https://geminicli.com/docs/cli/headless/#example-output)
      - [Processing Stream Events](https://geminicli.com/docs/cli/headless/#processing-stream-events)
      - [Real-World Examples](https://geminicli.com/docs/cli/headless/#real-world-examples)
    - [File Redirection](https://geminicli.com/docs/cli/headless/#file-redirection)
  - [Configuration Options](https://geminicli.com/docs/cli/headless/#configuration-options)
  - [Examples](https://geminicli.com/docs/cli/headless/#examples)
    - [Code review](https://geminicli.com/docs/cli/headless/#code-review)
    - [Generate commit messages](https://geminicli.com/docs/cli/headless/#generate-commit-messages)
    - [API documentation](https://geminicli.com/docs/cli/headless/#api-documentation)
    - [Batch code analysis](https://geminicli.com/docs/cli/headless/#batch-code-analysis)
    - [Code review](https://geminicli.com/docs/cli/headless/#code-review-1)
    - [Log analysis](https://geminicli.com/docs/cli/headless/#log-analysis)
    - [Release notes generation](https://geminicli.com/docs/cli/headless/#release-notes-generation)
    - [Model and tool usage tracking](https://geminicli.com/docs/cli/headless/#model-and-tool-usage-tracking)
  - [Resources](https://geminicli.com/docs/cli/headless/#resources)

## Overview

[Section titled “Overview”](https://geminicli.com/docs/cli/headless/#overview)

The headless mode provides a headless interface to Gemini CLI that:

- Accepts prompts via command line arguments or stdin
- Returns structured output (text or JSON)
- Supports file redirection and piping
- Enables automation and scripting workflows
- Provides consistent exit codes for error handling

## Basic Usage

[Section titled “Basic Usage”](https://geminicli.com/docs/cli/headless/#basic-usage)

### Direct Prompts

[Section titled “Direct Prompts”](https://geminicli.com/docs/cli/headless/#direct-prompts)

Use the `--prompt` (or `-p`) flag to run in headless mode:

```
gemini --prompt "What is machine learning?"
```

### Stdin Input

[Section titled “Stdin Input”](https://geminicli.com/docs/cli/headless/#stdin-input)

Pipe input to Gemini CLI from your terminal:

```
echo "Explain this code" | gemini
```

### Combining with File Input

[Section titled “Combining with File Input”](https://geminicli.com/docs/cli/headless/#combining-with-file-input)

Read from files and process with Gemini:

```
cat README.md | gemini --prompt "Summarize this documentation"
```

## Output Formats

[Section titled “Output Formats”](https://geminicli.com/docs/cli/headless/#output-formats)

### Text Output (Default)

[Section titled “Text Output (Default)”](https://geminicli.com/docs/cli/headless/#text-output-default)

Standard human-readable output:

```
gemini -p "What is the capital of France?"
```

Response format:

```
The capital of France is Paris.
```

### JSON Output

[Section titled “JSON Output”](https://geminicli.com/docs/cli/headless/#json-output)

Returns structured data including response, statistics, and metadata. This
format is ideal for programmatic processing and automation scripts.

#### Response Schema

[Section titled “Response Schema”](https://geminicli.com/docs/cli/headless/#response-schema)

The JSON output follows this high-level structure:

```
{

  "response": "string", // The main AI-generated content answering your prompt

  "stats": {

    // Usage metrics and performance data

    "models": {

      // Per-model API and token usage statistics

      "[model-name]": {

        "api": {

          /* request counts, errors, latency */

        },

        "tokens": {

          /* prompt, response, cached, total counts */

        }

      }

    },

    "tools": {

      // Tool execution statistics

      "totalCalls": "number",

      "totalSuccess": "number",

      "totalFail": "number",

      "totalDurationMs": "number",

      "totalDecisions": {

        /* accept, reject, modify, auto_accept counts */

      },

      "byName": {

        /* per-tool detailed stats */

      }

    },

    "files": {

      // File modification statistics

      "totalLinesAdded": "number",

      "totalLinesRemoved": "number"

    }

  },

  "error": {

    // Present only when an error occurred

    "type": "string", // Error type (e.g., "ApiError", "AuthError")

    "message": "string", // Human-readable error description

    "code": "number" // Optional error code

  }

}
```

#### Example Usage

[Section titled “Example Usage”](https://geminicli.com/docs/cli/headless/#example-usage)

```
gemini -p "What is the capital of France?" --output-format json
```

Response:

```
{

  "response": "The capital of France is Paris.",

  "stats": {

    "models": {

      "gemini-2.5-pro": {

        "api": {

          "totalRequests": 2,

          "totalErrors": 0,

          "totalLatencyMs": 5053

        },

        "tokens": {

          "prompt": 24939,

          "candidates": 20,

          "total": 25113,

          "cached": 21263,

          "thoughts": 154,

          "tool": 0

        }

      },

      "gemini-2.5-flash": {

        "api": {

          "totalRequests": 1,

          "totalErrors": 0,

          "totalLatencyMs": 1879

        },

        "tokens": {

          "prompt": 8965,

          "candidates": 10,

          "total": 9033,

          "cached": 0,

          "thoughts": 30,

          "tool": 28

        }

      }

    },

    "tools": {

      "totalCalls": 1,

      "totalSuccess": 1,

      "totalFail": 0,

      "totalDurationMs": 1881,

      "totalDecisions": {

        "accept": 0,

        "reject": 0,

        "modify": 0,

        "auto_accept": 1

      },

      "byName": {

        "google_web_search": {

          "count": 1,

          "success": 1,

          "fail": 0,

          "durationMs": 1881,

          "decisions": {

            "accept": 0,

            "reject": 0,

            "modify": 0,

            "auto_accept": 1

          }

        }

      }

    },

    "files": {

      "totalLinesAdded": 0,

      "totalLinesRemoved": 0

    }

  }

}
```

### Streaming JSON Output

[Section titled “Streaming JSON Output”](https://geminicli.com/docs/cli/headless/#streaming-json-output)

Returns real-time events as newline-delimited JSON (JSONL). Each significant
action (initialization, messages, tool calls, results) emits immediately as it
occurs. This format is ideal for monitoring long-running operations, building
UIs with live progress, and creating automation pipelines that react to events.

#### When to Use Streaming JSON

[Section titled “When to Use Streaming JSON”](https://geminicli.com/docs/cli/headless/#when-to-use-streaming-json)

Use `--output-format stream-json` when you need:

- **Real-time progress monitoring** \- See tool calls and responses as they
happen
- **Event-driven automation** \- React to specific events (e.g., tool failures)
- **Live UI updates** \- Build interfaces showing AI agent activity in real-time
- **Detailed execution logs** \- Capture complete interaction history with
timestamps
- **Pipeline integration** \- Stream events to logging/monitoring systems

#### Event Types

[Section titled “Event Types”](https://geminicli.com/docs/cli/headless/#event-types)

The streaming format emits 6 event types:

1. **`init`** \- Session starts (includes session\_id, model)
2. **`message`** \- User prompts and assistant responses
3. **`tool_use`** \- Tool call requests with parameters
4. **`tool_result`** \- Tool execution results (success/error)
5. **`error`** \- Non-fatal errors and warnings
6. **`result`** \- Final session outcome with aggregated stats

#### Basic Usage

[Section titled “Basic Usage”](https://geminicli.com/docs/cli/headless/#basic-usage-1)

```
# Stream events to console

gemini --output-format stream-json --prompt "What is 2+2?"

# Save event stream to file

gemini --output-format stream-json --prompt "Analyze this code" > events.jsonl

# Parse with jq

gemini --output-format stream-json --prompt "List files" | jq -r '.type'
```

#### Example Output

[Section titled “Example Output”](https://geminicli.com/docs/cli/headless/#example-output)

Each line is a complete JSON event:

```
{"type":"init","timestamp":"2025-10-10T12:00:00.000Z","session_id":"abc123","model":"gemini-2.0-flash-exp"}

{"type":"message","role":"user","content":"List files in current directory","timestamp":"2025-10-10T12:00:01.000Z"}

{"type":"tool_use","tool_name":"Bash","tool_id":"bash-123","parameters":{"command":"ls -la"},"timestamp":"2025-10-10T12:00:02.000Z"}

{"type":"tool_result","tool_id":"bash-123","status":"success","output":"file1.txt\nfile2.txt","timestamp":"2025-10-10T12:00:03.000Z"}

{"type":"message","role":"assistant","content":"Here are the files...","delta":true,"timestamp":"2025-10-10T12:00:04.000Z"}

{"type":"result","status":"success","stats":{"total_tokens":250,"input_tokens":50,"output_tokens":200,"duration_ms":3000,"tool_calls":1},"timestamp":"2025-10-10T12:00:05.000Z"}
```

### File Redirection

[Section titled “File Redirection”](https://geminicli.com/docs/cli/headless/#file-redirection)

Save output to files or pipe to other commands:

```
# Save to file

gemini -p "Explain Docker" > docker-explanation.txt

gemini -p "Explain Docker" --output-format json > docker-explanation.json

# Append to file

gemini -p "Add more details" >> docker-explanation.txt

# Pipe to other tools

gemini -p "What is Kubernetes?" --output-format json | jq '.response'

gemini -p "Explain microservices" | wc -w

gemini -p "List programming languages" | grep -i "python"
```

## Configuration Options

[Section titled “Configuration Options”](https://geminicli.com/docs/cli/headless/#configuration-options)

Key command-line options for headless usage:

| Option | Description | Example |
| --- | --- | --- |
| `--prompt`, `-p` | Run in headless mode | `gemini -p "query"` |
| `--output-format` | Specify output format (text, json) | `gemini -p "query" --output-format json` |
| `--model`, `-m` | Specify the Gemini model | `gemini -p "query" -m gemini-2.5-flash` |
| `--debug`, `-d` | Enable debug mode | `gemini -p "query" --debug` |
| `--include-directories` | Include additional directories | `gemini -p "query" --include-directories src,docs` |
| `--yolo`, `-y` | Auto-approve all actions | `gemini -p "query" --yolo` |
| `--approval-mode` | Set approval mode | `gemini -p "query" --approval-mode auto_edit` |

For complete details on all available configuration options, settings files, and
environment variables, see the
[Configuration Guide](https://geminicli.com/docs/get-started/configuration).

## Examples

[Section titled “Examples”](https://geminicli.com/docs/cli/headless/#examples)

#### Code review

[Section titled “Code review”](https://geminicli.com/docs/cli/headless/#code-review)

```
cat src/auth.py | gemini -p "Review this authentication code for security issues" > security-review.txt
```

#### Generate commit messages

[Section titled “Generate commit messages”](https://geminicli.com/docs/cli/headless/#generate-commit-messages)

```
result=$(git diff --cached | gemini -p "Write a concise commit message for these changes" --output-format json)

echo "$result" | jq -r '.response'
```

#### API documentation

[Section titled “API documentation”](https://geminicli.com/docs/cli/headless/#api-documentation)

```
result=$(cat api/routes.js | gemini -p "Generate OpenAPI spec for these routes" --output-format json)

echo "$result" | jq -r '.response' > openapi.json
```

#### Batch code analysis

[Section titled “Batch code analysis”](https://geminicli.com/docs/cli/headless/#batch-code-analysis)

```
for file in src/*.py; do

    echo "Analyzing $file..."

    result=$(cat "$file" | gemini -p "Find potential bugs and suggest improvements" --output-format json)

    echo "$result" | jq -r '.response' > "reports/$(basename "$file").analysis"

    echo "Completed analysis for $(basename "$file")" >> reports/progress.log

done
```

#### Code review

[Section titled “Code review”](https://geminicli.com/docs/cli/headless/#code-review-1)

```
result=$(git diff origin/main...HEAD | gemini -p "Review these changes for bugs, security issues, and code quality" --output-format json)

echo "$result" | jq -r '.response' > pr-review.json
```

#### Log analysis

[Section titled “Log analysis”](https://geminicli.com/docs/cli/headless/#log-analysis)

```
grep "ERROR" /var/log/app.log | tail -20 | gemini -p "Analyze these errors and suggest root cause and fixes" > error-analysis.txt
```

#### Release notes generation

[Section titled “Release notes generation”](https://geminicli.com/docs/cli/headless/#release-notes-generation)

```
result=$(git log --oneline v1.0.0..HEAD | gemini -p "Generate release notes from these commits" --output-format json)

response=$(echo "$result" | jq -r '.response')

echo "$response"

echo "$response" >> CHANGELOG.md
```

#### Model and tool usage tracking

[Section titled “Model and tool usage tracking”](https://geminicli.com/docs/cli/headless/#model-and-tool-usage-tracking)

```
result=$(gemini -p "Explain this database schema" --include-directories db --output-format json)

total_tokens=$(echo "$result" | jq -r '.stats.models // {} | to_entries | map(.value.tokens.total) | add // 0')

models_used=$(echo "$result" | jq -r '.stats.models // {} | keys | join(", ") | if . == "" then "none" else . end')

tool_calls=$(echo "$result" | jq -r '.stats.tools.totalCalls // 0')

tools_used=$(echo "$result" | jq -r '.stats.tools.byName // {} | keys | join(", ") | if . == "" then "none" else . end')

echo "$(date): $total_tokens tokens, $tool_calls tool calls ($tools_used) used with models: $models_used" >> usage.log

echo "$result" | jq -r '.response' > schema-docs.md

echo "Recent usage trends:"

tail -5 usage.log
```

## Resources

[Section titled “Resources”](https://geminicli.com/docs/cli/headless/#resources)

- [CLI Configuration](https://geminicli.com/docs/get-started/configuration) \- Complete configuration
guide
- [Authentication](https://geminicli.com/docs/get-started/authentication) \- Setup authentication
- [Commands](https://geminicli.com/docs/cli/commands) \- Interactive commands reference
- [Tutorials](https://geminicli.com/docs/cli/tutorials) \- Step-by-step automation guides

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.