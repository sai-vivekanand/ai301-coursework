# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

Eval: read Plan context (repro, scope, exclusions, test plan, deviations) alongside Candidate PR's Diff, Commits, Title, and Description. Live: use plan.md including Deviations, git diff main...HEAD, git log main..HEAD --oneline, and pr_draft.md; compare with the student's posted plan on the issue thread.

Good evidence maps actual changes and omissions in both directions. A documented deviation states what changed and why, and the description accurately represents the delivered result. An honestly disclosed bounded shortfall differs from a claim of full fidelity contradicted by the patch. Do not demand a particular heading in eval bundles when the same information is explicitly supplied elsewhere.

## Test evidence (harness category: not-tested)

Eval: compare Plan context's repro and Test plan to Candidate PR's Test evidence and Description; read required check names in Repo facts. Live: test_evidence.md contains captured commands and outputs, plan.md supplies the intended proof, the issue thread supplies prior reproduction, and the PR template/CONTRIBUTING supply required checks. pr_draft.md must accurately report those results.

Good evidence shows observable before/after behavior or a directly equivalent exercised regression, with actual branch results and repository check outcomes. A command and meaningful result can suffice without an entire terminal transcript. A narrow config-only change does not require an invented full suite if the repository specifies none. Failures and no-tests-collected outcomes can be honest evidence when explicitly identified with their reason and limits. A claim that tests pass without evidence, a skipped required check with no explanation, or future-tense testing does not establish a run.

## Diff quality (harness category: unreviewable)

Eval: Candidate PR's unified Diff and Commits, compared with plan scope and issue. Live: complete git diff main...HEAD and commit list. The file stat is useful inventory but never substitutes for inspecting hunks.

Good changes keep the fix and necessary tests visible, without debug remnants, commented-out alternatives, dead code, unrelated refactors, or broad cosmetic churn. Necessary test fixtures are legitimate changes; disclosed unrelated cleanup is still unrelated. Judge purpose, not raw size or commit count.

## Standards and comms (harness category: standards-wall)

Eval: Repo facts states PR-template asks and contribution/AI policy; Thread highlights supplies explicit maintainer direction. Compare these with Candidate PR's title and description. Live: inspect .github/PULL_REQUEST_TEMPLATE.md, docs/CONTRIBUTING.md, referenced policies, scope.md, and the issue thread; check pr_draft.md and voice-guide.md. Path Review's course always requires an AI tool-and-extent statement in Notes for Reviewers.

Good text fills the applicable template with specific content, addresses relevant requests, and gives required disclosure. N/A needs a reason when a section does not apply. Do not impose personal voice rules or the classroom AI rule on eval bundles. CI not yet run before PR creation must remain unticked; it is not missing local-test evidence. Whether description claims match the patch belongs to plan fidelity.
