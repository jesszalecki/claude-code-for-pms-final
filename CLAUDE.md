# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Read and write only within this directory.
  Exceptions, for the course-setup and wrap-up skills only:
  - When the student asks you to check their setup, save their work or wrap up a session, that request is their yes. You may run the GitHub command-line program installed at ~/.ccpm/gh for those checks and saves, and look in that folder to find it.
  - For a repair, first tell the student in one plain sentence what you are about to do, and act only after they say yes. Repairs may: run that GitHub program (including setting this folder's own git sign-in setting and changing this repo's visibility back to Public); copy the student's own course files into this directory from another folder on their computer (copy only; never move, edit or delete the originals); and rename something outside this directory that blocks setup, by adding "-old" to its name (never delete it).
  Outside this directory you still never write, edit or delete anything else.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

Sources: `00-rook/company/notes/handoff-from-priya.docx` and the wiki's
Company section (About, product one-pagers, Glossary, Team directory,
Releases, Q3 roadmap, plus comments on those pages). Read on 6 Oct 2026.

### My role
New PM for **Rook Dispatch**, started Mon 24 Aug 2026 (per wiki comments). Took over from
Priya Raghunathan, who left 21 Aug with no overlap. She was the only Dispatch PM for 14 months.

### The company
- Rook Industries sells coordination and provisioning software to
  independently operating masked **responders** and the **handlers** and
  **quartermasters** who support them. Rook doesn't employ responders.
- 241 staff, mostly remote. HQ is Site Aleph; there are also offices in Berlin,
  Singapore and Cornwall. Subscription is priced per active responder.
- Monthly release train with 4.x numbers. Routing config ships *in the
  release*; handlers can't change it at runtime.
- **Hard rule:** cover identities are never stored. Never design anything
  that assumes or reconstructs a responder's legal identity (Security
  Policy 4.1).

### Products
| | Rook Dispatch (mine) | Rook Supply |
|---|---|---|
| Does | Gets the right responder to an incident: ranks, pings, tracks take/turn-down | Gear: requisitions, approvals, maintenance, failure reports |
| Users | Handlers (web console), responders (phone app) | Handlers, quartermasters |

**Dispatch flow:** incident enters the console → responders are ranked by
routing priority → the top one gets pinged → taken (assigned), or turned
down or missed (goes to the next one).

**Dependency:** Dispatch writes the **Responder Availability Record**.
Supply reads it to schedule maintenance into low-callout windows. Any
change to how Dispatch computes it lands in Supply without warning.

### Vocabulary
- **Callout**: a request for a responder at an incident. **Ping**: a callout
  offered to one responder.
- **Taken / Turned down / Missed**: yes / no / no answer before the ping
  wait ran out. Missed and turned down are tracked separately.
- **Ping wait**: how long a ping stays on the phone. It's global and set per release
  (90s → **60s** in 4.2).
- **Routing priority**: the ranking score. Its inputs are proximity (travel time),
  availability, capability match and **recent acceptance history**.
  Turning down *or missing* a ping lowers a responder's rank for later callouts.
- **Capability tag**: e.g. flight, hazmat-tolerant, aquatic, de-escalation.
- **Coverage gap**: no available responder had the required tags. This is
  different from low acceptance: nobody *could* go, as opposed to nobody *would*.
- **Mutual aid / shared cover**: responders covering each other's areas.
  Not supported yet; in Q4 exploration.

**Metrics:** callout acceptance rate (headline, reported weekly in
aggregate), time-to-accept (median seconds), coverage gap.

