# The Method

> **What this document is.** The build manual for the system, written to survive losing
> everything else. There are no colleague names, no deal numbers, no partners, no queries
> and no company here. Only how it is built, and why.
>
> **Why it exists.** The content of the archive belongs to a job and ages with it. The
> method does not. If the archive is ever left behind, this file alone should be enough to
> rebuild the system on another machine, at another company, about another subject.
>
> **How to read it.** Top to bottom the first time. After that, section 12 works as a
> catalog: one line of reasoning per architectural decision, and that is the part that
> cannot be lost.

---

## 0. The problem this system solves

Three earlier attempts at organizing the same knowledge failed, and all three failed the
same way. **They produced too many files, not too few.**

I assumed for a long time that the earlier attempts had produced nothing. The opposite was
true. Together they had produced 74 files, and 56 of those were created in a single 48 hour
window. The archive was large and it still answered "not found" for something sitting one
directory away.

So the failure mode was never scarcity. It was volume without provenance, and it had four
specific defects worth naming, because each one turned into a rule later:

1. **Batch generation erases origin.** Fifteen stakeholder files were written at once, from
   one prompt, with the same footer. Once written, nothing in the file said it came from an
   automated sweep. They sat next to hand written notes carrying the same authority.
2. **The prompt asked for interpretation, and got it.** It requested "attitudes, political
   positions and risks", and out came political readings about named colleagues, written in
   the second person, with no mark saying this was a guess.
3. **Files were born as stubs.** Several were under 500 bytes and one was empty. The ritual
   of creating the file happened before there was anything to put in it.
4. **Each wave became cleanup for the previous one.** A system folder accumulated collision
   audits, consolidation logs in three versions, and eight backup archives. The machinery
   for cleaning grew alongside the thing that needed cleaning.

The diagnosis that opened the fourth attempt: **it failed for lack of a route to the data,
not for lack of the data.**

Two commitments come out of that, and they run through everything else:

1. **Little gets in, and what gets in has to survive time.**
2. **Reading is a design problem as large as writing.** A system that only teaches you how
   to write produces a warehouse.

And one rule that governs the rest:

> **A note without provenance is debt, not an asset.** A file nobody can trace costs more
> to verify than it would cost to rewrite, and until it is verified it contaminates
> everything resting on it.

The operational corollary is that finishing a sweep with 30 traceable notes beats finishing
with 100 plausible ones. The test is never how many files exist. It is how many survive
someone asking how you know that.

---

## 1. The golden rule

> **A piece of information becomes a file only if it will still be true in six months, or
> if it explains why a decision was made.**

Everything that fails that test stays in the session log and never becomes a note.

The reasoning: without a durability filter, the system accumulates whatever passed in front
of it and takes on the appearance of organization with no ability to answer anything. The
six month test is what separates knowledge from record keeping.

---

## 2. The funnel, in this order

Every new piece of material goes through five steps before it becomes a file:

1. **Observe.** What was literally said or shown. No interpretation yet.
2. **Check.** Does it match what already exists? Does it contradict something? Is context
   missing?
3. **Understand.** What was the *reasoning*? Why this decision and not the other one?
4. **Comprehend.** What does this change on the map? Does it confirm a pattern, open a
   branch, kill a hypothesis?
5. **Record.** Only what survived the four steps above.

**Step 3 is the most important and the most skipped.** It holds up everything else: the
reasoning outweighs the conclusion, because conclusions age and reasoning teaches. A file
that records what was decided is useful for a quarter. A file that records why it was
decided is useful the next time you have to decide.

**Inside step 3, the dialectic check.** Before a conclusion gets recorded here, argue the
opposite of it first. A weak hypothesis collapses on its own against the evidence sitting in
the same session when it is tested this way, and the conclusion that survives is stronger
for having faced the opposite case, not for having been accepted on the first pass.

---

## 3. The structure: branches

The archive splits into **branches by type of thing, not by subject**. Subjects change,
types do not. The five that exist, described generically:

| branch | what it holds |
|---|---|
| profile | how I write, decide, negotiate and position myself |
| people | one cumulative file per person I work with |
| decisions | one decision per file, and above all its reasoning |
| projects | one work front per file, cumulative |
| technical domain | what only exists inside the tools of the job |

