# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment fidelity | Repro report environment record, issue environment/version details, and repo-facts bug-report requirements | Pass if the report records the environment details needed to interpret and rerun the attempt, including relevant software version and platform when applicable, and either matches the issue's relevant environment or explicitly identifies and accounts for meaningful differences. | required |
| Followable reproduction | Repro report commands, inputs, setup steps, referenced files/resources, and the issue's original trigger | Pass if a stranger can recreate the contributor's attempted reproduction from the information provided and run through the tested scenario without guessing an essential command, configuration, input characteristic, or trigger step. Inputs do not need to be reproduced byte-for-byte when the report describes the properties necessary to recreate them. Fail if an essential resource or configuration is private, unavailable, or too underspecified to recreate. | required |
| Behavior matches issue | Repro artifacts such as terminal output, logs, screenshots, measurements, or other shown results, read against the issue's reported trigger and behavior | Pass if a successful reproduction's artifacts demonstrate the same reported behavior. An honest cannot-reproduce also passes when the contributor made a concrete attempt at the reported scenario, shows the actual result, and explicitly identifies relevant environment or trigger differences that may explain why the reported behavior did not occur. Fail when the contributor changes the essential target or trigger and presents a different error or adjacent symptom as reproduction of the issue. | required |
| Outcome honesty | Repro report conclusion, actual/expected statements, analysis, and the artifacts that support them | Pass if the conclusion says no more than the evidence proves. A supported reproduction or a well-evidenced cannot-reproduce both pass. Fail if the report claims reproduction, certainty, generality, or root cause that the shown evidence does not establish. | required |
| Upstream conventions | Candidate claim comment and repro report read against repo-facts bug-report requirements and contribution policy, including AI-use requirements | Pass if the claim is specific to the issue and states a concrete investigation/reproduction intent without guaranteeing a fix or deadline, and the communication follows applicable repository requirements. For these course packages, treat the work as AI-assisted. If the repository requires disclosure of AI use in issue comments or all communications, the candidate comment must explicitly disclose that assistance; absence of the required disclosure fails this check. If the repository is silent on AI, permits AI without disclosure, or requires disclosure only later in a pull request, lack of disclosure in the issue comment does not fail. | required |

## Verdict rule

Accept the package as ready only if every required check passes.

A failed required check means hold/reject.

An unclear result on a required check counts as failure because the package does not contain enough proof to post confidently.

Preferred checks, if added later, may help rank or improve a ready package but do not change the final accept/reject verdict.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->
