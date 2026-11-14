# Contribution: Add usage examples to mm tags --help

**Contribution Number:** [1]
**Student:** Sai Vivekanand Reddy Vangala
**GitHub Username:** sai-vivekanand
**Issue:** https://github.com/memtomem/memtomem/issues/3049
**Pull Request:** https://github.com/memtomem/memtomem/pull/3356

---

## Toolkit

Toolkit example retained from the course template:

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

**Unit 5: Adapting issue-scout to a Python CLI contribution**

2026-11-13: I configured the scout around Python, developer tools and small testable changes, using my earlier rubric and a broad-search strategy. I used direct grading on memtomem #3049 and #3050; both were accepted as straightforward, and I chose #3049. I then ran the full two-query funnel: 200 returned results became 165 unassigned recent survivors and five graded candidates, all accepted. Four came from one repository, so I would add repository diversity and use whole-word keyword matching in a future strategy revision.

**Unit 6: Guarding my claim and recording repository context**

2026-11-13: I installed the voice guard with an Upstream section covering claims, questions and pings, and added a local repository memory file with commands, conventions and the issue context. The wiring test blocked a comment with no body, and the real claim passed before posting. A Claude command initially consumed the prompt as part of its allowed-tools argument; separating the prompt with `--` fixed it, and an explicit Python interpreter avoided the older environment's startup problem.

**Unit 7: A ship-gate with an honest baseline exclusion**

2026-11-13: I installed the ship-gate and wrote a manifest using the issue's focused tests, broader CLI/tag/docs tests and the repository's Ruff commands. The gate passed all four runnable checks and accepted the PR package; the full baseline suite's Git-version failure is explicitly excluded and disclosed. The hook summary initially showed only one stop although both logs recorded it, and the PR review caught an output excerpt whose indentation had been normalized, so I checked the logs and corrected the excerpt before rerunning the gate.

**Unit 8: Checking the monitor against the actual PR thread**

2026-11-14: I installed the PR monitor and wrote a four-section playbook using the repository's response windows and five recent outside-contributor PRs. It classified the CLA bot's comment as FEEDBACK-IN, but its drafted move correctly said there was no review response to post and that the agreement required my own action; I kept the wait note local. The aggregate check count did not identify the failure, so I inspected the named GitHub checks and confirmed it was the unsigned CLA, then recorded human feedback as none yet rather than calling the bot message a review.

---

## Why I Chose This Issue

I found this issue through the course issue-selection site while looking for a small Python developer-tool contribution. I wanted a problem with a visible before-and-after result and tests I could run locally. The scout directly graded memtomem #3049 (tags help) and #3050 (pinned help), accepted both and rated both straightforward. I chose #3049 because the change is bounded to CLI help and its tests, fits my Python/testing interests, and gives me a chance to work through a real repository's review process.

The issue was created November 3, rather than being a years-old report. Before claiming it I read the thread, checked for a competing claim or PR, and read CONTRIBUTING.md. The repository states a five-business-day first-response target; that is a target, not a promise of a response or merge. The scout's verdict was useful evidence, but I still had to check ownership, repository activity and the current code myself. I changed the old Scope fit check to scope-feasible and added difficulty notes so real issues would not be rejected just for omitting sandbox-style detail.

Claim: https://github.com/memtomem/memtomem/issues/3049#issuecomment-6862609202

**Toolkit**

- Tool: issue-scout, used in direct-grade mode on #3049 and #3050 with my Python-focused profile and the patched rubric.
- What it produced: accept and straightforward for both; #3049 ranked first.
- Difficulties: direct grading does not establish availability or guarantee maintainer responsiveness; the later broad scan concentrated four of five results in one repository and ranked a one-day-old repository first.
- What changed: replaced Scope fit with scope-feasible, added the non-gating difficulty note, and recorded the dated patch in scan-notes.md.

---

## Understanding the Issue

**Problem Description**

The top-level tags help lists the subcommands but gives no copyable usage examples. It also omits the safety relationship between preview, --apply and --yes.

**Expected Behavior**

`mm tags --help` should show five examples covering list, preview rename, applied rename, merge and noninteractive delete, plus the note explaining that mutations preview by default and --yes requires --apply.

**Current Behavior**

The command exits 0 and shows the description, help option and four subcommands. There is no Examples block or safety note.

**Affected Components**

