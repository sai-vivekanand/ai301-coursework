# Toolkit Portfolio

**Student:** Sai Vivekanand Reddy Vangala

This portfolio records the tools used during my AI301 work. The current Assignment 6 deliverables are `linkedin-post.md` and `technical-writeup.md` in this folder; this page is a supporting toolkit record, not a replacement for those files.

The course supplied the tool frameworks. My workflow used configured rubrics, strategies, communication rules, manifests and a playbook, with AI assistance in their preparation and use. Codex also assisted with this documentation. I do not claim to have independently implemented the underlying tools.

## Featured Tools

The four featured tools cover different decisions: which issue to investigate, what to say publicly, whether a PR is ready, and whether a response is needed. They are useful together because each checks a different part of the contribution process. Their results still need to be compared with the code, logs and actual GitHub thread.

### Issue scout

**What it is, and the judgment hole I wrote:** Issue-scout searches and grades candidate issues. Its configurable judgment comes from the fit profile, search strategy and rubric. My configuration favored Python, developer tools and bounded changes with observable tests. The strategy searched open Python issues carrying good-first-issue or help-wanted labels, removed assigned and older candidates, and ranked the remaining results before grading five.

**How it evolved, dated:** On November 13, 2026, the earlier issue-select setup was adapted into issue-scout. The old Scope fit check was replaced with the course's scope-feasible row, and non-gating difficulty notes were added. This allowed the rubric to consider real issues without expecting every sandbox detail. Direct grading compared memtomem #3049 and #3050. A later broad scan exposed a ranking weakness: four of its five candidates came from one repository, while a one-day-old repository ranked first. Repository diversity and whole-word keyword matching remain proposed improvements, not completed patches.

**Evidence:** The direct run accepted both candidates and marked both straightforward. Issue #3049 was selected and claimed. The full scan reported:

```text
Q1: 100 results
Q2: 100 results
After deduplication and filters: 165 survivors
Top candidates graded: 5
Verdicts: 5 accept
Four of five candidates: memtomem-stm
```

The scout's acceptance was followed by a separate check of the issue thread and contribution rules. The resulting claim is at https://github.com/memtomem/memtomem/issues/3049#issuecomment-6862609202. The scan did not establish a guarantee of maintainer responsiveness.

### Voice guard

**What it is, and the judgment hole I wrote:** The voice guard checks outgoing GitHub text against a voice guide. The guide defines communication rules such as separating observations from explanations, avoiding unsupported promises and stating validation limits. Its Upstream section adds rules for claims, questions and pings.

**How it evolved, dated:** On November 13, 2026, the Upstream section was added and the canonical guide was connected to the existing course skills. An explicit Python interpreter avoided the older environment's startup problem. A wiring test deliberately supplied no comment body and was blocked. The actual claim passed later that day. On November 14, the guard also passed the PR description. A separate plan grader initially missed the guide's symlink; reading the canonical file and symlink directly confirmed that the guide existed and found no broken rule in the private plan comment.

**Evidence:** Excerpts from the guard log:

```text
2026-11-13 14:16 [hook] stop: no body the guard can read
  target: gh issue comment --help
2026-11-13 14:19 [hook] pass
  target: gh issue comment .../issues/3049 --body-file
2026-11-14 08:09 [hook] pass
  target: gh pr create --title Add usage examples and safety note to tags help
```

The wiring test demonstrated an expected block; the real claim and PR demonstrated that acceptable text could pass. These results establish behavior in the tested command path, not universal coverage of every way to post on GitHub.

### Ship-gate

**What it is, and the judgment hole I wrote:** The ship-gate runs project checks and PR precheck before a PR opens. Its configurable manifest names the commands, their repository sources and any dated exclusions. The PR rubric checks whether the plan, diff, evidence and description agree.

