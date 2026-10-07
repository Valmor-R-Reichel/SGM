# Criterion over repertoire

Everything that runs behind this repository was written by AI agents at my request: the scripts,
the tests, most of the queries I use at work. What is mine is something else. I decide what to
measure, what counts as an error, and what is allowed into the archive. And with whatever comes
back from the AI, I trust, but verify.

The README says that, in an environment with AI, the advantage moves to whoever holds the criteria
rather than the repertoire. This page tells how I got there, in the order it happened.

## Context

I have used artificial intelligence at work for some time, like almost everyone. In 2025 I started
treating it differently, giving it more room in my day, to think through a problem, review a text,
organize an analysis.

SQL went the same way. I know the logic of a query and not the syntax, so I split the work: I bring
the business rule and the number I expect to see, the AI writes the query, and I run it and check
the result against what I know of the operation. When the number does not add up, the conversation
goes back to the rule.

In the first half of 2026 I got access to agents that work inside the computer: they read the
files, run the commands, write the result to disk. First Antigravity, and today Claude Code, Codex
and Antigravity side by side. Before long they were doing things I knew how to ask for and did not
know how to do.

The first problem showed up quickly. The agent agrees with whoever is asking. I hand it a hypothesis
and it comes back better dressed, even when it is wrong. In July I wrote down my working rules for
it, under the heading "technical golden rules" (translated from Portuguese):

> Don't invent naive solutions. If it looks too easy, it is probably wrong.
> A pretty but wrong answer is worse than no answer. Prefer to be skeptical.

I did not know it yet, but much of what came later grew out of those two lines.

## The heavy archive: measure before you automate

Then I started this second brain: markdown notes that an agent reads before it answers and writes
at the end of each work session. Within five days there were dozens of notes and eight
consolidations a day, and each consolidation took longer than the one before.

The obvious way out was to ask for a script. The measurement came first. Reading back through the
session history, consolidation was using 54% of all the tokens spent working with the agent. And
the cause was not what I expected. Reading the rules and the notes cost little. The expensive part
was the queue: 202 edits made one at a time, each one forcing the agent to reread the entire
conversation.

That is where the first script came from, with a single rule: anything that gives the same result
every time moves out of the agent and into the script. Counting, listing, checking that a link
points to a note that exists. These were tasks where the agent spent turns and sometimes got it
wrong, and that a script does the same way every time. Whatever depends on reading and weighing
stays with the agent. And the script proposes, it never edits the notes.

It started with three things. The first is a snapshot: instead of the agent opening folder after
folder to learn how big the archive is, one command returns how many notes each subject has and
what is waiting for consolidation. The second is an index, a list of every note with its title and
date. Since every title is a claim, the list usually answers the question or points to the exact
note, and the agent reads the index before opening anything. The third is a check for what is
broken, like a link to a note that does not exist or a note without a date. It also ran an
evidence check: whether each sentence marked with a confidence level had the evidence that level
required.

That evidence check showed "trust, but verify" applying to the script itself, in both directions.
On its first run it found three problems. That seemed low, and it was: the script ignored text
between backticks, and the evidence marker is written precisely between backticks. Once that was
fixed, 55 showed up. Now it was too many. Almost all of them were correct markings, because a fact
proven by a system document does not need to repeat three times to be true. Counting evidence is
for one of my readings to become a fact, not for a document. The error was in the rule, and it was
replaced by one that can be checked without interpreting anything: a claim about another person
only reaches the highest level with at least one source that is not me telling it.

One of the checks almost did not survive. It was meant to tell two kinds of note apart, the file
that accumulates facts about a person or project and the note that asserts one thing. Two attempts
returned 100% false positives, and the conclusion that day was that it required judgment. It was
taken out of the script, with the reason written into the code. A week later it came back: the
mistake had been applying the same criterion to every folder. With one criterion per folder, it
returned zero false positives. What stayed was a rule: when a check is wrong 100% of the time,
first test whether the question was badly asked, and only then declare it impossible.

## The part I like best: the script types, I decide

Two days later, in a consolidation with some thirty edits queued up, I lost my patience. I wrote
"pelo amor de deus" (roughly, "for God's sake") and proposed a different split: the agent writes
all the texts into a single file, and a script applies everything at once.

Before, every change to a note was a round trip: the agent decided, wrote, waited, and only then
moved to the next one. Now it does all the thinking first and hands over a single file, the plan,
with everything that will change in that round: the new notes, the passages going into existing
notes, and the links between them. I read what is going to change and approve it with a click.
Only then does the script come in, and it carries out the plan in a single command.

The script follows three rules.

**First it shows, then it does.** By default it only simulates: it shows each file as it would look
and writes nothing. To write, it needs an explicit order. What I approve is exactly what it will do.

**It checks everything before writing anything.** The whole plan is assembled and checked before
the first file is written. If one piece is wrong, it cancels the entire batch instead of writing
half of it. Half a consolidation written would leave the archive in a state nobody decided on.

