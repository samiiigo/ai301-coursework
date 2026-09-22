# Unit 1 — Issue Selection

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40

Selected issue: #40. The installed skill accepted both candidates and ranked #40 first using the fit profile; #32 is the comparison candidate.

**Verdict output**

## Evidence Summary

**Repo facts (apply to both issues):** Not archived; default branch `main`; last push 2026-09-16 (6 days before today, 2026-09-22); no published releases; last 5 commits all human-authored by `Aburke225` (Andrew Burke), spanning 2026-08-24 to 2026-09-16; zero open PRs repo-wide; `docs/CONTRIBUTING.md` states no AI-assisted/AI-generated contribution policy (just "comment on the issue to let others know you're working on it"); `.github/PULL_REQUEST_TEMPLATE.md` has no AI-use disclosure requirement; no `AI_POLICY.md`/`AI_USAGE.md`/`AGENTS.md` file exists in the tree.

### Issue #40 — "Add a 'Copy link' button to share a public review summary"
| Check | Grade | Evidence |
|---|---|---|
| Maintainer activity | pass | 5/5 recent default-branch commits human-authored (Aburke225), most recent 2026-09-16 |
| Repository in use | pass | Not archived; last push 2026-09-16, 6 days old, well within 180 days |
| Bounded contribution | pass | Single feature: shareable read-only link, 30-day expiry, names 3 files (`ReviewPage.tsx`, `shareService.ts`, `reviews.py`); not an umbrella; issue is 12 days old |
| Available to work | pass | No assignees; empty comment thread (no claims); empty timeline cross-references; 0 open PRs repo-wide |
| AI contribution policy | pass | No ban found in CONTRIBUTING.md, PR template, or dedicated AI-policy files |
| Maintainer guidance (preferred) | pass | Issue opened by a Collaborator, names specific files and a scoped acceptance target (shareable expiring link) |

**Verdict: accept**

### Issue #32 — "`DELETE /profiles/{profile_id}` leaves the profile's embeddings in the vector store"
| Check | Grade | Evidence |
|---|---|---|
| Maintainer activity | pass | Same repo-wide commit evidence as above |
| Repository in use | pass | Same repo-wide evidence as above |
| Bounded contribution | pass | Single bug fix: cascade-delete embeddings on profile deletion, names 3 files (`profiles.py`, `profile_service.py`, `vector_store.py`); issue is 12 days old |
| Available to work | pass | No assignees; empty comment thread; empty timeline cross-references; 0 open PRs repo-wide |
| AI contribution policy | pass | Same repo-wide evidence as above |
| Maintainer guidance (preferred) | pass | Issue opened by a Collaborator, names specific files and a concrete bug behavior to verify against |

**Verdict: accept**

