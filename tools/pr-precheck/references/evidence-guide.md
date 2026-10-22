# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

Eval: read Plan context (accepted scope, exclusions, repro and deviations), then Candidate PR / Diff, Title, and Description. For example calib-01 plans removal of the first duplicate key only; the one-line deletion and description both retain the effective second value. Live: pair plan.md and its Deviations with git diff main...HEAD, then compare the first-line title and all claims in pr_draft.md; verify the issue and posted plan on the issue thread.

Good evidence accounts for additions and omissions in both directions. Every material changed behavior belongs to the plan or a reasoned recorded deviation; the description says what actually ships. A disclosed reduced outcome can pass. A claim that all planned work shipped while the diff omits a behavior cannot.

## Test evidence (harness category: not-tested)

Eval: pair Plan context's repro and Test plan with Candidate PR / Test evidence and the Description's testing claims; read Repo facts for check requirements. In calib-01 the strict parser's DuplicateOptionError becomes parsed OK and git config prints the retained effective value. Live: use plan.md's repro/test plan, the posted Unit 2 repro or house repro, and test_evidence.md command/output records; compare against pr_draft.md's checkboxes and docs/CONTRIBUTING.md/.github/PULL_REQUEST_TEMPLATE.md commands.

Good evidence names the changed-path input and observable outcome, plus real attempts/results for applicable repository checks. Distinguish executed tests from proposed tests, mocked dependencies from a real browser/database run, prior baseline evidence from current evidence, and empty suites from passes. A failed attempt with its reason can be honest evidence; missing required attempts and unsupported success claims cannot.

## Diff quality (harness category: unreviewable)

Eval: inspect Candidate PR / Diff and Commits against Plan context and the issue. Live: inspect the full git diff main...HEAD and git log main..HEAD, not only the stat or the author's summary. Check git status for code not included in that committed view.

Good diffs contain the issue fix and necessary supporting changes/tests. Debug prints, commented-out experiments, unrelated cleanup, and broad formatting churn fail even if the description admits them. A small deletion such as calib-01 needs no artificial complexity or extra commits to be reviewable.

## Standards and comms (harness category: standards-wall)

Eval: read Repo facts for template sections, contribution instructions and stated AI policy, and Thread highlights for explicit direction; compare with Candidate PR / Title, Description and Commits where applicable. Calib-01 has no template or stated AI policy, so do not invent either. Live: read .github/PULL_REQUEST_TEMPLATE.md, docs/CONTRIBUTING.md and referenced policies, the live issue discussion, scope.md house rules, and pr_draft.md. The Unit 4 instructions additionally require an AI-use disclosure under Notes for Reviewers and permit pending CI before opening a PR.

Good content fills each required section meaningfully or explains N/A, names the issue, accurately reports checks, and includes required disclosure in the author's own voice. Boilerplate placeholders, ignored maintainer requests, and absent required disclosure fail. Fidelity of description versus diff is evaluated separately in plan-fidelity. Live voice-guide.md notes are separate unless a rubric row explicitly gates on them.
