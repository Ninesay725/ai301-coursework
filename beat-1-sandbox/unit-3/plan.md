# Plan for #56

## Diagnosis

In [my reproduction](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56#issuecomment-5982105881), the same 1000-character input gave `without_heading: 0 []` and `with_heading: 1`; the headed control kept the text. The existing test failed with `assert 0 >= 1`. In `_extract_sections()`, content collection and saving depend on a heading being present, so a document with no heading produces no sections.

## Scope

I will change only `ingestion/chunking/structural_chunker.py` and `tests/unit/test_structural_chunker.py` on `fix/56-headingless-documents`. This covers documents with no recognized Markdown heading. Heading parsing, text before a heading, the semantic chunker, and the indexing pipeline will stay as they are.

## Approach

After `_extract_sections()` scans the lines, I will return one section containing `text.strip()`, an empty heading path, and heading level `0` if it never encountered a heading. The existing `chunk()` path will copy the source metadata and split sections over 800 tokens with `SemanticChunker`. Empty input will still return no chunks. I will remove the strict #56 xfail, check that the existing short example keeps its text and source metadata, and add a long headingless case to check that splitting still works. The existing headed-document tests will check for regressions.

## Verification

I will re-run my posted Python snippet through the real chunker: `'This is a plain document with no headings at all. ' * 20` should produce one chunk instead of zero; adding `'# Title\n'` should still produce one chunk containing the same text. The existing target test, run with `--runxfail -q --tb=short`, should pass instead of failing. I will run `python -m pytest tests/unit/test_structural_chunker.py -q --tb=short` to check short/large inputs, empty input and heading hierarchy, then run the repository's required checks before pushing.

## Risks and unknowns

A fallback for any empty section list could change heading-only documents, so I will trigger it only when no heading was seen. Large documents must still use the existing token-based split. The empty path and level `0` represent no heading; the pipeline passes chunk metadata onward without checking those fields. I have not verified the full RAG indexing pipeline, so this plan's evidence is limited to chunking.

## Deviations

The fix followed the plan; no scope or approach changed.
