---
url: "https://geminicli.com/docs/cli/sandbox/"
title: "Sandboxing in the Gemini CLI | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/cli/sandbox/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Sandboxing in the Gemini CLI

Copy as MarkdownCopied!

This document provides a guide to sandboxing in the Gemini CLI, including
prerequisites, quickstart, and configuration.

## Prerequisites

[Section titled “Prerequisites”](https://geminicli.com/docs/cli/sandbox/#prerequisites)

Before using sandboxing, you need to install and set up the Gemini CLI:

```
npm install -g @google/gemini-cli
```

To verify the installation

```
gemini --version
```

## Overview of sandboxing

[Section titled “Overview of sandboxing”](https://geminicli.com/docs/cli/sandbox/#overview-of-sandboxing)

Sandboxing isolates potentially dangerous operations (such as shell commands or
file modifications) from your host system, providing a security barrier between
AI operations and your environment.

The benefits of sandboxing include:

- **Security**: Prevent accidental system damage or data loss.
- **Isolation**: Limit file system access to project directory.
- **Consistency**: Ensure reproducible environments across different systems.
- **Safety**: Reduce risk when working with untrusted code or experimental
commands.

## Sandboxing methods

[Section titled “Sandboxing methods”](https://geminicli.com/docs/cli/sandbox/#sandboxing-methods)

Your ideal method of sandboxing may differ depending on your platform and your
preferred container solution.

### 1\. macOS Seatbelt (macOS only)

[Section titled “1. macOS Seatbelt (macOS only)”](https://geminicli.com/docs/cli/sandbox/#1-macos-seatbelt-macos-only)

Lightweight, built-in sandboxing using `sandbox-exec`.

**Default profile**: `permissive-open` \- restricts writes outside project
directory but allows most other operations.

### 2\. Container-based (Docker/Podman)

[Section titled “2. Container-based (Docker/Podman)”](https://geminicli.com/docs/cli/sandbox/#2-container-based-dockerpodman)

Cross-platform sandboxing with complete process isolation.

**Note**: Requires building the sandbox image locally or using a published image
from your organization’s registry.

## Quickstart

[Section titled “Quickstart”](https://geminicli.com/docs/cli/sandbox/#quickstart)

```
# Enable sandboxing with command flag

gemini -s -p "analyze the code structure"

# Use environment variable

export GEMINI_SANDBOX=true

gemini -p "run the test suite"

# Configure in settings.json

{

  "tools": {

    "sandbox": "docker"

  }

}
```

## Configuration

[Section titled “Configuration”](https://geminicli.com/docs/cli/sandbox/#configuration)

### Enable sandboxing (in order of precedence)

[Section titled “Enable sandboxing (in order of precedence)”](https://geminicli.com/docs/cli/sandbox/#enable-sandboxing-in-order-of-precedence)

1. **Command flag**: `-s` or `--sandbox`
2. **Environment variable**: `GEMINI_SANDBOX=true|docker|podman|sandbox-exec`
3. **Settings file**: `"sandbox": true` in the `tools` object of your
`settings.json` file (e.g., `{"tools": {"sandbox": true}}`).

### macOS Seatbelt profiles

[Section titled “macOS Seatbelt profiles”](https://geminicli.com/docs/cli/sandbox/#macos-seatbelt-profiles)

Built-in profiles (set via `SEATBELT_PROFILE` env var):

- `permissive-open` (default): Write restrictions, network allowed
- `permissive-closed`: Write restrictions, no network
- `permissive-proxied`: Write restrictions, network via proxy
- `restrictive-open`: Strict restrictions, network allowed
- `restrictive-closed`: Maximum restrictions

### Custom Sandbox Flags

[Section titled “Custom Sandbox Flags”](https://geminicli.com/docs/cli/sandbox/#custom-sandbox-flags)

For container-based sandboxing, you can inject custom flags into the `docker` or
`podman` command using the `SANDBOX_FLAGS` environment variable. This is useful
for advanced configurations, such as disabling security features for specific
use cases.

**Example (Podman)**:

To disable SELinux labeling for volume mounts, you can set the following:

```
export SANDBOX_FLAGS="--security-opt label=disable"
```

Multiple flags can be provided as a space-separated string:

```
export SANDBOX_FLAGS="--flag1 --flag2=value"
```

## Linux UID/GID handling

[Section titled “Linux UID/GID handling”](https://geminicli.com/docs/cli/sandbox/#linux-uidgid-handling)

The sandbox automatically handles user permissions on Linux. Override these
permissions with:

```
export SANDBOX_SET_UID_GID=true   # Force host UID/GID

export SANDBOX_SET_UID_GID=false  # Disable UID/GID mapping
```

## Troubleshooting

[Section titled “Troubleshooting”](https://geminicli.com/docs/cli/sandbox/#troubleshooting)

### Common issues

[Section titled “Common issues”](https://geminicli.com/docs/cli/sandbox/#common-issues)

**“Operation not permitted”**

- Operation requires access outside sandbox.
- Try more permissive profile or add mount points.

**Missing commands**

- Add to custom Dockerfile.
- Install via `sandbox.bashrc`.

**Network issues**

- Check sandbox profile allows network.
- Verify proxy configuration.

### Debug mode

[Section titled “Debug mode”](https://geminicli.com/docs/cli/sandbox/#debug-mode)

```
DEBUG=1 gemini -s -p "debug command"
```

**Note:** If you have `DEBUG=true` in a project’s `.env` file, it won’t affect
gemini-cli due to automatic exclusion. Use `.gemini/.env` files for gemini-cli
specific debug settings.

### Inspect sandbox

[Section titled “Inspect sandbox”](https://geminicli.com/docs/cli/sandbox/#inspect-sandbox)

```
# Check environment

gemini -s -p "run shell command: env | grep SANDBOX"

# List mounts

gemini -s -p "run shell command: mount | grep workspace"
```

## Security notes

[Section titled “Security notes”](https://geminicli.com/docs/cli/sandbox/#security-notes)

- Sandboxing reduces but doesn’t eliminate all risks.
- Use the most restrictive profile that allows your work.
- Container overhead is minimal after first build.
- GUI applications may not work in sandboxes.

## Related documentation

[Section titled “Related documentation”](https://geminicli.com/docs/cli/sandbox/#related-documentation)

- [Configuration](https://geminicli.com/docs/get-started/configuration): Full configuration options.
- [Commands](https://geminicli.com/docs/cli/commands): Available commands.
- [Troubleshooting](https://geminicli.com/docs/troubleshooting): General troubleshooting.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.