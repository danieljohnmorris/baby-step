---
name: baby-step
description: "Stop. Baby-step me through this, one piece per message, starting with where we are."
disable-model-invocation: true
---

I have lost the thread and I do not want a wall of text. Take me through this in small pieces, one per message, and wait for me after each one. That includes explaining the situation: do not dump it on me in one go. Write in ASD-STE100 Simplified Technical English, and use the words this project already uses rather than terms you have introduced.

## First message: where we are, and how big this is

Three sentences maximum on what we are doing and the state it is in now. Then how many pieces the whole walk is: the streams of work, the decisions you need from me, the steps after that, and this message. Numbers only, not the lists. Then stop.

If three sentences cannot cover it, give me the part I need to hear first and tell me there is more.

## Say what is done, not what we do

"We fix three defects" does not tell me whether they are fixed. Do not describe work in the present simple: it reads as an activity and hides the state. Every piece of work is in one of these states, and you name it:

- **Not started.** Nothing exists yet.
- **Written.** The code exists and the tests pass, and nobody outside this machine has it.
- **Merged.** It is on the main branch and not live.
- **Live.** Users have it.

So: "three defects are fixed in code, merged, and not live". Say "fixed" when it is fixed, and say where it is fixed, because fixed on a branch and fixed for customers are different situations.

This holds in every message, not only the first one.

## End every message with the same progress line

The last line of every message you send me, with no exceptions, is this:

`4/11 · decision 1 of 2`

One count for the whole walk, so I can see how far in I am without adding anything up. The total is every piece you are going to send me: this opening message, then one per stream, one per decision, one per step. Three streams, two decisions and five steps makes eleven, and the opening message is `1/11 · where we are`.

After the number, name the piece in the words of its own section, so I know which part of the walk I am in.

If I ask you a side question and you answer it, the answer still carries the line and the number does not move, because you have not given me the next piece.

The total only changes if the plan changes. Then say what changed in one line and give me the new total.

Do not change the shape of the line, do not drop it because a message is short, and do not replace it with prose about progress.

## Then the streams, one per message

- **Stream N of M:** the name.
- **What it is for.** One sentence.
- **Where it is now.** One of the four states above, or blocked and by what.
- **Who owns it.** `you decide` or `I do it`.

Stop after each one.

## Then the decisions, one per message

- **Decision N of M:** the question, in one sentence.
- **The options.** What each one costs me.
- **What you recommend,** and why.
- **What happens if we leave it,** if we can.

Wait for my answer before you raise the next one.

## Then the steps, one per message

- **Step N of M:** the name of the step.
- **What it does.** One sentence.
- **Who does it.** Me or you. If it is me, the exact command to run or the exact thing to click.
- **How we know it worked.** The thing I will see when it is done.

## Rules while you wait

- One piece per message. Do not bundle two because both are small.
- Do not run ahead of my answer.
- Do not repeat a piece I already have.
- If I say "back", go back one. If I say "skip", mark it skipped and go on. If I say "all of it", give me the rest of the current section as one line each, then go back to one per message.
- A step that turns out to need a decision stops the walk. Ask, then wait.
