# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56

Structural chunker silently drops documents that contain no headings.

**Verdict output**

The following is the installed skill's complete live-mode output on candidates #56, #57, and #60, preserved verbatim. The selected candidate is #56.

## Live-Mode Grading — `codepath/pathreview-ai301-fa26-s3`, issues #56, #57, #60

**Repo-level evidence used for all three:** not archived; `pushed_at` 2026-09-16 (5 days before today, 2026-09-21) — Repository continuity passes on recent push (no releases exist, which the rubric allows). Last 5 default-branch commits (2026-08-24 to 2026-09-16) authored/committed by human collaborator Aburke225 — Human maintenance passes on recent human-authored commits, reinforced by Aburke225 (COLLABORATOR) opening all three issues on 2026-09-10. `docs/CONTRIBUTING.md` covers branching, PR process, and CI requirements (lint/typecheck/unit/integration/frontend tests must be green) but contains no AI-use clause of any kind — silence passes Compatible contribution policy. Open-PRs query returned no results, so no open implementation PR exists anywhere in the repo referencing these issues.

### Ranked read-out

**Accepted (all three):**

1. **#60 – Faithfulness checker crashes on `text: None`** — cleanest, most bounded RAG-evaluation bug (a `.get()` default-value defect) with a concrete repro and a named failing test (`test_none_context_chunk_text`); best match to the stated preference for a small, focused RAG data-processing fix.
2. **#56 – Structural chunker drops headingless documents** — squarely a RAG ingestion/data-processing bug with a reproduction example and named test (`test_document_with_no_headings`), though the body leaves the exact remedy ("single block or alternative strategy") slightly more open than #60.
3. **#57 – Tech detector counts vendored/build files** — a well-scoped backend Python bug with two named failing tests (`test_node_modules_excluded`, `test_build_directory_excluded`), but it's a repo-analysis/agent-tooling fix rather than RAG-specific, so it fits the stated preference least among the three.

**Rejected:** none.