**Criterion for opening a new branch:** only when **three or more** items fail to fit any
existing branch and share a subject. A branch opened too early sits empty and clutters the
map.

When you open one, write its **folder note**, a file named after the branch itself
explaining what qualifies for entry. Without it, nobody knows six months later what that
folder was supposed to hold, and it turns into a dump.

Outside the branches sit the working folders: session logs, ingestion of external sources,
tooling, and an inbox for whatever has not been routed yet.

---

## 4. Where each thing goes, and what never becomes a file

| what showed up | goes to | becomes a file? |
|---|---|---|
| A fact about a person: role, style, preference, history | their file | yes, cumulative |
| A decision plus the reasoning behind it | decisions branch | yes, one per file |
| Progress, scope or risk on a project | the project file | yes, cumulative |
| How I write, speak, negotiate, position myself | profile branch | yes, with evidence |
| Screenshot of a real conversation | **a pointer**: channel, person, date and time | **no** |
| Export, spreadsheet, a source that **disappears** | ingestion folder, file copied | yes |
| Task, deadline, operational reminder | stays in the session log | **no** |
| Gossip, venting, noise | discard | **no** |
| I do not know where it fits | inbox, marked unrouted | decide later |

Three of those lines have reasoning worth spelling out, because they are not obvious.

**A screenshot becomes a pointer, not a file.** A live source can be consulted again.
Storing the image duplicates something that already exists in a more reliable place, and it
ages worse. Store the address, not the copy.

**An export becomes a file, and it is the exception.** The rule is not to copy sources. But
a source that disappears breaks re-verification: a number quoted without the file behind it
is a number nobody can audit later. If the source vanishes, it gets copied.

**Tasks and deadlines are left out on purpose.** Knowledge and operations have different
half lives. Mixing them in the same archive lets aged operational detail bury knowledge
that still holds. This creates a real problem, which is having nowhere to keep next steps,
and it stays open with eyes open rather than solved by contamination.

---

## 5. How a note is written

### The title is a claim, not a noun

`She decides by consensus, not by hierarchy` beats `Her`.

The reasoning is about reading, not aesthetics: when every title asserts something, **the
generated index answers most questions without opening a single file**. An index of nouns
forces you to open everything to find out what is inside.

Exception: cumulative files (a person, a project) do not assert, because they carry dozens
of claims and no single one of them is the file.

### The header

```yaml
---
branch: <branch name>
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: high | medium | low   # only on claim notes
sources: [<where it came from>]
---
```

`confidence` **does not exist** on a cumulative file. A file with ten claims does not have
one confidence level.

### Separate fact from reading

Fact: *she replied in four minutes*. Reading: *she seems to prioritize this topic*.

The reading goes in marked as a hypothesis and only becomes fact when it repeats. Without
that mark, yesterday's interpretation becomes tomorrow's data and nobody notices.

### A link crossing branches requires a comment

Like this: `[[note]], because it contradicts the agreed deadline`.

The comment is the only part that survives two years of forgetting. Why *this* decision
points at *this* person does not explain itself, and a link with no explanation is noise
wearing the appearance of a connection. Within the same branch it is welcome, not required:
proximity already says enough.

> This rule used to be broader and **was killed by measurement**. It required a comment on
> every link, and the count found hundreds with none, at zero adherence. See section 13.

### No note carries ambiguity

When two sources disagree and there is no way to decide, the doubt **leaves the note** and
goes whole into an open questions file, with both versions, the evidence for each, and the
condition that would resolve it.

When certainty arrives, the wrong version is **deleted**. The final note keeps only the
truth, plus one line reading `> discarded: <what> because <why>`, so that nobody redoes the
investigation a year later.

---

## 6. Confidence and evidence

**Confidence belongs to the claim, not to the file.** It is marked inline, attached to the
sentence:

```
`[medium · 2ev: meeting 05/08 · email 21/07]`
```

The same file can hold one `high` claim and one `low` claim.

**The ladder:** `low` is the default for any single observation. It rises to `medium` on the
second piece of evidence and `high` on the third.

