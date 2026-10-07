# Procedure: how this skill grades a plan package

## Read order

1. In live mode, read scope.md and confirm the repo; stop if it is unset or outside scope. Read voice-guide.md. In eval mode, use only the bundle and ignore those two files.
2. Read the rubric and evidence guide. Read the issue, thread and repo requirements, then the repro evidence before the plan and comment, so the proposed cause is checked against observed behavior.

## Evidence gathering

1. Record the reproduced input, actual result, expected result, and the plan's explanation of the cause.
2. Record the changed areas, exclusions, implementation steps, and prerequisites for Scope and Executability.
3. Pair each proposed test with the repro behavior or nearby regression it checks; record its expected observable result.
4. Record claims, material unknowns and how they will be checked, plus any deviations, for Honesty.
5. Compare the comment with the plan, maintainer requests, and explicit repo requirements for Thread and conventions. Follow the evidence guide's locations in either mode. In eval mode, use the course premise that every candidate used assistance: enforce explicit tool-and-extent disclosure requirements for comments, but do not apply PR-only requirements to a plan comment.

## Check execution

1. Grade every row in table order using its pass condition and gathered evidence. Re-read the relevant source if a fact is missing or conflicts; do not stop after one failure.
2. Use pass when the condition is met, fail when evidence contradicts it, and unclear when required evidence remains absent. Quote the deciding fact for each grade. Do not require extra sections or reject a concise plan merely for being short.

## Verdict assembly

1. Apply the rubric's verdict rule, including unclear. In live mode, separately report any broken voice-guide rule with its quote.
2. Summarize the deciding checks, then emit the final fenced JSON required by SKILL.md: item, every check with name/grade/evidence, and accept or reject. Put nothing after it.