### People
| Who | Role | Notes |
|---|---|---|
| Helen Achebe | Director of Product (my manager) | Owns roadmap and commitments. Site Aleph |
| Marcus Oyelaran | Eng Manager, Dispatch | Direct; first stop when unsure. Site Aleph |
| Wen Li | Staff Engineer | Built routing priority. The logic isn't written down, so learn it by talking to her. Berlin. Was away 14–24 Aug |
| Ravi Menon | Data Analyst | Owns the official weekly acceptance numbers. Singapore |
| Nadia Hoffmann | Support Lead | Hears about handler pain first. Worth a standing 15 min. Berlin |
| Sofia Marino | Product Designer | Console and phone app. Ran the September interviews. Site Aleph |

### Release history
- **4.0** (7 Apr): console navigation, responder profile redesign, routing override audit log.
- **4.1** (16 Jun): proximity uses travel time, bulk callout, push reliability.
  Mobile has been stable since this release.
- **4.2** (12 Aug): proximity weighted up vs. acceptance history; ping
  wait 90→60s; console filters persist; 3 defect fixes.

### Where things stand: the 4.2 problem
- Since 4.2, fewer pings are being taken and handler complaints are up.
  Callout tickets ran about 3× normal from release day (Wed 12 Aug) and were still elevated on 26 Aug.
- Nadia's ticket split is about ⅔ "my phone never goes off" and ⅓ "it was gone
  before I could answer." The second fits the 60s ping wait. Nobody has
  explained the first.
- On 14 Aug Marcus asked whether the proximity change was *meant* to apply
  to responders who've been turning jobs down, or whether that just fell out
  of the config. It's unanswered. Wen was away and said she'd look later.
- **Priya's view** (an opinion, not verified): the drop is mostly the usual August
  dip and should recover in September. Look at seasonality before pulling
  the routing change apart. Don't let this turn into a revert debate,
  because the change was a long-standing ask from wide-area responders.
- Three things changed at once: the routing weights, the ping wait, and the season.
  Plausible interaction to test: a shorter wait → more misses → lower
  acceptance history → lower rank → fewer pings ("phone never goes off").
- The only numbers so far are Marcus's rough pull. Ravi's real weekly data
  hasn't been looked at yet. The team planned to regroup on 4.2 once I'd had a
  week, and Nadia has a ticket breakdown ready.

### Roadmap loose ends (Q3 roadmap last reviewed 30 Jun, so stale)
- Committed for 4.2: Change to who gets pinged ✅ shipped. Ping timeout
  tuning ✅ (shipped as the 60s cut). **Availability Confidence** (a confidence
  score next to stated availability) ❌ *not in the 4.2 notes*, so it was
  probably one of the items squeezed out.
- Committed for 4.3: Requisition approval chains (Supply), still listed under Priya.
- Q4 exploring: Handler phone app, Shared cover between responders.
- **To do with Helen:** confirm which deferred items are still Q3
  commitments. That conversation never happened.

### Priya's other asks
- Write down how routing priority works. No document exists.
- Expect tickets about console filter persistence. She calls them cosmetic noise
  and says not to let them eat the first month.
- She admits she made fast calls she didn't always check. The risky ones are
  likely in parts nobody has examined, so use fresh eyes early.

