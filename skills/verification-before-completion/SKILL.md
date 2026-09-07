---
name: verification-before-completion
description: Check that completion, fix, build, or test claims are supported by evidence from the relevant code and environment before reporting success or publishing the work.
---

# Verification Before Completion

Make claims no broader than the evidence. Use the smallest relevant verification that proves the changed behavior and complete repository-required checks.

## Evidence Validity

Reuse current evidence until the relevant code, configuration, environment, target, or claim changes. A new message does not invalidate a completed check. Re-run when a later edit could affect the result, when live state may have drifted, or when the previous run did not cover the claim.

Track the command or interaction, target revision or artifact, relevant environment, result, and limitations. A passing check on another build or environment does not prove this one works.

## Before a Completion Claim

1. Identify the observable result that would support the claim.
2. Inspect the recorded evidence and decide whether it still applies.
3. Run missing or invalidated checks; read the relevant output and exit status.
4. Compare the result with the requested outcome, including requirements a test suite does not cover.
5. Report the actual state and any material verification gap.

## Match Evidence to the Claim

| Claim | Relevant evidence | Insufficient by itself |
|-------|-------------------|------------------------|
| Tests pass | Relevant test output with no failures on the current code | An expectation that they should pass |
| Linter is clean | Linter result covering the changed files or required scope | A check on unrelated files |
| Build succeeds | Successful build of the relevant target | Linter output |
| Bug is fixed | Original symptom or meaningful regression reproduction now passes | An edit that looks plausible |
| Regression test detects the bug | Failure on an affected baseline and success after the fix, or equivalent recorded evidence | A test that only mirrors implementation |
| Requested work is complete | Reviewed changes and acceptance evidence for the requested outcome | Agent self-report or tests alone |
| Production is healthy | Current evidence from the affected live target | Local compilation or a successful upload |

A focused check supports a focused claim. It need not prove the entire product correct.

## Regression Evidence

Prefer capturing a failure before implementing a testable fix. If the implementation is already present and the failure was not recorded, use a safe isolated baseline when needed. Preserve user work and never revert a shared worktree merely to demonstrate test order. Reuse recorded before/after evidence instead of repeating a fail/fix cycle for every report.

## Delegated Work

Review the delivered diff or artifact and the worker's evidence. Re-run checks when results are missing, ambiguous, stale, or do not cover integration with other changes. Do not repeat a valid check solely because another agent ran it.

## Reporting

State what changed, what was verified, and unresolved failures or limitations. Distinguish a baseline failure from a regression introduced by the change. If a required check cannot run, report that limit and do not convert it into a passing result.
