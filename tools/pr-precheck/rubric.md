# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan and claims match the diff | Plan context scope, test plan, and deviations; candidate diff and commits; PR title and description; issue and repro evidence | Every substantive change and omission is within the plan or explained by an explicit deviation with its reason. The title and description accurately state what the diff delivers and what remains undone. An honestly disclosed, bounded shortfall can pass; silently doing more or less, or claiming an outcome contradicted by the diff, fails. | required |
| Observable testing and repository checks | Plan test plan and repro steps compared with candidate test-evidence commands, observed output, and description; repo-facts required checks | Evidence shows the reproduced behavior exercised on the change with a concrete observed result and an expected result that distinguishes fixed from broken, plus outcomes of the repository's stated checks. A failed check or limited outcome may pass when its actual result, reason, and limit are disclosed without claiming success. A justified inapplicable check may be identified as such. Bare assurances, proposed future tests, or silently omitted required checks fail; absent requirements must not be invented. | required |
| Focused and reviewable diff | Unified diff and commit list compared with issue scope, plan, and deviations | The fix is inspectable without unrelated changes or debris: no leftover debug output, dead or commented-out implementation, unrelated refactors, or gratuitous formatting churn. Necessary supporting edits and regression tests are allowed. Explaining an unrelated change does not make it necessary. Do not reject based on commit count or patch length alone. | required |
| Repository standards and disclosure | Repo-facts PR template and contribution/AI policy; issue thread instructions; draft title and description; live scope rules | All applicable template sections and stated contribution/disclosure asks have substantive answers, and relevant maintainer instructions are addressed. N/A with a reason is acceptable for inapplicable sections. Disclose AI tool and extent when required; in live Path Review mode the course always requires this in Notes for Reviewers. Do not invent an AI rule for an eval repository with none. Pending CI before opening is not a failure if accurately left pending. | required |

## Verdict rule

Return `accept` only if every required check is pass. Any required fail or unclear yields `reject`. Preferred checks never change the verdict. Report honestly disclosed limitations in the evidence; do not convert them automatically into failure when the relevant pass condition allows them.