Module 2 (6 Oct), from the 4 interviews, `support_tickets` and the `pings` table:
- **Pings data confirms the loop.** Missed pings waited exactly 92s up to 8 Aug and 62s from 12 Aug. Missed went from 2% to 18% of pings, taken from 77% to 64%, and callouts nobody took from 5.5% to 11%.
- **Hardest hit:** Vesper, Meteor Mite, The Undertow and Farlight fell from about 9–12 callouts taken a week to about 1. They missed first, then stopped being pinged first (39→3 a week). Nightwell, The Gale, Stormwrack and Vantage each picked up 20–35% more pings. There's no workload cap and no limit setting.
- **Seasonality doesn't explain it.** Callouts dipped from about 145 to 120 a week, but Mite (0.8/wk) and The Gale (12.9/wk) are both in Eastgate.
- **Tickets:** 107 of 147 were filed on or after 12 Aug. 45 of those are callout problems (30 "phone never goes off", 15 "gone before I could answer"), all still open. Saved-filter complaints since the release: 12.
- **Sources barely overlap.** Only Ambrose appears in both the interviews and the tickets. Vesper and Mite (the interviewees' responders) never got a ticket. The interviews were console-UX scoped and never asked about 4.2. 3 of 4 interviewees raised vanishing callouts unprompted.
- **Still open:** Marcus's 14 Aug question (ask Wen directly), whether to roll back the 60s wait and/or stop misses from lowering rank, and resetting the four responders' rank.

Module 3 (7 Oct), Vesper's timeline (handler Aunt Dot, Old Town) from `pings`/`callouts` plus Dot's 3 Sep interview:
- **Vesper:** took 11–12 callouts a week before 4.2, then 6, 1, 0, 0. From 18 Aug, 28 Old Town callouts never reached Vesper (mostly Nightwell and Captain Vantage took them). Old Town got *busier* (12–14 a week), and Dot never filed a ticket.
- **Routing code is in the repo** (`00-rook/code/dispatch-routing/`). 4.2 changed only the timeout (90→60s) and weights (proximity 0.45→0.60, acceptance 0.40→0.25). There is no new regional logic.
- **How the score works (`history.py`):** misses and turn-downs both cost −0.12, a take earns only +0.08. There's one global score per responder, not one per area, so far-away misses hurt rank at home. It never recovers on its own (2019 TODO). The 60s cut was planned (Q3 roadmap), but its interaction with scoring probably wasn't.
- **Unexplained:** on 14–16 Aug, Vesper ranked behind out-of-area responders on Old Town callouts 41006, 41023 and 41034. Ask Wen, and confirm the repo code matches production.
- **Next:** trace Meteor Mite (also interviewed) and a winner (Nightwell) to check the pattern holds. Then brief Wen and Marcus: should misses count less, should scores decay, can the four be reset.

Module 4 (7 Oct), score replay (repo rules run over `pings` from 29 Jun) plus a full read of `00-rook`:
- **Hypothesis** (written up in `04-x-ray-vision/4.2-hypothesis.md`): the 60s wait caused misses, misses sank scores below a nearby rival's, and responders can't recover without being pinged. It fits Mite, Undertow and Farlight. Mite vs The Gale (both Eastgate) is the cleanest case: two misses, then The Gale was pinged first about 25 times in a row. Undertow's score fell 0.80→0.20 in 4 days, mostly from misses outside Harborside.
- **Vesper doesn't fit.** On 14–16 Aug her score was still 0.76–0.84 and she took all three of 41006/41023/41034 (asked third). On 18 Aug she was skipped while at 0.76 for Nightwell at 0.28. Unexplained: ask Aunt Dot or Wen about her location and availability.
- **The 4.2 weights helped low-score locals.** Under the old weights, a zero-score responder lost to a perfect one within about 40 min; under 4.2, about 19 min. Don't frame this as a weights revert. Priya's handover confirms the change was meant for nearby responders with weaker records (answers Marcus's 14 Aug question). The interaction with the 60s cut was never considered. No scores were reset at release.
- **Code facts:** the only way to gain points is a take (+0.08). Nothing else adds points: no decay, no reset, no handler restore. A miss and a "no" are the same call (−0.12). Scores sit in an in-memory dict keyed by name, with no dates or area, so the repo can't be exactly what's in production. About 40 unfilled callouts per period end after one ping, both before and after 4.2.
- **Open asks:** Wen (does production match the repo, where scores are stored and whether they reset, real stored scores 10 Aug–6 Sep, does a handler override earn points). Ravi (other responders fitting the pattern). Helen (whether to restore 90s or a compromise, and why the 60s cut was made).
- **Ideas drafted, not agreed:** reset the four now, quiet-responder alert in the console, harder-to-miss pings, an "I'm busy" pause (touches the Availability Record, so tell Supply), smaller miss penalty, score recovery, per-area scores.
