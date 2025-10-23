# Multi-Agent Observability Plugin

A Claude Code plugin that sets up comprehensive hook-based observability for real-time monitoring and visualization of Claude Code agents.

## Overview

This plugin automates the setup of the [Claude Code Hooks Multi-Agent Observability](https://github.com/disler/claude-code-hooks-multi-agent-observability) system in your projects. It includes all the necessary hook scripts, commands, and configuration files bundled within the plugin, so you don't need to manually copy files from another repository.

The plugin copies the complete `.claude` directory structure to your project and configures hook events to track agent behavior in real-time.

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

1. **[Astral uv](https://docs.astral.sh/uv/)** - Fast Python package manager (required for running hook scripts)
2. **[Multi-Agent Observability Server](https://github.com/disler/claude-code-hooks-multi-agent-observability)** - Clone and run the server to receive and visualize events

Note: All hook scripts and configuration files are bundled with this plugin. You only need the observability server running to receive events.

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
2. Copy the bundled `.claude` directory from the plugin to your project
3. Update the configuration with your project name
4. Verify the setup was successful

All hook scripts, configuration, and utilities are included in the plugin - no external files needed!

## Post-Setup

After running the setup command:

1. **Start the observability server** (from the observability repo):
   ```bash
   ./scripts/start-system.sh
   ```

2. **Open the dashboard** at `http://localhost:5173`

3. **Use Claude Code** in your project - all events will now be tracked and visualized in real-time

## What Gets Installed

The `.claude` directory installed in your project contains:
- `hooks/` - Python scripts that capture all Claude Code lifecycle events
  - **Core**: `send_event.py` - Universal event sender to observability server
  - **Event-specific hooks**: Pre/Post tool use, notifications, session events, etc.
  - **Utilities**: Model extraction and AI-powered event summarization (optional)
- `settings.json` - Complete hook configuration customized with your project name

**Focused on observability** - Only essential files for event tracking and visualization (no extra commands, agents, or UI customizations).

## Features

This streamlined plugin includes:
- ✅ **Event tracking** for all Claude Code lifecycle hooks
- ✅ **Safety features** - Blocks dangerous commands (`rm -rf`), prevents `.env` file access
- ✅ **AI summaries** (optional) - Generates concise event descriptions using Claude/OpenAI
- ✅ **Session logging** - Tracks sessions with local logging support
- ✅ **Model detection** - Automatically extracts model names from transcripts
- ✅ **Chat transcripts** - Optionally includes conversation history with Stop events

All features work out-of-the-box. AI summaries require `ANTHROPIC_API_KEY` or `OPENAI_API_KEY` (optional).

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
