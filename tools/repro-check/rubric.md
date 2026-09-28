# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Claim is specific and honest | The candidate claim comment compared with the issue title/body and thread highlights; compare any claim that reproduction is complete with the report's evidence. | Pass when the comment identifies the issue's actual symptom or a relevant technical target and gives a concrete, bounded next step or report of work. Any assertion that the bug was reproduced or diagnosed must be supported by the report. Fail generic assign-me language, unsupported certainty, or promises of a fix, timeline, or outcome the contributor cannot guarantee. | required |
| Environment is interpretable | The repro report's environment record compared with the issue's target version, platform, configuration, and relevant repo facts. | Pass when the report identifies the environment details material to the trigger and either matches the issue's relevant conditions or explicitly names and accounts for differences. Missing context that prevents interpreting the attempt, or a silent material mismatch, fails. A thread's suggestion that a fix shipped does not outweigh a direct artifact showing the issue behavior in the report's stated environment. | required |
| A stranger can rerun the attempt | The repro report's commands, inputs, configuration, setup references, and artifact locations; check whether any required private files or inaccessible services are supplied or described. | Pass when a stranger with the stated environment and access to the named public project can reconstruct the trigger and run the attempt without guessing a material input or relying on private, unavailable state. Do not require a fixed number of steps or a particular format. | required |
| Evidence matches the reported result | The report's output, logs, screenshots, measurements, or other artifacts compared directly with the issue's trigger and with the author's stated outcome (reproduced or cannot reproduce). | For a claimed reproduction, pass only when the artifact demonstrates the same symptom under the relevant trigger, not just a different error or adjacent behavior. For an explicit cannot-reproduce report, pass when it documents a concrete attempt to exercise the issue's scenario, shows what happened instead, and openly identifies a relevant limitation or trigger condition the attempt could not reach. Do not require a cannot-reproduce attempt to display the bug; fail only when it changes the reported trigger without acknowledging that difference, provides no observable result, or falsely claims confirmation. | required |
| Outcome is evidence-calibrated | The report's stated expected and actual behavior, conclusion, and any cannot-reproduce explanation compared with its artifacts and the issue's description. | Pass when the conclusion does not claim more than the artifacts show. An honest cannot-reproduce result passes when it records a genuine attempt and identifies the observed result or material difference; it does not claim confirmation. Fail when a mismatch or absence of evidence is described as confirming the issue. | required |
| Communication follows repo policy | The repo-facts block's bug-report and contribution-policy requirements compared with the claim and repro comments, including any AI-use disclosure requirement. | Pass when the comments meet any explicit repository requirement that applies to issue reports or AI disclosure. If the stated policy requires naming AI tools and the extent of assistance, that disclosure must appear; do not invent a disclosure requirement when repo facts state none. | required |

## Verdict rule

Accept only when every required check passes. A fail or unclear on any
required check means reject. Preferred checks, if added later, never
change the verdict.
