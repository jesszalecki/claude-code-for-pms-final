# 01 · Origin Story — prompts

**Context:** Rook Industries makes software for superheroes and the
people who handle them.

There are two products. Rook Dispatch is the one that gets a
superhero to where they're needed when there's an emergency — it
works out who is close enough and free enough to help, and gets hold
of them. Rook Supply keeps a responder's equipment serviceable and
accounted for, so a handler is never guessing whether the gear will
hold.

You joined two weeks ago as PM on Rook Dispatch. Release 4.2 shipped
on 12 August, shortly before you arrived. Responders have stopped
answering their phones the way they used to, and complaints have
gone up sharply. You were not in the room for any of it.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.
I just joined Rook Industries as PM for Rook Dispatch. Read everything in 00-rook/company/ and the company notes from the company wiki through the rook-wiki connector and add to the CLAUDE.md at the root of this folder, what you'd need to know to help me do my job here: the products, the people, the vocabulary, where things stand. Leave the session scope block at the top. Keep it under two pages.

### 2.
Pull every support ticket from the Rook database. Group them by theme, tell me how many are in each group, split each count into before and after the 4.2 release on 12 August, and quote one line from each group. Then tell me how many distinct people are behind each group, not just how many tickets.

### 3.
Check those ticket themes against the pings data. Show missed and taken rates week by week, and pings per week for every responder before vs. after 4.2. Who was hit hardest, and does that match who complained? Tell me what the data can't show.

### 4.
Read all the customer interviews in the wiki. For each one, tell me what went wrong, how the responder reacted when a ping arrived, what happened next and what the handler thinks caused it. Then tell me specifically where the interviews agree with the tickets and where they contradict them.

### 5.
What's contradictory or missing across everything in 00-rook — the handoff, the code, the changelog — compared against the wiki and the database? Rank what's most worth acting on.
