---
name: review-checklist
description: Reviews a product brief against the student's four pre-send checks (named owner, how we'll know it worked, scope at the end matches scope at the start, problem explained before the fix). Use it when the student says "review-checklist", "run my checklist on this brief", "review this brief", "check this brief before it goes out" or points at a brief and asks whether it's ready. Read-only - it reports, it never edits the brief.
---

# Review checklist

The student wants the same four checks run on a brief every time, without having to explain them again. Run exactly these four, in this order, and nothing else. Don't add your own extra criteria (tone, length, formatting); if something else is badly wrong, put it in one line at the very end under "Outside the checklist".

## 1. Find the brief

- If the student named a file or pasted text, use that. Briefs may be `.md`, `.txt` or `.docx` (read `.docx` with the docx skill or by extracting its text), or a wiki page via rook-wiki.
- If they didn't say which brief, look for the most recently changed brief in the current module folder and ask one short question to confirm: "Review `<file>`?"
- Read the whole brief before judging anything. Don't edit it, and don't create any files unless the student asks you to save the review.

## 2. Run the four checks

Give each check one verdict: **Pass**, **Partial** or **Missing**. Every verdict needs evidence: a short quote from the brief (under 20 words) and where it is (section heading or paragraph). For Missing, say where you looked.

### Check 1: It names who owns it
- **Pass:** a named person is the owner of the brief or the decision (e.g. "Owner: Helen Achebe").
- **Partial:** only a team, a role, "we", or several names with no single owner; or owners are named for some actions but not the brief as a whole.
- **Missing:** no owner anywhere, or "TBD".

### Check 2: It says how we'll know it worked
- **Pass:** at least one measurable signal, with a target or direction and a time frame (e.g. "acceptance back above 75% within 4 weeks of release").
- **Partial:** a metric is named but has no target or time frame, or the target is a placeholder (still say it's a placeholder and who is meant to fill it in).
- **Missing:** only vague goals ("improve the experience", "fewer complaints") or nothing at all.

### Check 3: The scope at the end matches the scope at the start
- Write down, in a few words, what the opening (summary, bottom line, problem statement) says the brief covers: who, which product, which problem.
- Then write down what the ending (proposal, asks, next steps, decisions needed) actually commits to or asks for.
- **Pass:** they match.
- **Partial:** the ending adds or drops something small, or quietly widens or narrows it (e.g. opens on four responders, ends asking for a change to everyone's scoring).
- **Missing:** the ending is about a different problem, or the opening never states a scope, so there's nothing to match against.
- Name exactly what was added or dropped.

### Check 4: It explains the problem before it proposes a fix
- Find where the problem is first explained (what's wrong, for whom, and the evidence) and where the first fix, proposal or solution appears.
- **Pass:** the problem and its evidence come first.
- **Partial:** a fix is mentioned first (often in the title or bottom line) but the problem is explained properly before the proposal section; or the problem is stated with no evidence.
- **Missing:** the brief leads with the fix and never really explains the problem.
- A bottom-line-first summary that states the problem *and* the ask in one breath is fine; judge the body.

## 3. Report it the same way every time

Use this exact layout in the chat:

```
Review checklist: <brief file name>
Ready to send: Yes / Not yet (<n> of 4 pass)

| Check | Verdict | Evidence |
|---|---|---|
| Names who owns it | Pass/Partial/Missing | "quote" (section) |
| Says how we'll know it worked | ... | ... |
| Scope at the end matches the start | ... | Start: ... / End: ... |
| Problem before fix | ... | ... |

Fixes
1. <one concrete edit per Partial or Missing check, in plain words, e.g. "Add 'Owner: <name>' under the title.">

Outside the checklist (optional, one line max)
```

- "Ready to send: Yes" only when all four pass.
- Keep fixes concrete and short. Suggest the wording, don't rewrite the brief. Don't invent facts (owners, targets) the brief doesn't support; if one is needed, say who should supply it.
- Plain, direct language. No scoring beyond the four verdicts.
- After the report, offer once: "Want me to make these fixes in the brief?" Only edit if they say yes.
