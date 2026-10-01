# Evidence guide: where proof lives in a reproduction package

Every check in `rubric.md` names evidence. This file says where that
evidence sits in a package and what it looks like when it is good.

An eval bundle has five sections, always in this order: `## Repo
facts`, `## Issue`, `## Thread highlights`, `## Candidate claim
comment`, `## Candidate repro report`. Live mode has the same five
parts scattered across GitHub and the student's working directory;
each family below says where.

## Environment

**Where it lives.** In a bundle: the environment line or paragraph
near the top of `## Candidate repro report` (often labelled
"Environment"), read against the version and platform stated in the
`## Issue` body and against the `latest release` and `bug reports`
lines in `## Repo facts` — the bug-report template line says what the
project itself asks a reporter to record. In live mode: the student's
draft repro file, read against the issue body on GitHub, the repo's
issue template under `.github/ISSUE_TEMPLATE/`, and the releases page
for what "current" means today.

**What good looks like.** A reader can name the version and the
platform without inferring either: "yq 4.53.3 (Homebrew), macOS 15.5
(arm64)" is enough; "latest version, my machine" is not. The version
and platform are the ones the issue targets, or the report says
outright that they differ and on which side it tested — "the issue was
filed against 4.53.2; I tested the current 4.53.3" is a pass, and the
same test with the delta unmentioned is not. A record that is absent
entirely is the common failure, not a thin one: if the report never
says what it ran on, nothing downstream of it can be placed.

## Steps

**Where it lives.** The steps or preparation block of `## Candidate
repro report` — the commands, the input file, the config. Read it
against the reproduction the `## Issue` body gives: issues in these
bundles usually carry the exact input document and the exact command,
and that is the thing the steps have to match. In live mode: the
student's draft, read against the issue body and any linked gist,
branch, or minimal reproduction.

**What good looks like.** A stranger holding only this package can get
to the same run. Every file is shown or fetchable, every command is
written out, every flag that matters is present, and the starting
state is stated. Two specific failures live here. The first is a step
nobody else can take: a private monorepo, a config that was never
pasted, "set up the project as usual". The second is quieter and
matters more — the input or command drifting from the issue's. Compare
them character by character where the issue gives an exact input: `1 =
{}` and `1: {}` are different programs, and a report that runs the
second is not reproducing the first. A deviation is fine when the
report says it deviated and why; it fails when it passes unremarked.

## Behavior shown

**Where it lives.** The fenced output blocks, log excerpts,
screenshots, and measurements inside `## Candidate repro report` — the
things the author's own run produced. Read each against the failure
the `## Issue` body describes: the error text, the panic, the exit
code, the wrong output. In live mode: the artifacts pasted into the
student's draft, read against the issue body and any maintainer reply
in the thread that narrows what the real trigger is.

**What good looks like.** The artifact exists, and it shows the
issue's failure rather than a neighbouring one. A tool can fail in
many ways; only one of them is the bug. A graceful argument-validation
error is not a capacity-overflow panic. A compile error from a
modified expression is not the path-expression bug the issue reports.
Garbled escape output with the terminal still running is not a crash.
Check the mechanism, not the mood: same error text, same exit, same
wrong value. Output that only proves the tool started — a version
banner, a session list, a window opening — is setup noise and shows
nothing about the behavior. Where the issue describes something
positional or ordered, the artifact has to show the order.

## Honesty

**Where it lives.** The seam between the report's conclusion — its
"Analysis", "Result", or closing paragraph in `## Candidate repro
report` — and the artifact above it. Also the claim comment's account
of what the author did, read against what the report actually shows.

**What good looks like.** The conclusion is the size of the evidence.
A report that says "reproduced" has an artifact showing the issue's
failure; a report that says "I could not reproduce" is a pass, not a
defect, when it shows the attempt it actually ran and names what
differed and what a triggering setup would likely need. What fails is
overreach in either direction: certainty narrated over the wrong
artifact ("this confirms the reported bug" under an error that is not
the reported bug), a root cause diagnosed with no transcript behind
it, "verified on two machines" where one run is shown, or a result
generalized to a build or release the author never tested. Read the
adverbs against the evidence — "deterministic", "guaranteed",
"exactly" — and ask what in the package backs each one.

## Comms

**Where it lives.** `## Candidate claim comment` first, read against
the `## Issue` body and `## Thread highlights` — a claim that engages
the thread can only have been written after reading it. Then both
comments read against the `contribution policy` line in `## Repo
facts`, which is where a project's AI rules are recorded when it has
any. In live mode: the student's draft claim, the issue thread, and
the repo's `CONTRIBUTING.md`, `AI_POLICY.md`, or equivalent.

**What good looks like.** The claim names this issue and no other:
the behavior, the version it reproduced on, a pointer someone left in
the thread, and a next step concrete enough to be wrong about. It
promises only what the author has done or will do next — "my next step
is tracing how range formatting decides the closing boundary" — and
never a deadline, a guaranteed fix, or a request to reserve the issue.
Boilerplate is the tell: if the same words would fit any issue in any
repo, they carry no information for the maintainer reading them.

On AI policy, read the policy line literally and apply only what it
says. Most projects state none, and then there is nothing to check.
Some welcome AI use with a human responsible, some require comments to
be in the contributor's own words, some explicitly say no disclosure
is asked for on issue comments — none of those are a disclosure
requirement. Only a policy that requires AI use to be disclosed in
comments creates one, and then the comment has to say the tool and the
extent of the help. Treat the package's own comments as AI-assisted
work when deciding whether that requirement is met.
