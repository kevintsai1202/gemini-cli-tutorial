---
url: "https://geminicli.com/docs/extensions/getting-started-extensions/"
title: "Getting Started with Gemini CLI Extensions | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/extensions/getting-started-extensions/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Getting Started with Gemini CLI Extensions

Copy as MarkdownCopied!

This guide will walk you through creating your first Gemini CLI extension.
You’ll learn how to set up a new extension, add a custom tool via an MCP server,
create a custom command, and provide context to the model with a `GEMINI.md`
file.

## Prerequisites

[Section titled “Prerequisites”](https://geminicli.com/docs/extensions/getting-started-extensions/#prerequisites)

Before you start, make sure you have the Gemini CLI installed and a basic
understanding of Node.js and TypeScript.

## Step 1: Create a New Extension

[Section titled “Step 1: Create a New Extension”](https://geminicli.com/docs/extensions/getting-started-extensions/#step-1-create-a-new-extension)

The easiest way to start is by using one of the built-in templates. We’ll use
the `mcp-server` example as our foundation.

Run the following command to create a new directory called `my-first-extension`
with the template files:

```
gemini extensions new my-first-extension mcp-server
```

This will create a new directory with the following structure:

```
my-first-extension/

├── example.ts

├── gemini-extension.json

├── package.json

└── tsconfig.json
```

## Step 2: Understand the Extension Files

[Section titled “Step 2: Understand the Extension Files”](https://geminicli.com/docs/extensions/getting-started-extensions/#step-2-understand-the-extension-files)

Let’s look at the key files in your new extension.

### `gemini-extension.json`

[Section titled “gemini-extension.json”](https://geminicli.com/docs/extensions/getting-started-extensions/#gemini-extensionjson)

This is the manifest file for your extension. It tells Gemini CLI how to load
and use your extension.

```
{

  "name": "my-first-extension",

  "version": "1.0.0",

  "mcpServers": {

    "nodeServer": {

      "command": "node",

      "args": ["${extensionPath}${/}dist${/}example.js"],

      "cwd": "${extensionPath}"

    }

  }

}
```

- `name`: The unique name for your extension.
- `version`: The version of your extension.
- `mcpServers`: This section defines one or more Model Context Protocol (MCP)
servers. MCP servers are how you can add new tools for the model to use.

  - `command`, `args`, `cwd`: These fields specify how to start your server.
    Notice the use of the `${extensionPath}` variable, which Gemini CLI replaces
    with the absolute path to your extension’s installation directory. This
    allows your extension to work regardless of where it’s installed.

### `example.ts`

[Section titled “example.ts”](https://geminicli.com/docs/extensions/getting-started-extensions/#examplets)

This file contains the source code for your MCP server. It’s a simple Node.js
server that uses the `@modelcontextprotocol/sdk`.

```
/**

 * @license

 * Copyright 2025 Google LLC

 * SPDX-License-Identifier: Apache-2.0

 */

import { McpServer } from '@modelcontextprotocol/sdk/server/mcp.js';

import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

import { z } from 'zod';

const server = new McpServer({

  name: 'prompt-server',

  version: '1.0.0',

});

// Registers a new tool named 'fetch_posts'

server.registerTool(

  'fetch_posts',

  {

    description: 'Fetches a list of posts from a public API.',

    inputSchema: z.object({}).shape,

  },

  async () => {

    const apiResponse = await fetch(

      'https://jsonplaceholder.typicode.com/posts',

    );

    const posts = await apiResponse.json();

    const response = { posts: posts.slice(0, 5) };

    return {

      content: [\
\
        {\
\
          type: 'text',\
\
          text: JSON.stringify(response),\
\
        },\
\
      ],

    };

  },

);

// ... (prompt registration omitted for brevity)

const transport = new StdioServerTransport();

await server.connect(transport);
```

This server defines a single tool called `fetch_posts` that fetches data from a
public API.

### `package.json` and `tsconfig.json`

[Section titled “package.json and tsconfig.json”](https://geminicli.com/docs/extensions/getting-started-extensions/#packagejson-and-tsconfigjson)

These are standard configuration files for a TypeScript project. The
`package.json` file defines dependencies and a `build` script, and
`tsconfig.json` configures the TypeScript compiler.

## Step 3: Build and Link Your Extension

[Section titled “Step 3: Build and Link Your Extension”](https://geminicli.com/docs/extensions/getting-started-extensions/#step-3-build-and-link-your-extension)

Before you can use the extension, you need to compile the TypeScript code and
link the extension to your Gemini CLI installation for local development.

1. **Install dependencies:**



```
cd my-first-extension

npm install
```

2. **Build the server:**



```
npm run build
```









This will compile `example.ts` into `dist/example.js`, which is the file
referenced in your `gemini-extension.json`.

3. **Link the extension:**

The `link` command creates a symbolic link from the Gemini CLI extensions
directory to your development directory. This means any changes you make
will be reflected immediately without needing to reinstall.



```
gemini extensions link .
```


Now, restart your Gemini CLI session. The new `fetch_posts` tool will be
available. You can test it by asking: “fetch posts”.

## Step 4: Add a Custom Command

[Section titled “Step 4: Add a Custom Command”](https://geminicli.com/docs/extensions/getting-started-extensions/#step-4-add-a-custom-command)

Custom commands provide a way to create shortcuts for complex prompts. Let’s add
a command that searches for a pattern in your code.

1. Create a `commands` directory and a subdirectory for your command group:



```
mkdir -p commands/fs
```

2. Create a file named `commands/fs/grep-code.toml`:



```
prompt = """

Please summarize the findings for the pattern `{{args}}`.




Search Results:

!{grep -r {{args}} .}

"""
```









This command, `/fs:grep-code`, will take an argument, run the `grep` shell
command with it, and pipe the results into a prompt for summarization.


After saving the file, restart the Gemini CLI. You can now run
`/fs:grep-code "some pattern"` to use your new command.

## Step 5: Add a Custom `GEMINI.md`

[Section titled “Step 5: Add a Custom GEMINI.md”](https://geminicli.com/docs/extensions/getting-started-extensions/#step-5-add-a-custom-geminimd)

You can provide persistent context to the model by adding a `GEMINI.md` file to
your extension. This is useful for giving the model instructions on how to
behave or information about your extension’s tools. Note that you may not always
need this for extensions built to expose commands and prompts.

1. Create a file named `GEMINI.md` in the root of your extension directory:



```
# My First Extension Instructions




You are an expert developer assistant. When the user asks you to fetch

posts, use the `fetch_posts` tool. Be concise in your responses.
```

2. Update your `gemini-extension.json` to tell the CLI to load this file:



```
{

     "name": "my-first-extension",

     "version": "1.0.0",

     "contextFileName": "GEMINI.md",

     "mcpServers": {

       "nodeServer": {

         "command": "node",

         "args": ["${extensionPath}${/}dist${/}example.js"],

         "cwd": "${extensionPath}"

       }

     }

}
```


Restart the CLI again. The model will now have the context from your `GEMINI.md`
file in every session where the extension is active.

## Step 6: Releasing Your Extension

[Section titled “Step 6: Releasing Your Extension”](https://geminicli.com/docs/extensions/getting-started-extensions/#step-6-releasing-your-extension)

Once you are happy with your extension, you can share it with others. The two
primary ways of releasing extensions are via a Git repository or through GitHub
Releases. Using a public Git repository is the simplest method.

For detailed instructions on both methods, please refer to the
[Extension Releasing Guide](https://geminicli.com/docs/extensions/extension-releasing).

## Conclusion

[Section titled “Conclusion”](https://geminicli.com/docs/extensions/getting-started-extensions/#conclusion)

You’ve successfully created a Gemini CLI extension! You learned how to:

- Bootstrap a new extension from a template.
- Add custom tools with an MCP server.
- Create convenient custom commands.
- Provide persistent context to the model.
- Link your extension for local development.

From here, you can explore more advanced features and build powerful new
capabilities into the Gemini CLI.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.