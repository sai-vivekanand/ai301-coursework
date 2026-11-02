# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

# Procedure

## Read order

1. Read the issue description first to identify the reported behavior, stated scope, and any repository-specific expectations.
2. Read the reproduction evidence next. Record what behavior was actually observed, the environment or code state when relevant, and what causal conclusions the evidence directly supports.
3. Read the contributor's plan in full, including diagnosis, scope, files, approach, test plan, risks or unknowns, and deviations if present.
4. Read the draft plan comment.
5. Read repository contribution or communication rules only when a rubric check depends on them.

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

## Evidence gathering

1. For the diagnosis check, compare each causal statement in the plan against the reproduction evidence. Separate facts demonstrated by the reproduction from explanations that are only hypotheses.
2. For scope, list each file, component, or behavior the plan says it will change. Check whether each planned change follows from the diagnosed cause and whether unrelated changes are excluded.
3. For the test plan, identify the original reproduced failure and the exact command, input, or behavior that exposed it. Determine whether the proposed post-fix test would exercise the same behavior and has a concrete expected result.
4. Compare the draft comment with the full plan. Make sure it does not add claims, scope, certainty, or promises that the plan and evidence do not support.
5. When repository conventions matter, inspect the provided repository rules or issue-thread context rather than guessing.

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->


## Check execution

1. Grade every rubric check independently as pass, fail, or unclear.
2. Use only the evidence sources named by that rubric row.
3. Mark pass only when the pass condition is directly supported.
4. Mark fail when available evidence contradicts the condition or clearly omits something required.
5. Mark unclear when the needed evidence is unavailable, ambiguous, or too incomplete to decide.
6. Do not repair the plan mentally. Grade what is written, not what the contributor could have meant.
7. Do not infer a root cause merely because the proposed fix sounds plausible.

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

## Verdict assembly

1. Collect the result of every rubric check.
2. Apply the rubric's verdict rule exactly.
3. Any failed required check produces a reject verdict.
4. Any unclear required check also produces reject unless the rubric explicitly states otherwise.
5. Preferred checks may be reported but never change the verdict.
6. Explain each failed or unclear check using the smallest specific piece of missing or conflicting evidence.
7. End with the required machine-readable verdict expected by the skill.

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->
