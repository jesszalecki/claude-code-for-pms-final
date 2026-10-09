# Product brief: A fair race for Vesper

*For Helen Achebe, Director of Product · Draft for discussion · 9 Oct 2026*
*Owner: Jessica Zalecki, PM, Rook Dispatch*

**Bottom line:** Since 4.2, a few missed pings can push a responder down the line for good. We propose making pings hard to miss *within* the 60-second ping wait, showing responders and handlers what's happening, letting responders set themselves Away, and fixing the scoring underneath. **Your decision:** approve resetting four responders' scores now.

## The problem, through Vesper's eyes
Vesper (Old Town) took 11–12 callouts a week before 4.2. Then it was 6, then 1, then 0. Old Town got busier, but 28 callouts went to Nightwell and Captain Vantage instead. Vesper's handler, Aunt Dot, hears the phone buzz on the kitchen counter and shouts upstairs, and by the time Vesper answers, "it's gone." Then come weeks when the phone just sits there.

- **Why:** a missed ping lowers routing priority as much as a turn-down, and only a taken callout raises it again. Once you fall behind, you stop being pinged and can't earn your place back.
- **Not just Vesper:** Meteor Mite, The Undertow and Farlight fell from 9–12 callouts a week to about 1. Four other responders picked up 20–35% more pings. There are 45 callout tickets, all still open.

## What we'd build

| For | What changes |
|---|---|
| **Vesper** (phone) | A full-screen ping, including the lock screen, with a countdown. Alerts get stronger at 30s and 15s. |
| | A status like Teams: tap **Available** to switch to **Away** and set the time pings come back on. Away means no pings, so being busy never counts as a miss. |
| | **Last 7 days** on the home screen: pings received against Vesper's normal 10–12, with recent pings listed. If it drops, it says why and when it picks back up. |
| | After a miss: what happened, what it means, and for how long. |
| **Aunt Dot** (console) | "Vesper has a ping — 42s left" banner, so Dot doesn't have to listen for a buzz. |
| | A quiet-responder flag that gives the reason, e.g. "4 missed pings since 12 Aug". |
| **Engineering** (Wen, Marcus) | Reset the four responders' scores now. **"Your turn" guarantee:** an available responder who hasn't been pinged for a local callout in 3 days is asked first on the next one. Misses expire after 3 days. |

*Clickable prototype of the phone screens: `05-super-speed/prototype.html`.*

## What we're not doing
Not changing the 60s ping wait · not reverting the proximity change · handlers can't take pings for responders · no raw scores shown · cover identity untouched.

## Success looks like
Within 4 weeks of the release that ships this: Vesper back to ~10 Old Town callouts a week · missed pings from 18% to ~2% · acceptance rate from 64% to ~77% · callout tickets back to their pre-4.2 weekly level (about a third of the rate since 4.2). *4 weeks is a placeholder. Ravi to confirm the window and the weekly baselines.*

## Decisions and dependencies
1. **Helen:** reset the four responders' scores now, ahead of the app work?
2. **Supply:** setting Away writes to the Responder Availability Record, so they need to sign off.
3. **Wen:** confirm production scores the same way the repo does (Vesper's 18 Aug skip is still unexplained).
4. **Wen and Marcus:** confirm the "your turn" guarantee and miss expiry, and set the real numbers. Letting scores drift back to the middle wouldn't be enough: a responder at 0.5 still trails an active rival by about 9 minutes of travel time. The prototype uses placeholders: 3 days, and normal means 10–12 pings a week.
