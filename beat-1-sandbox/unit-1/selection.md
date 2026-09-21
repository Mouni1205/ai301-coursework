# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
paste the output here, including the closing JSON block
```

    try/except — the fix is a few lines.
  - Unclaimed — pass. assignees: [], comments: 0, and the repo has zero pull requests
    (state=all → 0). The only timeline activity is two referenced events from
    commits in classmates' own fork repos (rafiatasafi/ai301-coursework,
    xyin20/ai301-coursework) — not PRs here, and under the Path Review house rule
    classmate claims don't block anyway. 
  - Contribution policy permits the work — pass. docs/CONTRIBUTING.md (189 lines)
    never mentions AI, agents, or generated code; no AI_POLICY.md; the PR template
    asks only for tests, CI, and xfail removal. Silence passes. 

  All five required checks pass → accept. On fit: this is exactly your profile's
  center — a backend API repo (FastAPI), an auth/security fail-closed bug, with a
  pytest unit test as the acceptance criterion.
    
  { 
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
    "checks": [
      {"name": "Maintainer alive", "grade": "pass",
       "evidence": "All 5 latest main commits authored by human collaborator 
  Aburke225, newest 2026-09-16 (4 days before today); issue opened by same account 
  with author_association COLLABORATOR"},
      {"name": "Repo in use", "grade": "pass",
       "evidence": "archived: false; pushed_at 2026-09-16T21:50:20Z with main moving;
  9 forks in active student use"},
      {"name": "Scope fits a newcomer", "grade": "pass",
       "evidence": "One bounded fix: 'Verification against a malformed hash should 
  fail closed (return False), not raise', names core/security.py and 
  tests/unit/test_security.py, 1-2 hour estimate, xfail test 
  test_verify_with_wrong_hash_format is the acceptance criterion"},
      {"name": "Unclaimed", "grade": "pass",
       "evidence": "assignees: [], comments: 0, repo has 0 pull requests total; only 
  two 'referenced' events from commits in classmates' own fork repos, which the Path 
  Review house rule does not treat as blocking"},
      {"name": "Contribution policy permits the work", "grade": "pass",
       "evidence": "docs/CONTRIBUTING.md contains no mention of AI, generated code, 
  or assistants; no AI policy file; PR template requires only tests, green CI, and 
  xfail removal"}
    ],
    "verdict": "accept"
  }    

For the required machine-readable ending, the live verdict is:

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
  "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "All 5 latest main commits authored by human collaborator Aburke225, newest 2026-09-16; issue opened by same account with author_association COLLABORATOR"},
    {"name": "Repo in use", "grade": "pass", "evidence": "archived: false; pushed_at 2026-09-16T21:50:20Z with main moving; 9 forks in active student use"},
    {"name": "Scope fits a newcomer", "grade": "pass", "evidence": "One bounded fix in core/security.py with a pytest acceptance criterion in tests/unit/test_security.py"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "assignees: [], comments: 0, and no pull requests in the repository"},
    {"name": "Contribution policy permits the work", "grade": "pass", "evidence": "The contribution policy contains no mention of AI, generated code, or assistants"}
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

The final complete run reported: `agreement: 19/20 scored items  (bar: 18/20: PASS)`. It also reported: `categories: claimed 4/4  clear-accept 7/8  dead-repo 3/3  policy 1/1  scope 4/4`.

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

I used issue-16 for this analysis. In the final run, the result was `issue-16  accept  accept   yes`. My rubric accepts it because the issue describes one bounded bug and gives concrete technical and expected-behavior information. I changed the scope check so that a diagnostic environment dump does not by itself make a single reported symptom too broad. The targeted run for issue-16 reported `agreement: 1/1 scored items`, and the final run also accepted it.

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

I chose the `Scope fits a newcomer` check:

> Pass if the issue asks for one bounded contribution and gives a concrete specification through reproduction steps, expected behavior, acceptance criteria, a named documentation home, or a maintainer diagnosis. A concrete issue filed by an Owner, Member, or Collaborator can pass even when the body is brief. Related file or documentation updates can be one contribution, and a detailed technical checklist, diagnostic environment dump, or several implementation suggestions for one reported symptom is evidence of scope rather than evidence of excess scope. Do not require a maintainer to have confirmed a contributor-authored issue or to have commented on a clear issue. Fail explicit umbrella or tracking issues, pure usage questions, unresolved design debates, unresolved product decisions or required assets, years of unresolved discussion, multiple abandoned attempts showing the real difficulty, issues with no actionable specification, or work explicitly involving broad core-internal changes. A short issue, missing reproduction steps, or a good-first-issue label is not automatically a failure

I wrote this check to distinguish detailed evidence from broad scope. It accepts one clearly defined contribution even when the issue includes diagnostic details, while still rejecting tracking issues, unresolved designs, abandoned attempts, missing specifications, and broad internal changes.

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

The broader scope check can accept a detailed issue with several related files, implementation suggestions, or diagnostic information. I accepted that trade-off because issue-16 is one bounded bug even though its report contains extensive environment details. The check still rejects explicit umbrella issues, unresolved design or product decisions, multiple abandoned attempts, and work with no actionable specification. The issue-16 targeted run passed `1/1`, and the final complete run passed `19/20`.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

Issue #72 fits my backend experience with APIs, authentication, security, and test-driven bug fixing. The live output describes a small fix in `core/security.py` with a corresponding test in `tests/unit/test_security.py`, and estimates the work at 1–2 hours. That fits the time available for a first contribution.

The verdict correctly identified that the issue is active, bounded, unclaimed, and permitted by the repository policy. It also matches my interest in backend and security work. My personal preference for Java, Spring Boot, banking, and financial systems helped me rank the issue, but it did not change the rubric verdict.

The anticipated difficulty is understanding the existing password-hash verification behavior and writing the test correctly. The live output identifies the relevant files and an xfail test, so the starting point is clear. I have not claimed the issue yet because Unit 1 selection is separate from Unit 2 claiming and environment setup.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
