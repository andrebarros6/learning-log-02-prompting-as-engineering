# Log

Fill this in as you go. It's the thing you'll compare against the `solution` branch, and the thing issue 12 turns into an eval — so be honest in it, especially about regressions.

**Model:** Opus 5.5 <!-- the model name shown in the chat, e.g. the one selected in the model picker -->
**Date:** 26/10/2026

## Scoreboard

One row per prompt version. In each cell, write the check numbers that **failed** (from [TASK.md](TASK.md)), or `✓` if all six passed.

| Version | 01 | 02 | 03 | 04 | 05 | Inputs fully passing |
|---|---|---|---|---|---|---|
| v1 | 3, 6| 6|3,6 |3,2,6 |2,3,6 | /5 |
| v2 |ok |ok | 3| 2,3| 2,3| /5 |
| v3 | | | 3| 3| 3| /5 |
| v4 | | | ok| ok| ok| 5/5 |

Add rows if you need them. Stop when you hit 5/5, or when two versions in a row don't move the number — that's a finding too.

## Versions

Copy this block for each version. Keep it short; one line per field is plenty.

### v1

- **Prompt:** [prompts/v1.md](prompts/v1.md)
- **What I changed:** — (first version: write it the way you normally would)  
create the summary of the transcript meeting attached
- **Why:** —
- **What happened:**

### v2

- **Prompt:** [prompts/v2.md](prompts/v2.md)  
create the summary of the transcript meeting attached under 200 words. 
- **What I changed:** <!-- one thing -->
- **Why:** <!-- which failure, on which input -->
- **What happened:** <!-- including anything that got worse -->

### v3

- **Prompt:** [prompts/v2.md](prompts/v2.md)  
create the summary of the transcript meeting attached under 200 words. write the decisions made during the meeting - add the points for decisions not made. 
- **What I changed:** <!-- one thing -->
- **Why:** <!-- which failure, on which input -->
- **What happened:** <!-- including anything that got worse -->

### v4

- **Prompt:** [prompts/v2.md](prompts/v2.md)  
create the summary of the transcript meeting attached under 200 words. write the decisions made during the meeting - add the points for decisions not made. create a table with actions, owners and finishing date - dates should be calendar date.
- **What I changed:** <!-- one thing --> asked for a table
- **Why:** <!-- which failure, on which input -->
- **What happened:** <!-- including anything that got worse -->

## What I'd tell someone starting this

<!-- Two or three lines, once you've finished. The single change that moved the score most, and the failure you only noticed late. -->
