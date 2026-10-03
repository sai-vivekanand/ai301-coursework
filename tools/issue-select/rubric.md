# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Repository activity | Repo-facts block: release dates and default-branch commit dates | Pass if the repository has either a release or a default-branch commit within the last 12 months. | required |
| Maintainer responsiveness | Repo-facts block: maintainer first-response sample, authorship of the candidate issue, and recent default-branch commit activity | Pass if at least one sampled recently updated issue has an owner/member/collaborator response within 90 days, OR the candidate issue was opened by an owner/member/collaborator, OR recent default-branch history shows owner/member/collaborator activity. Do not fail merely because some sampled issues have no maintainer comment. If none of these signals is present, fail. | required |
| Scope fit | Issue body and comment thread, including whether it is an umbrella/tracking issue, whether any unresolved requirement blocks the core task, maintainer statements about core internals, and prior abandoned attempts | Pass unless one of these applies: the issue is an umbrella/tracking issue meant to be split into separate work; a requirement, asset, UX/product decision, or implementation direction necessary to complete the core task is still TBD or under unresolved discussion; a maintainer states that the fix requires changes to core internals; it is only a usage/support question; or the history shows multiple abandoned implementation attempts indicating hidden difficulty. Optional, lower-priority, or "if needed" follow-up details do not cause failure when the main requested outcome is already specified. Age, a stale label, one old claim, one closed/unmerged PR, or touching multiple files do not by themselves cause failure. | required |
| Work availability | Repo-facts assignee field, linked-PR state, and issue comment thread | Pass only if there is no active assignee, no open linked PR implementing the issue, and no contributor explicitly saying they are currently working on it. | required |
| Contribution policy | Repo-facts contribution-policy field, including any AI/tooling policy | Fail if the repository explicitly bans AI-generated or AI-assisted code/documentation that this course workflow would produce. Pass if the policy is silent on AI, explicitly allows AI, or allows it subject to conditions such as disclosure, testing, human review, or personally understanding the contribution; those conditions must be followed but are not themselves a reason to reject the issue. | required |

## Verdict rule

Accept only if every required check passes.

A failed required check rejects the issue.

An unclear result on a required check counts as failure.

Preferred checks, if added later, may rank accepted issues but do not change the accept/reject verdict.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->
