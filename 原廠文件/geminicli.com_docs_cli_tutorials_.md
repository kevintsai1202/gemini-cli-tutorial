---
url: "https://geminicli.com/docs/cli/tutorials/"
title: "Tutorials | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/cli/tutorials/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Tutorials

Copy as MarkdownCopied!

This page contains tutorials for interacting with Gemini CLI.

## Setting up a Model Context Protocol (MCP) server

[Section titled “Setting up a Model Context Protocol (MCP) server”](https://geminicli.com/docs/cli/tutorials/#setting-up-a-model-context-protocol-mcp-server)

> \[!CAUTION\] Before using a third-party MCP server, ensure you trust its source
> and understand the tools it provides. Your use of third-party servers is at
> your own risk.

This tutorial demonstrates how to set up a MCP server, using the
[GitHub MCP server](https://github.com/github/github-mcp-server) as an example.
The GitHub MCP server provides tools for interacting with GitHub repositories,
such as creating issues and commenting on pull requests.

### Prerequisites

[Section titled “Prerequisites”](https://geminicli.com/docs/cli/tutorials/#prerequisites)

Before you begin, ensure you have the following installed and configured:

- **Docker:** Install and run [Docker](https://www.docker.com/).
- **GitHub Personal Access Token (PAT):** Create a new [classic](https://github.com/settings/tokens/new) or
[fine-grained](https://github.com/settings/personal-access-tokens/new) PAT with the necessary scopes.

### Guide

[Section titled “Guide”](https://geminicli.com/docs/cli/tutorials/#guide)

#### Configure the MCP server in `settings.json`

[Section titled “Configure the MCP server in settings.json”](https://geminicli.com/docs/cli/tutorials/#configure-the-mcp-server-in-settingsjson)

In your project’s root directory, create or open the
[`.gemini/settings.json` file](https://geminicli.com/docs/get-started/configuration). Within the
file, add the `mcpServers` configuration block, which provides instructions for
how to launch the GitHub MCP server.

```
{

  "mcpServers": {

    "github": {

      "command": "docker",

      "args": [\
\
        "run",\
\
        "-i",\
\
        "--rm",\
\
        "-e",\
\
        "GITHUB_PERSONAL_ACCESS_TOKEN",\
\
        "ghcr.io/github/github-mcp-server"\
\
      ],

      "env": {

        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_PERSONAL_ACCESS_TOKEN}"

      }

    }

  }

}
```

#### Set your GitHub token

[Section titled “Set your GitHub token”](https://geminicli.com/docs/cli/tutorials/#set-your-github-token)

> \[!CAUTION\] Using a broadly scoped personal access token that has access to
> personal and private repositories can lead to information from the private
> repository being leaked into the public repository. We recommend using a
> fine-grained access token that doesn’t share access to both public and private
> repositories.

Use an environment variable to store your GitHub PAT:

```
GITHUB_PERSONAL_ACCESS_TOKEN="pat_YourActualGitHubTokenHere"
```

Gemini CLI uses this value in the `mcpServers` configuration that you defined in
the `settings.json` file.

#### Launch Gemini CLI and verify the connection

[Section titled “Launch Gemini CLI and verify the connection”](https://geminicli.com/docs/cli/tutorials/#launch-gemini-cli-and-verify-the-connection)

When you launch Gemini CLI, it automatically reads your configuration and
launches the GitHub MCP server in the background. You can then use natural
language prompts to ask Gemini CLI to perform GitHub actions. For example:

```
"get all open issues assigned to me in the 'foo/bar' repo and prioritize them"
```

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.