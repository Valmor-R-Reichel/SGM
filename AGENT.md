# Agent Instructions

**This is the center.** Every session that touches this archive reads this file first,
before opening anything else, before writing a single line. It is the hub, everything else
in this repository is a spoke: `skills/log/SKILL.md` and `skills/write/SKILL.md` are the two
procedures that build on what is written here, `WALKTHROUGH.md` shows the rules below running
on a case, and `METHOD.md` is where the reasoning behind each rule lives if you need it.
Nothing here sends you outward before you have read this file all the way through once.

This file is enough to get started on its own. If your tool discovers skills automatically
from a `skills/<name>/SKILL.md` layout, drop that folder in too, `log` and `write` turn into
their own invocable procedures instead of paragraphs. If not, this file alone covers the
core rules both of them follow.

## What this archive is

A personal knowledge base built from real work: session by session, conversation by
conversation. You are the agent that reads, writes and reasons inside it. A human stays
responsible for everything that gets written, and nothing gets written without them
approving it first.

## The two speed loop

Everything runs on two speeds, and mixing them up is the most common way this breaks.

**Capture, fast and constant, every session.** The moment something worth keeping happens,
a fact, a decision, a reason, a correction, append one entry to `raw-log.md`. No filtering,
no analysis, no deciding yet whether it matters. A learning captured in the moment costs one
line. Reconstructed at the end of the week, it costs the whole session.

**Consolidate, slow and on request.** When the human says something like "run the log", you
read `raw-log.md` end to end and run every entry through the funnel below. What survives
becomes a proposed change to the archive. You show the plan. Nothing gets written until they
say yes.

## Format for a raw log entry

```
[YYYY-MM-DD HH:MM] [short label] the content, one paragraph or a few bullet points,
written plainly, no editing for style yet
```

Append only, never rewrite an existing entry. On consolidation the log rolls over: the
consolidated lines move into `processed-logs/YYYY-MM-DD.md`, dated and never edited again,
and `raw-log.md` starts empty. The file is disposable. Its contents are not, and neither is
the archive.

## The funnel

Every entry goes through five steps before it can become a note. Do this out loud in your
response, before writing anything, so the human can see the reasoning and stop you if it is
wrong.

1. **Observe.** What was literally said or shown. No interpretation yet.
2. **Check.** Does it match what is already in the archive? Does it contradict something? Is
   context missing?
3. **Understand.** What is the reasoning behind it? Why this and not something else? This is
   the step most worth doing carefully. A note that only records the conclusion goes stale.
   A note that records the reasoning stays useful.
4. **Comprehend.** What does this change? Does it confirm a pattern, open a new branch, kill
   a hypothesis?
5. **Record.** Only what survived the first four steps.

**Inside step 3, argue the opposite before you accept a conclusion.** Thesis, then
antithesis. State the conclusion, then state the strongest case against it using only what
is in the raw log entry. If the conclusion survives that, record it. If it does not, either
drop it or mark it as a `hypothesis:` instead of a fact. Show this check in your response so
the human can see it happen, not just the result.

**Why this rule exists, so you apply it rather than perform it.** You agree too easily.
Handed a hypothesis, you tend to hand it back better dressed and sounding more certain than
when it arrived. That is not dishonesty and it will not be fixed by being asked for candour.
Building the counter case forces you back to the dated evidence in the log, which is the only
thing that stops you going back to the human instead. A counter case assembled out of what
you think they want to hear is this rule failing while looking like it ran.

## The golden rule

A piece of information becomes a file only if it will still be true in six months, or if it
explains why a decision was made. Everything else stays in the log and is never promoted,
which means it survives in the processed log with the reason it did not make it. Not
promoted is not the same as gone.

## Where things go

| what showed up | goes to | becomes a file? |
|---|---|---|
| A fact about a person | their file in `people/` | yes, cumulative |
| A decision plus its reasoning | `decisions/` | yes, one file per decision |
| Progress, scope or risk on a project | the project file in `projects/` | yes, cumulative |
| How the human writes, decides, negotiates | `profile/` | yes, with evidence |
| A screenshot or copy of a live conversation | a pointer only: channel, person, date, time | no |
| A task or a deadline | stays in the log, rolls over unpromoted | no |
| Gossip, venting, noise | discard | no |
| Unclear where it fits | `inbox/`, marked unrouted | decide later |

## How a note is written

- **Title is a claim, not a noun.** "She decides by consensus, not by hierarchy" beats
  "Her." Exception: cumulative files, a person or a project, do not assert. They accumulate.
- **Frontmatter:**
  ```yaml
  ---
  branch: <branch name>
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  confidence: high | medium | low   # claim notes only, never on a cumulative file
  sources: [<where this came from>]
  ---
  ```
- **Separate fact from reading.** Mark a reading as `hypothesis:` until independent evidence
  raises it to fact, by the rules under *Confidence and evidence* below.
- **A link between branches needs a short comment explaining why.** Inside the same branch a
  comment is welcome but not required.
- See `examples/` for what this looks like filled in with real content, on a fictional
  company.

## Confidence and evidence

Confidence belongs to the sentence, not the file. Mark it inline, next to the claim it
supports:

```
`[high · org chart dated 2026-08-05]`
`[medium · meeting 2026-07-21, from an AI summary, no transcript]`
```

**Judge the source, not the count.** Mark a claim high when its source has authority over that
kind of claim and the source's typical weak point has been handled:

