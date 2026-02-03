# Agent Skills

A collection of [Agent Skills](https://agentskills.io) for AI coding assistants.

Agent Skills are an open format for giving agents new capabilities and expertise. Skills are portable across different agent products including Claude Code, Claude.ai, and other compatible agents.

## Installation

### Agent Skills CLI (Recommended)

Install any skill directly using `npx`:

```bash
# Install a skill
npx skills add linuxlewis/agent-skills/skills/agent-browser
npx skills add linuxlewis/agent-skills/skills/pr-responder
npx skills add linuxlewis/agent-skills/skills/ralph-runner
npx skills add linuxlewis/agent-skills/skills/openclaw-notify

# List installed skills
npx skills list

# Remove a skill
npx skills remove agent-browser
```

### Claude Code Plugin

Alternatively, use the Claude Code plugin system:

```bash
# Add marketplace
claude plugin marketplace add linuxlewis/agent-skills

# Install skills
claude plugin install agent-browser@linuxlewis-agent-skills
claude plugin install pr-responder@linuxlewis-agent-skills
claude plugin install ralph-runner@linuxlewis-agent-skills
claude plugin install openclaw-notify@linuxlewis-agent-skills
```

### Manual

Copy any skill folder from `skills/` to your agent's skills directory.

## Available Skills

### agent-browser

Browser automation using the `agent-browser` CLI.

- Navigate websites and interact with page elements
- Take screenshots and PDFs
- Fill forms, click buttons, scrape content
- Session management for multi-step workflows

**Requirements:** `npm install -g agent-browser`

### pr-responder

Review and respond to GitHub PR comments.

- Fetch and classify PR review comments
- Prioritize by actionability (bugs, security, style)
- Implement approved changes
- GitHub CLI commands reference

**Requirements:** GitHub CLI (`gh`) installed and authenticated

**Command:** `/respond` - Review PR comments for current branch

### ralph-runner

Run Ralph Wiggum autonomous coding loops.

- Execute PRD files with user stories
- Iterative implementation with fresh context per story
- Progress tracking and learnings
- Context file injection

**Requirements:** `ralph-cli` and Claude Code CLI

### openclaw-notify

Notify OpenClaw gateway when background tasks complete.

- Send completion notifications back to dispatching session
- Report success, failure, or blocked status
- Simple one-command interface

**Requirements:** `openclaw` CLI installed, gateway running

**Command:** `/notify <message>` - Send notification to OpenClaw

## Structure

```
agent-skills/
├── .claude-plugin/
│   └── marketplace.json        # Claude Code marketplace
├── skills/                      # Agent Skills compliant (portable)
│   ├── agent-browser/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── pr-responder/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── ralph-runner/
│   │   ├── SKILL.md
│   │   └── references/
│   └── openclaw-notify/
│       └── SKILL.md
├── plugins/                     # Claude Code specific (commands)
│   ├── pr-responder/
│   │   ├── .claude-plugin/plugin.json
│   │   └── commands/
│   └── openclaw-notify/
│       ├── .claude-plugin/plugin.json
│       └── commands/
└── README.md
```

## Agent Skills Format

Each skill follows the [Agent Skills specification](https://agentskills.io/specification):

```markdown
---
name: skill-name
description: What this skill does and when to use it.
license: MIT
compatibility: Required tools or environment
metadata:
  author: your-name
  version: "1.0.0"
---

# Skill Name

Instructions for the agent...
```

### Progressive Disclosure

Skills use progressive disclosure for efficient context:

1. **Metadata** (~100 tokens) - Name and description loaded at startup
2. **Instructions** (< 500 lines) - Full SKILL.md loaded when activated
3. **References** (as needed) - Additional docs in `references/` loaded on demand

## Creating New Skills

1. Create a folder in `skills/` with your skill name
2. Add `SKILL.md` with frontmatter and instructions
3. Optionally add `references/`, `scripts/`, or `assets/` directories
4. Update `marketplace.json` to register with Claude Code

See [agentskills.io](https://agentskills.io) for the complete specification.

## Links

- [Agent Skills Specification](https://agentskills.io/specification)
- [Example Skills (Anthropic)](https://github.com/anthropics/skills)
- [agent-browser CLI](https://github.com/anthropics/agent-browser)
- [Ralph Wiggum](https://github.com/snarktank/ralph)

## License

MIT
