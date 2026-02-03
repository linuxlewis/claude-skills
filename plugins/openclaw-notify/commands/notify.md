---
name: notify
description: Send a notification to OpenClaw gateway
arguments:
  - name: message
    description: The message to send
    required: true
---

# /notify

Send a notification to the OpenClaw gateway that dispatched you.

## Usage

```
/notify <message>
```

## Examples

```
/notify Done: Implemented OAuth and created PR #42
/notify Failed: Tests failing on auth middleware
/notify Blocked: Need API credentials to continue
```

## What It Does

Runs:

```bash
openclaw gateway wake --text "<message>" --mode now
```

This immediately pings the OpenClaw session that spawned you, so the user knows you're done (or stuck).

## When to Use

- Task completed successfully
- Task failed and you can't continue
- You need input/credentials/clarification

Don't use for progress updates — just final status.
