# Rubric: is this a good first issue?

## Evidence conventions

In eval mode, use only the snapshot and measure ages from its capture date. In live mode, use today's date and the sources below, following `scope.md` house rules. Read the entire issue thread before grading. Missing evidence is `unclear`; an explicitly empty list is evidence of absence. Labels and star counts alone cannot override a required failure.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | Repo facts: last 5 default-branch commits with authors, maintainer first-response sample; issue comments with dates and author_association. Live: default-branch commit history, merged PR authors, recent issue replies, and candidate thread. | At least one human-authored default-branch commit, bot merge of a human PR, or OWNER/MEMBER/COLLABORATOR issue reply within 90 days. Automated dependency commits alone do not pass. | required |
| Repository in use | Repo facts: archived flag, latest release, last push to any branch. Live: repository metadata, Releases, and branch history. | Repository is not archived, and either its latest release or its last push is within 180 days. No published release is acceptable when a recent push exists. | required |
| Bounded contribution | Issue body, labels, complete comment thread, and linked PR history; live equivalents in the issue and Development section. | The requested outcome is one identifiable bug fix, documentation change, test, or small feature. Coordinated edits to multiple documentation pages describing the same feature count as one bounded contribution; file count and checklist length alone do not make an umbrella. Reject explicitly identified umbrella/tracking work with independently scoped subprojects, unresolved competing designs, an explicit requirement to change core parser/compiler/architecture internals, or a pure usage question without a requested project change. Also reject an issue at least 730 days old with at least 2 closed unmerged implementation attempts. A short description, missing reproduction steps, or an acceptance checklist alone is not a failure when the requested change is identifiable. | required |
| Available to work | Repo facts: assignees and linked PR states; complete comment thread for claims, withdrawals, and PR references. Live: Assignees, Development, referenced PR state, and comments. | No current assignee, no open PR implementing the requested fix, and no unwithdrawn claim in the last 30 days or older claim with progress in the last 30 days. A closed unmerged PR alone is not an active claim. Explicit withdrawal or reassignment supersedes earlier claims; current thread evidence supersedes stale sidebar facts. Apply the Path Review exception for student claim comments only in live mode. | required |
| AI contribution policy | Repo facts: contribution policy. Live: root and .github CONTRIBUTING files, linked contributor rules, dedicated AI policy files, and PR templates. | No applicable explicit ban on AI-assisted or AI-generated contributions. Disclosure, personal understanding, testing, and human review requirements pass and must be reported as obligations. An explicitly unstated policy, or no policy found after checking these sources, passes; an inaccessible policy is unclear. | required |
| Maintainer guidance | Issue labels, author association, and maintainer comments in the snapshot or live issue. | At least one good-first-issue label or maintainer comment identifies the intended change, a relevant file, or a verification step. | preferred |

## Verdict rule

Return `accept` only if every required check is `pass`. Any required `fail` or `unclear` returns `reject`. Report every check with the deciding fact or quote. Preferred checks never change the verdict; use them and the live fit profile to rank accepted candidates. If all required checks pass but a preferred check is unclear or fails, the verdict remains `accept`.

