# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Specific claim | Claim comment read against the issue context and relevant thread requests. | Names the concrete behavior being investigated and a relevant reproduction or verification action. The claim shows understanding of this issue rather than offering generic help or guaranteeing a fix. | required |
| Environment | Repro report's environment record compared with the issue's affected setup. | Records versions, platform, dependencies, and configuration needed to interpret this issue's result. Relevant differences from the reported setup are explicit; another contributor can identify what was tested. | required |
| Rerunnable steps | Repro report's setup, inputs, commands or UI actions, and trigger. | A stranger can reach the tested condition from the stated starting point without guessing required setup, input contents, or actions. Referenced prerequisites are supplied or accessible. | required |
| Relevant artifacts | Repro report's quoted output, logs, screenshots, or test results compared with the issue's trigger and expected/actual behavior. | Artifacts show the tested input and outcome on the relevant path, not an adjacent error or startup alone. A cannot-reproduce report passes with output from a concrete attempt and explicit limits, even if a suspected trigger condition could not be achieved; it must not claim that condition was tested. | required |
| Honest conclusion | Claim and report conclusions compared with the environment, steps, and artifacts. | Says reproduced, cannot reproduce, or partially observed in terms supported by the evidence. Limits, untested conditions, and relevant differences remain explicit; local success does not prove a universal fix. | required |
| Repo conventions | Both comments compared with repo-facts, templates, contribution policy, and applicable live house rules. | Comments are understandable, respectful, and meet applicable reporting requirements. If policy requires AI-use disclosure in issue comments, the package must state the tool and extent of assistance; missing disclosure fails (course eval packages are treated as AI-assisted). No stated policy, or a PR-only disclosure rule, adds no issue-comment requirement. | required |

## Verdict rule

Accept only when every applicable required check passes. Reject if any required check fails or is unclear. Preferred checks never change the verdict. In claim-only live mode, apply the skill's exclusions for checks needing a repro report.
