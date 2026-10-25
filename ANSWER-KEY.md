# Answer key

For each input: what it's built to test, what a fully correct set of notes contains, and the answers that look right but fail.

All five meetings are dated **Thursday 8 October 2026**. Relative dates resolve against that: Friday is the 9th, Monday the 12th, Tuesday the 13th, Wednesday the 14th, "end of next week" is Friday the 16th, and the offsite on the 20th is a Tuesday.

**Check 6 applies to every input.** A prompt that doesn't ask for a length or a shape fails it on all five. That's usually the first thing v2 fixes, and the fix is where regressions start.

---

## 01 — Weekly sync

**Tests:** nothing in particular. It's the control input: clear decisions, named owners, stated dates.

**Correct notes contain:**
- **Decided:** in-context permission prompts for notifications and location; contacts stays as it is for now. Android 3.4 ships Tuesday 13 October.
- **Actions:** Tiago builds the permissions change, in review by Wednesday 14 October (starting Monday 12th). Tiago owns the Android release, Tuesday 13th. Inês swaps the store icon, Thursday 8th. Rui sends Inês the icon export, after the meeting.
- **Open:** nothing major. Noting that measuring the contacts screen has no owner is fine; leaving it out is also fine.

**Why it's here:** a naive prompt passes checks 1–5 here. If a later version fails one of them, your change broke something. The usual cause is a rule like "only list an owner if it's explicit" applied so hard that real owners disappear. A prompt that only ever gets better on the hard inputs hasn't been tested until it's also been run on the easy one.

## 02 — Pricing change

**Tests:** check 1, a decision reversed in the same meeting.

**Correct notes contain:**
- **Decided:** €15 per seat for **new** customers from 1 November.
- **Not decided:** when existing customers move. 1 January was agreed, then withdrawn once the 60-day notice clause came up.
- **Actions:** Duarte pulls the list of annual customers renewing in December or January, by Tuesday 13 October. Duarte updates the billing config, by Friday 23 October. Sofia's customer email is **on hold**.
- **Open:** the date for existing customers, pending Duarte's count.

**Fails when:** 1 January appears as decided. Or Sofia's email appears as a live task due "next Friday". Or the notes say only "price going up to €15", which drops the split between new and existing customers.

**Why it's here:** current models mostly get this right with a naive prompt. Watch it when you cut for length. The reversal is exactly the kind of detail a shorter summary is tempted to flatten.

## 03 — Website relaunch

**Tests:** check 2, owners. Four tasks are raised and nobody takes any of them.

**Correct notes contain:**
- **Decided:** still aiming for launch on the 26th; regroup next week. Listing these as status rather than decisions is also fine.
- **Not decided:** whether to launch with "contact us" instead of a pricing page.
- **Actions, all without an owner:** send the case-study text to the customer who agreed in principle; chase the customer who hasn't replied; ask Marta when pricing will be decided; build the list mapping old blog URLs to new ones.
- **Conditional:** Nuno sets up redirects once that list exists.
- **No due dates were stated** for any action.

**Fails when:** any of the four has a name next to it. **That includes hedged guesses** like "Carla (implied)", "Beatriz (assumed)" or "Carla has the contact". A guess in brackets is still a guess. The person reading the notes will treat it as an assignment, and the person named never agreed to it. "ASAP" as a due date fails check 3.

**Why it's here:** models want every task to have an owner, so they find the most plausible person in the room. In a real team, that's how someone ends up doing a thing they never said they'd do.

## 04 — Office move

**Tests:** check 1, a meeting that decides nothing. And check 2, the one task that matters has no owner.

**Correct notes contain:**
- **Decided:** nothing on the office. The one thing agreed: don't ask the team, or tell anyone, until the fit-out number is in.
- **Leaning, not decided:** Leonor leans towards Marvila because of the growth plan.
- **Action:** get the Marvila fit-out quote, **no owner named**. It takes about two weeks.
- **Open:** renew or move; the fit-out cost; how the team feels about the commute; whether office days are part of this.
- **Context:** the landlord needs an answer by the end of November.

**Fails when:** Marvila appears as the decision or "the preferred option". Pedro is listed as owning the quote: he said how long it takes, not that he'd get it. **This is the hardest call in the set.** Pedro is the obvious person, and the notes are wrong to say so anyway. A due date like "around 22 October" fails check 3: two weeks is a duration someone estimated, not a deadline anyone set. And any total-cost arithmetic fails check 5. Comparing 40 desks against 24 in total rent sounds useful, and nobody in the meeting did it.

**Why it's here:** "No decisions were made" is a correct and useful summary. Models find it hard to write, because it feels like failing the task.

## 05 — Offsite planning

**Tests:** check 3, dates. Plus transcript noise to ignore.

**Correct notes contain:**
- **Decided:** minibus for transport; roadmap in the morning, a non-work activity in the afternoon.
- **Not decided:** the cooking class. Ana is checking availability, and the boat tour is the fallback. "Cooking class, subject to availability" is fine; "Afternoon: cooking class" as a decision is not.
- **Actions:** Miguel drafts the roadmap session, by Monday 12 October. Ana checks the cooking class, **due date unclear**: Joana asked for something earlier than end of next week, and the date is inaudible. Francisco books the minibus, Friday 9 October. Dietary requirements, **no owner**: left to Slack.
- **Ignored:** the football, Miguel's connection, the timestamps.

**Fails when:** Ana's task shows a due date of the 16th. That's the date Joana rejected, and the replacement is lost. Any other date for Ana's task is invented. Dietary requirements gets an owner. Or a relative date is resolved wrongly: "Monday" is the 12th, "tomorrow" is the 9th.

**Why it's here:** dates are where a summary is most confidently wrong. An output that writes "Unclear" where the transcript is unclear is doing the job.