**But only independent evidence counts**, and this is the rule that protects the system
most. Evidence is the **event**, not the record. Someone narrating a meeting and the
transcript of that meeting are **one** piece of evidence, not two.

Operational test: **a different date AND a different type of source.** Types that count as
distinct: speech in a meeting, a message written by the person themselves, a screenshot, a
formal document, a system artifact, and second hand narration.

The reasoning: without that test, a reading of mine, observed again three times, climbs to
fact carrying a date and a source, looking exactly like data. The system would start lying
with the appearance of rigor.

**A claim about another person** only reaches `high` with at least **one source not
mediated by me**. Me saying the same thing three times stalls at `medium`.

**Exception in my own profile branch:** there the test is a different date plus a distinct
context. I am the primary source about myself, and demanding a different source type would
freeze the branch without protecting anything.

---

## 7. The cooperation marker, and how it shapes future collaboration

A second mechanism runs alongside the writing funnel: a marker per person, cooperated or
did not cooperate, updated after each meaningful interaction. This is not general trust. It
is a specific scoreboard, updated round by round, in the sense the term is used in game
theory.

The use: before deciding how much to help someone again, check the scoreboard first.
Unconditional cooperation has a cost that only shows up later, it turns into always being
the one who solves things and never being helped back. Round by round, weigh what is gained
by helping against what is gained by not, and the other person knows this is how the
weighing works. It is not silent manipulation, it is a declared rule.

This is not the neutral fact recording the rest of the system produces. It is a relational
decision instrument, built on the same habit of dating evidence that everything else here
uses. The difference is that the output here is not a note, it is a calibration of future
behavior.

---

## 8. How it gets read

This section exists because the first version of the system was entirely about writing and
had **not one line about reading**. The result was improvisation: sweep folders, open a
whole note, find out it was not there.

1. **Index first, always.** A generated file listing every note with title, date and link
   count. Because titles are claims, the index line usually answers the question. Never
   sweep the archive before looking at the index.
2. **The type of question says where to open.** A person, their file. Why something was
   decided, the decisions branch. A number, the note that asserts it cites file and column.
   Progress, the project file. What happened in a session, search the logs, never read them
   in sequence.
3. **Open in batches, and stop early.** Candidates go in one turn, not one at a time. And do
   not open the third if the first two already answered.
4. **Respect what the note declares about itself.** A hypothesis is not a fact. Quote the
   confidence level of the sentence you used. **A number is never repeated without opening
   its source**: either you open the file it cites, or you say you did not check.
5. **The center is the map, not the territory.** It tells you where the answer is, not what
   the answer is.

---

## 9. The division of work between machine, agent and human

The boundary that holds the design together:

> **What is deterministic belongs to the machine. What requires judgment belongs to the
> human.**

Four hard rules come out of it:

- **Scripts propose and never edit the archive.** Counting, validating, generating the
  index, scaffolding a file, zipping. Nothing that decides content.
- **A single skill writes to the branches.** All others propose. This is what closes the
  side door through which a second skill would start writing just a little.
- **Approval is a click, not free text.** A gate that asks the user to compose the
  authorization becomes a rubber stamp. A gate of options gets read.
- **Automation that acts without being called takes the decision away from whoever should
  be making it.** That is why the backup does not run on its own at the end of a ritual, and
  the validator does not fire at the start of a session.

The full circuit:

```
learning during the session
   â””â”€> raw log             (immediate append, one line, any session, zero cost)
        â””â”€> log skill      (gate: capture midweek, consolidate once or twice a week)
             â””â”€> funnel    (observe, check, understand, comprehend, record)
                  â””â”€> triage plus click approval
                       â””â”€> branches
                            â””â”€> script regenerates index, map and mirror
```

The raw log is the most underrated piece. It exists because **a learning captured in the
moment costs one line, and reconstructed at the end of the week costs the whole session.**

---

## 10. The tooling, and what each piece solves

None of these is sophisticated. Each one solves a measured problem.

| piece | solves |
|---|---|
| one line capture via keyboard shortcut | learning lost between the insight and the end of the session |
| index generated by script | search by sweeping, which is expensive and imprecise |
| deterministic validator | a rule that only gets enforced when someone remembers |
| consolidation skill with two modes | a fixed cost ritual applied to diminishing returns |
| layered backup | an archive that exists on one disk only |
| read only mirror | an external agent that needs to read without being able to write |

