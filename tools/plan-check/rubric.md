# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis | Stated cause and approach against the issue and repro evidence. | The cause explains the observed failure, and the change addresses that cause instead of hiding its symptom. | required |
| Scope | In-scope changes, exclusions, and affected files in the plan. | The work is one bounded fix for this issue; supporting changes are necessary, with unrelated rewrites excluded. | required |
| Executability | Named files or areas, approach, and order of work. | Another contributor can start implementing the change without guessing its key behavior or missing a prerequisite. | required |
| Test plan | Planned checks against the repro steps and observed output. | The plan rechecks the failing behavior with an observable expected result and checks nearby behavior the change could break. | required |
| Honesty | Claims, risks, unknowns, and any deviations against the available evidence. | No invented completed results or hidden deviations. A plausible cause consistent with the repro may remain unproven if the plan gives a concrete way to test it; material limits are stated. | required |
| Thread and conventions | Plan comment against thread highlights, repo requirements, and the plan. | The comment explains this plan, respects relevant maintainer requests and explicit contribution requirements, and makes no unsupported promises. | required |

## Verdict rule

Accept only when every required check passes. Fail or unclear (`?`) on any required check means reject. Preferred checks, if added, do not change the verdict.
