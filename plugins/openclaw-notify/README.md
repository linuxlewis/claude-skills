# openclaw-notify

Notify OpenClaw gateway when background tasks complete.

## Why

When OpenClaw dispatches Claude Code for background work, there's no built-in way to notify when done. This plugin provides:

1. **Skill** — Instructions for Claude on how/when to notify
2. **Command** — `/notify <message>` shorthand

## Installation

```bash
claude plugin install openclaw-notify@linuxlewis-skills
```

## Usage

### As a Skill

Claude automatically knows to call:

```bash
openclaw gateway wake --text "Done: your summary" --mode now
```

### As a Command

```
/notify Done: Created PR with OAuth implementation
```

## Requirements

- `openclaw` CLI installed and in PATH
- OpenClaw gateway running

## License

MIT
