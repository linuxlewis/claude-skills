# Claude Skills

Custom Claude Code plugins and skills marketplace.

## Installation

Add this marketplace to Claude Code:

```bash
claude plugin marketplace add linuxlewis/claude-skills
```

Then install plugins:

```bash
claude plugin install agent-browser@linuxlewis-skills
```

## Available Plugins

### agent-browser

Browser automation skill using the `agent-browser` CLI. Enables Claude to:

- Navigate websites
- Interact with page elements (click, type, fill)
- Take screenshots and PDFs
- Extract content from pages
- Handle forms and interactive elements

## Structure

```
claude-skills/
├── .claude-plugin/
│   └── marketplace.json   # Marketplace manifest
├── plugins/
│   └── agent-browser/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── skills/
│       │   └── agent-browser/
│       │       └── SKILL.md
│       └── README.md
└── README.md
```

## License

MIT
