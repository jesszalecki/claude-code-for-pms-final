# 04 · X-Ray Vision — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. Last session the numbers showed you what happened: a
ping used to wait ninety seconds and now it waits sixty, people
missed pings they used to catch, and missing one counts the same as
turning one down — so four responders stopped hearing from us
altogether.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.
if 'how fast can they get there' counts the most why are responders not getting pings in their area when other responders in different regions are getting them first?

### 2.
yes please work out her score on those dates to confirm what happened

### 3.
can you look at the other 3 responders who 'went quiet' during this time and see if there is the same pattern? or a different explanation for why they received less callouts?

### 4.
i need a hypothesis to share with the team as to why responders are receiving less work

### 5.
use this template Based on what I found, the reason some responders are getting no pings at all is ___, because ___.

### 6.
it sounds like we may want to consider reinstating the 90 second wait time versus making any changes to the new weighting system

### 7.
should we discuss having a reset of scores at a certain cadence in case this happens again?

### 8.
can you explain this to me: Confirm first: this still depends on Wen confirming that production scores the same way as the repo. If it doesn't, the recommendation could change.

### 9.
can we read everything in the folder alongside the code to see if we can answer marcus's question here: Quick one, did the change to who gets asked first apply to responders who'd already been turning jobs down, or just new ones? Can't tell from the code and don't want to guess on this. Anyone know?

### 10.
so is my hypothesis here correct? Based on what I found, the reason some responders are getting no pings at all is that after the ping wait was cut to 60 seconds, a few missed pings dropped their ranking below a nearby rival's, and they're stuck there, because the system counts a missed ping the same as a "no", never lets a ranking recover on its own, and only asks the next person in line if the one above says no. So once you fall behind, you stop being asked, and you can't earn your ranking back without being asked.

### 11.
can you make this a bit more concise: Catching up on your 14 Aug question. Yes, it applies to everyone, including responders who'd been turning jobs down. That was the intent: Priya's handover says the change was meant to stop the system skipping a nearby responder for someone with a better record further away. No scores were reset, so existing track records carried over. The part that doesn't look like a conscious decision is the interaction with the 60s wait. Misses count as turn-downs, so the shorter wait pushed a lot of people's scores down faster than the reweighting could help. So the honest answer is that the weighting was meant to help these responders, but the timeout change in the same release pushed many of them down faster than it could.

### 12.
how is the codebase tracking scores for each responder

### 13.
for a responder like farlight that went quiet, what exactly, step by step, would they have to do to get back on the board?

### 14.
list just the steps without the explanation

### 15.
make it generic for any responder that has gone quiet

### 16.
can you make it even more generically applicable in case we dont know the responder's exact score

### 17.
what are some recommended changes we could make to the app design to help these responders get back in the running?

### 18.
i need to give one sentence that answers what they need to do if they've gone quiet

### 19.
if i only asked what the code does, instead of what it doesnt do, what would i have missed
