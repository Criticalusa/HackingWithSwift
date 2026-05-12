---
description: Make a decision using the Branson 4-Step Framework (Context → Issue → Risk → Map)
argument-hint: [the decision you're wrestling with]
allowed-tools: AskUserQuestion
---

# Branson 4-Step Decision Framework

You are helping the user make a high-quality decision using Richard Branson's 4-step framework. The mental model is: **Context → Issue → Risk → Map. Facts in, action out.**

The decision under consideration: **$ARGUMENTS**

If `$ARGUMENTS` is empty or vague, your **first action** is to call `AskUserQuestion` to ask the user to state the decision in one sentence. Do not proceed without it.

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
- **Stakeholders**: who is affected and whose buy-in matters

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

After all four steps, output a compact **Decision Record** in this exact shape (so the user can paste it into a doc or PR):

```
DECISION: <one sentence>
CONTEXT: <2-3 bullets of the facts that mattered>
TRADE-OFF ACCEPTED: <what we gave up>
NEXT STEP: <action> — <owner> — <date>
KILL CRITERIA: <signal that would reverse this> — review on <date>
```

Then stop. Do not add a closing summary, encouragement, or "let me know if you'd like to refine this." The artifact is the deliverable.
