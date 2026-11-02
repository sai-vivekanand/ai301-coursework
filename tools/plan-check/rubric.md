# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis supported by reproduction | Repro evidence, issue description, and plan diagnosis | The plan's claimed cause must be supported by the reproduced behavior. It must not introduce a root cause that the reproduction does not establish. If the reproduction only proves a narrower condition, the diagnosis must stay within that evidence. | required |
| Scope matches diagnosis | Plan scope, files list, approach, issue description, and repro evidence | Every planned code or test change must directly address the diagnosed cause or be necessary to verify the fix. The plan must identify what it will change and avoid unrelated cleanup or expansion. | required |
| Test plan proves the fix | Repro evidence and plan test section | The plan must rerun the reproduced failure, or an equivalent test through the real affected code, and state an observable expected result that distinguishes fixed from still broken. | required |
| Files and approach are concrete | Plan files list and approach | The plan identifies the file or bounded area it intends to change and describes enough of the approach that a maintainer can understand what will change without requiring implementation details that cannot yet be known. | required |
| Comment and repository conventions | Draft plan comment, issue thread, repository contribution rules | The plan comment is specific to the issue, accurately represents the plan, does not promise unsupported outcomes or deadlines, and follows applicable repository communication requirements. | required |

## Verdict rule

Return `accept` only when every required check passes.

A failed required check means `reject`.

An `unclear` result on a required check also means `reject`, because missing or ambiguous evidence is not enough to establish that a plan is ready to post.

Preferred checks, if any are added later, do not change the final verdict.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->