**It only does what needs no judgment.** When the plan declares a link between two notes, it writes
the link on both sides. Every note it touches gets the day's date, which is the field the agent
forgets most and the only one you can get right without thinking. When a loose link turns up in the
middle of a text, it does not resolve it on its own: it flags it. Triage, contradiction and drafting
stay ahead of it, with the agent and with me.

That is why the script's rule changed from "proposes and never edits" to "proposes and never
decides". It now writes to the notes, but only what the agent drafted and I approved.

This separation between judgment and typing is what lets me trust the rest, and it came from an
idea of mine, without my knowing how to write a single line of it.

<details>
<summary>The comment that opens this part of the script</summary>

The original comment, in Portuguese:

```text
O gargalo medido em 12/08 nao e a digitacao, e a IDA E VOLTA: 202 Edit + 75
Write em turnos separados, cada turno reenviando uma conversa de 262k tokens.
Um Edit que erra a string por um espaco custa outro turno inteiro.

Isto NAO fura a secao 2.5 do plano ("propoe, nao edita"). O que aquela regra
protege e o julgamento — triagem, contradicao, redacao — e o gate de clique,
e os dois continuam ANTES daqui: o agente escreve o plano, o Valmor aprova o
plano, o script datilografa. Por isso o padrao e simular: gravar exige
`--gravar`, e sem a flag o comando continua so propondo.
```

In English:

```text
The bottleneck measured on 12/08 is not the typing, it is the ROUND TRIP: 202 Edit + 75
Write in separate turns, each turn resending a 262k-token conversation.
An Edit that misses the string by one space costs another full turn.

This does NOT break section 2.5 of the plan ("proposes, does not edit"). What that rule
protects is the judgment (triage, contradiction, drafting) and the click gate,
and both still come BEFORE this point: the agent writes the plan, Valmor approves the
plan, the script types. That is why the default is to simulate: writing requires
`--gravar`, and without the flag the command keeps only proposing.
```

```text
python vault.py aplicar <plan.md>             # simulates, writes nothing
python vault.py aplicar <plan.md> --gravar    # writes everything at once
```

</details>

## The tests: the question is mine, the execution is the agent's

Over time came the question everyone asks: does this work, or does it only look organized? I set up
the tests the same way I set up everything else. The question comes from me: what will be measured,
what counts as a correct answer, and what each result would prove. The predictions are recorded
before any data is collected. The agent runs it, and I check.

The first test measured the line that stays in place of a claim that fell, the `> discarded:` line
from the README. Its logic has three steps.

First, prove the trap works. I took cases where the error had come from an outside source and showed
the agent only that source, without the archive. It got two thirds of the answers wrong, a little
below the 70% I had set as the bar. If the trap did not catch, the rest of the test would prove
nothing.

Then, the same trap with the archive alongside, in two versions: the note with the discarded line
and the note without it. With the line, it was wrong 0% of the time. Without it, 15%. The
difference came from 4 of the 22 cases: the direction is consistent, and the sample is too small to
call it proof.

And before running it, what would bring the idea down was written down: if the difference between
the two versions were small, the line would be decoration. Writing that down beforehand is what
keeps me from adjusting the reading after I see the number.

The other half of the question did not close: I wanted to know whether keeping the why of each
correction helps more than keeping only the what, and the what alone was enough in that test.
Whether the why adds anything is still unmeasured, and the repository says so.

The second test measured the size of the center file the agent reads first. Cutting half of it made
no difference. Cutting too much did, because a correction that only lived there went with it. The
overall number seemed to confirm what I expected. Broken down question by question, a good part of
the errors came from a single question, with an outdated answer key. The conclusion got smaller,
and it got defensible.

The results and the caveats are in [`METHOD.md`](../METHOD.md).

## The hypothesis

The name of this page is a hypothesis, and I want to state it plainly.

To solve a problem with technology, you used to need to know the tools: which library to use, which
command to type, how to write it in that language. That is repertoire. With an AI agent, the
repertoire has moved. Today I do not say "use such-and-such library". I say "I need to get this
information over there, what is the most efficient way?", and the agent chooses and does it. The
repertoire is with the agent, and it grows with every new version of the model.

What stays with me is the criterion: what to ask, what counts as an error, when a number that looks
too good deserves suspicion, what is allowed into the archive. That is what the sections above try
to show, in what worked and in what did not.

I had basic notions of SQL and Python. With logic and AI, I started building queries and scripts I
could not have written on my own. It has been a time of discovery for me, and I keep moving forward
in it.

What is here is where I have arrived for now. Some choices may turn out to be unnecessary. I split
an entire book into parts for the agent to consult, and a folder with the files and a search by
meaning might have been enough. I do it this way today because it is how I managed to move forward
on the subject. When it is time to change, the decision will come from the same criterion.
