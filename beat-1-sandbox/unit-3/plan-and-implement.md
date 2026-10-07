# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

Ninesay725

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56#issuecomment-6041571308

My reproduction above returned `0 []` without a heading and one chunk when I added a heading to the same text. I plan to change `_extract_sections()` in `ingestion/chunking/structural_chunker.py` so a document with no heading becomes one section with an empty heading path and level `0`. The existing chunking code will preserve source metadata and split large sections. In `tests/unit/test_structural_chunker.py`, I'll remove the #56 xfail, check the short example's text and metadata, and add a long headingless case. I'll re-run the reproduction, the structural chunker tests, and the repository checks (lint, formatting, types, unit tests, and frontend tests). The fallback will require no heading to have been seen, so heading-only documents and current headed-document behavior stay unchanged. This is limited to chunking; I have not tested the full indexing pipeline.

## Your branch

**Branch**

`fix/56-headingless-documents`

**Evidence**

From the fork root, I ran the same reproduction before and after the change:

```powershell
@'
from ingestion.chunking.structural_chunker import StructuralChunker

text = 'This is a plain document with no headings at all. ' * 20
chunker = StructuralChunker()
plain = chunker.chunk(text, {})
headed = chunker.chunk('# Title\n' + text, {})
print('input_chars:', len(text))
print('without_heading:', len(plain), plain)
print('with_heading:', len(headed))
print('control_keeps_text:', headed[0].text == text.strip())
'@ | .\.venv\Scripts\python.exe -
```

Before:

```text
input_chars: 1000
without_heading: 0 []
with_heading: 1
control_keeps_text: True
```

After:

```text
input_chars: 1000
without_heading: 1 [Chunk(text='This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all. This is a plain document with no headings at all.', metadata={'heading_path': '', 'heading_level': 0, 'chunk_index': 0, 'char_start': 0, 'char_end': 999})]
with_heading: 1
control_keeps_text: True
```

The target test, with the optional pytest cache disabled:

```powershell
.\.venv\Scripts\python.exe -m pytest tests/unit/test_structural_chunker.py::TestStructuralChunker::test_document_with_no_headings --runxfail -q --tb=short -p no:cacheprovider
```

Before (exit 1):

```text
F                                                                        [100%]
================================== FAILURES ===================================
____________ TestStructuralChunker.test_document_with_no_headings _____________
tests\unit\test_structural_chunker.py:36: in test_document_with_no_headings
    assert len(result) >= 1
E   assert 0 >= 1
E    +  where 0 = len([])
=========================== short test summary info ===========================
FAILED tests/unit/test_structural_chunker.py::TestStructuralChunker::test_document_with_no_headings
1 failed in 0.32s
```

After (exit 0):

```text
.                                                                        [100%]
1 passed in 0.21s
```

The full structural chunker test file after the change:

```powershell
.\.venv\Scripts\python.exe -m pytest tests/unit/test_structural_chunker.py -q --tb=short -p no:cacheprovider
```

```text
................                                                         [100%]
16 passed in 0.21s
```

## Eval iterations

**Run history**

First full run: 17/20. After revising Honesty and how contribution requirements are applied, the partial run on pkg-04, pkg-06, pkg-07, pkg-09, pkg-10, pkg-14, and pkg-20 scored 6/7. The final full run scored 20/20, with a match in every category.

**Package analysis**

In pkg-09, my first run said reject and the gold label said accept. The plan used normalized paths "only for matching, never for output" and kept the change Windows-only. My Honesty check rejected a minor attribution mistake even though the fix and tests were usable. After I narrowed that check, the final run accepted it.

**Check rationale**

I changed Honesty to: "No invented completed results or hidden deviations. A plausible cause consistent with the repro may remain unproven if the plan gives a concrete way to test it; material limits are stated." The first version treated small wording issues as blockers. This version still rejects invented results but lets a testable explanation move forward.

**Trade-offs**

This can accept a plausible explanation that turns out to be wrong during the build. The partial run still rejected the wrong-cause canary pkg-07, but pkg-14 changed from reject on Test plan in the partial run to accept in the final run without another edit. That borderline result is a limit of the check.
