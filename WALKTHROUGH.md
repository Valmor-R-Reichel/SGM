# Walkthrough

Two cases. The first is invented and shows the shape. The second is real, and you can audit
every step of it without trusting me, because it happened to this repository and it is in the
commit history.

---

# Part 1: one captured line becomes three connected notes

Everything below is fictional. The company is Meridian Robotics, and the people in it do not
exist. The files referenced are in [`examples/`](examples/), and you can read them alongside
this.

## What got captured

On 3 February, during a partner call that was not about contracts, two lines went into
`raw-log.md`. They cost nothing to write and nobody decided anything about them yet:

```
[2027-02-03 09:14] [partner call] Priya said the EU distributor deal is stuck because their
legal team wants a liability clause we have never used before. She thinks it is a template
issue, not a real objection.

[2027-02-03 09:20] [partner call] Priya also mentioned that Jonas already has a version of
that clause from the Canada deal last year. Worth checking before drafting anything new.
```

Six more entries accumulated over the following week: a standup, a check in, an email, a
Slack message. Nothing was written well and nothing was filtered. That is the whole
discipline of the fast side of the loop.

## What the funnel did with it

On 10 February the log ran. Every entry went through five steps, out loud, before anything
could be written.

**1. Observe.** The deal was stuck. Priya named the liability clause as the reason. Sofia
drafted an updated clause starting from one Jonas already had. The distributor accepted it in
under an hour with no pushback.

**2. Check.** Nothing in the archive contradicted this. The project file said the contract
phase was open. Nobody had recorded a reason for the delay before.

**3. Understand.** The obvious conclusion is *the clause was the blocker and fixing it
unblocked the deal*.

**Then the antithesis, which is where this step earns its keep.** Argue the opposite using
only what is in the log. If the clause had really been the blocker, a distributor's legal
team would not accept a rewritten version in under an hour. Fast acceptance is evidence that
the clause was never what was holding it. What actually moved was the decision on 4 February
to push rather than wait, and that decision came from Priya's instinct, with no data behind
it that anyone saw.

The first conclusion did not survive. The second one did, and it is the one that got
recorded.

**4. Comprehend.** This opens a pattern worth watching rather than closing one: when a stuck
deal gets one specific technical explanation this early and this confidently, the explanation
may be a real problem attached to the wrong cause. That is a reading, not a fact. It goes in
marked `hypothesis:` at `[low · 1ev]`.

**5. Record.** Three files, and the reason each one exists.

## What it became

```
raw-log.md                    8 raw lines, 03/02 to 10/02
        |
        v  the funnel
decisions/the-liability-clause-was-never-the-real-blocker.md
        |
        +--> people/priya-nandan.md
        +--> projects/eu-distributor-partner-integration.md
```

**The decision note** carries the claim as its title, because a title that asserts something
answers the question before you open the file. It carries its confidence inline,
`[high · 2ev: Sofia's draft accepted without changes 02/06 · Priya's Slack message 02/10]`,
and it keeps the pattern separate and marked as a hypothesis, because one occurrence is one
occurrence.

It also has a section that only exists because of the raw log: *what I would have missed*.
Without the 09:20 entry mentioning that Jonas already had a usable clause, the next step
would have been drafting from scratch. That connection existed only because it was captured
the same day, in a call that was not about contracts.

**The person file** is cumulative and has no confidence in its frontmatter, because a file
with several claims does not have one confidence level. Each claim carries its own. It also
has a section called *still unknown, do not guess*, which is the part most systems have no
place for.

**The project file** is cumulative too, and its history table is the only place where the
sequence of events survives.

**The links** between them are not decoration. Each one says why it exists:

> `[[priya-nandan]], because her instinct to push turned out to be the actual variable, not
> the clause she named`

Six months from now the comment is the part still doing work. The link alone would not be.

## What did not survive

