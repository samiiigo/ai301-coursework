# Unit 4 — Test and Submit

## Your pull request

**Pull request**

Not opened, by explicit request. This preparation intentionally stops before committing, pushing, PR creation, or course-portal submission. The PR URL and the points that require an opened PR remain pending; no branch URL is substituted for a PR link.

Local draft: `D:/repo/codepath/pathreview-ai301-fa26-s3/pr_draft.md`. Full captured evidence: `D:/repo/codepath/pathreview-ai301-fa26-s3/test_evidence.md`.
Issue: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40
Course repository to submit later: https://github.com/samiiigo/ai301-coursework (confirmed against the local origin remote).

**Branch**

`fix/40-public-review-links`

The existing implementation HEAD is `0fa7cfeb9e83ed8b7c7dbf82d46ff80463d57a11`. No new commit or push was made during Unit 4 preparation.

## Eval iterations

**Run history**

One full run using the installed `C:/Users/samyo/.claude/skills/pr-precheck` and the starter's unchanged `run_eval.py`, with the harness-pinned Sonnet model:

> `agreement: 18/20 scored items  (bar: 18/20: PASS)`

> `categories: clear-accept 5/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`

Command, from the starter's eval folder:

```text
python run_eval.py --skill C:/Users/samyo/.claude/skills/pr-precheck --save-run eval-run.txt --out ../../unit4-evidence/eval-results-01.json
```

The complete harness-written output was copied byte-for-byte to this folder's `eval-run.txt`; its provenance header was not edited. Every category has at least one match. No partial runs or revisions followed this run because it met 18/20 and the category floor. The two disagreements were `pkg-02` and `pkg-08`, both gold accept but rubric reject; they are retained honestly rather than described as perfect agreement. These files are prepared locally and are not yet committed.

**Package analysis**

`pkg-02` (Textualize/rich#4208): my rubric returned `reject`; the gold label is `accept`. `observable-proof` was graded `unclear`, which the verdict rule treats as a required failure. All other checks passed.

The package states:

> Expected-after per the plan: the record survives the failed save, and
> a successful save still clears it (covered by the new test's second
> half). `pytest tests/ -q` passes (1462 passed, 12 skipped).

The grader's deciding evidence was:

> Repro and new test exercise only save_text; no execution evidence or disclosed limit for the changed save_html and save_svg paths, though the description claims all three fixed.

The diff applies the same export-without-clearing, write, then clear sequence to all three methods. The repro and the added regression directly exercise save_text, and the package reports a passing suite. The gold label accepts that focused proof; my check was applied more conservatively and demanded coverage or a disclosed limit for the other two changed methods. This is a false rejection against the answer key, not evidence that the gold label is wrong. I kept and documented the mismatch because the run already reached the stated target, while recognizing the check can be too strict for a mechanically repeated fix.

**Check rationale**

Exact current row from `tools/pr-precheck/rubric.md`:

> | observable-proof | Candidate test evidence paired with the original repro and the plan's test plan, including boundary cases. | Commands or concrete steps, inputs, and observed before/after outcomes establish the claimed behavior on the changed path. Relevant planned boundaries are exercised or their untested status and limits explicitly disclosed; a real negative or partial result may pass when the claims are narrowed accordingly. An assertion such as "tests pass", a test file without execution evidence, or proof of a different path does not pass. | required |

I adapted the Unit 3 test-plan idea into a comparison with executed PR evidence. Merely adding a test or writing "tests pass" does not establish that the original failure changed. The row requires an observable result on the changed path while allowing honestly reported negative/partial results. I rejected a blanket "all tests must pass" rule because the assignment accepts disclosed shortfalls and Path Review's integration directory currently contains no tests. I did not revise this wording after the full run; its conservative interpretation produced the pkg-02 mismatch above.

**Trade-offs**

The required proof and repository-check rows prefer explicit evidence over benefit of the doubt. This catches all four not-tested packages in the run, but falsely rejects pkg-02's representative regression and pkg-08's formatting statement. For pkg-08, the grader said:

> go generate, integration test and go test ./... are reported, but 'code formatted' is only asserted in the description with no command or outcome.

Gold accepts pkg-08; the candidate does report integration and Go tests and a clean cheatsheet regeneration, while stating that code is formatted. Requiring command-level formatting evidence is stricter than the answer key's reading. A future refinement could distinguish formatting attestations from behavioral test proof and allow representative tests for identical edits. That refinement has not been made or evaluated here. No check was loosened, so no canary rerun was necessary; the complete unchanged-tool run above remains the submitted-run artifact. The limitation I accept is false rejection of some adequately evidenced small PRs, not a claim that the check is optimal.


## Local draft precheck

The first live attempt was interrupted before a result was saved. The resumed Claude Sonnet run on October 9 returned `reject`: `plan-fidelity`, `observable-proof`, `repository-checks`, and `focused-diff` passed; `stated-standards` failed because all four existing application commit subjects omit the scope required by CONTRIBUTING.md. This live result is separate from the scored 18/20 evaluation run.

The remaining failure is now explicitly disclosed under Notes for Reviewers in `pr_draft.md`. The two non-gating voice suggestions were applied (plain success/error wording, removal of a defensive aside). These documentation edits do not repair the commit convention, and no new accept verdict is claimed. No commit was created or amended and no history was rewritten, as requested. Raw output: `D:/repo/codepath/unit4-evidence/live-precheck.txt`.
