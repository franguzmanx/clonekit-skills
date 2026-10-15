# Worked example: a steps kit

Leo runs a small design studio. Every Friday he bills his clients. He wants any AI to do it his way.

## The interview, short

- Share what? "My Friday billing. It's the same every week."
- For whom? "Freelancers and small studios who bill by the hour."
- The steps: "I export the hours, group them by client, draft one invoice each, check the totals, then send."
- Good work? "Every hour is billed once. Totals match the timesheet."
- Real effects? "Sending. I always look before it goes out."
- Never? "Never send without my OK. Never change a rate."

Shape: steps. It is a job with an order, and each step has a result.

## kit.yaml

```yaml
id: "@leo/weekly-invoices"
version: 1.0.0
title: Weekly client invoices
domain: finance
listing: "Every Friday, turn your timesheet into one checked invoice per client in {stripe}, ready for you to send."
deliverables:
  - "one draft invoice per client in Stripe"
  - "a one-page summary of hours and totals"
tools:
  - id: stripe
    name: Stripe
    url: https://stripe.com
understand:
  - id: timesheet
    ask: "Where do you track hours? Paste this week's export or name the tool."
  - id: rates
    ask: "What is each client's hourly rate?"
build:
  - id: group
    step: Group the hours by client
    instructions: "Read the timesheet. Sum hours per client and per project. List entries with no client and ask about them."
    check: "The total hours match the timesheet exactly."
  - id: draft
    step: Draft one invoice per client
    tool: stripe
    instructions: "Create a draft invoice for each client: one line per project, hours times that client's rate. Leave it as a draft."
    check: "Each total equals hours times rate. No rate was changed."
  - id: send
    step: Send the invoices
    tool: stripe
    instructions: "Show the summary page. Send the drafts only after the person says yes."
    approval: true
review:
  - "Every hour is billed once."
  - "The summary totals match the invoices."
guardrails:
  - "Never change a client's rate."
changelog: "First version."
```

No README.md is needed: the steps carry the know-how. Total time: about 10 minutes, then an optional `test_run` on another studio's timesheet.
