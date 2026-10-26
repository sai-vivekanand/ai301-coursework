# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

sai-vivekanand

[Your GitHub username, exactly as it appears on your profile — no `@`, no profile URL. Your
comments upstream are identified by this name.]

---

## Posted upstream

**claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-6154947466

I'd like to investigate #71, where the heading-hierarchy test fixture's indentation causes the Markdown content to be interpreted as a code block instead of headings.

I'll set up the repository locally, reproduce the failing test from my own environment, and report the exact command, environment, and observed behavior before working on any fix.

[Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.]

**Reproduction Comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-6405337665

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. Smoke run: 3/3 agreement.
2. First full run: 16/20 agreement; below the 18/20 bar and disclosure category floor unmet.
3. Targeted rerun after rubric revisions: 8/8 agreement.
4. Final saved full run: 20/20 agreement; PASS.

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

**Package analysis**

pkg-20

My first full-run rubric accepted the package, while the gold label was reject.

The reproduction evidence itself was strong, so the failure was not environment, followability, behavior, or honesty. The repository's AI policy required disclosure of all AI assistance, but the candidate comment did not disclose it. My original conventions check was not explicit enough about treating course packages as AI-assisted work, so the grader accepted the package.

I revised the Upstream conventions check so that, for course evaluation packages, required AI disclosure in issue comments or all communications is mandatory. After that change, pkg-20 was correctly rejected, matching the gold label.

[Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.]

**Check rationale**

grep '^| Upstream conventions' tools/repro-check/rubric.md

[Quote one check from the `rubric.md` you uploaded to `tools/repro-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.]

**Trade-offs**

I loosened the Followable reproduction and Behavior matches issue checks so that well-evidenced cannot-reproduce reports could pass. That fixed pkg-09 and pkg-10, but loosening those checks risked allowing wrong-target or unfollowable reports through. I therefore reran canaries including pkg-02, pkg-06, pkg-18, and pkg-19. They remained rejected, while pkg-05, pkg-09, and pkg-10 changed to the intended accepts.

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
