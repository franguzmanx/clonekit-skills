---
name: clonekit
description: Find and use expert know-how ("kits") from CloneKit. Use this when the user wants to do a job the way an expert does it (marketing, sales, ops, design, coding workflows) or asks for a proven playbook, template or process.
metadata:
  source: https://clonekit.ai
---

# CloneKit

CloneKit is a library of kits: know-how that people package once so any AI can use it. A kit is files your AI reads, steps your AI follows, or both.

## Connect (once)

- Claude Code: `claude mcp add --transport http clonekit https://clonekit.ai/mcp`
- Any app: `npx add-mcp https://clonekit.ai/mcp --name clonekit`
- Terminal: `npx clonekit setup`

## Use a kit

1. `search_kits` with what the user wants to get done, in plain words.
2. `get_kit` on the best match. Read what it promises and what it needs.
3. Free kits: read the files with `get_file`, or start the steps with `start_run` and follow `next_step` until `finish`.
4. Paid kits: show the price and link; the user buys on clonekit.ai.
5. Afterwards, `rate_kit` so others know if it worked.

## Share what you know

Use the `make-a-kit` skill (or the kit `@francisco/make-a-kit`) to turn the user's know-how into a kit and publish it.

Full guide for agents: https://clonekit.ai/llms.txt
