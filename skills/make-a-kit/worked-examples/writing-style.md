# Worked example: a files-only kit

Ana writes a newsletter. She wants any AI to draft in her voice.

## The interview, short

- Share what? "How I write. My AI should sound like me."
- For whom? "Me and my two editors."
- The know-how: she pastes three past issues and says: "Short sentences. I open with a scene, never a question. No exclamation marks. I end with one line the reader can act on."
- Good work? "It sounds like me read aloud. No word I'd have to look up."
- Never? "Never invent quotes or numbers."

Shape: files. Her voice is something to follow, not a job with steps.

## kit.yaml

```yaml
id: "@ana/my-writing-style"
version: 1.0.0
title: Ana's writing style
domain: content
listing: "Write newsletters and posts in Ana's voice: short sentences, a scene first, one clear action at the end."
review:
  - "Every sentence has 20 words or fewer."
  - "The first paragraph is a scene, not a question."
  - "No exclamation marks."
  - "It ends with one line the reader can act on."
guardrails:
  - "Never invent quotes, names or numbers. Mark gaps as [NEEDS SOURCE]."
changelog: "First version."
```

## README.md

```markdown
# Ana's writing style

Use this when you draft a newsletter, post or email for Ana or her editors.

## How Ana writes
- Short sentences. One idea each.
- Open with a scene: a place, a person, a moment. Never open with a question.
- Plain words. If a word needs a dictionary, use another.
- No exclamation marks. No "in today's world".
- End with one line the reader can do today.

## Examples
See examples.md: two openings she likes and one she rejected, with her reasons.
```

Files: `README.md` and `examples.md` (her three issues, pasted as they are). Total time: about 8 minutes.
