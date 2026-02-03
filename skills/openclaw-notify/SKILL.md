---
name: openclaw-notify
description: Notify OpenClaw gateway when background tasks complete. Use this to ping the user who dispatched you when running as a background agent.
license: MIT
compatibility: Requires openclaw CLI installed and gateway running
metadata:
  author: linuxlewis
  version: "1.0.0"
---

# OpenClaw Notify

When you're running as a background agent (dispatched by OpenClaw), use this to notify when your task is done.

## The Command

```bash
openclaw gateway wake --text "Your message here" --mode now
```

That's it. One command.

## When to Use

Call this **once** at the very end of your task:

```bash
# ✅ Good - clear summary of what you did
openclaw gateway wake --text "Done: Created PR #42 with OAuth implementation" --mode now

# ✅ Good - report failure too
openclaw gateway wake --text "Failed: Could not push branch - permission denied" --mode now

# ❌ Bad - don't spam multiple notifications
openclaw gateway wake --text "Starting work..." --mode now  # unnecessary
openclaw gateway wake --text "Halfway done..." --mode now   # unnecessary
```

## Message Format

Keep it short and useful:

```
Done: <what you accomplished>
Failed: <what went wrong>
Blocked: <what you need>
```

Include links if relevant (PR URLs, file paths, etc.)

## Example Workflow

When dispatched with a task like "implement feature X and make a PR":

```bash
# 1. Do your work
# ... implement feature ...
# ... commit changes ...
# ... push branch ...
# ... create PR ...

# 2. Notify when done (LAST step)
openclaw gateway wake --text "Done: PR #15 created - https://github.com/org/repo/pull/15" --mode now
```

## Requirements

- `openclaw` CLI must be installed and in PATH
- Gateway must be running (it usually is if you were dispatched by it)

## Troubleshooting

If the command fails:

```bash
# Check if openclaw is available
which openclaw

# Check gateway status
openclaw gateway status
```

If gateway isn't running, your notification won't be delivered — but that's fine, the user will check on you eventually.
