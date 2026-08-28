# Agent Instructions

Read this before you write anything to this archive. It is the operating manual, not the
reasoning behind it. For why any of this exists, see `METHOD.md`.

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

Append only, never rewrite an existing entry. The raw log is disposable once consolidated.
The archive is not.

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

## The golden rule

A piece of information becomes a file only if it will still be true in six months, or if it
explains why a decision was made. Everything else stays in the raw log and is never
promoted.

## Where things go

| what showed up | goes to | becomes a file? |
|---|---|---|
| A fact about a person | their file in `people/` | yes, cumulative |
| A decision plus its reasoning | `decisions/` | yes, one file per decision |
| Progress, scope or risk on a project | the project file in `projects/` | yes, cumulative |
| How the human writes, decides, negotiates | `profile/` | yes, with evidence |
| A screenshot or copy of a live conversation | a pointer only: channel, person, date, time | no |
| A task or a deadline | stays in the raw log | no |
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
- **Separate fact from reading.** Mark a reading as `hypothesis:` until it repeats and
  earns the right to be treated as fact.
- **A link between branches needs a short comment explaining why.** Inside the same branch a
  comment is welcome but not required.
- See `examples/` for what this looks like filled in with real content, on a fictional
  company.

## Confidence and evidence

Confidence belongs to the sentence, not the file. Mark it inline, next to the claim it
supports:

```
`[medium · 2ev: meeting 05/08 · email 21/07]`
```

Low is the default for a single observation. It rises to medium on the second independent
piece of evidence, high on the third.

**Evidence only counts if it is independent.** A person's account of a meeting and the
transcript of that meeting are one event, not two. The test is a different date and a
different type of source.

A claim about someone else only reaches high with at least one source not mediated by the
person telling you about it.

## The approval gate

You never write to `people/`, `decisions/`, `projects/`, `profile/`, or any technical branch
without the human approving first. Present the proposed note, or the diff to an existing
one, and wait for an explicit go ahead: a click, a yes, a "do it." Never treat silence or a
change of subject as approval.

This starter kit does not ship a script that automates indexing or validation. Until one
exists, you are the only mechanism enforcing this gate, which makes it more important, not
less.

## How to read the archive back

- Ask for, or generate, a list of file titles before opening files. In a small archive this
  can be a directory listing. Do not sweep folders blind.
- The type of question tells you where to look. A person, their file. Why something was
  decided, `decisions/`. Progress, the project file.
- Open in batches, and stop as soon as you have an answer. Do not open a third file to
  confirm what two already answered.
- Respect what a note says about itself. A hypothesis is not a fact. Never repeat a number
  without opening the file that sourced it.

## What you are not

You do not decide on your own what is worth keeping. You apply the funnel and show your
reasoning, and the human approves every write. You do not run automation on your own
initiative. You do not guess someone's motive and record it as fact.
