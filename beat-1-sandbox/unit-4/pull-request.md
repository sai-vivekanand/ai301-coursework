# Unit 4 — Test and Submit

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/274

**Branch**

`fix/71-heading-fixture-indentation` from `sai-vivekanand/pathreview-ai301-fa26-s3`, targeting `codepath/pathreview-ai301-fa26-s3:main`. Fixes issue #71.

## Eval iterations

**Run history**

One full scored run, with the installed `~/.claude/skills/pr-precheck` directory: **20/20**. Exact saved line: `agreement: 20/20 scored items  (bar: 18/20: PASS)`.

Exact category line: `categories: clear-accept 7/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`.

No partial or calibration runs were needed, and no components were revised after the full run. The eval transcript is the untouched harness output, and the submitted component fingerprints match it. The separate live checks grade my own draft and do not contribute to this agreement score. The first live check rejected missing formatting/frontend outcomes in the draft and evidence file. I added those captured outputs and the baseline control output; the second live check accepted all four checks. The skill files were unchanged throughout.

**Package analysis**

`pkg-01`: my skill returned `reject`, matching the gold label `reject` in the standards-wall category. Repo facts requires "closes #xxxx with the issue number", "all code checks passed (pre-commit)", and "an entry in the latest doc/source/whatsnew/vX.X.X.rst when fixing a bug". The candidate description omits the closing reference, the diff has no whatsnew entry, and no pre-commit result is reported. The evaluator's standards evidence says: "Description lacks 'closes #66657', there is no whatsnew entry in the diff, and pre-commit and type-annotation items are unaddressed". That is enough to reject under the standards check even though the package shows concrete repro and parser-suite evidence. The run also flagged a plan/diff mismatch and the unreported pre-commit run; the category label does not prevent multiple checks from failing.

**Check rationale**

Exact current check from the uploaded rubric:

| Repository standards and disclosure | Repo-facts PR template and contribution/AI policy; issue thread instructions; draft title and description; live scope rules | All applicable template sections and stated contribution/disclosure asks have substantive answers, and relevant maintainer instructions are addressed. N/A with a reason is acceptable for inapplicable sections. Disclose AI tool and extent when required; in live Path Review mode the course always requires this in Notes for Reviewers. Do not invent an AI rule for an eval repository with none. Pending CI before opening is not a failure if accurately left pending. | required |

I rewrote Unit 3's comment/convention check for a completed PR: the relevant comparison is the actual template and stated policy against the filled title and description. I rejected a universal AI-disclosure gate in eval mode because the bundles have different repository policies. The classroom requirement is explicit for live Path Review mode. I also made pending CI distinct from omitted local checks, since a pre-opening tool cannot truthfully require a result from a PR that does not yet exist. These choices were in the first evaluated version; no later tuning was necessary.

**Trade-offs**

The standards check deliberately does not impose requirements absent from an eval repository. In `pkg-19`, the evaluator recorded: "No PR template or AI policy in repo facts; contribution ask 'tests with fixes' satisfied by the added operator test; no maintainer instructions in thread". My verdict and gold both say `accept`. Adding a universal disclosure or template rule would risk rejecting this valid package. At the same time, both standards-wall packages (`pkg-01` and `pkg-20`) were rejected in the full run, so this distinction did not erase that category. The testing check also permits honest failures with reasons, which preserves transparency but is not a guarantee that a maintainer will merge a PR. The 20/20 result establishes agreement on these frozen packages, not correctness on every future PR.
