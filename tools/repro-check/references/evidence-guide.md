# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

### Where it lives

In eval mode, look at the issue context for the reporter's environment and target version, the repo-facts block for required bug-report fields, and the reproduction report for the contributor's OS, software version, installation method, code state, runtime, driver, shell, or other environment details relevant to the issue.

In live mode, compare the GitHub issue's reported environment and repository instructions with the environment recorded in the student's draft reproduction report.

### What good looks like

The report records enough environment information for another contributor to understand what was tested and to repeat the attempt. Relevant differences from the issue's environment or version are explicitly stated rather than silently substituted. A difference is acceptable when the report acknowledges it and the reproduction remains meaningful.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

### Where it lives

In eval mode, compare the issue's trigger and example commands with the setup, input files, commands, configuration, and execution steps in the reproduction report.

In live mode, compare the original GitHub issue and repository setup instructions with the student's draft steps.

### What good looks like

A stranger can recreate the contributor's attempted reproduction and execute it through the tested scenario without guessing an essential command, configuration, input characteristic, or trigger step. Inputs do not need to be byte-for-byte identical when the report states the properties needed to recreate them. An inaccessible private repository, configuration, or other essential resource makes the attempt unfollowable.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

### Where it lives

Look at the issue's expected and actual behavior, then inspect the reproduction report's concrete artifacts: terminal output, stack traces, logs, screenshots, measurements, generated files, or other observed results.

### What good looks like

For a successful reproduction, the artifact shows the same behavior the issue describes rather than merely a nearby failure.

For a cannot-reproduce result, the contributor must show a concrete attempt at the reported scenario and the actual result they observed. Relevant environment or trigger differences should be stated explicitly. A cannot-reproduce does not need to produce the bug; it needs to prove that a faithful, interpretable attempt was made.

Changing the essential target or trigger and then presenting a different error as the reported bug is not valid evidence.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

### Where it lives

Compare the claim comment, reproduction conclusion, expected/actual statements, analysis, and any root-cause statements directly with the artifacts shown.

### What good looks like

The language is no stronger than the evidence. A successful reproduction says what was observed. An honest cannot-reproduce reports the failed attempt, records relevant differences, and avoids pretending the issue is fixed or invalid.

Root-cause claims, statements such as "guaranteed reproducible," and broad claims about affected environments require evidence that actually supports them.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

### Where it lives

In eval mode, read the candidate claim comment and reproduction report against the issue context, repo-facts bug-report requirements, and contribution policy, including any AI-use policy.

In live mode, read the student's draft comments against the live issue thread, repository contribution docs/templates, and applicable AI-assistance rules.

### What good looks like

The claim refers to the specific issue and states what the contributor intends to investigate or reproduce. It does not make promises about a guaranteed fix or delivery date.

The reproduction is written in the contributor's own words, states what actually happened, and follows repository-specific requirements. If the repository requires disclosure of AI assistance, the comment includes it. If the repository is silent or merely allows AI subject to responsibility/testing, lack of disclosure is not itself a failure unless the policy requires it.

For course evaluation packages, treat the work as AI-assisted. If the repository requires AI-use disclosure in issue comments or all communications, the comment must contain that disclosure. If disclosure is required only for pull requests, or the repository is silent/permissive without an issue-comment disclosure requirement, its absence from an issue comment is not a failure.

