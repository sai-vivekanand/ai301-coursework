# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

sai-vivekanand

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-6569784474

I reproduced #71 at commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088` on macOS arm64 with Python 3.11.4. My reproduction and control output are in https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-6405337665.

The indented fixture returned `[]` and failed `assert len(headings) > 0`. Removing the common indentation from the same content produced four headings with levels 1, 2, 3, and 2.

I plan to remove the unintended indentation from the Markdown fixture in `tests/unit/test_readme_parser.py` and remove its issue #71 (H-04) strict `xfail` marker. The parser implementation and other tests are outside this change.

I will rerun `python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail` and the same command without `--runxfail`. Both should pass normally, with the existing assertions detecting heading levels 1, 2, and 3. I will also run the repository checks before pushing `fix/71-heading-fixture-indentation` to my fork. If the fixture correction does not resolve the failure, I will revisit this diagnosis before expanding the scope.

## Your branch

**Branch**

`fix/71-heading-fixture-indentation` on `sai-vivekanand/pathreview-ai301-fa26-s3`.

**Evidence**

Before (Unit 2, Python 3.11.4, original repository virtual environment activated):

```bash
python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```

```text
============================= test session starts ==============================
platform darwin -- Python 3.11.4, pytest-9.1.1, pluggy-1.6.0 -- /Users/sai_vivek_vangala/Documents/codepath/ai301/unit2/pathreview-ai301-fa26-s3/.venv/bin/python
cachedir: .pytest_cache
rootdir: /Users/sai_vivek_vangala/Documents/codepath/ai301/unit2/pathreview-ai301-fa26-s3
configfile: pyproject.toml
collecting ... collected 1 item

tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy FAILED [100%]

=================================== FAILURES ===================================
_______________ TestReadmeParser.test_extract_heading_hierarchy ________________

self = <tests.unit.test_readme_parser.TestReadmeParser object at 0x10a83e010>
parser = <ingestion.parsers.readme_parser.ReadmeParser object at 0x10a850850>

    @pytest.mark.xfail(
        strict=True,
        reason="issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings",
    )
    def test_extract_heading_hierarchy(self, parser):
        """Test heading hierarchy extraction."""
        markdown = """
        # Main Title
        Some content
    
        ## Subsection
        More content
    
        ### Sub-subsection
        Even more content
    
        ## Another Section
        Final content
        """
        headings = parser._extract_heading_hierarchy(markdown)
    
        assert isinstance(headings, list)
>       assert len(headings) > 0
E       assert 0 > 0
E        +  where 0 = len([])

tests/unit/test_readme_parser.py:156: AssertionError
=========================== short test summary info ============================
FAILED tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy
============================== 1 failed in 0.03s ===============================

```

After (temporary Python 3.13.3 environment, pytest 9.2.0):

The original Anaconda environment stalled before producing a result, so I installed the declared development dependencies in a temporary environment. This environment difference is recorded in the plan's Deviations section.

```bash
/private/tmp/ai301-unit3-venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```

```text
/private/tmp/ai301-unit3-venv/lib/python3.13/site-packages/pytest_asyncio/plugin.py:300: PytestDeprecationWarning: The configuration option "asyncio_default_fixture_loop_scope" is unset.
The event loop scope for asynchronous fixtures will default to the "fixture" caching scope. Future versions of pytest-asyncio will default the loop scope for asynchronous fixtures to "function" scope. Set the default fixture loop scope explicitly in order to avoid unexpected behavior in the future. Valid fixture loop scopes are: "function", "class", "module", "package", "session"

  warnings.warn(PytestDeprecationWarning(_DEFAULT_FIXTURE_LOOP_SCOPE_UNSET))
============================= test session starts ==============================
platform darwin -- Python 3.13.3, pytest-9.2.0, pluggy-1.7.0 -- /private/tmp/ai301-unit3-venv/bin/python
cachedir: .pytest_cache
benchmark: 5.3.1 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
hypothesis profile 'default'
rootdir: /Users/sai_vivek_vangala/Documents/codepath/ai301/unit2/pathreview-ai301-fa26-s3
configfile: pyproject.toml
plugins: pytest_httpserver-1.2.0, platformdirs-4.14.3, benchmark-5.3.1, cov-7.1.0, hypothesis-6.170.14, anyio-4.16.0, asyncio-1.4.1.post1
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collecting ... collected 1 item

tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [100%]

============================== 1 passed in 0.94s ===============================

```

