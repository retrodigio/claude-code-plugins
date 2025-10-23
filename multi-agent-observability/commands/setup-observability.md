You are helping the user set up multi-agent observability for their Claude Code project.

## Task

Set up the Claude Code hooks multi-agent observability system in the current project by:

1. **Ask for project name**: Prompt the user for a unique project identifier (e.g., "my-api-server", "react-app"). This will be used as the `--source-app` parameter in the hook events.

2. **Locate the plugin template**: Use the Glob tool to find the `.claude-template` directory within the multi-agent-observability plugin. It will typically be located in the Claude Code plugins directory at a path like:
   ```
   ~/.config/claude-code/plugins/*/multi-agent-observability/.claude-template
   ```
   or
   ```
   ~/.claude-code/plugins/*/multi-agent-observability/.claude-template
   ```

3. **Copy the .claude directory**: Once located, copy the entire `.claude-template` directory to the current working directory and rename it to `.claude`:
   ```bash
   cp -R <plugin-path>/.claude-template ./.claude
   ```

4. **Update settings.json**: Replace all instances of `cc-hook-multi-agent-obvs` in the `.claude/settings.json` file with the project name provided by the user.

5. **Verify the setup**: Confirm that:
   - The `.claude` directory was copied successfully
   - The `settings.json` file was updated with the correct project name
   - All hook scripts are present in `.claude/hooks/`
   - The directory structure includes: hooks/, commands/, agents/, status_lines/, and settings.json

6. **Provide next steps**: Inform the user that they need to:
   - Ensure `uv` (Astral uv) is installed for running the Python hook scripts
   - Clone and run the observability server from: https://github.com/disler/claude-code-hooks-multi-agent-observability
   - Start the server: `./scripts/start-system.sh`
   - Open the dashboard at `http://localhost:5173`
   - The hooks will now send events to `http://localhost:4000/events` when Claude Code performs actions

## Important Notes

- The bundled .claude-template directory contains: hooks/, commands/, agents/, status_lines/, and settings.json
- The settings.json uses `$CLAUDE_PROJECT_DIR` environment variable for paths, which Claude Code provides
- All hook commands use `uv run` to execute Python scripts
- The `--source-app` parameter in settings.json identifies this project in the observability dashboard

## Error Handling

If the `.claude-template` directory cannot be found, inform the user and suggest:
- Reinstalling the plugin with `/plugin install multi-agent-observability`
- Checking that the plugin was installed correctly
- Manually checking the Claude Code plugins directory
