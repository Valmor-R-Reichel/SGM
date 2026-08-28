# Second Brain Method

A method for building a personal knowledge base that an AI agent can read, and that a
human stays accountable for.

It is a set of rules about three things: what earns a place in the archive, how a claim
carries its own evidence, and where the line sits between what a machine may decide and
what a person must. The tooling underneath is deliberately thin. Plain markdown files, a
script with no external dependencies, and an agent that reads the rules before it writes
anything.

> You do not need to know the tool. You need to know the reasoning.

## The problem it solves

Three earlier attempts at organizing the same knowledge failed, and all three failed the
same way: they produced too many files, not too few. The archive held hundreds of notes
and still answered "not found" for something sitting one directory away.

The diagnosis was that it failed for lack of a route to the data, not for lack of the
data. Two commitments follow from that, and they run through everything else here:

1. **Little gets in, and what gets in has to survive time.**
2. **Reading is as much a design problem as writing.** A system that only teaches you to
   write produces a warehouse.

## Core rules

**The golden rule.** A piece of information becomes a file only if it will still be true
in six months, or if it explains why a decision was made. Everything else stays in the
session log and never becomes a note.

**The rationale outweighs the conclusion.** A file that records what was decided is
useful for a quarter. A file that records why it was decided is useful the next time you
have to decide.

**Titles are claims, not nouns.** `She decides by consensus, not by hierarchy` beats
`Her`. This is a reading decision rather than a stylistic one: when every title asserts
something, the generated index answers most questions before you open a file.

**Confidence attaches to the sentence, not to the file.** A note with ten claims does not
have a single confidence level, so each claim carries its own inline, along with the
sources behind it.

**Evidence only counts when it is independent.** Someone's account of a meeting and the
transcript of that meeting are one piece of evidence, not two. The operational test is a
different date and a different type of source. Without it, a reading of mine, observed
again three times, climbs to fact with a date and a source attached, and starts to look
like data.

**Deterministic work belongs to the machine, judgment belongs to the person.** Scripts
propose and never edit the archive. A single skill has write access to it. Approval is a
click rather than free text, because a gate that asks you to compose the authorization
becomes a rubber stamp.

**A rule below fifty percent measured compliance goes back on the table.** Not revoked
automatically, but reviewed with the measurement beside it, and either rewritten to match
what actually happens or dropped. Two rules have already gone that way, and both are
documented with their numbers.

## Repository layout

```
README.md            you are here
METHOD.md            the full method, written to survive losing everything else
docs/
  01-problem.md      why three earlier attempts failed
  02-funnel.md       observe, check, understand, comprehend, record
  03-note-anatomy.md claim titles, frontmatter, marking a hypothesis
  04-evidence.md     the confidence ladder and the independence test
  05-reading-path.md how the archive gets read back
  06-machine-vs-human.md the gates, and the reasoning behind each one
  07-rules-that-died.md rules revoked by measurement, with the numbers
  08-limits.md       where this does not work
examples/            synthetic notes from a fictional company
```

## Limits

The method assumes an operator who stands behind the output. The machine holds the
structure and the person holds the accountability, because the person is the one in the
room on Monday and the one who pays for a wrong claim. Without that operator you get a
well organized archive that nobody is answerable for.

It was also built for one person's working knowledge. Nothing here has been tested as a
shared team archive, and several of the rules would probably break under multiple
writers.

## How this repository was written

The method is operated with an AI assistant, and so was this repository: drafted with
one, edited by me. That is the same arrangement the method describes, so leaving it out
would be strange. What I do not delegate is the judgment about what stays.

## Status

A first version ran daily from June 2026. It was torn down and rebuilt from scratch in
August, for the reason described above, and the current version is documented in full in
`METHOD.md`. The `docs/` breakdown and the synthetic examples are being written.

## License

CC BY 4.0. Use it, adapt it, credit it.
