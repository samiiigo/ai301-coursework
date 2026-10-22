# Procedure: how this tool grades a PR package

## Read order

1. Determine live or eval mode. In live mode read scope.md first and enforce refusal conditions, then voice-guide.md. In eval ignore both and use only the supplied bundle.
2. Read rubric.md, this procedure, and references/evidence-guide.md. Record check order, required/preferred weights, and the verdict rule; stop if the rubric or procedure is empty.
3. Read issue context, thread direction, and repo requirements. List requested behavior, template sections, required commands, and explicit policies. In live mode retrieve the issue discussion and read the local PR template and docs/CONTRIBUTING.md. The Unit 4 pre-opening workflow defers CI; record that specific exception, not a general exemption from standards.
4. Read the reproduction and accepted plan before the diff. Record in-scope/out-of-scope boundaries, expected files and behaviors, planned tests, and Deviations. Use the house plan/repro if supplied.
5. Read the full diff and commit list. Live: use git diff main...HEAD and git log main..HEAD, record HEAD and base, and use git status --short to flag excluded uncommitted code. Do not treat documentation preparation files as code in the committed diff.
6. Read test evidence, then the title and description last. This prevents a confident summary from replacing comparison against actual artifacts.

## Evidence gathering

1. Plan fidelity: pair each changed hunk/behavior with a plan item or an explicit deviation and reason. Also map plan items to the diff to catch silent omissions. Compare each material title/description claim with the implementation and note any narrower, honestly stated outcome.
2. Test evidence: pair the original repro and each planned behavior/boundary with its before, expected after, observed after, command/steps, inputs, and environment. Mark missing or mocked evidence and disclosed limitations. Separately pair every repository-required check with an actual attempt and outcome. Do not turn no tests collected into a passing suite.
3. Diff quality: inspect all changed files and commits for debug statements, dead or commented-out code, unrelated behavior, and formatting-only churn. Record concrete hunks; do not judge by file count.
4. Standards and comms: map each stated template/policy/thread requirement to actual candidate content. Read AI disclosure where required. Match checkboxes to reported results. In live mode separately note voice rules with exact quotes. Never infer unstated repo requirements.
5. If a live source cannot be read, record which retrieval failed. Missing facts remain missing; do not use memory or author confidence to fill them.

## Check execution

1. Execute plan-fidelity, observable-proof, repository-checks, focused-diff, and stated-standards in table order.
2. Apply each row's pass condition to its gathered evidence. Re-read the relevant paired source sections if they conflict; no need to re-read the whole package when the deciding evidence is already explicit.
3. Use pass for supported satisfaction, fail for a demonstrated violation, and unclear for evidence absent or too incomplete to decide. Provide a short deciding quote or fact for each grade.
4. Evaluate honest deviations and limited outcomes according to each row. Do not demand all originally planned work if the plan and description openly narrow it, and do not let disclosure excuse unrelated hunks or missing required check attempts.
5. Never consult gold labels or change a rule within a run. Report a procedure gap in the summary and do not invent a replacement step.

## Verdict assembly

1. Apply rubric.md after every check is graded. All required checks must pass for accept; any required fail or unclear yields reject. Preferred checks never gate.
2. Summarize every check. For a reject, lead with the first failing or unclear required check in rubric order and quote its deciding evidence; list the other failures too. For accept, cite the supporting pairings and disclose material limitations.
3. Include live voice notes separately, without changing the verdict on their own.
4. End with the fixed fenced JSON schema from SKILL.md: item, all checks once in rubric order with one-line evidence, and verdict. Nothing follows it.