Normal run after removing the marker:

```bash
/private/tmp/ai301-unit3-venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v
```

```text
/private/tmp/ai301-unit3-venv/lib/python3.13/site-packages/pytest_asyncio/plugin.py:300: PytestDeprecationWarning: The configuration option "asyncio_default_fixture_loop_scope" is unset.
The event loop scope for asynchronous fixtures will default to the "fixture" caching scope. Future versions of pytest-asyncio will default the loop scope for asynchronous fixtures to "function" scope. Set the default fixture loop scope explicitly in order to avoid unexpected behavior in the future. Valid fixture loop scopes are: "function", "class", "module", "package", "session"

  warnings.warn(PytestDeprecationWarning(_DEFAULT_FIXTURE_LOOP_SCOPE_UNSET))
============================= test session starts ==============================
platform darwin -- Python 3.13.3, pytest-9.2.0, pluggy-1.7.0 -- /private/tmp/ai301-unit3-venv/bin/python
cachedir: .pytest_cache
benchmark: 5.3.1 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
hypothesis profile 'default'
rootdir: /Users/sai_vivek_vangala/Documents/codepath/ai301/unit2/pathreview-ai301-fa26-s3
configfile: pyproject.toml
plugins: pytest_httpserver-1.2.0, platformdirs-4.14.3, benchmark-5.3.1, cov-7.1.0, hypothesis-6.170.14, anyio-4.16.0, asyncio-1.4.1.post1
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collecting ... collected 1 item

tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [100%]

============================== 1 passed in 0.21s ===============================

```

Additional control in the same temporary environment: exported the original test file from the base commit, then ran it through the unchanged production parser. This is a baseline copy, not a claim that the fixed working tree failed.

```bash
git show 2f4e82f52efbcfcc57d65b3fa5348672163ca088:tests/unit/test_readme_parser.py > /private/tmp/test_readme_parser_unit3_before.py
/private/tmp/ai301-unit3-venv/bin/python -m pytest /private/tmp/test_readme_parser_unit3_before.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```

```text
/private/tmp/ai301-unit3-venv/lib/python3.13/site-packages/pytest_asyncio/plugin.py:300: PytestDeprecationWarning: The configuration option "asyncio_default_fixture_loop_scope" is unset.
The event loop scope for asynchronous fixtures will default to the "fixture" caching scope. Future versions of pytest-asyncio will default the loop scope for asynchronous fixtures to "function" scope. Set the default fixture loop scope explicitly in order to avoid unexpected behavior in the future. Valid fixture loop scopes are: "function", "class", "module", "package", "session"

  warnings.warn(PytestDeprecationWarning(_DEFAULT_FIXTURE_LOOP_SCOPE_UNSET))
============================= test session starts ==============================
platform darwin -- Python 3.13.3, pytest-9.2.0, pluggy-1.7.0 -- /private/tmp/ai301-unit3-venv/bin/python
cachedir: .pytest_cache
benchmark: 5.3.1 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
hypothesis profile 'default'
rootdir: /private/tmp
plugins: pytest_httpserver-1.2.0, platformdirs-4.14.3, benchmark-5.3.1, cov-7.1.0, hypothesis-6.170.14, anyio-4.16.0, asyncio-1.4.1.post1
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collecting ... collected 1 item

../../../../../../../private/tmp/test_readme_parser_unit3_before.py::TestReadmeParser::test_extract_heading_hierarchy FAILED [100%]

=================================== FAILURES ===================================
_______________ TestReadmeParser.test_extract_heading_hierarchy ________________

self = <test_readme_parser_unit3_before.TestReadmeParser object at 0x1074fef30>
parser = <ingestion.parsers.readme_parser.ReadmeParser object at 0x1072b0d70>

    @pytest.mark.xfail(
        strict=True,
        reason="issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings",
    )
    def test_extract_heading_hierarchy(self, parser):
        """Test heading hierarchy extraction."""
        markdown = """
        # Main Title
        Some content
    
        ## Subsection
        More content
    
        ### Sub-subsection
        Even more content
    
        ## Another Section
        Final content
        """
        headings = parser._extract_heading_hierarchy(markdown)
    
        assert isinstance(headings, list)
>       assert len(headings) > 0
E       assert 0 > 0
E        +  where 0 = len([])

/private/tmp/test_readme_parser_unit3_before.py:156: AssertionError
=============================== warnings summary ===============================
../../../../../../../private/tmp/test_readme_parser_unit3_before.py:9
  /private/tmp/test_readme_parser_unit3_before.py:9: PytestUnknownMarkWarning: Unknown pytest.mark.unit - is this a typo?  You can register custom marks to avoid this warning - for details, see https://docs.pytest.org/en/stable/how-to/mark.html
    @pytest.mark.unit

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
=========================== short test summary info ============================
FAILED ../../../../../../../private/tmp/test_readme_parser_unit3_before.py::TestReadmeParser::test_extract_heading_hierarchy
========================= 1 failed, 1 warning in 0.52s =========================

```


