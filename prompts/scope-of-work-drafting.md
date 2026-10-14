# Scope of work drafting

**The job:** write an SOW tight enough that the bids you get back are comparable and
the change orders you get later are few.

**Why the obvious prompt fails:** "write a scope of work for X" returns a competent
template full of language like "contractor shall perform all work in a professional
manner." That sentence has never prevented a single change order. Change orders come
from *boundaries* — who supplies what, what happens when conditions differ from
expected, what "done" means — and a template doesn't know your boundaries. The prompt
has to make the model interrogate you before it drafts.

## The prompt

Run this in two passes. The interview is the part that does the work.

### Pass 1 — interrogation

```
I need to write a scope of work. Before you draft anything, interview me.

The work: [2–4 SENTENCES. What, where, why now.]
Property/site type: [E.G. 40-UNIT RESIDENTIAL, OCCUPIED OFFICE FLOOR, VACANT RETAIL]
Budget range: [OR "not disclosing to bidders"]
Timing constraints: [E.G. MUST BE DONE AFTER HOURS, BEFORE A LEASE START, ETC.]

Ask me the questions whose answers most change what a contractor would bid, focusing on
the ambiguities that typically become change orders: who supplies materials, site
access and hours, existing conditions and what happens if they differ from assumed,
disposal and debris, protection of adjacent areas, permits and inspections, utility
shutdowns and coordination with occupants, what constitutes substantial completion,
warranty, and whether anything is being matched to existing finishes.

Ask them in priority order, grouped, no more than 6 at a time, and wait for my answers
before continuing. If my answer to something is "I don't know," say what the common
options are and what each one typically costs the owner, then move on — do not stall.

Do not draft the SOW until I say I'm done answering.
```

### Pass 2 — draft

```
Now draft the scope of work using only what I told you.

Structure:
1. Project summary and location
2. Scope included — specific, numbered, measurable
3. Scope explicitly EXCLUDED
4. Owner-furnished items and owner responsibilities
5. Site conditions, access, and working hours
6. Permits, inspections, and code compliance responsibility
7. Materials and submittals — including anything being matched to existing
8. Schedule, milestones, and liquidated damages if any
9. Acceptance criteria — what specifically must be true for this to be complete
10. Warranty
11. Bid format — tell bidders exactly how to structure their price so bids are comparable

Rules:
- Every scope item must be verifiable. "Clean the space" is not verifiable. "Remove all
  debris from the unit and adjacent corridor; floors broom-clean; dispose off-site" is.
- The EXCLUSIONS section is the most valuable part of this document. Be thorough and
  specific there. If something plausibly might be read as included and isn't, exclude it
  by name.
- Where I did not give you enough information, write >> TBD: [the decision I still owe]
  rather than inventing a provision. Do not insert placeholder boilerplate.
- Section 11 should require unit pricing for anything likely to vary in quantity, so
  that a change in quantity doesn't become a renegotiation.
- Plain English. No "whereas," no "said contractor."
```

## What to check in the output

- **Read the exclusions out loud.** If you can think of something a contractor could
  plausibly claim was out of scope and it's not listed, add it. This section is cheap
  to extend and expensive to have omitted.
- **Test the acceptance criteria:** could two reasonable people disagree about whether
  the job is done? If yes, it isn't an acceptance criterion yet.
- **Resolve every `>> TBD` before issuing.** A TBD that reaches a bidder becomes an
  assumption, and their assumption will not be yours.

## Adapting it

- **Repeat work:** keep the Pass-1 answers in a file. Most of them are property
  constants, not project variables — access hours, disposal rules, insurance
  requirements. Reuse them and only re-interview on the deltas.
- **Small jobs:** skip Pass 1 and just demand the exclusions section. Even on a
  $2,000 job, exclusions are where the surprise lives.
- **This is not a contract.** It's the scope that an agreement references. Terms,
  insurance, indemnity, payment, and dispute resolution belong in the contract, and
  that belongs with a lawyer — not with a language model.

---

Built by [JK Labs](https://jkilabs.gumroad.com). If you'd rather learn to write prompts
like this than copy them,
[Prompt Coach](https://jkilabs.gumroad.com/l/promptcoach?utm_source=github&utm_medium=repo&utm_campaign=ops-prompt-library&utm_content=scope-of-work-drafting)
is the method behind it.
