# baby-step

You type `/baby-step` when the agent is ten moves ahead of you. It stops and takes you through the work one piece per message, waiting after each one.

It is a companion to [`wait-what`](https://github.com/danieljohnmorris/wait-what). That skill repairs one message you did not follow. This one repairs a whole piece of work you have lost track of.

## What it does

Four sections, in order, one message at a time:

1. **Where we are.** Three sentences on the work and the state it is in, then how many pieces the whole walk is: streams of work, decisions you owe, steps after that.
2. **The streams,** one per message: what it is for, where it is now, and whether you decide it or the agent does it.
3. **The decisions,** one per message: the question, the options and their cost, a recommendation, and what happens if you leave it.
4. **The steps,** one per message: what it does, who does it, and what you will see when it worked.

Say "back" to go back one, "skip" to pass over one, or "all of it" to get the rest of the current section as a list and drop the pacing.

Every message ends with the same line, so you always know how far in you are:

```
4/11 · decision 1 of 2
```

One count for the whole walk, not one per section. Eleven is the opening message plus three streams plus two decisions plus five steps. Ask a side question and the answer carries the line unchanged, because a digression is not progress.

## The explanation gets stepped too

The first version of this had the agent lay out the whole situation in one message and then step through the work. That is the wrong way round. Work you have lost the thread of is work whose shape you cannot hold, so a complete map of it is another wall of text, arriving at the exact moment you said you could not read one. If the situation were small enough to take in one message you would not be typing `/baby-step`.

So the situation is paced on the same terms as the steps. What you get up front is short: three sentences and a count. The count matters more than it looks. It tells you how long this is and how much of it is your decision before you agree to any of it, and it is cheap to read in a way a list of nine streams is not.

Decisions get their own messages for the same reason. A decision buried in a description of a stream gets skimmed past, and a decision that arrives alongside work already in progress is not really being asked.

Holding to one piece per message is the part models resist. Two adjacent small items look like one item to a model optimising for a helpful answer, and once it bundles two it will bundle five. Hence "all of it": the pacing needs an exit you control, or you will start fighting the skill instead of using it.

## Why ASD-STE100

Same reason as `wait-what`. ASD-STE100 Simplified Technical English is a controlled language written for aircraft maintenance manuals: an approved dictionary of about 900 words, one meaning per word, short sentences, active voice, one instruction per sentence. Asking for "plain English" gets a model's guess at plain English. Naming a specification gives it a target it already knows, and one it can be wrong against.

It matters more here than in a re-pitch, because these messages are instructions you are going to follow.

## Install

Claude Code, per user:

```bash
git clone https://github.com/danieljohnmorris/baby-step.git /tmp/baby-step
cp -R /tmp/baby-step/skills/baby-step ~/.claude/skills/baby-step
```

Per project, swap `~/.claude/skills` for `.claude/skills`. For omp, use `~/.omp/agent/skills`.

Then type `/baby-step`. The agent will not reach for it on its own: `disable-model-invocation: true` is set, because only you know when you stopped following.

## When to use it

When you are about to say yes to a plan you have not read. When the work has more than one thread and you cannot hold them at once. When you are being asked to run commands you do not understand the purpose of.

It does not plan the work. If the work is too big to hold in one session, that is a different job.

## Licence

MIT. Copyright (c) 2026 Daniel Morris. The single-purpose, model-invocation-disabled skill shape, and the use of ASD-STE100, are taken from Matt Pocock's [`wait-what`](https://github.com/mattpocock/skills).
