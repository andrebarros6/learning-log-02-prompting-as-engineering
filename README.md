# Learning Log — Exercise 02: Prompting as engineering

**Issue 2 of 30 · Working with the models** · [Read the issue](https://barrosbuilds.com/log) · [All exercises](https://github.com/andrebarros6/learning-log)

**Kind:** inside Claude · **Needs:** a Claude account (the free plan works), git · **Cost:** free

Replace one-shot prompt guessing with a loop you can repeat, and keep the evidence of what each change actually did.

---

## The theory

Most prompting advice is folklore. "You are a world-class expert." "Take a deep breath." "I'll tip you." These spread because they sometimes seem to work. Nobody checks whether the output got better or just different, and nobody checks it on more than one input.

What reliably moves output is duller:

- **Specificity beats incantation.** "Under 200 words, decisions first" changes the output. "Be concise" barely does.
- **Examples beat adjectives.** One worked example of the output you want says more than a paragraph describing it.
- **Stated shape beats implied shape.** If you want three headed sections, say so. The model can't read the format you had in mind.

None of these is a trick. Each one closes a gap between what you meant and what you wrote.

So treat a prompt the way you'd treat code: **write it, run it against several inputs, look at where it fails, change one thing, run it again.** One change at a time, because if you change three things and the output improves, you don't know which one did it, or whether one of the other two made something worse.

Several inputs, because a prompt tuned on one input is tuned to that input. It looks like progress. It's overfitting.

This loop is manual, and with five inputs it's already tedious. That's the point. Issue 12 automates it. You'll appreciate that more once you've done it by hand.

## What you'll do

This one happens in the Claude chat window. No code, no API key.

1. **Read the task and the five inputs.** [TASK.md](TASK.md) says what good output looks like: six pass/fail checks. [`inputs/`](inputs/) holds five meeting transcripts.
2. **Write v1 the way you normally would.** Don't engineer it yet. You need an honest baseline, or you can't tell what the loop bought you.
3. **Run it on all five, score all five.** Write down which checks failed on which input in [LOG.md](LOG.md).
4. **Change one thing.** Pick the failure that matters most, change the prompt to target it, save it as the next version, and run all five again. Not just the one that failed.
5. **Repeat** until everything passes, or until two versions in a row don't move the score.
6. **Diff v1 against your last version.** That diff is the lesson: every line in it is there because a specific input failed without it.

## When this is not the right tool

**Don't iterate a prompt against a single input.** You'll fix that input, and the fix will look like success. It may not survive the next one. Five inputs is the minimum here for that reason.

And don't reach for this loop for a one-off. If you're asking something once and you'll read the answer yourself, just ask. The loop pays off for prompts you reuse, on inputs you won't check by hand every time.

---

## Setup

```bash
git clone https://github.com/andrebarros6/learning-log-02-prompting-as-engineering
cd learning-log-02-prompting-as-engineering
```

Open [claude.ai](https://claude.ai) in a browser, or the desktop app. Any model works. **Write down which one you're using** at the top of LOG.md, because the same prompt behaves differently on different models.

## Run it

For each prompt version, five runs, one per input:

1. **Open a fresh chat for every run.** Not a new message in the same chat. Issue 1 showed why: everything earlier in a conversation is resent with every turn. Run input 02 in the chat where you ran input 01, and the model has read both meetings.
2. Paste your prompt, then the transcript underneath it, as one message.
3. Score the output against the six checks in TASK.md and fill in the scoreboard. Read the transcript yourself to judge it. The output is only wrong if you can say what the meeting actually said.

Twenty-odd short chats in all. If the free plan's usage limit stops you partway, spread the runs over a day. The exercise doesn't care when you run them, only that every version gets all five inputs.

Save every version as its own file: `prompts/v1.md`, `prompts/v2.md`, and so on. Never edit an old one. At the end:

```bash
git diff --no-index prompts/v1.md prompts/v4.md
```

## Checking your work

There's no `pytest` here. The check is your log against the solution branch:

```bash
git checkout solution
```

It has `ANSWER-KEY.md`, which gives, for each input, what a fully correct set of notes contains and which check each input is built to test. Go through your scoreboard input by input.

**The miss to look for isn't a fail you couldn't fix. It's a pass that should have been a fail.** If the answer key flags something your scoring let through, your v4 isn't as good as your log says, and neither is your eye yet. That's worth more than the prompt.

The branch also has `SOLUTION.md`: my own run, with my prompt versions and what moved the score.

## Bring your own prompt

The meetings are scaffolding. **The exercise is a prompt you already use in a real workflow**: the one you paste into a chat every week and tidy up the result of by hand.

Do it after the solution, because your own material has no answer key:

1. Collect five real inputs it runs on. Pick different ones, including the awkward one you always fix by hand.
2. Write the checks first: four to six things the output must get right, each one pass/fail.
3. Run the loop.

Put your own material in a `mine/` folder. It's gitignored. Don't commit real meetings or work documents to a public repo.

---

## Questions, corrections, things that broke

[Discussions on the hub repo](https://github.com/andrebarros6/learning-log/discussions) are one place for all exercises.

Found a step that's gone stale because a tool changed? Open an issue here. Corrections are genuinely welcome; things breaking in public is the format.

## Licence

MIT. See [LICENSE](LICENSE). The exercise is yours to keep.
