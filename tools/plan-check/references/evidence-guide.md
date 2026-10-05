# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

Where it lives: In an eval package, read the issue context, repro-evidence
block, and the plan's diagnosis and evidence quotes. In live mode, read
the issue description, the student's posted repro comment, and the
corresponding diagnosis in `plan.md` and `comment.md`.

Good evidence links the stated cause to an observed behavior from the
reproduction and explains the issue symptom. A plausible cause without
support in the quoted repro is not established.

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

## Scope

Where it lives: In an eval package, inspect the plan's scope, exclusions,
named files, and approach beside the issue request and diagnosis. In live
mode, inspect those plan statements and compare them with the issue and
repository facts.

Good scope names the behavior being changed and keeps implementation to
the code and tests needed for that cause. It excludes unrelated cleanup
or feature work and does not leave the diagnosed cause unaddressed.

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

## Executability

Where it lives: In the plan's file list and ordered approach, compared
with repository facts in the eval bundle or the repository's relevant
source and tests in live mode.

Good evidence identifies a valid starting point and concrete actions a
contributor can begin without guessing a material file or step. A vague
intention such as "fix the handler" does not identify an executable
approach.

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

## Test plan

Where it lives: In the plan's test plan and quoted reproduction evidence.
Compare commands, inputs, and expected results with the trigger and
observed output in the repro block or posted repro comment.

Good evidence exercises the relevant path in the real code and names an
observable result that would fail before the fix and pass after it. A
test that cannot reach the trigger or has no expected result cannot
establish the fix.

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

## Honesty

Where it lives: In the plan's risks, unknowns, assumptions, and
deviations. Read these alongside the diagnosis and test plan to identify
unresolved dependencies or claims not established by the evidence.

Good evidence labels material uncertainty and avoids presenting an
assumption as a fact. If implementation deviated, a useful note names
the change and its reason; the absence of deviations needs no invented
issue.

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

## Comms

Where it lives: In the candidate plan comment compared with issue-thread
highlights and the repo-facts block. In live mode, read the thread and
the repository's contribution, issue-template, and AI-use rules when
present.

Good communication gives this contributor's own evidence-based
diagnosis, bounded change, and test plan. It responds to relevant
maintainer direction and meets stated repository requirements; do not
invent requirements when the repo facts are silent.

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->
