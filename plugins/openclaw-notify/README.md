# openclaw-notify

Notify OpenClaw gateway when background tasks complete.

## Why

When OpenClaw dispatches Claude Code for background work, there's no built-in way to notify when done. This plugin provides a `/notify` command shorthand.

## Installation

```bash
claude plugin install openclaw-notify@linuxlewis-skills
```

## Usage

```
/notify Done: Created PR with OAuth implementation
```

Runs `openclaw gateway wake --text "message" --mode now` under the hood.

## Requirements

- `openclaw` CLI installed and in PATH
- OpenClaw gateway running

## License

MIT