Dependencies: a standard script interpreter, no external libraries. The choice is
deliberate. A corporate machine without administrator rights installs nothing, and a system
that depends on installation dies on the first new machine.

---

## 11. How the system is measured

The metric is **how many times it prevented an error or delivered a finished argument**, not
the count of notes, kilobytes or links.

**Why counting files was the wrong metric.** Counting measures production, and production is
exactly what killed the three earlier attempts. The curve makes it visible:

| period (August) | notes created | notes updated | ratio |
|---|---|---|---|
| days 1 to 3 | 61 | 42 | **1.45** |
| days 4 to 7 | 19 | 37 | **0.51** |

Production fell by 69 percent and the archive got better, not worse. A metric that points
down while the thing improves is measuring the wrong quantity.

The mechanism behind that is worth stating on its own: **depth comes from revision, not from
the number of files.** A note rewritten ten times is worth more than ten notes written once.
The apparent rework is the specialization itself, and counting files rewards precisely the
wrong behavior.

**A prevented error only counts when all three conditions hold:** the archive entered the
decision before the output existed; without it the output would have been different and
worse; and the output can be named, meaning a message that was sent, a number that was
quoted, a meeting that was run.

---

## 12. The catalog of reasoning

This is the section that cannot be lost. One line per architectural decision, grouped by
theme. If everything else disappears, this is what the system gets rebuilt from.

### On what gets in

- **The six month rule.** Without a durability filter, an archive becomes a dump wearing the
  appearance of method.
- **A live source becomes a pointer, only what disappears gets archived.** Copying a source
  that still exists creates two versions that will diverge.
- **Every number cites the file and the column.** A number without provenance is not
  auditable, and an archive that cannot be audited lies with confidence.
- **Evidence only counts when independent.** Without this, a re-observed reading becomes
  fact.
- **A claim about someone else needs a source not mediated by me** to reach the top of the
  ladder. My own repetition is not corroboration.

### On the shape of files

- **The title is a claim.** It turns the index into an answer and saves opening the file.
- **A comment is required only on links that cross branches.** The broader version was
  measured and had zero adherence.
- **The size cap per note was dropped.** It was being broken in most cases, and a rule the
  evidence shows unenforced is debt, not a rule.
- **How large a file should be depends on how the agent reads it.** If the agent loads the
  file whole, size is price. If it enters the folder and takes whatever fits, size is loss.
  There is no general answer, and advice that assumes the wrong mechanism will sound wrong
  while being perfectly correct about a different setup.
- **Depth comes from revision, not from the number of files.**
- **Ambiguity leaves the note.** Doubt lives in its own file, and when it resolves the wrong
  version is deleted with one line saying what was discarded.

### On automation

- **Deterministic is machine work, judgment is human work.**
- **A script proposes and never edits the archive.**
- **No skill writes directly to a branch**, except the single one designed for it.
- **Approval becomes a click**, because a free text gate becomes a rubber stamp.
- **Routing is by inferred context, not by a table of conditions.** A table covers the
  anticipated case and fails silently on the rest.
- **Backup is not automatic.** It is an explicit act, with the choice of destination
  attached.

### On cost

- **A fixed cost ritual applied to diminishing returns is what killed the previous system.**
  It is now instrumented: cost per file produced is measured, and when it climbs, the ritual
  splits into cheaper modes.
- **Read in batches, not one file at a time.** The measured bottleneck was not too much
  reading, it was no parallelism.
- **Continuous capture costs one line, reconstruction costs a session.**

### On boundaries and risk

- **The archive is local and does not leave the machine without an explicit decision.** No
  automatic sync.
- **Personal cloud storage is worse on both axes at once** when the content belongs to an
  employer: it trades an indexed file for a named exfiltration alert.
- **An external agent reads through a locked mirror, never through the real path.** Whatever
  it produces enters through the funnel like any other source.
- **A derived artifact points at the source rather than copying it.** Two copies diverge in
  two weeks.
- **Audio and meeting processing runs locally.** Meeting content does not leave the machine.
- **The criterion for installing something is reach, not origin.**
- **The folder a session opens in decides where its history is indexed.** Opening in the
  wrong place separates the work from the archive without warning.

