# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

**Where it lives:** In eval mode, read the candidate plan's diagnosis/cause statements against the package's repro-evidence block, especially the observed output, expected-vs-actual statement, and implementation facts. In live mode, use `plan.md` plus the student's posted Unit 2 reproduction comment on the issue.

**What good looks like:** The diagnosis explains the same failure the reproduction actually showed and cites or quotes facts that support the cause. It does not upgrade a suspicion into a proven root cause or ignore a decisive contradictory artifact.

## Scope

**Where it lives:** Read the candidate plan's in-scope/out-of-scope statements, files-to-touch list, approach, and any stated cleanup. Compare them with the issue body and relevant-files hints. In live mode, also read the repository's contribution guidance for expectations about focused changes.

**What good looks like:** The plan is one issue-sized change. Every named file or new component has a direct role in delivering the requested behavior, and unrelated refactors or redesigns are explicitly excluded.

## Executability

**Where it lives:** Read the plan's files/areas and approach sections, then compare with repo facts about the actual architecture and conventions. In live mode, inspect the relevant repository files only as needed to confirm that the named areas exist and the proposed flow fits the codebase.

**What good looks like:** Another contributor can identify where to start, what each changed area will do, and how data/control moves through the change without asking the author to invent the core design.

## Test plan

**Where it lives:** Read the candidate plan's test plan against the repro-evidence steps, output, expected behavior, and issue acceptance requirements. In live mode, the student's Unit 2 repro is the baseline before-fix test unless the plan explains why a real-code replacement is needed.

**What good looks like:** The planned check observes the user-visible failure path before and after the fix, states the expected post-fix result, and covers material boundaries named by the issue. Generic commands such as "run tests" may supplement but do not replace a decisive behavior check.

## Honesty

**Where it lives:** Read risks, assumptions, unknowns, and the `## Deviations` section. Compare strong claims in the diagnosis and approach with what the repro evidence actually proves. After a build, compare the recorded deviations with the changed implementation described by the updated plan.

**What good looks like:** Unknown implementation choices are labeled as such, likely risks are named, and the author does not claim evidence they do not have. If the build changed from the posted plan, the difference and reason are recorded; if nothing changed, that is stated explicitly in the author's own words.

## Comms

**Where it lives:** In eval mode, read the candidate plan comment against issue context, thread highlights, and the repo-facts block. In live mode, compare `comment.md` with the live issue thread, the student's reproduction comment, `docs/CONTRIBUTING.md`, and any repository AI-use policy.

**What good looks like:** The comment is specific to the issue and the author's own reproduction, summarizes diagnosis/scope/test intent without relying on "same as above," respects maintainer instructions, and follows applicable repository conventions. AI disclosure is required only when the repository policy says it is required for issue comments.
