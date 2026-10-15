---
name: make-a-kit
description: Turn what you know into a CloneKit kit in about 10 minutes. Your AI asks a few questions, writes the kit, checks it, shows you a preview and publishes it when you say yes.
metadata:
  clonekit: "@francisco/make-a-kit"
  version: 1.0.0
  source: https://clonekit.ai/@francisco/make-a-kit
---

# Make a kit

Turn what you know into a CloneKit kit in about 10 minutes. Your AI asks a few questions, writes the kit, checks it, shows you a preview and publishes it when you say yes.

# Make a kit

Use this kit when a person wants to share what they know as a CloneKit kit: a rule, their voice, a checklist, a method, or a job done step by step. You interview them, write the kit, check it, show a preview and publish it after they say yes. Aim for about 10 minutes of conversation.

Files in this kit:

- `kit-format.md`: the kit.yaml fields you need, with their limits.
- `worked-examples/writing-style.md`: a files-only kit (the AI reads it).
- `worked-examples/weekly-invoices.md`: a steps kit (the AI runs it).

## 0. Check the connection

Call `whoami`. You need `creator_tools: true` and a handle. If the person has no handle, tell them to pick one on their CloneKit dashboard (Kits page) and reconnect CloneKit. Then continue.

## 1. Interview (5 minutes)

Ask one question at a time. Use their language. Quote their words. Stop asking when you can write the kit.

1. "What do you want to share? Something your AI should know or follow, or a job it should do step by step?"
2. "Who is it for, and what do they get?" (This becomes the title and listing.)
3. "Show me the know-how itself. Paste it, say it, or point me to the files." Read what they give you. Ask for one good example and one bad one.
4. "How do you know the work is good?" (This becomes the review list.)
5. Only for a job: "Walk me through it, from the first minute to the end. What do you check at each step? Which steps publish, spend money or message people?"
6. "Anything the AI must never do?" (This becomes guardrails.)

If they already have the material in a public GitHub repo, use `import_kit` instead of writing files. If they have a SKILL.md, AGENTS.md or CLAUDE.md, it works as the kit's entry file as it is.

After the interview, say back what you understood in 3 lines. Let them correct it.

## 2. Pick the shape

The content decides the shape:

| The person shares | Shape | What you write |
|---|---|---|
| Something to know or follow (voice, rules, taste, a checklist, a library) | files | kit.yaml + README.md + any other files |
| A job with an order, where each step has a result | steps | kit.yaml with `build` steps and `deliverables` |
| A job that also needs reference material | both | steps, plus files the steps point to |

Pick the smallest shape that holds the know-how. Most kits are files. Tell the person which shape you picked and why, in one line.

## 3. Write the kit

Follow `kit-format.md`. Copy the closest worked example and change it.

- Title: 3 to 80 characters, the thing they get.
- Listing: one line, 20 to 400 characters, written like a request a person would send their AI. No links.
- README.md: the first lines say when to use the kit. Then the know-how, in the person's words. Keep it as short as the material allows.
- Review: 2 to 6 checks the AI can verify before it shows its work.
- Free is the default. If the person wants to charge, see "Paid kits" in `kit-format.md`.

Keep their material faithful. Convert formats (doc to Markdown, sheet to CSV); do not summarize it away.

## 4. Check it

Call `validate_kit` with the kit.yaml text and every file. For each issue, apply its `fix` and check again. Read every warning: it usually means a field name is wrong.

## 5. Show a preview

Call `create_kit` with the same yaml and files. It saves a private draft and returns a `preview_url`. Give the link to the person and show them, in the chat, the title, the listing and the first lines of README.md (or the step titles). Ask: "Is this right? Should I change anything?" Apply their changes with `update_kit` (same version) and show the preview again.

For a steps kit, offer a `test_run` on a real case that is not theirs. It is optional for a free kit and earns the Tested badge.

## 6. Publish

When the person says it is ready, call `publish_kit` with the kit's ref. The first publish of a kit answers `needs_creator_ok` with a preview and a code. Show that preview. Call `publish_kit` again with `confirm` set to the code only after the person says yes.

A free kit that passes the automatic check is live at once. If the check holds it, a person at CloneKit reviews it, usually within a day; there is nothing to change. Give the person the kit's link to share. `list_my_kits` shows where each version stands.

To change a published kit later: raise `version` (1.0.0 to 1.1.0), call `create_kit`, then `publish_kit` with a one-line `changelog`.

## If the person uses a terminal

The same flow works with the CloneKit CLI: `clonekit init`, edit the files, `clonekit validate`, then `clonekit publish`. The CLI shows the preview and asks for the OK on the first publish.

## Files

Read these when the task needs them:

- [kit-format.md](kit-format.md)
- [worked-examples/weekly-invoices.md](worked-examples/weekly-invoices.md)
- [worked-examples/writing-style.md](worked-examples/writing-style.md)

From CloneKit: https://clonekit.ai/@francisco/make-a-kit (v1.0.0). The latest version is always there.