### On replacing an older system

- **Replace, do not coexist.** The old system takes no new writing and is not a source of
  truth. But while migration is unfinished it remains a **declared consultation source**, and
  whoever consults it says where the answer came from.
- **Divergences between the old and the new are layers of time, not conflicts to arbitrate.**
  Two different versions are usually two photographs from different moments.
- **The migration queue says which file to look in, not what to migrate.** Read as a task
  list, it recreates the accumulation the new system exists to avoid.
- **Migrate by route, not by volume.** One migrated item that answers a real question beats a
  hundred transferred ones.

---

## 13. Mistakes that became rules

These are not anecdotes. Each one cost work and turned into a criterion.

- **A rule being broken is debt, not a rule.** This happened twice, with a size cap and with
  a requirement that every link carry a comment. In both cases measurement showed low or zero
  adherence, and the fix was adjusting the rule to real behavior rather than enforcing it
  harder. A rule below fifty percent measured adherence goes back on the table.
- **A successful install is not verified operation.** An integration was installed, never
  produced the artifact it was supposed to produce, and nobody noticed for two days. What was
  missing was checking the **output**, not the code.
- **Measure whether the source moves before building the mirror.** A dashboard idea died in
  five minutes of measurement: the data it would read was not being updated, so the dashboard
  would either lie or sit silent.
- **Proving a backup and moving a backup are different operations.** A restore test turned
  into an unnecessary copy leaving the machine, because the test used the wrong file and a
  channel that was not part of the test.
- **A crawler without a login is not evidence that a logged in human has no access.** An
  automated check landed on a login screen and became a wrong conclusion about permissions.
- **A reviewer without context is good for surface, not for architecture.** It catches
  ambiguity the author can no longer see, and gets it wrong when it opines on structure.
- **When correcting another session's work, hand over the check, not the conclusion.** A
  conclusion without the path forces the verification to be redone.
- **An agent without access to the source catches internal coherence and misses provenance.**
  It will notice that a document promises a file the document never delivers, because that is
  checkable by reading. It will not notice that 47 percent is not close to zero, because that
  requires opening the archive.

---

## 14. What is mine and what belongs to an employer

The archive mixes two things with different owners, and they need different handling:

- **Job knowledge:** clients, processes, people, queries, numbers. It stays in corporate
  storage and does not travel with me.
- **Method and profile:** this document, the funnel, the conventions, the tooling, and how I
  think and write. That travels with me.

Three rules learned while separating the two:

1. **Allowlist, never a blocklist.** When the destination is an external service, a blocklist
   lets new files leak by forgetting. On an allowlist, the new file stays out until someone
   decides otherwise.
2. **Choosing the file is not enough, the content has to be audited.** A file can sit in the
   right branch and name half a dozen people inside it.
3. **A profile cannot be separated from third parties by selecting files, only by
   rewriting.** How I negotiate can only be described by saying who I negotiated with. That
   is the reason this document exists separately: it carries the method without carrying the
   people.

The measurement that produced this section is worth keeping, because it reframed what the
archive is. One week in, **25 of the 31 decisions in the archive were about method, not
about the business.** In a week I had built more method than corporate knowledge, and the
layer I get to take with me was already the larger part. That count is a snapshot from that
week, not a ratio that holds by construction. It has not been rechecked since, and a system
whose decisions branch keeps growing should expect that ratio to drift, in either
direction, as new decisions get made.

---

## 15. How to update this document

**Write here when:**

- I made an architectural decision about how the system works
- I killed a rule by measurement, and the reason matters more than the new rule
- I found a mistake that became a criterion, of the kind in section 13
- I changed the funnel, the confidence ladder, or the machine/human boundary

**Do not write here when:**

- it is content, not method
- it depends on who the employer is, who the colleague is, or what the number is
- it is a task, a deadline, or a status

**The test before saving**, and there are two questions:

1. Could a stranger reading only this file rebuild the system? If not, detail is missing.
2. Would a competitor reading only this file learn anything about the company I work at? If
   so, there is too much, and it has to come out.

The first question is the goal. The second is the condition.
