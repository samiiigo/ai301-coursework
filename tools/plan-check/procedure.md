# Procedure: how this skill grades a plan package

## Read order

1. Determine whether the run is live mode or eval mode. In live mode, read `scope.md` first and stop if the issue is outside the configured Path Review repository or the Repo line is still a placeholder.
2. Read `rubric.md` and record every check, its evidence source, pass condition, weight, and the verdict rule before looking at the candidate plan.
3. Read `references/evidence-guide.md` so each evidence family has a known location.
4. Read the issue context and thread highlights first. Record the requested behavior, explicit constraints, relevant files, and any maintainer instructions.
5. Read the repo-facts block or, in live mode, the repository contribution docs. Record branch naming, required tests/checks, templates, and any AI-disclosure requirement that applies to issue comments.
6. Read the reproduction evidence before the plan. Record the exact observed failure, the expected behavior, the decisive steps/artifacts, and any implementation facts the reproduction established.
7. Read the candidate plan completely. Record its diagnosis, in-scope/out-of-scope boundaries, files, approach, test plan, risks/unknowns, and deviations.
8. Read the candidate plan comment last and compare it with both the plan and the issue thread. This order prevents the comment's confidence or wording from biasing the evidence read.

## Evidence gathering

1. For diagnosis evidence, pair each causal statement in the plan with the specific repro fact it claims to explain. Record supporting quotes or mark the support absent.
2. For cause-targeting evidence, trace the plan's proposed change from the reproduced failure mechanism to the expected corrected behavior. Record whether the same failure path would be changed or bypassed.
3. For scope evidence, list every area/file the plan says it will touch and every explicit out-of-scope item. Flag work that is not necessary for the stated issue.
4. For executability evidence, extract the concrete implementation flow: entry point, backend/service work, frontend work, data passed between them, and where validation/error handling occurs. Note any material step that still requires invention.
5. For test evidence, map each planned test to a reproduced step or issue requirement. Record the observable assertion for: the original failure, successful behavior after the fix, and any boundary behavior named by the issue.
6. For honesty evidence, record every risk, assumption, unknown, or deviation. Compare certainty in the diagnosis/approach with what the repro and repo facts actually establish.
7. For communications evidence, compare the plan comment with the issue body/thread and repo conventions. Record whether it is issue-specific, self-contained, and compliant with any stated contribution-policy requirement.

## Check execution

1. Execute checks in this order: `diagnosis-grounded`, `cause-targeted`, `scope-bounded`, `executable`, `test-proves-fix`, `uncertainty-honest`, `thread-and-conventions`.
2. For each check, use only the evidence family named in that rubric row plus the already-recorded issue/repro/repo facts needed by that row.
3. Grade `pass` only when the stated pass condition is satisfied by evidence present in the package.
4. Grade `fail` when present evidence contradicts the pass condition.
5. Grade `unclear` only when the evidence required by the check is genuinely absent or too incomplete to decide; do not use `unclear` merely because the executor is uncertain.
6. Record one short deciding quote or fact for every grade. Do not replace evidence with general comments such as "looks good."
7. Do not rescue a failed check with polish from another section. For example, a detailed test plan cannot make an unsupported diagnosis pass.

## Verdict assembly

1. Apply the verdict rule from `rubric.md` after all checks are graded.
2. Treat every `unclear` on a required check as a failure.
3. Return `accept` only when all required checks pass; otherwise return `reject`.
4. In the readable summary, name each failed or unclear required check and the evidence that decided it. In live mode, also report any voice-guide rule the draft comment breaks.
5. Emit the required fenced JSON block last. Include every check exactly once, with `pass`, `fail`, or `unclear`, one-line evidence, and the final binary verdict.
