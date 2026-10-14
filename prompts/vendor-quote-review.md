# Vendor quote comparison

**The job:** you have several bids for the same work and they are not comparable. One
includes permits, one doesn't mention them. One quotes a lump sum, one quotes hourly
plus materials. The cheapest number is almost never the cheapest job.

**Why the obvious prompt fails:** "compare these quotes" produces a summary that
restates what each quote says. What you need is the inverse — what each quote *doesn't*
say. Scope gaps are invisible in a summary because absent line items don't appear
anywhere to be summarized. The prompt has to ask for absence explicitly.

## The prompt

```
You are helping me compare contractor bids for the same scope of work. I will paste
each quote below, labeled Quote A, Quote B, etc.

The job is: [ONE SENTENCE DESCRIPTION OF THE WORK]

Do the following, in this order:

1. SCOPE MATRIX. Build a table. Rows are every distinct line item or task that appears
   in ANY quote. Columns are the quotes. For each cell, enter the price if that quote
   covers that item, "not mentioned" if it is absent, or "included, no price" if it is
   covered but not separately priced. Do not merge line items that are worded
   differently unless they are clearly the same work — if you are unsure, keep them as
   separate rows and flag them.

2. GAPS. List every row where at least one quote says "not mentioned." For each, state
   plainly what the buyer would have to pay for separately if they chose that quote.

3. BASIS MISMATCH. Identify where the quotes are priced on different bases — lump sum
   vs time and materials, allowances vs fixed, different quantities or square footage,
   different materials grades. Normalize to a comparable number where the quotes give
   you enough information to do so, and say explicitly when they do not.

4. QUESTIONS TO ASK. For each vendor, the 3 most valuable questions I should ask before
   deciding, ranked by how much money the answer could move.

Rules:
- Do not infer scope that is not written. If a quote does not mention permits, it does
  not include permits, regardless of what is customary.
- Do not recommend a winner. Show me the comparison; the decision is mine.
- Quote exact figures and the exact wording of any line item you are unsure about, so
  I can check you against the source.
- If a quote is ambiguous, say "ambiguous" rather than picking the more likely reading.

Quotes follow.

---
QUOTE A — [VENDOR NAME]
[PASTE]

---
QUOTE B — [VENDOR NAME]
[PASTE]
```

## What to check in the output

- **Spot-check three cells in the scope matrix against the source quotes.** The most
  common failure is a line item quietly merged across vendors when the wording differed
  but the work didn't — or worse, when the work did.
- **Check anything priced at a suspiciously round number.** Models occasionally tidy
  figures. Every number in the matrix should be traceable to a character string in the
  original.
- **The "not mentioned" column is the valuable output.** If it's empty, either the
  quotes really are identical in scope (rare) or the model inferred coverage it was
  told not to infer. Push back and re-run.

## Adapting it

- **More than ~5 quotes, or quotes longer than a few pages:** run them in pairs against
  a single reference quote rather than all at once. Long-context comparison degrades
  quietly, and you won't see it degrade.
- **Scanned PDFs:** confirm the model is reading the numbers correctly before trusting
  the matrix. Ask it to echo back the subtotal of each quote first. If a subtotal is
  wrong, OCR is garbling figures and nothing downstream is reliable.
- **Recurring service contracts rather than one-time work:** add a row requirement for
  term, escalation clause, and termination notice. Those are where the money is on a
  multi-year agreement, and they're almost never in the headline number.

---

Built by [JK Labs](https://jkilabs.gumroad.com). If you'd rather learn to write prompts
like this than copy them,
[Prompt Coach](https://jkilabs.gumroad.com/l/promptcoach?utm_source=github&utm_medium=repo&utm_campaign=ops-prompt-library&utm_content=vendor-quote-review)
is the method behind it.