`packages/memtomem/src/memtomem/cli/tags_cmd.py` defines the Click group. `packages/memtomem/tests/test_cli.py::TestHelpEpilog` checks rendered help. Tag services and command behavior do not need modification.

**Toolkit**

- Tool: repository inspection and repro-check, used to connect observed help output to the Click group and existing tests.
- What it produced: a diagnosis of missing epilog text, supported by captured output and the group decorator.
- Difficulties: the issue quotes older test context; the current width loop already covers recall and index too.
- What changed: preserve all existing commands when adding tags to that loop.

---

## Reproduction Process

**Environment Setup**

macOS 15.3.2 on Apple Silicon; Python 3.13.3; uv 0.13.8; memtomem 0.7.8. The baseline is upstream commit `ee619385f2f9f9997d092a72ac79a9039bad4b09`. I cloned the repository and ran `uv sync --python /opt/homebrew/bin/python3.13`. uv was installed in a separate local tooling environment, so my commands use its full executable path. Other machines can use any supported Python 3.12+ interpreter. Help output does not require a configured model or database.

**Steps to Reproduce**

1. Clone `https://github.com/memtomem/memtomem.git`, enter it, and check out `ee619385f2f9f9997d092a72ac79a9039bad4b09`.
2. Run `uv sync` with a supported Python interpreter.
3. Run `uv run mm tags --help`. It exits successfully but has no examples or explanation of the relationship between `--apply` and `--yes`.
4. Run `uv run pytest packages/memtomem/tests/test_cli.py::TestHelpEpilog -q`: the existing six tests pass because none checks tags help.

**Reproduction Evidence**

- **Commit showing reproduction:** none; this is a command-output reproduction on the baseline commit above.
- **Screenshots/logs:** captured terminal output:

```text
Usage: mm tags [OPTIONS] COMMAND [ARGS]...

  Manage tags: list, rename, delete, or merge them across all chunks.

Options:
  -h, --help  Show this message and exit.

Commands:
  delete  Remove NAME from every visible chunk that carries it (the...
  list    List visible tags and their chunk counts, most frequent first.
  merge   Fold one or more SOURCES tags into --into TARGET across all...
  rename  Rename OLD_TAG to NEW_TAG across every visible chunk that...
```

- **My findings:** this is a missing-help problem, not a crash or an incorrect tag mutation. Existing tests passing does not cover the missing behavior. Baseline focused result: `6 passed in 0.30s`.

**Toolkit**

- Tool: repro-check, run against the claim and local reproduction draft using the real-repository scope.
- What it produced: accept; all five required checks passed, including followable reproduction and outcome honesty.
- Difficulties: the issue is a documentation omission, so a successful command exit alone cannot demonstrate the expected behavior.
- What changed: recorded the actual output and explicitly distinguished missing help from runtime failure; kept the report local rather than posting it to the issue.

---

## Solution Approach

**Analysis**

At upstream ee619385f2f9f9997d092a72ac79a9039bad4b09, `uv run mm tags --help` exits 0 but has no Examples block or --apply/--yes explanation. The tags group in packages/memtomem/src/memtomem/cli/tags_cmd.py has only a docstring and no epilog. The six existing TestHelpEpilog tests pass but do not cover tags. The Reproduction Process section above contains the captured evidence; repro-check accepted the local draft. This is a help-text omission, not a tag mutation defect.

**Proposed Solution**

Add a TAGS_EPILOG string and attach it to the existing Click group, matching the raw paragraph pattern in search.py. Show list, preview rename, applied rename, merge and noninteractive delete examples. Put the safety note outside the raw block: rename, merge and delete only preview until you add --apply; --yes needs --apply. Keep service logic, flags and other help unchanged.

**Implementation Plan**

1. Add a TestHelpEpilog test checking exit 0 and each complete example line, plus the whitespace-normalized safety note. Add tags to the existing 80-column loop without removing commands. Run it before implementation and save the expected failures.
2. Add TAGS_EPILOG with Click's backspace marker to preserve separate example lines; pass epilog=TAGS_EPILOG to the group.
3. Re-run the focused tests and mm tags --help. Run manifest tests, lint and format; compare any unrelated failures against unchanged main. Save before/after evidence in test_evidence.md.
4. Keep the PR to these two files, use Fixes #3049, disclose AI assistance, and run the ship-gate before opening it.

No implementation scope changes; the validation adjustment is recorded below. The existing width loop includes search, add, recall and index; preserve all four even though the issue quotes an older version. No reproduction report or plan comment will be posted upstream.

