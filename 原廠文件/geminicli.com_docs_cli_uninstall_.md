---
url: "https://geminicli.com/docs/cli/uninstall/"
title: "Uninstalling the CLI | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/cli/uninstall/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Uninstalling the CLI

Copy as MarkdownCopied!

Your uninstall method depends on how you ran the CLI. Follow the instructions
for either npx or a global npm installation.

## Method 1: Using npx

[Section titled “Method 1: Using npx”](https://geminicli.com/docs/cli/uninstall/#method-1-using-npx)

npx runs packages from a temporary cache without a permanent installation. To
“uninstall” the CLI, you must clear this cache, which will remove gemini-cli and
any other packages previously executed with npx.

The npx cache is a directory named `_npx` inside your main npm cache folder. You
can find your npm cache path by running `npm config get cache`.

**For macOS / Linux**

```
# The path is typically ~/.npm/_npx

rm -rf "$(npm config get cache)/_npx"
```

**For Windows**

_Command Prompt_

```
:: The path is typically %LocalAppData%\npm-cache\_npx

rmdir /s /q "%LocalAppData%\npm-cache\_npx"
```

_PowerShell_

```
# The path is typically $env:LocalAppData\npm-cache\_npx

Remove-Item -Path (Join-Path $env:LocalAppData "npm-cache\_npx") -Recurse -Force
```

## Method 2: Using npm (Global Install)

[Section titled “Method 2: Using npm (Global Install)”](https://geminicli.com/docs/cli/uninstall/#method-2-using-npm-global-install)

If you installed the CLI globally (e.g., `npm install -g @google/gemini-cli`),
use the `npm uninstall` command with the `-g` flag to remove it.

```
npm uninstall -g @google/gemini-cli
```

This command completely removes the package from your system.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.