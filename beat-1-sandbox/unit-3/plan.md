# Plan for #71

Issue: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71

## Diagnosis

My Unit 2 reproduction at commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088` failed because the Markdown fixture in `TestReadmeParser::test_extract_heading_hierarchy` has leading indentation. My posted evidence is https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-6405337665.

Command (with the repository virtual environment activated):
```bash
python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```
Observed output:
```text
assert len(headings) > 0
E       assert 0 > 0
E        +  where 0 = len([])
```
My control check returned `[]` with indentation preserved. Applying `textwrap.dedent()` to the same content returned:
```text
[{'level': 1, 'text': 'Main Title', 'line': 1},
 {'level': 2, 'text': 'Subsection', 'line': 4},
 {'level': 3, 'text': 'Sub-subsection', 'line': 7},
 {'level': 2, 'text': 'Another Section', 'line': 10}]
```
The heading extractor requires the heading marker at the beginning of the line. This control isolates fixture indentation as the condition preventing extraction.

## Scope

Correct the fixture indentation and remove the strict expected-failure marker for issue #71 (H-04). Keep the Markdown content and existing assertions. No production parser changes or unrelated test cleanup.

## Files

- `tests/unit/test_readme_parser.py`

## Approach

1. Create `fix/71-heading-fixture-indentation` from the current clean `main` on my fork.
2. Move the fixture headings and text to column zero within the string, preserving their content.
3. Remove the issue #71 `pytest.mark.xfail` decorator.
4. Inspect the diff and run the checks below.
5. Commit only the test file; keep `plan.md` and `comment.md` out of the fix commit.

## Test Plan

Run both commands from the repository root with the existing virtual environment:
```bash
.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v
.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```
Both must report PASSED, with the existing assertions detecting heading levels 1, 2, and 3. The second reruns the Unit 2 failure through the same parser and test. Save actual output before and after. Also run the README parser tests and repository lint, formatting, type, unit, and frontend checks before pushing; record any environment limitations honestly.

## Risks and Unknowns

The main risk is changing fixture content beyond whitespace; inspect the diff for that. If the corrected fixture still fails, revise the diagnosis and plan before expanding implementation scope. The existing local Python environment may need troubleshooting: a fresh pre-fix invocation exited before pytest output, so the prior Unit 2 output remains the established before evidence until a new run completes.

## Deviations

The code change matched the plan: only the heading-hierarchy fixture indentation and issue #71 xfail marker changed. The existing assertions and parser implementation are unchanged. Validation required an environment deviation: the original Anaconda-based Python 3.11.4 environment stalled in OS-level waits, so I created a temporary Python 3.13.3 environment at `/private/tmp/ai301-unit3-venv` with the declared development dependencies. The saved Unit 2 output remains the historical before evidence. This changes the validation environment, not the implementation scope. Full validation results are recorded in plan-and-implement.md.
