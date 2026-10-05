# Plan: handle malformed stored password hashes in issue #72

Issue: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72

## Diagnosis

The reproduction shows that `verify_password("password", "not_a_valid_bcrypt_hash")` raises `passlib.exc.UnknownHashError` instead of returning `False`. The malformed stored hash is not a format recognized by Passlib's `CryptContext`, and the exception currently escapes `verify_password` to its caller. The issue asks for authentication verification to fail closed on this input.

Reproduction evidence: “This raises passlib.exc.UnknownHashError: hash could not be identified. Expected behavior: verify_password() returns False.” The focused test already expresses the desired result, but is marked `xfail` for issue #72.

## Scope

In scope: convert Passlib's `UnknownHashError` for an unrecognized stored hash into `False` in `verify_password`, and enable the existing regression test by removing its strict `xfail` marker.

Out of scope: changing password hashing, supported hash schemes, authentication routes, error handling for unrelated exceptions, or database behavior. I will not catch all exceptions, since unexpected failures should remain visible.

## Files

- `core/security.py` — handle the specific unknown-hash exception around password verification.
- `tests/unit/test_security.py` — enable the existing malformed-hash regression test.

## Approach

1. Import `UnknownHashError` from `passlib.exc`.
2. Wrap only the `pwd_context.verify` call in a `try`/`except UnknownHashError`; return `False` for that exception and preserve the current boolean result for recognized hashes.
3. Remove the strict `xfail` marker from `test_verify_with_wrong_hash_format`, keeping its assertion that the result is `False`.
4. Run the focused test, then the security unit tests. Confirm valid hashes still return true for the right password and false for a wrong password.

## Test plan

From the repository root, use the same setup and direct reproduction commands from Unit 2:

```sh
python3 -m venv .venv
.venv/bin/pip install -e ".[dev]"
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -v
.venv/bin/python -c 'from core.security import verify_password; print(verify_password("password", "not_a_valid_bcrypt_hash"))'
```

Before the change, the direct call is expected to raise `UnknownHashError`; the focused test is expected to report XFAIL because it is marked as an expected failure. After the change, the focused test should pass without xfail, and the direct call should print `False`. Then run `.venv/bin/pytest tests/unit/test_security.py -v`; all security tests should pass, including valid-hash success and wrong-password rejection cases.

Before opening a PR, follow `docs/CONTRIBUTING.md` and run `make check && make test-unit`.

## Risks and unknowns

The handler should catch only `UnknownHashError`. If Passlib raises a different exception for another malformed encoding, that case remains visible and should be assessed separately rather than hidden by a broad catch. The focused reproduction uses the repository's stated Passlib 1.7.4 and bcrypt 4.3.0.

## Deviations

The implementation followed the plan: `verify_password` catches only `UnknownHashError`, and the existing regression test is no longer marked xfail. The direct reproduction prints `False`; the focused test and all 25 tests in `tests/unit/test_security.py` pass. `make test-unit` passes with 376 passed and 52 expected failures. In `make check`, Ruff and Black pass, but mypy stops in the installed NumPy stub `numpy/__init__.pyi:737` with “Type statement is only supported in Python 3.12 and greater.” The commit's pre-commit Ruff, Black, and mypy hooks all pass. No implementation files beyond the two planned files changed.
