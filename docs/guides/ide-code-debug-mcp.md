# IDE Code Debug MCP Integration Guide

**Version:** 1.0.0
**Last Updated:** 2026-03-20
**Repository:** https://github.com/ygorhora/ide-code-debug

---

## Overview

The `ide-code-debug` extension integrates VS Code's debugger with Claude Code through MCP (Model Context Protocol). Once the extension is running, Claude Code can control breakpoints, step through execution, inspect variables, and analyze the call stack — all without leaving the AI assistant.

The extension runs an HTTP MCP server on `http://127.0.0.1:3100/mcp` (localhost only). This project's `.mcp.json` registers that server so Claude Code discovers it automatically on startup.

---

## Prerequisites

- VS Code 1.85+ or Cursor
- `ide-code-debug` extension installed
- Claude Code CLI installed and authenticated
- This project open at `/home/user/Claudecode`

---

## Quick Start

```bash
# 1. Open VS Code Command Palette
#    Ctrl+Shift+P (Linux/Windows) or Cmd+Shift+P (macOS)

# 2. Run: "IDE Code Debug: Register with Claude Code"

# 3. Reload Claude Code — the MCP server is now active
claude
```

---

## Step-by-Step Setup

### Step 1: Install the Extension

Search for `ide-code-debug` in the VS Code Extensions panel (`Ctrl+Shift+X`) and install it.

Or via CLI:

```bash
code --install-extension ide-code-debug
```

### Step 2: Start the MCP Server

The extension auto-starts the MCP server when VS Code launches. To confirm:

1. Open VS Code Command Palette
2. Run `IDE Code Debug: Register with Claude Code`
3. You should see a notification confirming the server is running on port 3100

### Step 3: Verify the Connection

Open a Claude Code session in this project:

```bash
cd /home/user/Claudecode
claude
```

Claude Code reads `.mcp.json` on startup and connects to `http://127.0.0.1:3100/mcp` automatically. The MCP server `ide-code-debug` will be listed in your available tools.

### Step 4: Confirm Available Tools

In your Claude Code session:

```
What MCP tools are available from ide-code-debug?
```

You should see tools such as:
- Breakpoint management (set, remove, list)
- Debug session control (start, stop, restart)
- Step execution (step over, step into, step out)
- Variable inspection
- Call stack analysis
- Thread management

---

## Configuration

The MCP server is configured in `.mcp.json` at the project root:

```json
{
  "mcpServers": {
    "ide-code-debug": {
      "url": "http://127.0.0.1:3100/mcp"
    }
  }
}
```

| Field | Value | Description |
|-------|-------|-------------|
| Server name | `ide-code-debug` | Identifier; tools appear as `mcp__ide-code-debug__*` |
| `url` | `http://127.0.0.1:3100/mcp` | HTTP MCP endpoint (localhost only) |

This configuration is project-scoped — it is only active when Claude Code opens this project directory.

---

## Usage Examples

### Set a Breakpoint

```
Set a breakpoint at line 42 in src/index.ts
```

### Inspect a Variable

```
Inspect the value of `config` in the current debug frame
```

### Step Through Code

```
Step over the next line and show me the updated local variables
```

### Analyze the Call Stack

```
Show me the current call stack
```

---

## Troubleshooting

### MCP server not listed in Claude Code

The VS Code extension is not running. Ensure VS Code is open and the extension is active, then restart Claude Code.

### Connection refused on port 3100

Another process is using port 3100, or the extension failed to start.

```bash
# Check what is using port 3100
lsof -i :3100

# If port is free but extension won't start, reload VS Code window:
# Ctrl+Shift+P → "Developer: Reload Window"
```

### Tools return errors (no active session)

Start a debug session in VS Code first (`F5`), then invoke the MCP tools from Claude Code.

### Validate .mcp.json syntax

```bash
node -e "JSON.parse(require('fs').readFileSync('.mcp.json', 'utf8'))" && echo "JSON valid"
```

---

## Security Notes

- The MCP server binds exclusively to `127.0.0.1` — not accessible from other machines.
- No authentication is required (restricted to localhost).
- Do not expose port 3100 via firewall rules or reverse proxies.
- Variable inspection can expose sensitive runtime data; use in trusted local environments only.

---

## Related

- [ide-code-debug GitHub repository](https://github.com/ygorhora/ide-code-debug)
- [AIOS MCP Usage Rules](../../.claude/rules/mcp-usage.md)
- [Story 1.1](../stories/1.1.story.md)