Repository validation in the temporary environment:

- `/private/tmp/ai301-unit3-venv/bin/ruff check .`: `All checks passed!`
- `/private/tmp/ai301-unit3-venv/bin/black --check .`: `110 files would be left unchanged.`
- `/private/tmp/ai301-unit3-venv/bin/mypy api/ core/ ingestion/ rag/ agent/ safety/ --ignore-missing-imports`: `Success: no issues found in 76 source files`.
- `/private/tmp/ai301-unit3-venv/bin/python -m pytest tests/unit/test_readme_parser.py -v`: `14 passed, 1 xfailed`.
- `LLM_PROVIDER=mock /private/tmp/ai301-unit3-venv/bin/python -m pytest tests/unit -v --tb=short`: `376 passed, 52 xfailed, 2 warnings in 12.71s`. The first sandboxed attempt had 30 tokenizer-data download errors; rerunning with network access resolved them.
- `LLM_PROVIDER=mock /private/tmp/ai301-unit3-venv/bin/python -m pytest tests/integration -v --tb=short`: no tests collected (exit 5), which the repository CI explicitly treats as success while this suite is empty.
- From `frontend/`, `npm ci` then `npm test -- --run`: 2 test files passed, 18 tests passed.
- `git diff --check`: passed.

## Eval iterations

**Run history**

1. Calibration-only launch inside the sandbox: both cases errored before a verdict (`claude exited 1`); no scored packages.
2. Calibration retry with network access: calib-01 accept and calib-03 reject, both matching gold; 0 scored packages.
3. First and final full scored run: **18/20**. Exact harness line: `agreement: 18/20 scored items  (bar: 18/20: PASS)`.

Category coverage: `clear-accept 5/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4`.

No rubric tuning or further scored runs followed this passing full run. Before calibration, I corrected the rubric's `ready/hold` labels to the required `accept/reject` output vocabulary and aligned the procedure. The saved transcript was generated by the harness, not edited by hand.

**Package analysis**

`pkg-14`: my rubric decided `reject`; gold says `accept`. The failing check was "Diagnosis supported by reproduction". The candidate diagnosis states: "the reattach path wires the client's stdin to the session before the query responses have been consumed". Its plan also says "exact functions to be pinned in the PR after tracing the query issuance with debug logs". The evaluator treated the claimed internal ordering as stronger than the supplied behavioral evidence, which shows leakage on reattach and clean control runs but does not show that ordering directly. The gold label accepts this bounded plan; my check produced a conservative false rejection.

**Check rationale**

Exact current rubric row:

| Diagnosis supported by reproduction | Repro evidence, issue description, and plan diagnosis | The plan's claimed cause must be supported by the reproduced behavior. It must not introduce a root cause that the reproduction does not establish. If the reproduction only proves a narrower condition, the diagnosis must stay within that evidence. | required |

I kept this evidence requirement instead of accepting a technically plausible cause merely because its proposed fix sounds reasonable. The calibration trap demonstrates why this matters: calib-03 was rejected while calib-01 was accepted. I corrected the verdict vocabulary, but did not loosen this check to make the live plan pass. The live plan has a direct indented-versus-dedented control from my own posted reproduction.

**Trade-offs**

This strict evidence rule can reject a useful provisional diagnosis. `pkg-14` is the concrete cost: the full run rejected it even though gold accepts it. `pkg-02` was also a false rejection, with "Scope matches diagnosis" and "Comment and repository conventions" failing because of the sibling cursor-advance change and how the comment described it. I retained the rubric after the passing run rather than claiming these disagreements were resolved. The full run matched all four wrong-cause cases and both thread-convention cases, and its five-category tally establishes that no category was missed completely. This evidence supports the stated trade-off; it does not establish perfect generalization.