Most of the week did not become anything. Sofia's note about the data processing agreement
template being two versions behind is real, useful, and stayed in the raw log, because it
will not be true in six months and it does not explain a decision.

That is not a loss. **A log that records everything is as useless as one that records
nothing.**

---

# Part 2: the same method, applied to this repository

The example above is invented. This one is not, and you do not have to trust me for any of
it. Every claim below is a commit in this repository, and `git log` will show you the same
thing it showed me.

## The gate's scoreboard

In its first 43 hours, this repository had **nine assertions written into it that could not
be backed**. All nine were caught and corrected before anyone outside had read the
repository: eight were removed, and one was fixed by adding the file the text had already
promised.

The number is not the point. The point is that they fall into three failure modes, and they
are always the same three.

### Failure mode 1: promised what does not exist

| what | commit |
|---|---|
| the README pointed to files that were not in the repository | `8039c7d` |
| the README announced a CC BY 4.0 license with **no LICENSE file present** | `cf9b72c` |
| section 10 listed six tools, none of which ship here, reading like an inventory of what you had just downloaded | `cf9b72c` |

The second one is the sharpest, and the commit message says why: *the promise was not
cosmetic, it was void.* With no license file, the legal default is all rights reserved. The
repository was saying "use it, adapt it, credit it" while prohibiting all three.

It is also the one of the nine that was corrected by adding rather than by removing. The
sentence was fine. The file standing behind it was missing.

### Failure mode 2: presented a snapshot as a standing property

| what | commit |
|---|---|
| a 25 of 31 ratio, measured in mid August, presented as current | `011f1e0` |
| the creation and revision table, same problem | `011f1e0` |
| a 53 percent link adherence figure, never rechecked, presented as a property of the method | `011f1e0` |

This is the most dangerous of the three, because **the number is true.** It is just not true
now. Nothing about the sentence looks wrong, which is exactly why it survives review.

### Failure mode 3: invented provenance

| what | commit |
|---|---|
| claimed an earlier version of this method ran in June. It never did | `1e6d3dd` |
| adherence numbers that did not match the measurement | `8039c7d` |
| a table said "days 1 to 3" when the three active days **were not consecutive** | `cf9b72c` |

The June claim is the one to sit with. A different personal system existed before this one and
was explicitly not migrated, only its lessons were. Conflating the two invented a version
history this method never had. Nobody lied. A model filled a plausible gap, and plausible is
what makes it hard to catch.

## The one that matters most

The last item in mode 3 looks like the smallest, and it is the most important thing in this
document.

The table originally read *days 1 to 3*. The underlying measurement covered three active days
that were not consecutive. The false precision was **introduced while cleaning up the wording
of the table**, in an edit whose entire purpose was to make the text better.

An improvement created an unbacked claim.

That is where errors actually come from. Not from drafting, where everyone is paying
attention, but from revision, where nobody is. It is the argument for the gate in one line:
the gate is not there to catch a machine writing badly. It is there to catch a machine
writing well about something it does not know.

## What this demonstrates

The exit door described in the README is not a policy in this repository, it is a log. Nine
claims entered, nine were checked, nine failed. Eight left, and the ninth stayed once the
file it kept promising finally arrived. What stayed behind is one line each in a commit
message saying what fell and why, so nobody redoes the investigation.

**Leaving is a write, not a delete.** This section is what that looks like when it runs.

And the shape of the history is itself a measurement. Section 11 of [`METHOD.md`](METHOD.md)
says the archive should be creation heavy at first and revision heavy afterwards, and gives
the ratio it measured on the archive this method runs on: 1.45, then 0.51. Five of the first
twelve commits here are corrections. Nobody planned that. It is what the method looks like
from the outside when it is running.

---

## Where to go next

- [`AGENT.md`](AGENT.md) to run it. It is the only file an assistant needs.
- [`METHOD.md`](METHOD.md) for the reasoning behind every rule.
- [`examples/`](examples/) for the four files from Part 1, in full.
