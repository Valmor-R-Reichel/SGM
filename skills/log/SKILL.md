---
name: log
description: The consolidation ritual for this archive. Reads the raw log, applies the funnel from AGENT.md, proposes what becomes a note, and writes only after explicit approval. Use at the end of a work session, or whenever the human says "run the log," "consolidate," or "update the archive."
---

# /log, the consolidation ritual

You are closing out raw material and turning what survives into notes. This file is the
procedure. For the rules it follows, the funnel, confidence, where things go, see
`AGENT.md`.

**Your job is not to summarize. It is to decide what deserves to survive, and why.** A log
that keeps everything is as useless as one that keeps nothing.

---

## Two modes, decide this first

**Capture mode, the default on a normal day.** Append to `raw-log.md`, nothing else. Report
in one line: "N entries captured, will consolidate later." If something in the session
contradicts the archive, capture it with a `CONTRADICTS:` prefix and move on, consolidation
resolves it later, with more material on the table.

**Consolidation mode, the full ritual below.** Run it when the raw log has grown large
enough that leaving it any longer risks losing the thread (tune the threshold to what feels
right for your context window, somewhere around 30 to 40 entries is a reasonable start), or
whenever the human explicitly asks.

Running the expensive ritual on every small session is a known failure mode: a fixed cost
process applied on top of shrinking returns is what killed an earlier version of this kind
of system. Splitting into two modes is the fix. Consolidating in batches also improves
judgment on its own, the rule that evidence only counts when independent needs several days
on the table to notice that the same thing showed up through different sources.

---

## Steps for consolidation mode

**0. Load context.** Read `AGENT.md`, a quick listing of what already exists (folder
contents, or a generated index if one exists), and `raw-log.md` in full.

**1. Sweep the raw log for:**
- What is new: a fact, a person, a project, a constraint, a deadline not yet recorded.
- The reasoning behind anything decided or discarded. This is the highest value item in the
  sweep. If you do not know why, mark it as a gap and ask, do not fill it by guessing.
- What changed: contradictions with what is already in the archive. A contradiction is
  high value information, either the archive is stale or the situation changed.
- How the human wrote or conducted themselves in the session, raw material for `profile/`.

**2. Screenshots and copies of real conversations.** Never store the image or the full
transcript. Store a pointer: channel, person, date, time. The one exception is a source that
could genuinely disappear (a channel the human might leave, a person who might no longer be
reachable, a message with a retention limit), in which case save it and say explicitly why
you broke the rule.

**2.5. Argue the opposite, on every conclusion, before it reaches a bucket.** For each thing
you are about to propose as a fact, state it, then state the strongest case against it using
only what is in the raw log. Show both in your response, not just the survivor. A conclusion
that does not survive is dropped, or proposed as a `hypothesis:` instead.

This is the step that most often fails while appearing to run. If the counter case is
assembled out of what the human seems to want to hear, nothing was tested. It has to be built
from dated evidence in the log, and going back to that evidence is the whole point.

**3. Sort into three buckets before writing anything.** This is the gate, and nothing skips
it:
- **Discard.** Noise or short lived. Stays noted in the closing report with a one line
  reason. No approval needed, nothing here is being promoted.
- **New.** Clean, no conflict with what already exists.
- **Conflicting.** Contradicts something already recorded. Name exactly which file would be
  superseded.

Present all three buckets to the human in one shot, and wait for an explicit yes on each
item, a click or a clear go ahead, not silence and not a change of subject. If your tool
supports a structured choice prompt, use it instead of free text, a gate that asks the human
to compose their own authorization turns into a rubber stamp over time.

**4. Filter what got approved through the golden rule again.** A piece of information
becomes a file only if it will still be true in six months, or if it explains why a decision
was made. When in doubt, leave it in the log rather than promoting it, promoting later is
cheap, cleaning up a cluttered archive later is not.

**5. Write.** Update the `updated:` date on anything you touch. Fix both directions of any
link you add: if a decision points at a person, that person's file should point back, with
a comment explaining why, whenever the link crosses branches.

**6. Close.** Clear the consolidated part of `raw-log.md`. Keep a short note of what did
**not** survive and why, this line matters as much as what did, it is what lets anyone audit
later whether the filter is too tight or too loose.

---

## What to report at the end

1. What got added, one reason per item.
2. What got discarded, and why.
3. Any contradictions the session raised.
4. What is still a hypothesis, and how much evidence it has so far.
5. At most two open questions, the ones that unblock the most.

Be honest about what stayed unclear. A report that says "could not determine the reasoning
for this" is worth more than one with a plausible reasoning invented to fill the gap.

---

## A note on scale

This starter kit has no script yet, everything above happens by you reading and writing
files directly. Once an archive grows large enough that finding things by listing folders
gets slow, the natural next step is a small deterministic tool: something that counts files,
checks for broken links, and turns a written plan into a batch of file writes in one pass
instead of one edit at a time. None of that changes anything in this file, it only changes
how mechanically step 5 gets executed.

---

## Never

- Invent a fact about a person. No evidence, ask instead of filling the gap.
- Promote a hypothesis to a fact before a third independent piece of evidence shows up.
- Record a judgment of someone's character. A file exists to work better with a person, not
  to rate them.
- Store a credential, a token, or another person's sensitive data.
- Sync the archive outside this machine without being explicitly asked.
- Run one file at a time what could have been read or written in a single batch.
