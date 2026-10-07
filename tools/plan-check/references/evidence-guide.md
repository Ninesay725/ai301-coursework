# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

Use the issue, Repro evidence, and Candidate plan's cause and approach. Live: read the issue and my posted repro, then the evidence quoted in the drafts. The cause must explain that observed failure; a workaround that hides it is not a cause-level fix.

## Scope

Use the plan's changes, exclusions, and files. Good scope is one fix with necessary supporting work; vague promises to redesign nearby systems do not bound it.

## Executability

Use the plan's file or area names, implementation steps, and dependencies. A contributor can identify the first change and its intended behavior; unresolved prerequisites must have a concrete next step.

## Test plan

Compare the plan's tests with the repro's inputs, commands, and outputs. Good tests revisit the failure, name the expected result, and check affected neighboring behavior. Manual checks can be enough when they are decisive.

## Honesty

Compare the plan and comment's claims, risks, unknowns, and Deviations with the repro evidence. A plausible cause can remain a hypothesis when paired with a decisive test; it must not claim an unrun check passed. Note minor wording or attribution issues separately unless they change the diagnosis, scope, or test outcome. Material unknowns need a check, and deviations need a reason.

## Comms

Compare Candidate plan comment with Thread highlights and Repo facts; live, read the issue discussion and the repo's contribution docs. Respect explicit requests and contribution conditions, without inventing requirements the repo never states. The comment should explain its own plan and agree with the draft. Missing optional polish is not a failure.
