# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

samiiigo

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40#issuecomment-5922330326

Hi, I'd like to take this as a first contribution. Issue [#40](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40) asks for a "Copy link" button that generates a read-only link to a review summary that works without login and expires after 30 days.

Next I'm going to inspect the current sharing behavior in frontend/src/pages/ReviewPage.tsx and the review routes in api/routes/reviews.py, including how access is currently protected. I'll reproduce the current behavior and report back with my findings before making any changes.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40#issuecomment-5922456109

## Reproduction Report

I reproduced the current sharing behavior for issue #40.

### Environment

| Tool | Version |
|---|---|
| OS | Windows 11 |
| Commit | `2f4e82f52efbcfcc57d65b3fa5348672163ca088` |
| Git | `2.54.0.windows.1` |
| Python | `3.14.7` |
| Node.js | `v24.18.0` |
| npm | `12.0.1` |
| Docker | `29.7.2, build a7dcaa6` |
| Docker Compose | `v5.5.0` |
| Browser | Chrome, with Incognito used for the unauthenticated test |

### Steps to reproduce

1. Started PostgreSQL and Redis with `docker compose up -d`.
2. Ran `make setup`.
3. Started the application with `make run`.
4. Opened `http://localhost:5173` and logged in with the seeded account `user1@example.com`.
5. Navigated to a completed review.
6. Clicked the **Share** button.
7. Pasted the copied URL into a text editor. The copied URL was:

   `http://localhost:5173/reviews/2b52d27d-3ccc-4e7f-a179-5e45a9380c93`

8. Opened a Chrome Incognito window with no active PathReview session.
9. Navigated to the copied review URL.

### Expected behavior

Per issue #40, the Share action should generate a read-only review link that can be opened without logging in and expires after 30 days.

### Actual behavior

Opening the copied URL while logged out redirected me to the login page instead of displaying a public read-only review.

The Share button currently copies the normal `/reviews/<review-id>` URL rather than generating a separate public share URL.

I also checked the current implementation:

- `ReviewPage.tsx` uses `window.location.href` in the Share handler, so it copies the current authenticated review URL directly.
- `/reviews/:reviewId` is wrapped in `ProtectedRoute`, which prevents unauthenticated users from viewing the review page.
- `frontend/src/services/shareService.ts`, which is referenced by the issue, does not currently exist in the repository.
- `api/routes/reviews.py` does not contain a public or token-based endpoint for accessing a shared review.

I could not directly test the requested 30-day expiration behavior because the current implementation does not create a public share token or expiring share URL.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

- Run 1: `agreement: 20/20 scored items  (bar: 18/20: PASS)`
- Confirming full run saved to `eval-run.txt`: `agreement: 20/20 scored items  (bar: 18/20: PASS)`

Both runs matched all 20 scored packages, and the category floor was satisfied:

> `categories: clear-accept 8/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`

The final agreement line in `eval-run.txt` is:

> `agreement: 20/20 scored items  (bar: 18/20: PASS)`

Because the first full run already agreed with all 20 gold labels, I did not need to use `--only` or revise the rubric based on an eval disagreement.

**Package analysis**

Package `pkg-01` (source: `httpie/cli#1640`, category: `clear-accept`):

- Rubric decision: `accept`
- Gold label: `accept`

The package's reproduction report gives a specific environment:

> `Environment: HTTPie 3.2.4 (pip), Python 3.12.4, multidict 6.6.0, macOS 14.5 (arm64).`

It also gives an exact command that another person could run:

> `$ http --offline post pie.dev/post 'header1: xyz' x=1`

The report clearly distinguishes the expected and actual behavior:

> `Expected: both requests carry Content-Type: application/json, since the body is a JSON object either way.`

and:

> `Actual: with exactly one custom header present, the Content-Type header is absent from the request, matching the report.`

My rubric therefore accepted the package because the environment is recorded, the reproduction steps are repeatable without guessing, and the shown output directly supports the claimed behavior. This matches the gold `accept` label.

**Check rationale**

Quote from `tools/repro-check/rubric.md`:

> | steps-complete | The repro report's steps, read against the input, command, flags, and configuration the issue itself gives to work from | Pass if a stranger holding only this package could run the steps top to bottom and land on the same run: every file's contents are shown or fully pinned down (not merely paraphrased in a way that could vary the result), and every command, flag, and setting needed is given, with no step depending on material the reader cannot obtain (a private repo, an unshared config, a resource the issue itself never pastes the content of). A detail the report leaves to the reader passes when it plainly cannot change whether the failure triggers (which package names fill an otherwise-valid list); it fails when the missing or swapped detail is exactly what decides the outcome — whether the failure actually fires is `artifact-matches-claim`'s question, not this one. Fail if a material step has to be invented, if the run depends on unobtainable material, or if a file's exact content is only paraphrased where the paraphrase could change the result. | required |

I kept this check because the main goal of a reproduction report is not just to describe a bug, but to give another person enough information to independently repeat the reproduction top to bottom. I preferred this wording over a looser requirement such as simply asking whether "steps are present," because a list of steps can still be incomplete if the reader has to invent material steps or guess unshared configurations. The pass condition makes the threshold concrete: every file, command, flag, and setting must be given so that a stranger can land on the same run without guessing.

**Trade-offs**

The `steps-complete` check intentionally favors strict reproducibility over giving incomplete reports the benefit of the doubt. Under this condition:

> `Fail if a material step has to be invented, if the run depends on unobtainable material, or if a file's exact content is only paraphrased where the paraphrase could change the result.`

That means a report describing the correct bug could still fail if important reproduction details are missing (e.g. `pkg-18` where reproduction steps rely on an unshared config/private monorepo). The trade-off is that the rubric can reject a genuine report whose author observed the right behavior but did not document enough for someone else to repeat it.

I accepted that trade-off because this assignment treats reproducible evidence as more important than a correct-sounding conclusion. My first full eval still matched `20/20` gold labels and every category, so this stricter threshold did not require any further revision or canary re-runs.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