Note on #57 and #60: each carries a same-day claim comment from a different classmate (`ApoorvThite`, `pkmaster21`), both `author_association: NONE`. Per the Path Review house rule in `scope.md`, classmates' claim comments don't block an issue, so Available work still passes on both.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/60",
    "checks": [
      {"name": "Human maintenance", "grade": "pass", "evidence": "Issue opened 2026-09-10 by Aburke225 (COLLABORATOR); repo's last 5 default-branch commits are human-authored/committed by Aburke225 through 2026-09-16, within 90 days of 2026-09-21."},
      {"name": "Repository continuity", "grade": "pass", "evidence": "repo not archived; pushed_at 2026-09-16, 5 days before today; no releases exist but recent push suffices per rubric."},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Body describes one fix: `chunk.get(\"text\", \"\")` returns None instead of default when key exists with None value, causing a TypeError in `\" \".join(...)`; single identifiable code change."},
      {"name": "Attempt history", "grade": "pass", "evidence": "Issue created 2026-09-10, only 11 days old (far under 730 days), so the age+2-abandoned-attempts failure condition cannot trigger."},
      {"name": "Available work", "grade": "pass", "evidence": "Open, no assignee, no linked/open PR found (open-PR query empty); only claim is pkmaster21's 2026-09-21 comment (author_association NONE), which the Path Review house rule says does not block the issue."},
      {"name": "Compatible contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md covers branching/PR/CI rules and testing but has no AI-use clause; silence passes per rubric."},
      {"name": "Verification foothold", "grade": "pass", "evidence": "Body supplies concrete before/after behavior and names the failing test `test_none_context_chunk_text`."},
      {"name": "Newcomer invitation", "grade": "pass", "evidence": "Issue carries labels bug, good first issue, rag, tier-1."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56",
    "checks": [
      {"name": "Human maintenance", "grade": "pass", "evidence": "Issue opened 2026-09-10 by Aburke225 (COLLABORATOR); same human-authored commit history through 2026-09-16 applies repo-wide."},
      {"name": "Repository continuity", "grade": "pass", "evidence": "repo not archived; pushed_at 2026-09-16, within 180 days of 2026-09-21."},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Body describes one fix: `StructuralChunker.chunk()` returns an empty list for documents with no markdown headings, dropping them from the RAG index; one identifiable behavior change."},
      {"name": "Attempt history", "grade": "pass", "evidence": "Issue created 2026-09-10, 11 days old, well under the 730-day threshold, so the failure condition cannot trigger."},
      {"name": "Available work", "grade": "pass", "evidence": "Open, no assignee; comments endpoint returned an empty array (no claims at all); no open PR found."},
      {"name": "Compatible contribution policy", "grade": "pass", "evidence": "Same repo-wide CONTRIBUTING.md silence on AI-assisted workflows."},
      {"name": "Verification foothold", "grade": "pass", "evidence": "Body includes a ~1000-character example producing zero chunks and names the failing test `test_document_with_no_headings`."},
      {"name": "Newcomer invitation", "grade": "pass", "evidence": "Labels: bug, good first issue, ingestion, tier-1."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/57",
    "checks": [
      {"name": "Human maintenance", "grade": "pass", "evidence": "Issue opened 2026-09-10 by Aburke225 (COLLABORATOR); same human-authored commit history through 2026-09-16 applies repo-wide."},
      {"name": "Repository continuity", "grade": "pass", "evidence": "repo not archived; pushed_at 2026-09-16, within 180 days of 2026-09-21."},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Body describes one fix: `tech_detector.py` fails to exclude `node_modules/` or `build/` directories, skewing detected primary language; single identifiable change."},
      {"name": "Attempt history", "grade": "pass", "evidence": "Issue created 2026-09-10, 11 days old, well under the 730-day threshold, so the failure condition cannot trigger."},
      {"name": "Available work", "grade": "pass", "evidence": "Open, no assignee, no open/linked PR found; only claim is ApoorvThite's 2026-09-21 comment (author_association NONE), which the Path Review house rule says does not block the issue."},
      {"name": "Compatible contribution policy", "grade": "pass", "evidence": "Same repo-wide CONTRIBUTING.md silence on AI-assisted workflows."},
      {"name": "Verification foothold", "grade": "pass", "evidence": "Body gives a concrete repro (2 Python files vs 6 vendored JS files misreport JavaScript as primary) and names failing tests `test_node_modules_excluded` and `test_build_directory_excluded`."},
      {"name": "Newcomer invitation", "grade": "pass", "evidence": "Labels: bug, good first issue, agent, tier-1."}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

**Run history**

I ran the full evaluation on September 21, 2026. The official script checked all 20 cases using my installed rubric and the pinned Sonnet model. The result was:

```text
categories: claimed 4/4  clear-accept 7/8  dead-repo 3/3  policy 1/1  scope 3/4
agreement: 18/20 scored items  (bar: 18/20: PASS)
```

Before the successful run, I clarified that repository continuity means `not archived AND (has a push within 180 days OR a release within 365 days)`, and a quick maintainer response only counts as recent activity if it happened within 90 days. I made these changes before getting any scored results. I did not run smaller sets of cases or change the rubric after the passing run. `eval-run.txt` was saved by `run_eval.py --save-run` and was not edited by hand.

**Issue analysis**

For **issue-19**, the rubric returned **reject**, but the expected answer (gold label) is **accept**. The issue says, `There are two potential causes which should be fixed:`. It lists slow matching and a screen update that waits for matching to finish. Under `Additional suggestions:`, it suggests multiprocessing, matching only expanded categories, and applying rewrites in a separate thread.

The run failed the `Bounded contribution` check for this reason:

> Issue lists two competing unresolved root-cause hypotheses plus three separate additional-suggestion subprojects (multi-processing, category-scoped matching, separate rewrite-application thread) with no maintainer narrowing to a single change.

The model treated the suggestions as several separate tasks. I think it was too strict here. The person who opened the issue is a `COLLABORATOR`, and all the suggestions address the same problem: selecting a large subgraph freezes the screen. That may explain why the gold label accepts it. The model also used the word `competing`, but the issue never says that only one of the two causes can be true.

All other required checks passed. The preferred checks `Verification foothold` and `Newcomer invitation` failed, but preferences do not affect the final verdict. Removing them would not change this result.

**Check rationale**

The current `Bounded contribution` row in `tools/issue-select/rubric.md` is quoted exactly:

> | Bounded contribution | Issue body, labels, and full comment thread, especially maintainer clarification of the requested change. | The issue asks for one identifiable code, test, documentation, or configuration change. Reject an umbrella/tracking issue with independent subprojects, a pure usage/support question, unresolved competing designs, or an explicit maintainer warning that the fix requires substantial core-internals work. A short description, missing reproduction steps, or a missing good-first-issue label does not by itself fail this check. A checklist implementing one outcome is not an umbrella issue. | required |

A short issue can still describe a clear task, while a detailed issue with a beginner-friendly label can still be too broad. I look at what needs to change and read the comments in case a maintainer has explained the scope more clearly. Steps to reproduce the problem would help me get started, but I would not reject an otherwise suitable issue just because they are missing, so I kept them as a preference under `Verification foothold`.

**Trade-offs**

The sentence `A checklist implementing one outcome is not an umbrella issue.` allows a task to have several related steps. But **issue-20** shows a risk: the rubric accepted it while the gold label rejected it. The issue says `Success looks like: logo tool in the shapes toolbar` and lists placement, resizing, movement, and correct export. It also says `Logo asset TBD.` The check passed for this reason:

> Issue requests one new toolbar shape with stated success criteria and an explicit out-of-scope carve-out; no maintainer warning of core-internals difficulty (0 comments).

Issue-20 sounds like one task, but it may need changes to the toolbar, shape data, and export code. A maintainer has not confirmed that this feature is wanted. Meanwhile, issue-19 was rejected even though its suggestions address one bug.

Requiring maintainer approval for every feature might catch issue-20, but it could also reject useful new requests. Accepting every issue with one main goal could let in tasks that are too large. My rubric passed the required score but did not match the expected answers on these two cases. Next, I would make the rule clearer about which steps are required and which are only suggestions, then test both cases again.

---

## Selection rationale

**Selection rationale**

In #56, text without headings is dropped before the system can use it to answer questions. I have worked with Python, backend services, and RAG, and the issue points to one part of `StructuralChunker` and an existing test. I would first get the project running and reproduce the bug, then estimate how much time the fix will take alongside my other coursework. The skill checked that the project is active, the task is small enough and available, and the contribution rules allow the work. It ranked #60 first because its fix is smaller and clearer, but I chose #56 because I want to understand how missing text affects RAG answers. I would check that text and source information are kept, empty and large documents are handled, and documents with headings still work. Once the bug is fixed, I would also remove the relevant test's `xfail(strict=True)` marker. When I checked on September 21, #56 was open with no assignee or comments. I will check again before claiming it in Unit 2. Classmates can work on the same issue, so another student's claim alone would not block me; the main task should be explaining my plan clearly and showing how to reproduce the bug. I have not posted a claim comment yet.

---

Related paths: `eval-run.txt` in this directory; `tools/issue-select/` for the matching skill files.
