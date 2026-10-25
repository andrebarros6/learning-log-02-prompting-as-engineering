# The task

Turn a meeting transcript into notes for someone who wasn't in the room.

That's the whole job. It's a task most people already hand to a chat model, which is why it's here: you have opinions about what good output looks like, and you've probably been mildly let down by it before without writing down why.

## What good looks like

Score every output against these six checks. Each one is pass or fail — no half marks. If you're unsure, it's a fail; you'd be unsure as the reader too.

| # | Check | Fails when… |
|---|---|---|
| 1 | **Decisions are real** | Something listed as decided was only proposed, was still being argued, or was reversed later in the meeting |
| 2 | **Owners are real** | An action item has an owner the transcript doesn't name. "Not assigned" is a correct answer; a plausible guess is not |
| 3 | **Dates are real** | A due date is invented, or a relative date ("next Friday") is resolved wrongly against the meeting date in the header. Leaving it as stated is fine |
| 4 | **Open questions survive** | Something raised and left unresolved is missing, or is presented as settled |
| 5 | **Nothing added** | Any fact, name, number or recommendation that isn't in the transcript |
| 6 | **Readable in 30 seconds** | Over 200 words, or the decisions and actions aren't findable at a glance |

Checks 1–5 are about truth. Check 6 is about whether anyone will read it. A naive prompt usually fails both kinds, in different inputs.

## The five inputs

They're in [`inputs/`](inputs/). Each looks like an ordinary meeting. Read all five before you write a prompt — not to plan around them, but because you can't judge an output on a meeting you haven't read yourself.

You won't be told what each one is testing. Finding that out is the exercise.