**How it evolved, dated:** The first manifest, prepared November 13, 2026, included the full CI test selection, lint and formatting. The baseline run failed on an unrelated Git worktree test. A separate run reproduced the problem with Git 2.42.0, which rejected `--relative-paths`; the test's skip condition missed that error spelling. The revised manifest recorded the full check as a dated exclusion and required the focused help tests, broader CLI/tag/documentation tests, lint and formatting. The updated plan was regraded and accepted. The PR review also identified an excerpt whose indentation had been normalized; the description was corrected and the gate rerun. The opening hook passed again on November 14.

**Evidence:** The baseline result that drove the revision was:

```text
FAILED test_nested_worktree_exclusion.py::test_worktree_written_with_relative_paths_is_excluded
1 failed, 22596 passed, 426 skipped, 46 deselected, 1 xfailed
```

The revised manifest subsequently produced:

```text
ship-gate: repo check 1/4 `Help examples`: ok (3s)
ship-gate: repo check 2/4 `CLI and tag regression coverage`: ok (5s)
ship-gate: repo check 3/4 `Lint`: ok (0s)
ship-gate: repo check 4/4 `Format`: ok (0s)
ship-gate: PASS.
```

The after-change focused run passed seven tests, and the broader run passed 347. The full suite was not rerun locally after the help change. That limitation was disclosed in PR #3356; a gate pass did not turn the excluded baseline check into a pass.

### PR monitor

**What it is, and the judgment hole I wrote:** The monitor reads PR activity and drafts a possible next move into a local file. It does not post automatically. Its playbook defines response rules, waiting thresholds, nudge etiquette and walk-away criteria.

**How it evolved, dated:** The monitor and playbook were prepared during November 13–14, 2026, and the first PR runs took place November 14. The playbook used the repository's five-business-day first-response target and a sample of five recently merged outside-contributor PRs. It required waiting at least ten calendar days and seven business days before a first-review nudge. The first run classified the CLA bot comment as feedback, but the generated draft correctly recommended no review reply. The playbook did not undergo a second substantive revision during this run; its existing rules were sufficient to keep an unnecessary response off the thread.

**Evidence:** The monitor's output included:

```text
state: FEEDBACK-IN
review decision: REVIEW_REQUIRED
```

Its draft then distinguished the bot request from human review:

```text
MOVE: No review response to draft. The only thread item is the CLA bot's request, and signing is the author's own act.
```

The draft stayed local. The named GitHub checks were inspected separately to confirm that the failing status was the unsigned CLA. The five sampled first-response waits were approximately 0.48, 0.09, 3.82, 3.57 and 1.16 hours for PRs #3317, #3285, #3283, #3250 and #3249. That small sample of merged PRs did not override the documented response window.

## Inventory

- **Issue-select:** the original issue-grading skill from earlier coursework; its rubric and profile supplied the starting point for issue-scout.
- **Repro-check:** checks environment details, reproducible steps, observed behavior and honest claims. It accepted the #3049 claim and local reproduction report; that report was not posted upstream.
- **Plan-check:** checks diagnosis, scope, verification and implementation specificity. The Unit 3 evaluation achieved 18/20 agreement, with false rejections on pkg-02 and pkg-14. For #3049, it accepted both the initial plan and the documented validation adjustment.
- **PR precheck:** evaluates whether the committed diff, description, tests and repository requirements agree. It passed all four rubric checks for #3356 as part of the ship-gate.
- **Repository memory file:** local `CLAUDE.local.md` records project commands, conventions and issue context. It is excluded from the upstream contribution.
- **pytest:** runs regression and broader tests. It demonstrated two failures before the help implementation, seven focused passes afterward and 347 broader passes.
- **Ruff:** checks code style and formatting. Repository-wide checks passed; formatting reported 1,188 files already formatted.
- **uv and the project virtual environment:** provide the project's Python dependencies and command environment. The tooling uses an explicit uv path rather than assuming an activated global environment.
- **Git and GitHub CLI:** record changes, inspect issues and reviews, push the fork branch and open the upstream PR. The contribution commit is `8f8ddedb8c26f6e6d5089d0375803058b6062e3f`.
- **Codex and Claude Code:** provided implementation and documentation assistance and executed the configured course workflows. Their summaries were checked against underlying evidence when discrepancies appeared.

