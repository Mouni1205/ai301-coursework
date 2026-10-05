# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

1. In live mode, read `scope.md` first and confirm the issue belongs to
   the configured Path Review repository. Stop if it is outside scope or
   the repo line is still a placeholder. In eval mode, do not consult
   scope or outside sources.
2. Read `rubric.md`, `references/evidence-guide.md`, and this procedure;
   list each check and its evidence sources before grading.
3. Read the whole package in this order: issue context and thread
   highlights, repo facts, reproduction evidence, candidate plan, then
   candidate plan comment. Record the issue symptom, what the repro
   actually showed, relevant maintainer direction, and stated repo
   requirements.
4. In live mode, read the student's posted reproduction comment and
   relevant issue thread; use repository docs only for stated repo
   facts. If no student reproduction comment is available, use only
   reproduction evidence quoted in the candidate drafts and record that
   limitation. Do not fail a check solely because the posted repro
   comment is absent when the drafts contain concrete repro evidence.
   In eval mode, treat the bundle as the complete evidence.

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

## Evidence gathering

1. For diagnosis, extract the plan's causal claim and the quoted repro
   observation that supports it; compare both with the issue symptom.
2. For scope, list the planned change, exclusions, and named files or
   areas. Compare the list with the stated cause and requested behavior.
3. For executability, record the plan's target files and implementation
   actions in their proposed order, then check those targets against
   available repository facts.
4. For testing, record the command, input, code path, expected result,
   and any regression case. Compare them with the reproduction trigger
   and observed failure.
5. For uncertainty, note explicit assumptions, risks, unknowns, and
   deviations. For communication, compare the candidate comment with
   thread direction and explicit repo-facts requirements.
6. In eval mode, quote or identify only facts in the bundle. In live
   mode, identify the issue or repository location for each external
   fact; never fill gaps with assumptions.

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

## Check execution

1. Grade each rubric row using only its named evidence, in table order.
   Use the evidence guide to locate the plan section or source.
2. Mark `pass` only when every condition in that row's pass condition is
   supported. Mark `fail` when evidence contradicts a condition. Mark
   `unclear` only when the package genuinely lacks evidence needed for
   that decision; do not use it to avoid checking an available source.
3. For each grade, keep one concise quote or concrete fact that explains
   the decision. Do not let a polished comment compensate for a weak
   diagnosis, scope, approach, or test.

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

## Verdict assembly

1. Apply the verdict rule in `rubric.md`: accept only if every required
   check passes; any required fail or unclear means reject. Preferred
   checks do not affect the verdict.
2. Report every check with its name, grade, and deciding quote or fact.
   State the binary verdict and use the required fenced JSON output
   format from `SKILL.md`, with no text after the JSON block.

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->
