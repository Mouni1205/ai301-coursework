# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis follows the reproduction | The plan's diagnosis and quoted reproduction evidence compared with the issue's stated symptom and repro-evidence block. | Pass when the proposed cause explains the reproduced symptom and cites an observation that supports it. Fail when the diagnosis contradicts the observed result, substitutes an unsupported cause, or omits the repro evidence needed to connect cause and symptom. | required |
| Scope is bounded to the cause | The plan's in-scope and out-of-scope statements, target files, and approach compared with the diagnosis and issue request. | Pass when the change addresses the supported cause with a limited set of relevant code or test changes. Pass when unrelated behavior and broad rewrites are excluded. Fail when the plan expands beyond the issue or changes only a symptom while leaving the diagnosed cause untouched. | required |
| Approach is executable | The plan's named files or code areas, ordered implementation steps, and stated behavior compared with the repository facts and issue context. | Pass when the plan names a relevant code area and either specifies the implementation action or gives a concrete next investigation step with a stated method for locating the exact change point. Exact function names may remain open when the plan identifies how it will pin them down. Fail when it offers only broad exploration, an unspecified future fix, or steps that leave the starting point or material action to guesswork. | required |
| Test plan proves the intended behavior | The plan's test commands, inputs, and expected results compared with the repro-evidence steps and artifacts. | Pass when the plan reruns the relevant trigger against the real code and names an observable result that distinguishes success from failure. Pass when it includes relevant regression coverage for unchanged behavior. Fail when the test cannot reach the code path, lacks an expected result, or cannot detect the reported failure. | required |
| Uncertainty is stated accurately | The plan's risks, unknowns, assumptions, and any deviation note compared with its diagnosis, scope, and test plan. | Pass when unresolved facts that could affect implementation or validation are identified as unknowns, and the plan does not promise an unverified outcome. A deviation is acceptable when the plan states what changed and why. Fail unsupported certainty that hides a material risk or conflict. | required |
| Comment fits the thread and repo | The candidate plan comment compared with issue-thread highlights and repo-facts requirements, including contribution and AI disclosure policy. | Pass when the comment presents the contributor's own diagnosis, bounded scope, and validation plan; addresses any relevant maintainer direction; and meets explicit repository requirements. Fail generic or piggybacked text, a material contradiction with the thread, or a missing required disclosure. Do not infer requirements from silence. | required |

## Verdict rule

Accept only when every required check passes. Any required fail or
unclear means reject. Preferred checks, if added later, never change
the verdict.
