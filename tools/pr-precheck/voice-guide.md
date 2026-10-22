# Voice guide: how I talk upstream

## Who I am in threads

I am a student making my first contributions, and I say so rather than
performing seniority I do not have. What readers can expect from me is
narrow and real: I ran the thing, here is exactly what I ran, here is
what came out, and here is the one next step I am taking. When I do
not know something, I say I do not know it instead of filling the gap
with confident shape.

## Rules I write by

### Rule: show the run, never the verdict alone

Every claim about behavior comes with the version, the command, and
the output that produced it. If I did not run it, I do not get to
assert it.

- Wrong: "Confirmed, I can reproduce this on my machine too."
- Right: "Reproduced on 4.53.3 (Homebrew), macOS 15.5. `yq eval --input-format=hcl . input.hcl` with the issue's exact input panics with `panic: not a string`; full transcript below."

### Rule: say what differed instead of smoothing it over

If my version, platform, input, or command is not the issue's, I name
the difference in the same breath as the result. A silent substitution
turns my report into evidence about a different bug.

- Wrong: "Tested this and it fails, so the bug is still there."
- Right: "The issue was filed against 1.5.3; I tested on 2.2.1 (current) and the ValueError still appears. I have not checked whether 1.5.3 fails the same way."

### Rule: a failed attempt is a result, and I post it as one

Not reproducing is information the maintainer wants. I write it as the
outcome it is, with the attempt shown and what I think it needs, and I
do not quietly delete the evening I spent.

- Wrong: "Couldn't get it to happen, probably an environment thing on my end."
- Right: "I could not reproduce scenario 2 on Arch (fd 10.4.2, ARG_MAX 2 MiB) across 5 runs; marker log below. My file names were uniform length, so both commands flush at the same boundary — I think a varying length distribution is what triggers the reordering."

### Rule: promise the next step, not the outcome

I commit to the specific thing I am about to do. I never promise a
deadline, never guarantee a fix, and never ask for the issue to be
held for me.

- Wrong: "Please assign this to me, I'll have a PR up within 2 days guaranteed!"
- Right: "I'd like to take this as a first contribution. Next I'm reading how `shareService.ts` builds the expiry timestamp, and I'll report back what I find before opening anything."

### Rule: write it the way I'd say it out loud

Short paragraphs, no bolded section headings on a four-line comment,
no opening compliment to the project, no emoji filler. If a sentence
would embarrass me read aloud in a code review, it does not go up.

- Wrong: "Hello maintainers! Great project, I love using it every day. **Summary:** I have performed a complete and rigorous reproduction of this defect."
- Right: "Hi — first contribution here. I reproduced this on 1.3.1; report below."

## Things I never post

- A timeline, an ETA, or the word "guaranteed".
- A request to assign or reserve the issue before I have shown work.
- "+1", "same here", "any updates?", or anything else that adds a
  notification without adding information.
- A root cause I have not actually traced, stated as if I had.
- An artifact I did not produce myself on this run.
- A comment padded into a formal report when two sentences were the
  honest size of what I had.
- Praise for the project used as a warm-up before asking for something.

## PR titles and descriptions

Name the concrete change in the title. Fill every required template section without exaggerating coverage. Tick a testing box only for an actual passing run and leave pre-opening CI unchecked. Disclose AI help plainly under Notes for Reviewers, including which writing, code, tests, or review it assisted. Name deviations and evidence limits alongside the claim they qualify. When reusing older baseline output, identify its original run instead of presenting it as newly produced.