## The Arc

**Beat 1**

Date: 2026-11-02
Friction: Plan evaluation required explicit rules and an executable procedure rather than informal judgments about whether a plan looked reasonable.
Change: The completed plan-check rubric, evidence guide and procedure were evaluated and committed alongside the Unit 3 work in commit 26713d5.
Result: The final complete evaluation recorded 18/20 agreement; pkg-02 and pkg-14 exposed the cost of strict required checks.

**Beat 2**

Date: 2026-11-13
Friction: Real issues did not consistently contain the tidy scope information available in sandbox exercises.
Change: The scout's Scope fit row was replaced with scope-feasible, and difficulty notes were added before grading the two real candidates.
Result: Both #3049 and #3050 were accepted as straightforward; #3049 was independently checked for availability and claimed.

**Beat 3**

Date: 2026-11-13
Friction: Outgoing claims needed to follow the voice guide, and the installation needed observable proof that the guard actually ran.
Change: Added Upstream communication rules, installed the hook and ran a deliberately incomplete comment command as a wiring test.
Result: The missing-body command was blocked; the actual issue claim later passed and was posted.

**Beat 4**

Date: 2026-11-13
Friction: The full baseline test selection failed on a Git-version incompatibility unrelated to the help change.
Change: Reproduced the failing test separately, recorded a dated manifest exclusion, revised the validation plan and disclosed the missing post-change full-suite run.
Result: The updated plan-check accepted the adjustment, and the four runnable ship-gate checks passed. The PR description retained the limitation.

**Beat 5**

Date: 2026-11-13 to 2026-11-14
Friction: The initial PR description normalized the indentation of the captured help output.
Change: Replaced that excerpt with the actual captured indentation and reran the gate before opening the PR through Claude Code.
Result: The final description passed the gate and voice guard; upstream PR #3356 opened on November 14.

**Beat 6**

Date: 2026-11-14
Friction: The monitor's feedback classification included a CLA bot request, which could be mistaken for a human review requiring a reply.
Change: Compared the draft with the real thread and named checks, applying the playbook's rules about bot comments and personal agreement signatures.
Result: The wait note remained local, and no unnecessary response or automated signature was posted.

**Beat 7**

Date: 2026-11-18 verification of November 14 activity
Friction: The original contribution record said there was no human review and CI had not yet reported, so that snapshot was no longer sufficient for the portfolio.
Change: Read the live review record and named CI results before preparing the audience-specific portfolio pieces.
Result: Verified an APPROVED review from collaborator pandas-studio and successful main CI checks, including Ubuntu, macOS and Windows tests. The PR remained open and unmerged, with the CLA unsigned.

## Limitations and What's Next

The toolkit helps organize evidence and catch inconsistencies, but it does not establish truth merely by returning accept or PASS. Its judgments depend on the rubric, available context and command coverage. A model can miss a symlink, summarize only one of two hook stops, or treat a bot comment as feedback. The response is to inspect the underlying artifact when the distinction matters.

The next improvements are to diversify scout results across repositories, replace substring ranking with whole-word matching, and make named check failures easier to see in monitor reports. The local environment also needs a Git version supporting the worktree test's required option before that validation gap can be closed. These are proposed next steps, not changes already completed.

The PR still requires the contributor's own decision about the agreement and any further response requested by reviewers. Review approval, CI success and merge are separate states. Neither a course deadline nor a tool-generated suggestion justifies claiming a merge that has not happened.

**Tool limits.**

issue-scout: A recent owner commit and an accept verdict do not prove responsiveness, availability or suitability; the current ranking can over-concentrate one repository.
voice-guard: It checks the configured outgoing-command path and wording rules; it cannot guarantee factual accuracy or inspect every browser-posted message automatically.
ship-gate: A pass covers the configured runnable checks and disclosed exclusions, not every possible defect or every environment; the full post-change local suite was not run.
pr-monitor: Aggregate status can obscure the failing check, and bot activity can trigger a feedback classification; drafts need human comparison with the thread and must not sign agreements for the author.
