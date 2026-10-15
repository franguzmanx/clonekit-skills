# kit.yaml, the parts you need

A kit is kit.yaml plus files. Only `id`, `title` and `listing` are required. The kit also needs content: at least one file or one build step.

## Every kit

```yaml
id: "@handle/kit-name"   # the person's handle; lowercase letters, numbers and dashes
version: 1.0.0           # raise it for every published change
title: "My writing style"            # 3-80 characters
listing: "One line on who it's for and what their AI gets."   # 20-400 characters
domain: content          # marketing | design | engineering | operations | sales | content | finance | other
review:                  # checks the AI does before it shows its work
  - "One concrete check per line."
guardrails:              # things the AI must never do with this kit
  - "One rule per line."
changelog: "First version."
```

Files sit next to kit.yaml: `README.md` first (the AI reads it first), then any others (`rules/`, `templates/`, `data/prices.csv`). Text formats only: .md .txt .csv .tsv .json .yaml .yml .svg.

## Steps kits only

```yaml
deliverables:            # what the person gets at the end; things, not business results
  - "a sent invoice for each client"
tools:                   # tools the steps use; the url is the only place a link may go
  - id: stripe
    name: Stripe
    url: https://stripe.com
understand:              # questions to ask before the run; the AI researches first
  - id: clients
    ask: "Who do you bill each week, and how much?"
build:
  - id: draft
    step: Draft the invoices          # short title
    tool: stripe                      # optional; must match a tools id
    instructions: "What to do, in detail. Long text can go in steps/01-draft.md."
    check: "How the AI knows this step is done right."
  - id: send
    step: Send the invoices
    tool: stripe
    instructions: "..."
    approval: true                    # the person says OK first: publishing, paying, messaging, deleting
```

Optional: `choose` (A/B choices with 2 or more options), `inputs`, `outputs`, `refs` (books, essays, skills; `kind: source | skill | template`).

## Rules the validator enforces

- No links in kit.yaml text or in step files. Links go only in `tools[].url` and `refs[].url`.
- `deliverables`, `choose` and `approval` need build steps. A files-only kit lists no deliverables.
- `{tool-id}` in the listing must match a tool or ref id. Leave it out if you have no tools.
- Ids are unique: steps, tools, refs, questions, choices.
- A step file named in `instructions` (like `steps/01-draft.md`) must exist.
- Unknown fields are ignored with a warning: `steps` should be `build`, `description` should be `listing`, `checks` should be `review`.

## The automatic check (before publish)

It blocks or holds kits with: hidden text (HTML comments) aimed at the AI, invisible characters, live keys or tokens, commands that download and run a script, lines that send secrets somewhere, and text that tells the AI to skip permissions or hide things from the person. Write plain instructions in plain sight and it passes.

## Paid kits

Free is the default (`pricing: { model: free }`). A paid kit sets `pricing: { model: one_time, amount_usd: 29 }` and a `refund` (`7_days` is a good default). A person at CloneKit reviews paid kits, and a paid steps kit needs a passed `test_run` first. Suggest a price; the person decides.
