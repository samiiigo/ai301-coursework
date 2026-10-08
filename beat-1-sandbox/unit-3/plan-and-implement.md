# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

samiiigo

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40#issuecomment-6050520166

In my [Unit 2 reproduction](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40#issuecomment-5922456109) on commit `2f4e82f`, I ran `docker compose up -d`, `make setup`, and `make run`. Share copied `/reviews/2b52d27d-3ccc-4e7f-a179-5e45a9380c93`; opening it in Chrome Incognito redirected to login. `ReviewPage.tsx` copies `window.location.href`, and `/reviews/:reviewId` is behind `ProtectedRoute`. There is no current public/token endpoint or expiry path.

My plan is to keep the existing owner-only review route protected and add a separate share flow: an authenticated endpoint will verify ownership and create a signed review-share token with a 30-day expiry, and an unauthenticated endpoint will validate that token and return only the referenced review summary. On the frontend I'll add `shareService.ts`, change the Share button to copy the new public URL, and add an unprotected read-only shared-review route/page.

I'll build this on `fix/40-public-review-links` in my fork. Only completed reviews can be shared. The public response will contain score and feedback, without profile identifiers or internal errors. Tokens will carry a share purpose and review id, require an expiry, and omit the login subject claim. Revocation, custom expiry, and unrelated cleanup are out of scope.

I’ll test this by re-running my Unit 2 Incognito flow and checking that the new URL opens without a session while the normal `/reviews/:reviewId` route stays protected. I’ll also test ownership, incomplete reviews, valid/expired/malformed/wrong-purpose tokens, rejection of share tokens as login credentials, and clipboard failures before running the repo’s required checks. I still need to confirm the best invalid-link status convention while implementing.

## Your branch

**Branch**

`fix/40-public-review-links` in `samiiigo/pathreview-ai301-fa26-s3`.
The implementation is committed and pushed at `0fa7cfeb9e83ed8b7c7dbf82d46ff80463d57a11`.

Branch: https://github.com/samiiigo/pathreview-ai301-fa26-s3/tree/fix/40-public-review-links

**Evidence**

Original before evidence: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/40#issuecomment-5922456109

At baseline commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088`, the posted commands were `docker compose up -d`, `make setup`, and `make run`. The copied URL was:

> `http://localhost:5173/reviews/2b52d27d-3ccc-4e7f-a179-5e45a9380c93`

The posted observation was:

> Opening the copied URL while logged out redirected me to the login page instead of displaying a public read-only review.

Additional automated before/after check, run from the fork root:

```powershell
.\.venv\Scripts\python.exe -m pytest tests/unit/test_review_sharing.py -q --tb=short
```

Before adding the implementation, the real routes returned 404 for share creation:

```text
assert response.status_code == 200
E   assert 404 == 200
6 failed, 9 passed, 1 warning in 3.51s
```

After the implementation and six additional malformed-expiry test cases:

```text
21 passed, 1 warning in 1.15s
```

The route checks call the production router and JWT helpers, replacing only the database dependency. Frontend tests render the real App/public/private routes with HTTP responses mocked, checking logged-out public access, continued private-route protection, score/feedback rendering, copy success, and API/clipboard failures.

```powershell
cd frontend
npm.cmd test -- --run src/pages/__tests__/ReviewSharing.test.tsx
```

```text
Test Files  1 passed (1)
Tests  9 passed (9)
```

Full backend suite: `396 passed, 53 xfailed`. Full frontend suite: `27 passed` with `--testTimeout=15000`; the same existing URL-length test hit its default five-second timeout before and after the change. Lint, formatting, production frontend build, and the Python 3.11 typecheck passed. The existing integration directory collected no tests.

I checked the running app and confirmed that it works as expected. The shared `/shared/reviews/<token>` link opens in Incognito without requiring login and displays the review score and feedback. The original private `/reviews/<review-id>` URL redirects to login when opened without a session. The shared page displays the score of `81/100` and feedback without Copy link or Export controls.

These are my manual browser observations, separate from the automated test output above. The earlier Docker startup problem no longer blocks this verification. Saved automated command output is included in the adjacent `evidence/` folder; the full local transcripts are also in `D:\repo\codepath\unit3-evidence`.

## Eval iterations

**Run history**

The available saved full run, written `2026-10-01T02:13:30Z`, reports:

> `agreement: 18/20 scored items  (bar: 18/20: PASS)`

> `categories: clear-accept 5/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4`

No additional full eval or `--only` retry was run during this continuation. The saved run's hashes match the installed rubric, evidence guide, procedure, and SKILL.md, so the passing run was preserved unchanged. Earlier runs, if any, are not reconstructed or claimed here.

**Package analysis**

`pkg-05`: the saved rubric result is `reject`; gold is `accept`. The run reports `failed: uncertainty-honest`.

The package says:

> Risk: none identified beyond one extra network request per channel per 24h, which is the constant's existing meaning.

Its implementation approach says:

> Approach: compute the cached response's age from the cache file's stored timestamp; treat the response as stale when age exceeds the constant, even if every cached notice is unexpired.

My interpretation of the disagreement is that the honesty check can treat this confidently specified timestamp mechanism as an unresolved assumption, even though the issue and thread have already settled the bounded TTL approach. The saved summary identifies the failed check but does not preserve a fuller per-check explanation, so this interpretation is not claimed as a recovered grader trace. Gold accepts the bounded plan.

**Check rationale**

Exact check retained in `tools/plan-check/rubric.md`:

| uncertainty-honest | The plan's risks, unknowns, assumptions, and Deviations section when applicable | Pass if unresolved implementation choices or risks are named as unknowns/risks rather than presented as established facts, and any known deviation from a posted plan is recorded with why. Fail if uncertainty that could materially change the build is hidden behind certainty or a known deviation is omitted. | required |

I kept this wording to require plans to expose material unknowns and record actual deviations, rather than treating a confident description as sufficient evidence. I did not revise it in this continuation because the saved full run already met both the agreement bar and category floor.

**Trade-offs**

The strict wording can produce false holds on otherwise reasonable plans: `pkg-05` is a concrete example, rejected by the saved run while gold accepts it. I am retaining that known trade-off, not claiming perfect calibration. The rubric and procedure were not changed, so the existing 18/20 result still describes the submitted files; no canary rerun is claimed.
