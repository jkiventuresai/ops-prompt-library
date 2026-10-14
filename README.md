# Ops Prompt Library

AI prompts for the paperwork that runs buildings, vendors, and field work.

Most prompt libraries are written for developers or marketers. This one is written
for operations: the person reviewing three contractor bids that don't line up, turning
a site walkthrough into an SOP somebody will actually follow, or writing an incident
report that holds up six months later when it matters.

Every prompt here is built around the same idea: **an LLM is only as good as the
constraints and source material you hand it.** A prompt that says "review this quote"
gets you a summary. A prompt that says "list every line item present in Quote A and
absent from Quote B, and do not infer missing scope" gets you the thing you were
actually trying to find.

## The prompts

| Prompt | Use it when |
|---|---|
| [Vendor quote comparison](prompts/vendor-quote-review.md) | You have 2–5 bids for the same job and they don't line up |
| [SOP from messy notes](prompts/sop-from-messy-notes.md) | A procedure lives in someone's head and needs to live on paper |
| [Scope of work drafting](prompts/scope-of-work-drafting.md) | You want fewer change orders on the next job |
| [Incident report](prompts/incident-report.md) | Something happened and the written record has to be defensible |

## How to use these

1. Copy the prompt block.
2. Replace the `[BRACKETED]` placeholders. Don't skip this — the placeholders are
   where your actual context goes, and the prompt is mostly useless without it.
3. Paste your source material (quotes, notes, transcript) after the prompt.
4. Read the output critically. Every prompt here includes a "what to check" section
   because none of this output should be forwarded unread.

These work on any current frontier model (Claude, ChatGPT, Gemini). They're written in
plain language rather than model-specific syntax, so they don't rot when a model
version changes.

## A note on what these can and can't do

These prompts are good at structure, comparison, and first drafts. They're bad at
knowing your building, your contract terms, your jurisdiction's code, and whether the
vendor is lying. They reduce the time between "I have a pile of material" and "I have
a reviewable draft." They do not replace the review.

Nothing here should be treated as legal, safety, or code-compliance advice.

## Want the full system?

These are individual prompts. If you want the underlying method — how to build prompts
like these for your own recurring work instead of copying someone else's —
[**Prompt Coach**](https://jkilabs.gumroad.com/l/promptcoach?utm_source=github&utm_medium=repo&utm_campaign=ops-prompt-library&utm_content=readme)
is the $20 version of it.

## Contributing

Found a prompt that works? Open an issue with the prompt, the job it does, and one
real example of input and output. Prompts that haven't been used on real work get
declined — the whole point of this library is that everything in it has been run.

## License

[CC0 1.0](LICENSE) — public domain. Use these commercially, modify them, ship them
inside your own documentation. No attribution required.

---

Maintained by [JK Labs](https://jkilabs.gumroad.com).
