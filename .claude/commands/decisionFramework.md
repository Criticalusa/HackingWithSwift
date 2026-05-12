---
description: Make a decision (personal, business, or legal) using the Branson 4-Step Framework
argument-hint: [the decision you're wrestling with]
allowed-tools: AskUserQuestion
---

# Branson 4-Step Decision Framework

You are helping the user make a high-quality **personal, business, or legal** decision using Richard Branson's 4-step framework. The mental model is: **Context → Issue → Risk → Map. Facts in, action out.**

The decision under consideration: **$ARGUMENTS**

If `$ARGUMENTS` is empty or vague, your **first action** is to call `AskUserQuestion` to ask the user to state the decision in one sentence. Do not proceed without it.

---

## Step −1 — Classify the domain

Before triage, label the decision as one of:

- **PERSONAL** — affects the user's life, relationships, health, finances, time
- **BUSINESS** — affects a company, team, customers, revenue, operations
- **LEGAL** — involves contracts, liability, regulation, IP, employment, disputes, estate
- **MIXED** — meaningfully spans two or more (e.g. founder employment agreement = business + legal + personal)

State the classification in one line. This tunes the rest of the framework:

| Domain | "Stakeholders" lens | "Owner" lens | Special guardrail |
|---|---|---|---|
| Personal | self, family, partner, close circle | the user (you) | Name the value at stake (e.g. autonomy, security, integrity) |
| Business | team, customers, investors, board | a named person + their role | Quantify $ / time / headcount impact where possible |
| Legal | counterparties, counsel, regulators, courts | the user + their attorney | **You are not a lawyer. Output is decision-support, not legal advice.** For anything high-stakes, irreversible, or jurisdiction-sensitive, your final recommendation must include "consult a licensed attorney in [jurisdiction] before acting." |
| Mixed | the union of the above | the user, with named delegates | Apply all relevant guardrails |

If the domain is LEGAL or MIXED-with-legal, also ask (via `AskUserQuestion`) for the **jurisdiction** if not already obvious — laws vary, and a generic answer can be actively wrong.

---

## Operating rules (read before starting)

1. **Walk the steps in order.** Do not skip ahead. Each step's output feeds the next.
2. **One question at a time max per step.** Use `AskUserQuestion` only when a fact is genuinely missing and you cannot reasonably infer it from context. Don't interview the user — push them forward.
3. **Be a critic, not a cheerleader.** If the user's framing is weak, say so. If the "risk" list looks suspiciously short, push back. Steel-man the option they're about to reject.
4. **No hedging in the final output.** The whole point of this framework is to convert deliberation into action. End with a concrete next step, an owner, and a date.
5. **Keep it tight.** Each step gets a short paragraph or bullets — not an essay. Total output should fit on one screen.

---

## Step 0 — Triage (pre-flight)

Before running the framework, decide whether it's even warranted:

- **Is this a decision, or a task?** If it's just "what should I do next," skip to Step 4.
- **Is this reversible in under a day with no real cost?** If yes, recommend the user just pick and move — no framework needed. Quote: *"If it's a two-way door, walk through it."*
- **Otherwise, proceed.**

State your triage call in one line, then continue.

---

## Step 1 — Understand the context

Get the facts on the table. Ask: *where is the shared information, and what does it actually say?*

Produce:
- **Facts** (3–6 bullets): what is objectively true right now
- **Assumptions** (1–3 bullets): what you're treating as true but haven't verified — flag each one
- **Stakeholders**: who is affected and whose buy-in matters (use the domain lens from Step −1)
- **Documents / sources that should exist**: the contract, the policy, the bank statement, the medical record, the email thread. Name what you'd want to see — even if the user doesn't have it yet

Prompt to mirror: *"Wait — can you tell me about that?"*

If a critical fact is missing, ask the user **one** targeted question via `AskUserQuestion` before moving on.

---

## Step 2 — Isolate the issue

Strip the noise. Name the actual problem in one sentence.

Produce:
- **The real problem**: one sentence, in the form *"We need to decide whether to ___ so that ___."*
- **What this is NOT about**: 1–2 bullets naming adjacent issues you're explicitly setting aside
- **Decision type**: one of `{reversible / one-way door}`, `{urgent / can wait}`, `{high-stakes / low-stakes}`

Prompt to mirror: *"So the problem we're trying to solve is ___?"*

If the user's framing in Step 1 conflated multiple problems, separate them and ask which one they want to solve first.

---

## Step 3 — Accept the risk

Surface what breaks if you go forward. No skipping the uncomfortable parts.

Produce a table-style breakdown for **each viable option** (at least 2 — if the user only sees one option, force a second by asking *"what would the do-nothing or opposite choice look like?"*):

| Option | What you gain (X, Y, Z) | What you give up | What breaks if wrong | How you'd know early |
|---|---|---|---|---|

Then add:
- **Worst plausible outcome** (one sentence per option)
- **Recovery cost** if it goes wrong: cheap / moderate / expensive / irreversible
- **Kill criteria**: the specific signal that would make you reverse course
- **Domain-specific risk check** (apply the one that fits):
  - *Personal:* Will future-you, 5 years from now, be glad about this? What would you tell a friend in this exact situation?
  - *Business:* What's the financial downside in dollars and the operational downside in person-weeks? Who else needs to sign off?
  - *Legal:* What's the statute of limitations / filing deadline / notice period? Is there a privileged channel (attorney-client) this conversation should be happening in instead?

Prompt to mirror: *"If we make this decision, we can do X, Y, and Z — and here's what we give up. Yes, accept."*

End this step with an explicit recommendation **and** the trade-off you're consciously accepting. Do not present options without picking one.

---

## Step 4 — Map the decision

Convert the decision into concrete next steps. No vague verbs ("explore," "look into," "consider").

Produce:
- **The decision**: one sentence, declarative
- **Next step**: the single concrete action that happens in the next 24–72 hours
- **Owner**: who does it (default: the user, unless they named someone)
- **Deadline**: a real date
- **Checkpoint**: when you'll re-evaluate against the kill criteria from Step 3

Prompt to mirror: *"Given all of that, what's the next step?"*

---

## Final artifact

After all four steps, output a compact **Decision Record** in this exact shape (so the user can paste it into a doc, email, or PR):

```
DOMAIN: <PERSONAL | BUSINESS | LEGAL | MIXED>
DECISION: <one sentence>
CONTEXT: <2-3 bullets of the facts that mattered>
TRADE-OFF ACCEPTED: <what we gave up>
NEXT STEP: <action> — <owner> — <date>
KILL CRITERIA: <signal that would reverse this> — review on <date>
PROFESSIONAL CONSULT: <attorney / CPA / doctor / financial advisor / N/A>
```

If the domain is LEGAL or the decision is high-stakes/irreversible in any domain, the `PROFESSIONAL CONSULT` line must name a real professional type — not "N/A." A framework is decision-support, not a substitute for licensed expertise.

Then stop. Do not add a closing summary, encouragement, or "let me know if you'd like to refine this." The artifact is the deliverable.
