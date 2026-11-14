# Contribution: Add usage examples to mm tags --help

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Sai Vivekanand Reddy Vangala
**GitHub Username:** sai-vivekanand
**Issue:** https://github.com/memtomem/memtomem/issues/3049
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Adapting issue-scout to a Python CLI contribution**

2026-11-13: I configured the scout around Python, developer tools and small testable changes, using my earlier rubric and a broad-search strategy. I used direct grading on memtomem #3049 and #3050; both were accepted as straightforward, and I chose #3049. Direct grading helped compare the candidates, but it is not a completed top-five scan, and I still need that scan for the Unit 5 tool exercise.

**Unit 6: Guarding my claim and recording repository context**

2026-11-13: I installed the voice guard with an Upstream section covering claims, questions and pings, and added a local repository memory file with commands, conventions and the issue context. The wiring test blocked a comment with no body, and the real claim passed before posting. A Claude command initially consumed the prompt as part of its allowed-tools argument; separating the prompt with `--` fixed it, and an explicit Python interpreter avoided the older environment's startup problem.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I found this issue through the course issue-selection site while looking for a small Python developer-tool contribution. I wanted a problem with a visible before-and-after result and tests I could run locally. The scout directly graded memtomem #3049 (tags help) and #3050 (pinned help), accepted both and rated both straightforward. I chose #3049 because the change is bounded to CLI help and its tests, fits my Python/testing interests, and gives me a chance to work through a real repository's review process.

The issue was created November 3, rather than being a years-old report. Before claiming it I read the thread, checked for a competing claim or PR, and read CONTRIBUTING.md. The repository states a five-business-day first-response target; that is a target, not a promise of a response or merge. The scout's verdict was useful evidence, but I still had to check ownership, repository activity and the current code myself. I changed the old Scope fit check to scope-feasible and added difficulty notes so real issues would not be rejected just for omitting sandbox-style detail.

Claim: https://github.com/memtomem/memtomem/issues/3049#issuecomment-6862609202

**Toolkit**

- Tool: issue-scout, used in direct-grade mode on #3049 and #3050 with my Python-focused profile and the patched rubric.
- What it produced: accept and straightforward for both; #3049 ranked first.
- Difficulties: direct grading does not establish availability or guarantee maintainer responsiveness, and I have not yet completed the broad top-five scan.
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

At upstream ee619385f2f9f9997d092a72ac79a9039bad4b09, `uv run mm tags --help` exits 0 but has no Examples block or --apply/--yes explanation. The tags group in packages/memtomem/src/memtomem/cli/tags_cmd.py has only a docstring and no epilog. The six existing TestHelpEpilog tests pass but do not cover tags. Full local evidence is ../unit6/repro-draft.md; repro-check accepted it. This is a help-text omission, not a tag mutation defect.

**Proposed Solution**

Add a TAGS_EPILOG string and attach it to the existing Click group, matching the raw paragraph pattern in search.py. Show list, preview rename, applied rename, merge and noninteractive delete examples. Put the safety note outside the raw block: rename, merge and delete only preview until you add --apply; --yes needs --apply. Keep service logic, flags and other help unchanged.

**Implementation Plan**

1. Add a TestHelpEpilog test checking exit 0 and each complete example line, plus the whitespace-normalized safety note. Add tags to the existing 80-column loop without removing commands. Run it before implementation and save the expected failures.
2. Add TAGS_EPILOG with Click's backspace marker to preserve separate example lines; pass epilog=TAGS_EPILOG to the group.
3. Re-run the focused tests and mm tags --help. Run manifest tests, lint and format; compare any unrelated failures against unchanged main. Save before/after evidence in test_evidence.md.
4. Keep the PR to these two files, use Fixes #3049, disclose AI assistance, and run the ship-gate before opening it.

No deviations so far. Existing width loop includes search, add, recall and index; preserve all four even though the issue quotes an older version. No reproduction report or plan comment will be posted upstream.

**Toolkit**

- Tool: plan-check, used on plan.md and a private plan-comment.md with the accepted local reproduction.
- What it produced: accept with all five required checks passing.
- Difficulties: the grader reported the voice guide missing even though the installed path is a valid symlink; its required rubric verdict passed, but that voice review needs checking against the canonical file. It also identified the risk of overlapping work in PR #3013.
- What changed: kept local evidence excluded from commits and will check upstream changes before opening the PR. The plan comment remains local as the course requires.

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

**2026-11-13**

Claimed #3049 after checking availability and reserved it on the course site. Reproduced the missing help at ee61938 and saved the output. The six existing help tests passed, demonstrating that the missing tags coverage was not caught.

**2026-11-13**

Installed the ship-gate and created a manifest from CI. Both guard logs recorded the expected wiring-test stop, although Claude summarized only one. Plan-check accepted the two-file approach. On branch codex/3049-tags-help, the new example test and expanded width test fail before the implementation: 2 failed, 5 passed. The formatter also caught a wrapping change in the new assertion; I applied the repository formatter.

**Toolkit**

- Tool: pytest, Ruff and the course plan-check/ship-gate workflow.
- What it produced: an accepted plan and regression failures tied directly to missing examples.
- Difficulties: a tool summary omitted one hook stop; the first uv test invocation was blocked from its cache by the execution sandbox.
- What changed: verified the actual hook logs and reran tests with the required filesystem permission instead of treating setup failure as a product defect.

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
