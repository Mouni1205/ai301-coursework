# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

Mouni1205

---

## Posted upstream

**Claim comment**

[Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.]

**Reproduction comment**

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. The first complete run reported: `agreement: 17/20 scored items  (bar: 18/20: below the bar)`. Its category line was `categories: clear-accept 5/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`.
2. I re-ran the disagreements and canaries (`pkg-01,pkg-02,pkg-09,pkg-10,pkg-16`): `agreement: 5/5 scored items`; `categories: clear-accept 3/3  wrong-target 2/2`.
3. The next complete run reported: `agreement: 18/20 scored items  (bar: 18/20: PASS)`. It still rejected `pkg-09` and `pkg-10`, both gold-labeled accept.
4. After clarifying how the artifact check handles an honest cannot-reproduce attempt, I re-ran `pkg-02,pkg-09,pkg-10,pkg-16`: `agreement: 4/4 scored items`; `categories: clear-accept 2/2  wrong-target 2/2`.
5. The final complete run reported: `agreement: 20/20 scored items  (bar: 18/20: PASS)`. Its category line was `categories: clear-accept 8/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`.

**Package analysis**

For `pkg-09`, my first complete run decided `reject` while the gold label was `accept`. The report explicitly says, `I did not find a knob to force a smaller limit from the CLI.` My first wording treated failure to show the exact differential flush trigger as failure of the artifact check, even though the report documented a concrete attempt, its observed marker order, and the limitation honestly. I revised the check to evaluate the evidence against the report's stated cannot-reproduce outcome. The final full run decided `accept`, matching the gold label.

**Check rationale**

> Evidence matches the reported result | The report's output, logs, screenshots, measurements, or other artifacts compared directly with the issue's trigger and with the author's stated outcome (reproduced or cannot reproduce). | For a claimed reproduction, pass only when the artifact demonstrates the same symptom under the relevant trigger, not just a different error or adjacent behavior. For an explicit cannot-reproduce report, pass when it documents a concrete attempt to exercise the issue's scenario, shows what happened instead, and openly identifies a relevant limitation or trigger condition the attempt could not reach. Do not require a cannot-reproduce attempt to display the bug; fail only when it changes the reported trigger without acknowledging that difference, provides no observable result, or falsely claims confirmation. | required |

I revised this check after the first full run because `pkg-09` and `pkg-10` were honest cannot-reproduce reports, but their artifacts were being judged as though every report had to show the bug. The revised wording lets a documented attempt pass when it states what happened and what limited the attempt, while keeping wrong-trigger and unsupported-confirmation cases rejectable.

**Trade-offs**

The revised check accepts an honest cannot-reproduce attempt even when the issue's hidden trigger condition could not be reached; it does not treat that result as proof the bug is absent. To check that this did not loosen rejection of wrong-target reports, I re-ran canaries: `pkg-02  reject  reject   yes` and `pkg-16  reject  reject   yes`. The final full run matched `20/20`, including all `4/4` wrong-target packages and the single `disclosure 1/1` package.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