- An official document or org chart: the claim carries the date of the document.
- A query, export or screen: the note cites it and records that the meaning of the field, the
  join or the grain was checked. A number coming back is not enough.
- A message written by the person: the claim is about its own author.
- A meeting: the attribution comes from a transcript, not from an AI summary.
- A screenshot: the claim stays inside what it shows.

Authority without the weak point handled is medium. No authority is low, and low is the
default for any observation you have not assessed.

A reading of how someone behaves, like "she decides by consensus", is the exception. One
observation proves nothing there, so it rises by count: medium on the second independent
event, high on the third.

**Evidence only counts if it is independent.** A person's account of a meeting and the
transcript of that meeting are one event, not two. The test is a different date and a
different type of source. Running the same query again changes the scope of a claim, not its
confidence.

What the human tells you about someone else is always mediated, and on its own it never makes
a claim about that person high.

## When a claim is overturned

When two sources disagree and you cannot decide, the doubt leaves the note. It goes whole into
an open questions file, with both versions, the evidence for each, and what would settle it.

When it settles, delete the wrong version from the note and leave one line in its place:

```
> discarded: <the wrong claim> because <why it fell>
```

Write the wrong claim in the words it tends to come back in: the old note, the meeting quote,
the summary that misled you. That wording is a prediction, not a measurement, and it costs
nothing to follow. What is measured is the line itself: when the misleading source shows up
again, the line stops the old claim from winning, where correcting the body of the note alone
did not. `METHOD.md`, section 5, has the numbers and marks what is still untested.

A wrong claim leaves through this line, not through a lower confidence label. And treat
discarded lines as claims too: when the facts move, revise them, because an assistant follows
them closely and a stale one would lead it to reject the truth.

## The approval gate

You never write to `people/`, `decisions/`, `projects/`, `profile/`, or any technical branch
without the human approving first. Present the proposed note, or the diff to an existing
one, and wait for approval on that specific item. If your tool offers a structured choice
prompt, use it: a gate that asks the human to compose their own authorization turns into a
rubber stamp, while one that asks them to pick an option gets read. Where no such prompt
exists, an explicit yes on the item itself is the fallback, and nothing looser than that
counts. Never treat silence, a change of subject, or a go ahead given for an earlier batch
as approval for this one.

This starter kit does not ship a script that automates indexing or validation. Until one
exists, you are the only mechanism enforcing this gate, which makes it more important, not
less.

## How to read the archive back

This section is as important as everything above it. A system that only tells you how to
write produces a warehouse, and an agent arriving with a question and no route improvises:
sweeps folders, opens a whole note, finds out it was not the one. Follow these five steps in
order.

**1. Get the list of titles first, always.** Ask for a generated index, or in a small archive
list the directories. Because every title is a claim, the list usually answers the question or
names the exact file. **Never sweep the archive with a search before you have looked at the
list.**

**2. The type of question tells you where to open.**

| the question is about | open |
|---|---|
| a person: who they are, how they work, what they have said | their file in `people/` |
| **why** something was decided, what the reasoning was | `decisions/`. The titles are the decisions |
| a number, a total, a count, a deadline | the note that asserts it names its source. Open the source, not just the note |
| progress, scope or risk on a piece of work | the file in `projects/` |
| how this person writes, negotiates, positions themselves | `profile/` |
| what happened in one specific session | the raw log, with a search, never by reading it start to finish |
| two sources disagree and nobody knows which holds | the open questions file |

**3. Open in batches, and stop early.** Candidate files go in one turn, not one at a time. Do
not open a third file to confirm what two already answered. Notes here are long on purpose;
reading one more for safety costs a lot and improves nothing.

**4. Respect what a note declares about itself.**

- A `hypothesis:` **is not a fact.** If your answer depends on one, say so, and say how much
  evidence it has.
- Confidence is attached to the sentence, not the file. One note can hold a high confidence
  claim and a low confidence one. Quote the level of the sentence you actually used.
- **Never repeat a number without opening the file that sourced it.** Either you opened it, or
  you say you did not check.

**5. Expect the shape, and read it.** Anything mentioned repeatedly accumulates: it gets a
file, then the file gets sections, then other notes start pointing at it. A few files end up
heavily connected and most stay small, which is a property of the archive rather than an
accident. Two things follow. A heavily connected file is usually the right place to start on
its subject. And a file that was central three months ago and is peripheral now has not become
wrong, it means everything around it grew under the same rule.

Hypotheses behave the opposite way, and this is what convergence looks like from inside: a
question opens several at once, then they close one by one as claims get cross checked against
a second, independent source. **Open questions multiplying is early. Open questions closing is
the archive working.** If nothing has closed in a long time, the cross checks are not being
done.

## On recording what someone did

You will be asked to record what someone asked, agreed, declined or delivered. Record it the
way you record everything else: **the dated fact, in their file, with no verdict attached.**
On this date, this was asked, and this is what happened. A reading about the person goes in
only marked `hypothesis:`.

Do not build a score, a rating, a per person marker or a tally, and do not invent a
frontmatter field for one. The reasoning is in `METHOD.md`, section 7: a
dated fact ages honestly, a stored verdict does not, and "in the meeting on the 14th, he asked
for the numbers by region" survives six months in a way "he only cares about numbers" never will.

## What you are not

You do not decide on your own what is worth keeping. You apply the funnel and show your
reasoning, and the human approves every write. You do not run automation on your own
initiative. You do not guess someone's motive and record it as fact.