### Ranking
Both accepted. Per the fit profile in `scope.md`, the student explicitly prefers **#40** — it combines the frontend work (React `ReviewPage.tsx`) they enjoy with backend processing (`shareService.ts`, `reviews.py`), matching their stated interest in prototyping across the stack; #32 is the stated comparison candidate. (Note: #40's 5–8 hr estimate may exceed the student's ~5 hr budget, while #32's 4–6 hr estimate fits more comfortably — but per `scope.md` this is a planning consideration, not a rank-reversing factor, since the student's own stated preference already names #40 first.)

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "5/5 recent default-branch commits human-authored by Aburke225, latest 2026-09-16"},
      {"name": "Repository in use", "grade": "pass", "evidence": "Not archived; last push 2026-09-16, 6 days before today (2026-09-22)"},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Single shareable-link feature naming ReviewPage.tsx, shareService.ts, reviews.py; no umbrella language"},
      {"name": "Available to work", "grade": "pass", "evidence": "No assignees; 0 comments; 0 open PRs repo-wide; no cross-referenced PRs in timeline"},
      {"name": "AI contribution policy", "grade": "pass", "evidence": "CONTRIBUTING.md and PR template contain no AI-use ban or disclosure requirement; no dedicated AI policy file exists"},
      {"name": "Maintainer guidance", "grade": "pass", "evidence": "Opened by a Collaborator naming specific files and a scoped 30-day-expiry acceptance target"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/32",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "5/5 recent default-branch commits human-authored by Aburke225, latest 2026-09-16"},
      {"name": "Repository in use", "grade": "pass", "evidence": "Not archived; last push 2026-09-16, 6 days before today (2026-09-22)"},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Single cascade-delete bug fix naming profiles.py, profile_service.py, vector_store.py; no umbrella language"},
      {"name": "Available to work", "grade": "pass", "evidence": "No assignees; 0 comments; 0 open PRs repo-wide; no cross-referenced PRs in timeline"},
      {"name": "AI contribution policy", "grade": "pass", "evidence": "CONTRIBUTING.md and PR template contain no AI-use ban or disclosure requirement; no dedicated AI policy file exists"},
      {"name": "Maintainer guidance", "grade": "pass", "evidence": "Opened by a Collaborator naming specific files and a concrete deletion-cascade bug to reproduce"}
    ],
    "verdict": "accept"
  }
]
```

## Eval iterations

**Run history**

Two initial attempts produced no agreement score: one stalled under restricted networking and was interrupted; the other was interrupted after authentication failures. A diagnostic reported "Failed to authenticate. API Error: 401 OAuth access token has been revoked." Neither counts as a completed evaluation. After signing in again:

1. First complete run: "agreement: 17/20 scored items  (bar: 18/20: below the bar)". It disagreed on issue-01, issue-19, and issue-20. The original transcript is preserved in eval-run-01.txt.
2. Clarified Bounded contribution so coordinated documentation edits for one feature are not rejected just because they touch multiple files. Targeted rerun of issue-01 and issue-07: "agreement: 2/2 scored items". This partial run tested the change and a repository-inactivity canary; it is not the submitted full run.
3. Confirming complete run with the current rubric: "agreement: 18/20 scored items  (bar: 18/20: PASS)". This is the harness-written eval-run.txt. Category results: "categories: claimed 4/4  clear-accept 7/8  dead-repo 3/3  policy 1/1  scope 3/4".

**Issue analysis**

Scored snapshot issue-01 is conda/conda#16475, "Add permanent docs for installing PyPI packages with `conda install`". The initial rubric verdict was reject; the gold label is accept. The initial run's scope evidence said: "Issue asks for a new task page plus edits to manage-pkgs.rst, pip-interoperability.rst, new-features.md, and optionally troubleshooting.rst — multiple independently shippable doc subprojects bundled as one issue."

The snapshot instead ties these edits to one documentation outcome: "Keep the feature card short and point users to the new task page." Moving instructions to a permanent page and updating pointers are coordinated parts of that outcome. The revised check makes that distinction explicit. In the final run, the rubric verdict is accept and the gold label is accept. This analysis uses the frozen eval issue-01, not a current Path Review issue with the same number.

**Check rationale**

The complete current Bounded contribution row from tools/issue-select/rubric.md is quoted below:

> | Bounded contribution | Issue body, labels, complete comment thread, and linked PR history; live equivalents in the issue and Development section. | The requested outcome is one identifiable bug fix, documentation change, test, or small feature. Coordinated edits to multiple documentation pages describing the same feature count as one bounded contribution; file count and checklist length alone do not make an umbrella. Reject explicitly identified umbrella/tracking work with independently scoped subprojects, unresolved competing designs, an explicit requirement to change core parser/compiler/architecture internals, or a pure usage question without a requested project change. Also reject an issue at least 730 days old with at least 2 closed unmerged implementation attempts. A short description, missing reproduction steps, or an acceptance checklist alone is not a failure when the requested change is identifiable. | required |

The clarification prevents file count or checklist length from acting as a substitute for scope. Several documentation files can support one concrete outcome. The check still rejects explicit umbrella projects, unsettled designs, required core-internal changes, pure usage requests, and old issues with repeated unsuccessful implementation attempts.

**Trade-offs**

The clarification changed issue-01 from reject to accept, matching its gold label. The issue-07 canary remained reject in the targeted rerun, and the full confirmation still matched all three dead-repo cases. This check remains conservative about performance work: the final run reports "issue-19  accept  reject" because it treats that snapshot's proposed performance changes as too broad. It also misses the scope concern in issue-20 (gold reject, rubric accept), whose concrete feature description passes the current rule. The final score is 18/20, not perfect agreement; the policy, availability, and activity checks do not resolve those scope judgments.

## Selection rationale

**Selection rationale**

1. I chose #40 because it combines frontend work with some backend processing, and I love making prototypes and designs. Even though its estimated 5–8 hours exceeds my original five-hour budget, I would love to work on it because I am learning React and it would give me hands-on experience.
2. The verdict identified #40 as one defined feature in an active repository, with no current assignee or linked work. Beyond those checks, I weighed my interest in prototypes and design and the opportunity to learn React through hands-on work. That learning opportunity makes the extra time worthwhile to me; it affects my choice without changing the rubric's accept/reject verdict.
3. I do not expect much difficulty claiming #40 because it was open and unassigned when checked, and the course allows students to work on shared issues. I will check its status again before claiming it in Unit 2. I have not posted a claim comment yet.




