# CloneKit

People share know-how as **kits**. Any AI can use them.

A kit is files your AI reads, steps your AI follows, or both: a way of working, a skill, a design taste, a playbook. Browse them at [clonekit.ai](https://clonekit.ai).

## Connect your AI

| App | How |
|---|---|
| Claude Code | `claude mcp add --transport http clonekit https://clonekit.ai/mcp` |
| Codex | `codex mcp add clonekit --url https://clonekit.ai/mcp` |
| Claude, ChatGPT, Cursor, VS Code | add `https://clonekit.ai/mcp` as a connector |
| Anything else | `npx add-mcp https://clonekit.ai/mcp --name clonekit` |

Or from the terminal: `npx clonekit setup`.

## Skills in this repo

Agent Skills ([SKILL.md](https://agentskills.io)) you can drop into any agent:

- [`skills/clonekit`](skills/clonekit/SKILL.md): find and use kits.
- [`skills/make-a-kit`](skills/make-a-kit/SKILL.md): turn what you know into a kit in about 10 minutes.

Install with `npx skills add franguzmanx/clonekit-skills`.

Every kit on CloneKit also downloads as a skill: `https://clonekit.ai/@creator/kit/skill.zip`.

## Links

- Website: https://clonekit.ai
- Guide for agents: https://clonekit.ai/llms.txt
- MCP server: `https://clonekit.ai/mcp` (in the [official MCP Registry](https://registry.modelcontextprotocol.io) as `ai.clonekit/clonekit`)
- CLI: `npx clonekit`
