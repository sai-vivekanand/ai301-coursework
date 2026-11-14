# Explaining the contribution

Use these as prompts, not a script to claim work you cannot explain.

1. **Problem:** `mm tags --help` lists the commands but does not show examples or tell users that mutations preview unless --apply is supplied.
2. **Evidence:** Show the captured before output. The original six help tests pass because tags is not covered.
3. **Design:** Follow the existing SEARCH_EPILOG pattern. Click wraps normal prose; a backspace marker starts a raw paragraph so example commands stay separate.
4. **Regression test:** Compare complete output lines, normalize whitespace only for the safety note, and include tags in the existing 80-column check. Before the implementation, two tests fail and five pass.
5. **Scope:** Help and test files only. Tag mutation services and flags stay as implemented.
6. **Review process:** Explain the claim, reproduction check, plan check, ship-gate and actual PR status using the final contribution story. A merge is welcome but not required by the assignment.
7. **AI use:** Codex helped implement, test and document; Claude ran the course checks. Be ready to explain the string, decorator argument and every assertion yourself.

Demo command: `uv run mm tags --help`. It displays help without modifying tags.
Do not run the delete or merge examples on your real data for the presentation.

PR: https://github.com/memtomem/memtomem/pull/3356

Actual current status: awaiting human review; unsigned CLA; local scoped tests and gate passed. Full baseline had one documented Git-version failure. Use the contribution story for the precise results.
