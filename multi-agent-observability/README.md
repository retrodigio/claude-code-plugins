# Multi-Agent Observability Plugin

A Claude Code plugin that sets up comprehensive hook-based observability for real-time monitoring and visualization of Claude Code agents.

## Overview

This plugin automates the setup of the [Claude Code Hooks Multi-Agent Observability](https://github.com/disler/claude-code-hooks-multi-agent-observability) system in your projects. It copies the necessary `.claude` directory and configures hook events to track agent behavior in real-time.

## What It Does

The observability system captures and visualizes:
- Tool usage (before and after execution)
- User prompts and interactions
- Session lifecycle events
- Subagent activity
- Context compaction events

All events are sent to a visualization dashboard where you can monitor multiple concurrent agents with session tracking, event filtering, and live updates.

## Prerequisites

Before using this plugin, ensure you have:

1. **[Astral uv](https://docs.astral.sh/uv/)** - Fast Python package manager (required for hook scripts)
2. **[Multi-Agent Observability Server](https://github.com/disler/claude-code-hooks-multi-agent-observability)** - Clone and run the observability system

## Installation

This plugin is available in the retrodigio marketplace:

```bash
/plugin marketplace add retrodigio/claude-code-plugins
/plugin install multi-agent-observability
```

## Usage

Navigate to your project directory and run:

```bash
/setup-observability
```

The command will:
1. Ask for a unique project identifier (e.g., "my-api-server", "react-app")
2. Copy the `.claude` directory with all hook scripts and configuration
3. Update the configuration with your project name
4. Verify the setup was successful

## Post-Setup

After running the setup command:

1. **Start the observability server** (from the observability repo):
   ```bash
   ./scripts/start-system.sh
   ```

2. **Open the dashboard** at `http://localhost:5173`

3. **Use Claude Code** in your project - all events will now be tracked and visualized in real-time

## What Gets Installed

The `.claude` directory contains:
- `hooks/` - Python scripts that capture Claude Code lifecycle events
- `settings.json` - Hook configuration with your project identifier
- `commands/` - Additional Claude Code commands (optional)
- `agents/` - Pre-configured agents (optional)
- `status_lines/` - Custom status line scripts (optional)

## Tracked Events

- PreToolUse - Before tool execution
- PostToolUse - After tool completion
- UserPromptSubmit - User prompt submission
- Notification - User interactions
- Stop - Response completion
- SubagentStop - Subagent finished
- PreCompact - Context compaction
- SessionStart - Session started
- SessionEnd - Session ended

## Learn More

- [Multi-Agent Observability Documentation](https://github.com/disler/claude-code-hooks-multi-agent-observability)
- [Claude Code Hooks Mastery](https://github.com/disler/claude-code-hooks-mastery)
- [Official Claude Code Hooks Documentation](https://docs.anthropic.com/en/docs/claude-code/hooks)

## Support

For issues or questions:
- Open an issue in the [marketplace repository](https://github.com/retrodigio/claude-code-plugins)
- Check the [observability system documentation](https://github.com/disler/claude-code-hooks-multi-agent-observability)