Review notes (2026-11-13): PR #3013 is still open; re-check before opening our PR and preserve both additions if it merges. The branch is codex/3049-tags-help. The manifest names the CI selection `pytest -m "not ollama and not llm"`, Ruff lint and Ruff format; it uses an absolute uv executable path. Local working files are excluded by the ship-gate installer. A separate voice review read the canonical guide and its symlink successfully and found no broken rule.

Validation adjustment (2026-11-13): the full baseline CI selection has one unrelated failure because Git 2.42.0 does not support worktree add --relative-paths and the test does not recognize its error spelling. Reproduced that test separately before the help implementation. Move the full check to the dated exclusion table and gate on the issue-named focused test, broader CLI/tags/docs tests and repository-wide Ruff checks. Disclose the baseline failure and that the full suite was not rerun after the help change. No code scope change.

**Toolkit**

- Tool: plan-check, run on the local plan and private comment against the accepted reproduction.
- What it produced: accept before implementation and accept after the validation adjustment.
- Difficulties: the first grader missed a valid voice-guide symlink; the full baseline run later revealed an unrelated Git-version failure.
- What changed: verified the canonical voice guide in a separate review, documented the baseline failure and updated the plan's validation scope. Neither the report nor the plan comment was posted upstream.

---

## Testing Strategy

I first captured `mm tags --help` without an Examples block. The new line-based example assertion and expanded width check then failed on the original implementation: **2 failed, 5 passed**. After adding TAGS_EPILOG, the same class passed: **7 passed**. The actual help now prints all five requested commands and wraps the safety note as prose while preserving each example line.

Broader verification: `uv run pytest packages/memtomem/tests/test_cli.py packages/memtomem/tests/test_tags_cmd.py packages/memtomem/tests/test_docs_guards.py -q` produced **347 passed, 1 warning**. Repository-wide Ruff lint passed and Ruff format reported **1188 files already formatted**, using the CI lint job's path list.

The full baseline selection `uv run pytest -m "not ollama and not llm" --tb=short -q` produced **1 failed, 22596 passed, 426 skipped, 46 deselected, 1 xfailed** in 1324.16 seconds. The failure was `test_worktree_written_with_relative_paths_is_excluded`: local Git 2.42.0 rejects `worktree add --relative-paths` with exit 129, and the test's skip check expects a different error spelling. Rerunning that test alone before the help implementation reproduced the failure. I recorded it in the manifest's dated exclusions; I did not change that unrelated test. The full suite was not rerun after the help change, and GitHub CI must be distinguished from these local results.

**Toolkit**

- Tool: pytest, Ruff, captured CLI output and the ship manifest.
- What it produced: before/after regression evidence, 347 passing related tests, repository-wide lint/format passes and a documented baseline failure.
- Difficulties: the full baseline took about 22 minutes and failed on an unsupported Git option unrelated to the help text.
- What changed: used the issue's focused test plus broader CLI/tag/docs coverage for the runnable gate checks, disclosed the full-suite limitation and regraded the updated plan.

---

## Implementation Notes

**2026-11-13**

Claimed #3049 after checking availability and reserved it on the course site. Reproduced the missing help at ee61938 and saved the output. The six existing help tests passed, demonstrating that the missing tags coverage was not caught.

**2026-11-13**

Installed the ship-gate and created a manifest from CI. Both guard logs recorded the expected wiring-test stop, although Claude summarized only one. Plan-check accepted the two-file approach. On branch codex/3049-tags-help, the new example test and expanded width test fail before the implementation: 2 failed, 5 passed. The formatter also caught a wrapping change in the new assertion; I applied the repository formatter.

**2026-11-13**

Added TAGS_EPILOG using the existing raw-paragraph convention and committed the two-file change as `8f8dded`. The help regression went from two failures to seven passes, and the broader CLI/tag/docs run passed 347 tests. Recorded the full-suite baseline Git failure rather than expanding this PR into worktree behavior.

**2026-11-14**

Opened upstream PR #3356 through Claude Code after both guards passed. Ran the installed monitor in state and drafting modes. Its wait note stayed local because there was only a CLA bot request, with no human review to answer. Recorded the PR link and actual status in this story.

**Toolkit**

