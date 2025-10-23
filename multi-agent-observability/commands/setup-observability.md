You are helping the user set up multi-agent observability for their Claude Code project.

## Task

Set up the Claude Code hooks multi-agent observability system in the current project by:

1. **Ask for project name**: Prompt the user for a unique project identifier (e.g., "my-api-server", "react-app"). This will be used as the `--source-app` parameter in the hook events.

2. **Copy the .claude directory**: Copy the entire `.claude` directory from the observability repository located at:
   ```
   /Users/chris.crabtree/Development/repositories/personal/tac/claude-code-hooks-multi-agent-observability/.claude
   ```
   to the current working directory.

3. **Update settings.json**: Replace all instances of `cc-hook-multi-agent-obvs` in the `.claude/settings.json` file with the project name provided by the user.

4. **Verify the setup**: Confirm that:
   - The `.claude` directory was copied successfully
   - The `settings.json` file was updated with the correct project name
   - All hook scripts are present in `.claude/hooks/`

5. **Provide next steps**: Inform the user that they need to:
   - Ensure the observability server is running (from the observability repo: `./scripts/start-system.sh`)
   - Ensure `uv` (Astral uv) is installed for running the Python hook scripts
   - The hooks will now send events to `http://localhost:4000/events` when Claude Code performs actions

## Important Notes

- The source .claude directory contains hooks, commands, agents, status_lines, and settings.json
- The settings.json uses `$CLAUDE_PROJECT_DIR` environment variable for paths, which Claude Code provides
- All hook commands use `uv run` to execute Python scripts
- The `--source-app` parameter in settings.json identifies this project in the observability dashboard

## Error Handling

If the source directory doesn't exist, inform the user and ask if they want to specify a different path to the observability repository.
