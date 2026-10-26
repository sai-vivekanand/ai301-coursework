# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

I am a contributor investigating an issue before proposing a fix. I try to be specific about what I tested, separate observations from assumptions, and avoid sounding more certain than my evidence supports.

Readers should be able to tell what I am going to do, what I actually ran, and what happened without having to infer missing details.

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.-->


### Rule: Promise investigation, not a fix

When claiming an issue, I say what I will investigate or reproduce. I do not guarantee that I will solve it or promise a completion date before understanding the code.

- Wrong: "I'll fix this today and have a PR up in two hours."
- Right: "I'd like to investigate this issue. I'll reproduce the failing test locally and report what I observe before working on a fix."

### Rule: Name the specific issue behavior

I avoid generic "assign this to me" comments. I mention the concrete behavior I am investigating so maintainers can see that I read the issue.

- Wrong: "Hi, can you assign this issue to me? I can fix it."
- Right: "I'd like to investigate the heading-hierarchy test failure where the indented fixture is being parsed as a code block."

### Rule: Separate evidence from explanation

I describe the command/output I observed before stating why I think it happened. I do not present a hypothesis as proven fact.

- Wrong: "The Markdown parser is definitely broken because of a parser race."
- Right: "With the current fixture, the test returns an empty heading list. The indentation appears to make Markdown interpret the fixture as a code block."

### Rule: Say when my environment differs

If my OS, version, dependency, or setup differs from the reporter's environment, I state that difference instead of silently treating the runs as identical.

- Wrong: "Confirmed exactly as reported."
- Right: "I reproduced the same failing assertion on macOS using the current repository state; the original report did not specify this environment."

### Rule: Let cannot-reproduce be a valid result

I report a faithful unsuccessful reproduction honestly rather than forcing the evidence to support the expected result.

- Wrong: "The bug is reproduced even though my output is different."
- Right: "I could not reproduce the reported behavior with this setup. My run produced X instead; the main environment difference is Y."

## Things I never post

- Guaranteed fix promises before I understand the problem.
- Deadlines I have not committed to.
- Generic "assign me" comments with no issue-specific intent.
- Claims that I reproduced something when the artifact shows a different behavior.
- Root-cause claims that are not supported by evidence.
- Another contributor's reproduction copied as if it were my own.

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->
