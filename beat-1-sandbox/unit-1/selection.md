# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**
https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
  Two things to know before you start:
  - Someone is ahead of you. nancyAfycodes posted a claim, a reproduction, and a plan with a named
    branch (fix/71-heading-fixture-indent), the last on 2026-10-02. Your PR may land second. That
    doesn't count against you here, since credit goes to the PR you open, not whether it merges.
  - CI may need a maintainer's go-ahead. docs/CONTRIBUTING.md says a first PR from a new contributor
    waits for a maintainer to approve the CI run. The markers are strict=True, so leaving the xfail
    marker in place will fail CI once your fix makes the test pass.

  It also fits your profile well: Python, a test fixture, and practice with a codebase you haven't
  worked in.

  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71",
    "checks": [
      {"name": "Repository activity", "grade": "pass", "evidence": "Last default-branch commit
  2026-09-16 (16 days ago); no releases, but a commit within 12 months satisfies the check."},
      {"name": "Maintainer responsiveness", "grade": "pass", "evidence": "Issue opened by Aburke225 
  (author_association COLLABORATOR), who also authored the last 5 default-branch commits."},
      {"name": "Scope fit", "grade": "pass", "evidence": "Single bounded fix: remove 8-space fixture 
  indentation and xfail marker H-04 in tests/unit/test_readme_parser.py; est. 1-2 hours; no TBDs or 
  core-internals warning."},
      {"name": "Work availability", "grade": "pass", "evidence": "No assignees, no linked or open PR for
  #71; nancyAfycodes' claim comments are classmate claims, which the Path Review house rule says do not
  block."},
      {"name": "Contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template
  are silent on AI use."}
    ],
    "verdict": "accept"
  }
  
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**
# eval run written by run_eval.py at 2026-10-02T05:17:19Z
# model: sonnet (pinned)
# graded: /Users/sai_vivek_vangala/.claude/skills/issue-select
# packages: 20 scored
#   rubric.md  sha256:c9c809c137731858
#   SKILL.md  sha256:bbb295bf984701fd
#
grading 20 bundle(s) with rubric.md, model sonnet, 5 worker(s)...
  issue-02: reject
  issue-04: accept
  issue-01: accept
  issue-05: reject
  issue-06: accept
  issue-03: reject
  issue-07: reject
  issue-09: accept
  issue-11: accept
  issue-08: reject
  issue-10: reject
  issue-13: reject
  issue-14: accept
  issue-15: reject
  issue-16: accept
  issue-12: reject
  issue-17: reject
  issue-18: reject
  issue-19: accept
  issue-20: reject

item      gold    verdict  agree  note
issue-01  accept  accept   yes    
issue-02  reject  reject   yes    
issue-03  reject  reject   yes    
issue-04  accept  accept   yes    
issue-05  reject  reject   yes    
issue-06  accept  accept   yes    
issue-07  reject  reject   yes    
issue-08  reject  reject   yes    
issue-09  accept  accept   yes    
issue-10  reject  reject   yes    
issue-11  accept  accept   yes    
issue-12  reject  reject   yes    
issue-13  reject  reject   yes    
issue-14  accept  accept   yes    
issue-15  reject  reject   yes    
issue-16  accept  accept   yes    
issue-17  reject  reject   yes    
issue-18  reject  reject   yes    
issue-19  accept  accept   yes    
issue-20  reject  reject   yes    

categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 4/4
agreement: 20/20 scored items  (bar: 18/20: PASS)

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

**Issue analysis**
"issue-12 reject accept NO graded accept" was a disagreement in my first full run. My rubric returned accept, while the gold label was reject. The issue passed activity, maintainer, scope, and availability checks, but BookWyrm's contribution policy explicitly said it does not accept AI-generated code or documentation. My original policy check was too vague to reliably catch that distinction, so I revised it to reject explicit AI bans while allowing policies that permit AI subject to conditions such as disclosure, testing, or human review.
[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`

issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

**Check rationale**
| Contribution policy | Repo-facts contribution-policy field, including any AI/tooling policy | Fail if the repository explicitly bans AI-generated or AI-assisted code/documentation that this course workflow would produce. Pass if the policy is silent on AI, explicitly allows AI, or allows it subject to conditions such as disclosure, testing, human review, or personally understanding the contribution; those conditions must be followed but are not themselves a reason to reject the issue. | required |

I made this check explicit after issue-12 passed my initial rubric incorrectly. The important distinction is between a repository that prohibits the AI-assisted workflow entirely and a repository that allows it with conditions. I did not want disclosure or human-review requirements to reject otherwise valid issues.

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

**Trade-offs**
This check intentionally gives up otherwise good issues when the repository explicitly prohibits the AI-assisted contribution workflow. Issue-12 is the concrete example: it passes the liveness, scope, and availability checks but is still rejected because of the repository policy. The rule does not reject repositories that merely require disclosure, testing, or human review.

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

---

## Selection rationale
Issue #71 fits my interests and available time because it is a Python/testing problem with an estimated effort of 1–2 hours. The failure is narrow and reproducible, which makes it a good issue for learning the contribution workflow without spending most of the time discovering the scope.

The rubric correctly identified that the repository is active, the issue is bounded, there is no blocking open PR, and the contribution policy permits the workflow. Outside the rubric, I preferred #71 over the accepted documentation/config issue because I wanted a bug with an observable failing test that I could independently reproduce.

I expect claiming it to be straightforward because the issue identifies the failing test, relevant files, and expected correction. Another student has already claimed and reproduced it, but the Path Review house rule explicitly allows multiple students to work on the same issue, so I still need to produce my own claim and independent reproduction in Unit 2.

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
