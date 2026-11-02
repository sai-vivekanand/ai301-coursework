# Procedure: how this tool grades a PR package

## Read order

1. In live mode apply the frame's scope gate and read the voice guide; in eval mode ignore both. Read the rubric and evidence guide before grading.
2. Read issue, thread, and repository standards. Record the reported behavior, explicit maintainer constraints, required checks, template asks, and AI policy. This establishes the actual requirements before assessing the author's claims.
3. Read the plan context, including reproduced observations, scope boundaries, proposed tests, and all deviation notes. Record intended changes and explicit omissions with reasons.
4. Read the complete committed diff and commit list. Map actual changes before reading the description's persuasive claims.
5. Read the test evidence and then the title and description. Pair actual results with claims and required checks. In live mode use the exact input files and Git commands named in SKILL.md; in eval mode stay within the bundle.

## Evidence gathering

1. For plan fidelity, map each changed behavior/file to plan scope or a reasoned deviation. Also map each planned behavior back to a diff hunk or explicit omission. Compare every substantive description claim with that map. Record hidden additions, hidden omissions, or contradictory completion claims.
2. For testing, pair each repro/test-plan behavior with the actual command or concrete scenario and observed branch result. Compare expected and actual outcomes. Separately list each repo-required check and its reported outcome or justified inapplicability. Distinguish an honest failing run from a check never run and silently omitted; do not treat checkbox prose alone as output.
3. For reviewability, scan all hunks and commits for unrelated edits, debug statements, dead code, and formatting churn. Determine whether supporting edits are needed for this issue; a deviation note does not excuse unrelated cleanup.
4. For standards, pair each actual template/policy/thread ask with the corresponding title or description text. Record missing content, disclosures, and misleading checkboxes. In live Path Review mode include the course AI-use requirement and check the personal voice guide separately.

## Check execution

1. Execute every rubric row in table order using only its named evidence. Grade pass when the condition is supported, fail when contradicted or a required artifact is demonstrably omitted, and unclear when unavailable or ambiguous evidence prevents a decision.
2. Quote or identify a concrete deciding fact for each grade. For missing evidence, name exactly what was sought and where it should appear.
3. Evaluate recorded deviations before deciding that scope differs silently. Accept honest partial outcomes only under the row's stated condition; do not assume every shortfall passes or every failing test rejects.
4. Do not mentally repair the PR, infer unreported test runs, fetch eval sources, or add unstated repository requirements. Cross-check the relevant paired artifacts again when a contradiction appears; otherwise reuse the gathered map.
5. Report any step the procedure cannot specify as a gap. Report live voice-rule violations with the rule quoted; apply no additional verdict gate beyond the rubric.

## Verdict assembly

1. Collect every row's grade, then apply the rubric's required/preferred rule and explicit unclear handling.
2. For reject, lead the readable explanation with the first failing or unclear required row in rubric order, quoting its deciding evidence; also report the other row outcomes. For accept, report any disclosed limitations without inventing a third verdict.
3. End with the exact fenced JSON schema from SKILL.md: item, checks with name/grade/evidence, and binary verdict. Emit nothing after the block.
