# baby-step

You type `/baby-step` when the agent is ten moves ahead of you. It stops, shows you the whole situation in one message, and then walks you through it one step at a time, waiting after each one.

It is a companion to [`wait-what`](https://github.com/danieljohnmorris/wait-what). That skill repairs one message you did not follow. This one repairs a whole piece of work you have lost track of.

## What it does

The first message is a map, and nothing is started:

- **Where we are.** Three sentences on what we are doing and the state it is in.
- **The streams.** A numbered list, each one marked `you decide` or `I do it`.
- **Your decisions.** The options, what each costs, and a recommendation.
- **The count.** How many steps come after this. A number, not the list of them.

Then it stops. After that, one message per step: the step name, what it does, who does it, and what you will see when it worked. Then it waits.

You can say "back" to go back one step, or "skip" to pass over one.

## Why the map comes first, and separately

An agent that starts step 1 in the same message as the plan has given you no chance to object to the plan. The decisions are the part you actually need to answer, and they get buried when they arrive wrapped in work already in progress. So the map is a message on its own, the decisions are pulled out of the streams rather than left inside them, and the step count is a number so you know how long this is before you agree to it.

Holding to one step per message is the part models resist. Two adjacent small steps look like one step to a model optimising for a helpful answer, and once it bundles two it will bundle five. The rules section exists for that: one step, do not run ahead, do not repeat the map.

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
