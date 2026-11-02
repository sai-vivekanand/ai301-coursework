# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

Where it lives:
In an eval package, read the candidate plan's diagnosis or explanation of the cause, then compare it with the Repro evidence section and the issue context. In live mode, read the diagnosis in plan.md, the reproduction evidence quoted in the plan, the student's posted reproduction comment on the issue thread, and the issue description when needed.

What good looks like:
The stated cause must explain behavior that the reproduction actually demonstrates. A diagnosis passes when it stays within the evidence instead of inventing a broader root cause simply because that explanation sounds plausible. If the reproduction establishes only a condition or correlation, the plan should not present a stronger causal claim as proven.

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

## Scope

Where it lives:
In an eval package, look at the candidate plan's scope statement, files or areas list, approach, and any explicit out-of-scope statements. Compare those with the issue context and the diagnosis. In live mode, use the scope, files, and approach sections in plan.md, together with the issue thread when it establishes limits or maintainer expectations.

What good looks like:
The plan names a bounded set of changes that directly address the diagnosed problem. Every file or area listed should have a clear reason to change, and the plan should avoid unrelated cleanup, speculative refactors, or expanding the issue beyond what the reproduction supports.

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

## Executability

Where it lives:
In an eval package, read the candidate plan's files or areas section, implementation approach, and ordered work steps. In live mode, use the corresponding sections of plan.md.

What good looks like:
A stranger should be able to begin the work without asking the author what file to inspect, what behavior to change, or what sequence to follow. The plan does not need line-by-line implementation detail, but it should identify the affected file or bounded area and describe the intended change concretely enough to execute.

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

## Test plan

Where it lives:
In an eval package, compare the candidate plan's test plan with the Repro evidence block, especially the command, input, observed failure, and artifacts that demonstrated the bug. In live mode, compare the test section in plan.md with the student's posted reproduction evidence and any quoted before-state evidence in the plan.

What good looks like:
The test plan reruns the original reproduction or an equivalent check through the real affected code and states an observable expected result after the fix. A decisive test should make it possible to distinguish "the bug still exists" from "the bug is fixed." Statements such as "run tests" or "verify the fix" without a specific check and expected result are not enough.

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

## Honesty

Where it lives:
In an eval package, read the plan's risks, unknowns, assumptions, and deviations section if present. Also compare confident claims in the diagnosis and approach against the reproduction evidence. In live mode, use the Risks/Unknowns and Deviations sections of plan.md, along with the rest of the plan and the issue thread.

What good looks like:
The plan distinguishes demonstrated facts from things that are still uncertain. Known risks or unresolved questions should be stated rather than hidden behind false confidence. If implementation later differs from the posted plan, the deviation should say what changed and why instead of silently rewriting the history.

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

## Comms

Where it lives:
In an eval package, read the candidate plan comment and compare it with the issue context, thread highlights, and repo-facts block, including templates, CONTRIBUTING requirements, and any AI-use disclosure rules. In live mode, compare comment.md with the GitHub issue thread, the full plan.md, the repository's contribution documentation, and any applicable communication or AI-disclosure requirements.

What good looks like:
The comment should be specific to the issue and accurately summarize the plan's diagnosis, scope, and verification approach without adding unsupported claims or guarantees. It should respond to relevant maintainer signals in the thread and follow repository requirements that apply to issue comments. Boilerplate that could be pasted onto any issue, silent scope expansion, or missing required disclosure should not pass.

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->
