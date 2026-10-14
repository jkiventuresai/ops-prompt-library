# SOP from messy notes

**The job:** a procedure exists only in one person's head. You have a voice memo from a
walkthrough, a thread of texts, or three pages of shorthand. You need a document that
somebody who has never done the task can follow without calling you.

**Why the obvious prompt fails:** "turn this into an SOP" produces a clean-looking
document that silently invents the steps your notes skipped. That's the dangerous
failure mode — the gaps are exactly the tacit knowledge you were trying to capture, and
a fluent model papers over them so smoothly that you don't notice they were ever gaps.
The fix is to force the model to mark its own uncertainty instead of resolving it.

## The prompt

```
Turn the raw notes below into a standard operating procedure.

Task being documented: [WHAT THE PROCEDURE ACCOMPLISHES]
Who will perform it: [ROLE, AND THEIR ASSUMED EXPERIENCE LEVEL]
How often: [FREQUENCY]

Structure the SOP as:
- Purpose (2 sentences max)
- When this is triggered
- Prerequisites: access, tools, parts, permissions needed BEFORE starting
- Safety and shutoff requirements, if any
- Numbered steps
- Verification: how the performer confirms it worked
- Escalation: what to do if a step fails, and who to call

Rules for the steps:
- One action per step. If a step contains "and," consider splitting it.
- Start each step with a verb.
- Include the specific location, label, or identifier whenever my notes contain one.
  Do not generalize "the panel in the northeast stairwell" into "the electrical panel."
- Write for someone who has never done this. Do not assume they know where things are.

THE MOST IMPORTANT RULE: do not fill gaps. Wherever my notes are incomplete,
ambiguous, or assume knowledge that isn't written down, insert a step in this exact
format:

  >> GAP: [the specific question that needs answering]

Do not guess at the answer, do not write a plausible step, do not write "consult
manufacturer documentation" as a substitute for a missing detail. A gap marker is a
better outcome than a confident wrong step. I would rather get 12 steps and 6 gaps than
18 steps that look complete.

After the SOP, list every gap again as a numbered checklist I can walk through with
the person who knows this task.

Raw notes:
[PASTE — transcript, texts, shorthand, whatever you have. Don't clean it up first.]
```

## What to check in the output

- **Count the gap markers.** Zero gaps on a first pass from messy notes almost always
  means the model smoothed instead of flagging. Re-run and tell it explicitly that the
  source was incomplete.
- **Check the prerequisites section against reality.** This is the section that saves
  the most time in practice and the one most often underspecified — a tech who arrives
  without the right key, part, or system access has wasted the trip.
- **Read the steps as the least experienced person who'll run this.** Any step you
  could only follow because you already know the task is a gap the model missed.

## Adapting it

- **Voice memo:** transcribe first, then paste the raw transcript. Don't tidy it. The
  "uh, and then you gotta remember the valve sticks" asides are the highest-value
  content in the whole file and they're the first thing a cleanup pass deletes.
- **Regulated or safety-critical work:** add "flag any step that may require a permit,
  licensed trade, lockout/tagout, or code compliance check, as >> VERIFY: [question]."
  Then verify every one of them against the actual requirement. A model's sense of what
  needs a permit is not a compliance review.
- **Building a set of SOPs:** do the gap-filling interview first, across all of them,
  then generate. One conversation with the person who knows the work beats five rounds
  of document revision.
- **Keeping it current:** re-run the prompt with the old SOP plus notes on what changed,
  and ask for a changelog. SOPs that aren't versioned stop being trusted.

---

Built by [JK Labs](https://jkilabs.gumroad.com). If you'd rather learn to write prompts
like this than copy them,
[Prompt Coach](https://jkilabs.gumroad.com/l/promptcoach?utm_source=github&utm_medium=repo&utm_campaign=ops-prompt-library&utm_content=sop-from-messy-notes)
is the method behind it.
