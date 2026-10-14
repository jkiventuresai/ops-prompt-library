# Incident report

**The job:** something happened — a leak, an injury, a failure, a tenant complaint that
escalated — and you need a written record that is accurate, complete, and still useful
six months from now when someone asks what happened.

**Why the obvious prompt fails, and why this one is the riskiest in this library:** an
LLM writing an incident report will produce confident narrative prose. Narrative prose
fills causal gaps, because that's what narrative does. In a document that may be read
by an insurer, a lawyer, or a regulator, an invented detail or an unsupported causal
claim is worse than a missing one. So this prompt is built to do the opposite of what
the model wants to do: separate observation from inference, and refuse to speculate.

**Do not send the output of this prompt anywhere without reading every line against
what you actually know.** It is a structuring tool for your own account of events. It
is not a witness.

## The prompt

```
Help me structure an incident report from my raw account below. You are organizing
what I tell you — you are not reconstructing the event.

Incident type: [LEAK / INJURY / EQUIPMENT FAILURE / PROPERTY DAMAGE / OTHER]
Date and time of incident: [WHEN]
Date and time I am writing this: [WHEN]
Location: [BE SPECIFIC — BUILDING, FLOOR, UNIT, ROOM]
Reported by: [WHO FIRST REPORTED IT, AND HOW]

Produce:

1. SUMMARY — 3 sentences. What happened, where, current status.

2. TIMELINE — a table: time, event, source of that information. The source column is
   required for every row and must be one of: "directly observed by me", "reported by
   [named person]", "system/log record", or "unknown". If I did not tell you the time,
   write "time not established" — do not estimate it.

3. OBSERVED FACTS — only what was directly seen, measured, photographed, or recorded.
   No causes in this section.

4. REPORTED STATEMENTS — what people said, attributed to them, in their framing. Mark
   clearly that these are statements, not established facts.

5. ACTIONS TAKEN — what was done, by whom, when.

6. CURRENT STATUS — what is resolved, what is temporary, what is still open.

7. OPEN QUESTIONS — what is not yet known, and who could answer it.

Absolute rules:
- Do not state a cause. If my account suggests one, put it in OPEN QUESTIONS as a
  question to be verified, not in the facts.
- Do not add any detail I did not give you. Not a time, not a measurement, not a
  weather condition, not a part name, not a quantity.
- Where my account is unclear, write >> UNCLEAR: [what you'd need to know] rather than
  choosing the more likely reading.
- Do not characterize anyone's conduct, intent, or state of mind. "Did not respond to
  three calls" is a fact. "Was unresponsive" is a characterization.
- Neutral register. No minimizing, no dramatizing, no "fortunately" or "unfortunately."

My account:
[PASTE — write it however it comes out. Don't organize it first; that's this prompt's job.]
```

## What to check in the output

- **Every timeline row has a source.** If any row's source is blank or vague, that row
  is an assumption wearing a timestamp.
- **Hunt for causal language in sections 3–5.** Words like "because," "due to,"
  "caused by," "as a result of," and "failed to" smuggle in conclusions. Move every one
  of them to OPEN QUESTIONS unless you can personally prove it.
- **Check every number, time, and measurement against your own knowledge.** These are
  what get quoted back at you.
- **If the output reads better than your account did, be suspicious.** Fluency is the
  tell. Your raw account was uncertain in places; the report should still be uncertain
  in those same places.

## Adapting it

- **Injury or anything potentially litigable:** stop. Follow your organization's
  reporting procedure and your insurer's requirements first; those have deadlines and
  formats that override anything here. Use this only to organize your own notes
  beforehand, and loop in counsel before the account goes anywhere.
- **Multiple witnesses:** run each person's account separately, then compare the
  timelines yourself. Do not ask the model to reconcile conflicting accounts into one
  narrative — the conflicts are information, and merging destroys them.
- **Equipment failure specifically:** add a section for asset ID, make/model, install
  date, last service date, and warranty status. Pull those from your records, not from
  the model.
- **Photos:** reference them by filename in the timeline. A report that mentions
  "photos were taken" without identifying them is much weaker than one that names them.

---

Built by [JK Labs](https://jkilabs.gumroad.com). If you'd rather learn to write prompts
like this than copy them,
[Prompt Coach](https://jkilabs.gumroad.com/l/promptcoach?utm_source=github&utm_medium=repo&utm_campaign=ops-prompt-library&utm_content=incident-report)
is the method behind it.
