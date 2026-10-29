# Solution — Exercise 02

## What's on this branch

- **[ANSWER-KEY.md](ANSWER-KEY.md):** for each input, what it tests, what correct notes contain, and the answers that look right but fail. Check your scoreboard against it before you read on.
- **[`prompts/`](prompts/):** my prompt versions, v1 to the last one, unedited.
- **[LOG.md](LOG.md):** my filled-in log.

## What I found

Run on Opus 5.5 in claude.ai, 26 October 2026.

**v1 passed 0 of 5.** Eight words: "create the summary of the transcript meeting attached". Length (check 6) failed on every input. Dates (check 3) failed on four. Owners (check 2) failed on 04 and 05.

**The change that moved the score most was the most specific one.** v2 added "under 200 words". Check 6 disappeared on all five inputs at once: 0/5 → 2/5. "Be concise" wouldn't have done that. A number did.

**Asking for what wasn't decided stopped the invented owners.** v3 asked for the decisions, and the points not decided. The owner failures on 04 and 05 went away: once the output had a place for "nobody took this", the model stopped assigning someone.

**Dates only fell to stated shape.** Check 3 failed on 03, 04 and 05 through three versions. v4 asked for a table of actions, owners and finishing dates, with dates as calendar dates, and 03–05 passed. "Tomorrow" became Fri 9 Oct, "Monday" became Mon 12 Oct.

**Where I broke my own rules:**

- My first attempt jumped from v1 straight to a much fuller prompt. It improved things, and I couldn't say which part did it. I threw it away and restarted one change at a time. That's the run on this branch.
- Even then, v3 changes two things and v4 changes three: table, owners, date format. I believe "calendar date" fixed check 3, but this log can't prove it.
- I didn't rerun v3 and v4 on 01 and 02, the inputs already passing. The blanks in the scoreboard are honest: I don't know whether they regressed.

**The pass that should have been a fail.** I scored 05 on v4 as a pass. The answer key says otherwise: the table gives Ana's cooking-class check a due date of Fri 16 Oct 2026. That's "end of next week", the date Joana pushed back on. The date she asked for instead is inaudible. The correct cell says unclear. Asking for calendar dates fixed the relative ones and pushed the model to fill the one that didn't exist. So v4 is 2 of 3 verified, not 5/5.

**v1 → v4 in one line:** every word I added describes the output — its length, its sections, its table, its date format. None of it is a magic phrase. The next version would add one line: if a date or owner isn't stated, write "unclear".
