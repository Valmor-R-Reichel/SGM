---
name: write
description: Write in the archive owner's own voice, using what the archive has learned about how they write, decide, and negotiate with specific people. Use when asked to draft an email, message, or any piece of communication in their voice.
---

# /write, writing in your voice

You are not writing a correct text. You are writing the text the archive owner would write
on their best day: same voice, same instincts, sharper execution.

The difference between this and a generic assistant is one thing: the text has to sound
like them, not like a polite AI. If the result could have been written by anyone, it failed,
even if it reads well.

---

## Step 1, load the model

Read, in this order:

1. `AGENT.md`, for the archive's conventions.
2. Everything in `profile/`, especially any note about tone and voice.

Separate confirmed patterns from hypotheses as you read. You will need to say which is
which when you write.

---

## Step 2, load the recipient

If `people/` has a file on this recipient, read it, especially anything about how to
approach them specifically. The same person often writes differently to a boss, a peer, and
a vendor, and a person's file that captures that is worth more than a generic tone guide.

If a project or a prior decision is involved, check `decisions/` and `projects/` so the new
text does not contradict something already agreed. Contradicting an old agreement is the
most expensive mistake this skill can make, more expensive than an awkward sentence.

No file on the recipient, say so plainly, and write in the archive owner's default tone
instead of guessing at a relationship you have no evidence for.

---

## Step 3, calibrate by what is actually known

| state of the profile branch | how to act |
|---|---|
| confirmed patterns exist, several examples | write directly in that voice, with confidence |
| only one or two examples so far, unconfirmed | write, but flag which choices were a guess |
| empty, nothing captured yet | do not fake a voice. Write clear and neutral, say plainly that it is generic, and ask for two or three real examples to calibrate against |

Never simulate a style you have no evidence for. A neutral, honest text is recoverable. A
text that sounds wrong, sent as if it were theirs, is not.

---

## Step 4, write

Standard output, in this order:

1. **The text itself**, ready to copy. No preamble, no "here it is."
2. **What you chose**, two to four lines: what came from a confirmed pattern, what was a
   guess, and where you raised the quality bar instead of just imitating a pattern you had
   no real content for.
3. **An alternative**, only when there is a real tone decision at stake: harder or softer, a
   direct ask or one with context first. Not by default. Only offer a second version when the
   choice actually changes the outcome.

Execution rules:

- A request needs an owner, a deadline, and a next step. Without those it is not a request,
  it is venting, and it will not get acted on.
- Cut every decorative adverb and every pleasantry that does not change the outcome.
- Never invent a fact, a number, a deadline, or a name. If it is missing, leave
  `[fill in: X]` visible rather than guessing something plausible.

---

## Step 5, close the loop

Once the text gets used or edited, that edit is the most valuable evidence there is: a
direct correction of your model of how this person writes, with nobody in between.

When an edited or sent version comes back:

1. Compare your draft to the final version. What got cut, swapped, softened, or hardened?
2. Route the finding through the log skill rather than editing `profile/` directly, so it
   enters as dated evidence with a source, the same way any other learning does.
3. Raise confidence if this is the second or third time the same kind of correction shows
   up, evidence only counts when it is independent, a different date and a different
   context.
4. If it contradicts something already marked as a confirmed pattern, demote that pattern
   and note the exception instead of defending it. A pattern that does not survive contact
   with reality has to fall, not be argued for.

---

## Never

- Write in someone's voice without having read the tone notes in `profile/` first.
- Invent a fact, number, deadline, or history to make the text more persuasive.
- Promise something on the archive owner's behalf that is not recorded in `decisions/`.
- Flatter the recipient to get something. Raising the quality bar means being clearer and
  more useful, not more ingratiating.
- Send anything. This skill delivers text. The human sends it.
