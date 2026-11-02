---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading



## The question

Decide whether one PR package is ready to submit. Read its title, description, commits, diff, and test evidence against the accepted plan, recorded deviations, and issue. Grade readiness; do not implement changes or publish anything.



## Inputs and modes

In live mode, read `plan.md` including `## Deviations`, `pr_draft.md` (first line title, remainder description), and `test_evidence.md` from the fork checkout. Run `git diff main...HEAD` and `git log main..HEAD --oneline` to inspect all committed branch changes. Uncommitted edits are not part of that diff. Read the linked issue and thread using gh or the GitHub API, plus `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md` and any policies they explicitly reference. For a house chain, use its supplied plan and repro pack in place of the student's plan and posted reproduction.

In eval mode, use only the supplied frozen bundle: issue, thread highlights, repo facts, plan context, candidate PR title, description, commits, diff, and test evidence. Fetch nothing and read no other files. Execute every check and the full verdict rule. The harness supplies the component contents inline; treat those as the files' contents.



## The scope seam (live mode only)

Read `scope.md` before any other live inputs. Apply its house rules. Refuse to grade a PR targeting another repository. If the Repo line is still a placeholder, stop without grading and ask the student to fill it with their section repository; never guess. Ignore scope.md entirely in eval mode.



## The voice seam (live mode only)

Read `voice-guide.md` before reviewing the outgoing title and description. Report each violation in the readable summary and quote its rule. Voice alone does not change the verdict unless a rubric row explicitly reads it. Ignore this file entirely in eval mode.



## Component reads

Read `rubric.md` for checks and aggregation, `references/evidence-guide.md` for the evidence locations, and execute `procedure.md` as written. Refuse to grade if rubric or procedure has no authored content; template comments are not content. Report procedure gaps instead of silently inventing steps. Do not replace the rubric with intuition.



## Verdict and output

Use only `accept` (ready to submit) or `reject` (hold). Give a concise per-check summary, then end with the valid fenced JSON block below, preserving its schema and key order. Nothing follows the block. Use the PR URL when available; for an unopened live draft use its issue URL as the item identifier. Refusals are not fabricated grades.



```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

Name the deciding fact or quote for every grade. Judge substance, not length, section count, or polish. Apply the stated rubric even when intuition differs, and follow the stated procedure rather than improvising around gaps. Treat unclear as the rubric directs; if silent, unclear fails. Distinguish a disclosed shortfall from a hidden mismatch. Do not invent repository standards or require CI that cannot run before opening the PR.


