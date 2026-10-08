# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis-grounded | The candidate plan's diagnosis read against the repro-evidence block's observed behavior and implementation facts | Pass if the diagnosis explains the reproduced failure without contradicting the shown evidence, and any stated cause is supported by facts present in the package rather than guessed. Fail if it ignores a decisive repro fact, claims a cause the evidence does not support, or describes a different failure. | required |
| cause-targeted | The plan's proposed approach and files read against the diagnosis and repro evidence | Pass if the planned change addresses the mechanism that produces the reproduced failure rather than only hiding the visible symptom, and the connection from cause to change is explicit enough to verify. Fail if the repro would still fail for the same reason after the proposed work. | required |
| scope-bounded | The plan's in-scope and out-of-scope statements, named files/areas, and approach | Pass if the work is one bounded change tied to the issue, names what will change and what will not, and avoids unrelated cleanup or rewrites. New files are allowed when they are directly needed for the issue. Fail if the plan expands into unrelated refactors, redesigns, or repository-wide changes. | required |
| executable | The plan's files-to-touch list and approach, read against the repo-facts block and issue context | Pass if a stranger could begin implementation from the plan without asking the author what component to change, what behavior to add, or how the pieces connect. The plan must name concrete files or areas and the main data/control flow. Fail if material implementation decisions are left as vague verbs such as "fix sharing" or "update backend." | required |
| test-proves-fix | The plan's test plan read against the repro-evidence steps and expected/actual behavior | Pass if the tests re-run the decisive reproduction path or an equivalent real-code check, state the observable post-fix result, and include coverage for the issue's important boundary behavior. Fail if the plan only says to run generic tests, checks implementation details without observing the user-visible failure, or omits a required issue behavior such as expiry or unauthenticated access. | required |
| uncertainty-honest | The plan's risks, unknowns, assumptions, and Deviations section when applicable | Pass if unresolved implementation choices or risks are named as unknowns/risks rather than presented as established facts, and any known deviation from a posted plan is recorded with why. Fail if uncertainty that could materially change the build is hidden behind certainty or a known deviation is omitted. | required |
| thread-and-conventions | The candidate plan comment read against the issue/thread highlights and repo-facts contribution conventions | Pass if the comment is specific to this issue and reproduction, does not piggyback on another student's plan, and follows stated repository conventions that apply before building (including branch/test/contribution or AI-disclosure rules when the package says they apply). Fail if it ignores a maintainer constraint, contradicts the thread, or is generic enough to fit another issue. | required |

## Verdict rule

Accept (ready) only if every required check passes. A `fail` or `unclear`
on any required check produces reject (hold). `unclear` counts as a fail
because evidence that is missing from the package cannot support a plan
that is ready to post and build from.
