# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

Mouni1205

**Plan comment**

Permalink: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5987002601

> On macOS 26.6.2 (arm64), Python 3.13.7, Passlib 1.7.4, and bcrypt 4.3.0 at commit `2f4e82f`, I ran `verify_password("password", "not_a_valid_bcrypt_hash")`. It raised `passlib.exc.UnknownHashError: hash could not be identified`; the focused test reported XFAIL because it is marked as an expected failure. This matches issue #72's report that the exception escapes instead of returning `False`.
>
> I plan to catch only Passlib's `UnknownHashError` in `verify_password` and return `False`, then remove the xfail marker from that regression test. I will leave unrelated exceptions and authentication behavior unchanged. I will rerun the focused reproduction and the security unit tests, checking that malformed hashes return `False` while valid hashes still verify correctly.

## Your branch

**Branch**

`fix/72-malformed-password-hash`

Created and committed locally as `53e15ab`; this clone's `origin` is the shared CodePath repository, so the branch is not yet present on a personal fork.

**Evidence**

Before, on commit `2f4e82f`:

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -v
```

```text
tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format XFAIL [100%]
======================== 1 xfailed, 3 warnings in 0.49s ========================
```

```sh
.venv/bin/python -c 'from core.security import verify_password; print(verify_password("password", "not_a_valid_bcrypt_hash"))'
```

```text
passlib.exc.UnknownHashError: hash could not be identified
```

After, on `fix/72-malformed-password-hash`:

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -v
```

```text
tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format PASSED [100%]
========================= 1 passed, 1 warning in 0.38s =========================
```

```sh
.venv/bin/python -c 'from core.security import verify_password; print(verify_password("password", "not_a_valid_bcrypt_hash"))'
```

```text
False
```

Additional checks: `make test-unit` completed with 376 passed and 52 expected failures. `make check` passed Ruff and Black; mypy stopped in `.venv/lib/python3.13/site-packages/numpy/__init__.pyi:737` with `Type statement is only supported in Python 3.12 and greater`. The commit's pre-commit Ruff, Black, and mypy hooks all passed.

## Eval iterations

**Run history**

1. First full run: `agreement: 19/20 scored items  (bar: 18/20: PASS)`. The category line was `categories: clear-accept 6/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4`.
2. After refining the executable-approach condition, I re-ran `pkg-14,pkg-10,pkg-17,pkg-18`: `agreement: 4/4 scored items`; `pkg-14` changed to accept and the three unbuildable canaries remained rejects.
3. Next full run: `agreement: 20/20 scored items  (bar: 18/20: PASS)`. Category line: `categories: clear-accept 7/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4`.
4. After adding a procedure fallback for a missing posted repro comment, full run: `agreement: 20/20 scored items  (bar: 18/20: PASS)`; the same category line matched all packages.
5. After clarifying that missing posted repro alone does not fail a check, the final full run again reported `agreement: 20/20 scored items  (bar: 18/20: PASS)` with `categories: clear-accept 7/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4`. This is the run saved in `eval-run.txt`.

**Package analysis**

For `pkg-14`, my first full run decided `reject` while the gold label was `accept`. It rejected the plan because exact functions were left to be identified, even though the plan named the relevant `zellij-server` and `zellij-client` areas and a concrete next step: trace query issuance with already-working debug logs. I revised the executable-approach check to accept a named code area plus a specific method for locating the final change point. The retry decided `accept`; the three unbuildable canaries stayed reject.

**Check rationale**

> Approach is executable | The plan's named files or code areas, ordered implementation steps, and stated behavior compared with the repository facts and issue context. | Pass when the plan names a relevant code area and either specifies the implementation action or gives a concrete next investigation step with a stated method for locating the exact change point. Exact function names may remain open when the plan identifies how it will pin them down. Fail when it offers only broad exploration, an unspecified future fix, or steps that leave the starting point or material action to guesswork. | required

I revised this condition after `pkg-14` showed that requiring the exact functions too early can reject an actionable plan that names a subsystem and a concrete tracing method. The unbuildable canaries confirmed the change still rejects plans with only broad exploration and an unspecified future fix.

**Trade-offs**

The revised condition accepts plans that still need to locate the exact function, when they identify the code area and a concrete method for doing so. I re-ran the three unbuildable canaries (`pkg-10`, `pkg-17`, `pkg-18`); all remained rejects. The final full eval matched all 20 labels, including every category.
