# Unit 1 preparation status

Prepared on 2026-09-22. This is a working note, not the graded selection write-up.

- Filled tools/issue-select/rubric.md with five required evidence checks and one preferred check.
- Updated scope.md to codepath/pathreview-ai301-fa26-s3 and the supplied experience: Python, Java, C++, SQL, React, JavaScript; five hours available.
- Copied rubric.md and scope.md into the installed skill at C:/Users/samyo/.claude/skills/issue-select/.
- First full-eval attempt: interrupted after stalling with no verdicts or agreement score under restricted networking.
- Second full-eval attempt: interrupted after Claude authentication errors; no valid agreement score. Diagnostic returned: "Failed to authenticate. API Error: 401 OAuth access token has been revoked."
- No completed evaluation or live-mode grading exists yet. eval-run.txt remains the original placeholder; do not submit it as an evaluation.

## Resume

1. Run `claude auth login` and sign back into the CodePath account.
2. Run the official harness from the starter materials' eval directory, using the installed rubric and SKILL.md. Save the complete run to beat-1-sandbox/unit-1/eval-run.txt and detailed results to eval-results.json. Do not edit the harness output.
3. Inspect disagreements and category totals. Revise with partial runs if needed, then save a confirming full run.
4. The student chose these two candidates on 2026-09-22; these replace the initial suggestions:
   - https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40 — Public read-only review sharing, copy-link button, and 30-day expiry; estimated 5–8 hours.
   - https://github.com/codepath/pathreview-ai301-fa26-s3/issues/32 — Delete profile embeddings from the vector store; estimated 4–6 hours.
   Both were open, unassigned, and had zero comments when checked. Neither has a live rubric verdict yet.
5. Choose an accepted issue and paste the actual output verbatim into selection.md. Fill Run history, Issue analysis, Check rationale, and Trade-offs from actual run evidence. Ask the student for their own selection reflections.
6. Upload the final skill files and Unit 1 artifacts using the assignment's GitHub web flow. Submit the entire repository link: https://github.com/samiiigo/ai301-coursework . Verify grader visibility before submitting.

Do not post a claim comment in Unit 1.


## Evaluation progress after authentication was restored

- Complete run 1: "agreement: 17/20 scored items  (bar: 18/20: below the bar)". Preserved unchanged as eval-run-01.txt with details in eval-results-01.json.
- Revised only the Bounded contribution check to distinguish coordinated documentation edits from explicitly identified umbrella/tracking projects.
- Targeted run 2: "agreement: 2/2 scored items" for issue-01 and issue-07. Results are in eval-partial-02.json. This is not a full run.
- Confirming full run 3 completed: 18/20, PASS; see Current status below.
- The student prefers #40: "because it is a front end thing with some backend processing, i love to make prototypes and designs". Scope now records that preference. #32 remains the comparison candidate.

## Current status

- Confirming complete run: "agreement: 18/20 scored items  (bar: 18/20: PASS)". Saved by the harness as eval-run.txt; 20 results, zero execution errors.
- Installed skill live run completed: both #40 and #32 accepted, with #40 ranked first. Actual output is saved as live-verdict.txt and copied verbatim into selection.md.
- #40 selected based on the student's stated preference. No issue comments or claims were posted.
- selection.md contains the evaluation write-up and all three completed selection reflections, incorporating the student's React learning motivation and approved claiming-difficulty wording. No reflection placeholders remain.
- Nothing has been uploaded or submitted yet.

