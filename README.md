# Claude Code Plugins

A marketplace for Claude Code plugins maintained by retrodigio.

## Installation

Add this marketplace to your Claude Code installation:

```
/plugin marketplace add retrodigio/claude-code-plugins
```

## Available Plugins

Check the marketplace for available plugins or browse the directories in this repository.

## Contributing

To add a plugin to this marketplace:

1. Create a new directory for your plugin
2. Add a `.claude-plugin/plugin.json` file with your plugin configuration
3. Update `.claude-plugin/marketplace.json` to include your plugin
4. Submit a pull request

## Plugin Structure

Each plugin should follow this structure:

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── command.md
└── README.md
```

For more information about creating plugins, see the [official Claude Code plugin documentation](https://docs.claude.com/en/docs/claude-code/plugins).