- Tool: pytest, Ruff and the course plan-check/ship-gate workflow.
- What it produced: an accepted plan and regression failures tied directly to missing examples.
- Difficulties: a tool summary omitted one hook stop; the first uv test invocation was blocked from its cache by the execution sandbox.
- What changed: verified the actual hook logs and reran tests with the required filesystem permission instead of treating setup failure as a product defect.

---

## Pull Request

**PR Link:** https://github.com/memtomem/memtomem/pull/3356

**PR Description:** The PR adds five tags help examples and the preview/apply/yes safety note, with tests for complete example lines, the normalized prose note and terminal width. It includes Fixes #3049, the before/after evidence, 7 passing help tests, 347 passing related tests and repository-wide Ruff results. It explicitly discloses the unrelated full-baseline Git failure, the absence of a post-change full-suite rerun and the extent of Codex/Claude assistance. The repository's template is preserved, with web changes marked N/A and the CLA left pending the contributor's own signature.

**Maintainer Feedback:**

- 2026-11-14: none yet from a human maintainer. The [CLA bot](https://github.com/memtomem/memtomem/pull/3356#issuecomment-6877750433) requested a signature; the failing status is `CLA / PR #3356`. No review response was posted. The author must read and, if they agree, sign the CLA personally.

**Status:** Awaiting review

At the recorded check, the PR was open and mergeable but behind main, with REVIEW_REQUIRED. GitHub's main test workflow had not reported results. A merge is not required to submit this assignment, and these facts do not imply that CI passed.

**Toolkit**

- Tool: ship-gate and pr-precheck, followed by Claude Code's guarded `gh pr create`.
- What it produced: PASS for the four runnable manifest checks and all four PR rubric checks; PR #3356 opened against memtomem/memtomem. The final opening hook reran the gate on November 14 and passed; voice-guard also logged pass.
- Difficulties: one unrelated baseline failure required an explicit exclusion, and the first description excerpt normalized indentation rather than preserving captured output.
- What changed: disclosed the baseline limitation, corrected the excerpt, reran the gate and kept the CLA checkbox pending personal action. No local plan, manifest, evidence draft or memory file entered the upstream diff.

---

## Learnings and Reflections

**Technical Skills Gained**

This change taught me how Click formats help epilogs: ordinary prose wraps, while a raw paragraph marked with `\b` preserves the example lines. A substring assertion would miss an epilog flattened into one paragraph, so the regression test compares complete output lines and separately normalizes whitespace for the prose note. It also checks the rendered width rather than just the source string length.

**Challenges Overcome**

The issue quoted an older version of the test class, so I checked the current code and preserved the newer recall and index coverage. Tool output also needed checking: one hook summary omitted a guard that had logged its stop, and a plan grader missed a valid voice-guide symlink. Reading the underlying logs and guide resolved those discrepancies instead of changing working configuration unnecessarily.

**What I'd Do Differently Next Time**

I would run the broad scout scan earlier and make its ranking more diverse across repositories. I would also estimate the full test suite's runtime before starting it, while still keeping a small regression test that demonstrates the issue directly. A recent issue and a responsive repository improve the chance of useful feedback, but neither guarantees a merge; the contribution needs clear evidence regardless of the outcome.

---

## Resources Used

- [Issue #3049](https://github.com/memtomem/memtomem/issues/3049): the requested examples, safety note, two-file scope and overlapping-PR warning.
- [CONTRIBUTING.md](https://github.com/memtomem/memtomem/blob/main/CONTRIBUTING.md): setup, checks, PR template expectations and response windows.
- [Search help implementation](https://github.com/memtomem/memtomem/blob/ee619385f2f9f9997d092a72ac79a9039bad4b09/packages/memtomem/src/memtomem/cli/search.py): the existing raw-paragraph epilog pattern.
- [Existing CLI tests](https://github.com/memtomem/memtomem/blob/ee619385f2f9f9997d092a72ac79a9039bad4b09/packages/memtomem/tests/test_cli.py): line-based assertions and the width guard.
- [Unit 6 materials](https://github.com/codepath/ai301-unit6-starter), [Unit 7 materials](https://github.com/codepath/ai301-unit7-starter) and [Unit 8 materials](https://github.com/codepath/ai301-unit8-starter): guard installation, real-repository scopes, ship-gate and PR monitor.
- Codex helped inspect the repository, implement the change, run commands and draft this story. Claude Code ran the course grading tools and guarded GitHub commands. The presentation notes use this diff and the captured results as prompts for my own explanation.
