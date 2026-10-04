# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

Where it lives: in an eval bundle, the repro report's environment section (usually near the top, before the steps), read against the repo-facts block's stated language/runtime and the issue context's named target version. In live mode, the student's draft repro comment, read against the repo's install docs (README, CONTRIBUTING.md) and the issue thread's own stated version if the reporter gave one.

What good looks like: the OS/platform, the language or runtime version, and the package's own version (or commit hash/tag) are all named as specific values, not described generically. If the environment doesn't match what the issue targets (a different OS, a newer or older package version), that mismatch is called out explicitly rather than left implicit — a report that reproduces on a different version than the issue names, without saying so, is not sufficient even if it matches on everything else.

## Steps

Where it lives: the repro report's numbered or ordered steps section, read starting from a clean/default install state. In live mode, the draft comment's own step list, read against what the package's actual CLI or API surface requires to reach the reported behavior.

What good looks like: every step a stranger would need is present and in order — the exact install/setup command, the exact invocation (command run or code executed), and the exact input or arguments used — with no implied step skipped between "set up" and "see the behavior." A step that says "configure it as usual" or omits the triggering input is not followable, even if the overall narrative sounds plausible.

## Behavior shown

Where it lives: the artifact itself — an output excerpt, error trace, or screenshot — usually at the end of the repro report or inline after the steps. Read it directly against the issue context's own description of the bug: same error type, same message text or code, same missing/wrong output.

What good looks like: the artifact's content is the same failure the issue describes, not a different failure encountered along the way (a setup error instead of the reported runtime bug, a different error message that happens to occur in the same function, a log from a code path the issue never mentions). If no artifact is shown at all — just a narrative claim — this fails regardless of how confident the narrative sounds.

## Honesty

Where it lives: the repro report's stated conclusion line (reproduced / could not reproduce), read side-by-side with whatever evidence section backs it up — the artifact under "Behavior shown" for a reproduced claim, or the specific point of divergence for a cannot-reproduce claim.

What good looks like: the claim points to a specific piece of evidence rather than asserting a result in general terms ("I reproduced it" with nothing else is not sufficient). An honest cannot-reproduce — stating plainly that the documented steps were followed and the issue's behavior did not occur, with enough detail to show the attempt was real — is a pass. A claimed reproduction whose cited artifact actually shows a different failure (see "Behavior shown") is a fail, however confidently it's stated.

## Comms

Where it lives: in an eval bundle, the claim comment and repro comment text, read against the repo-facts block's contribution policy (CONTRIBUTING.md or equivalent) and the issue context it's responding to. In live mode, the student's actual draft comment, read against the repo's real docs and templates on GitHub.

What good looks like: the comment names the specific issue (number or exact title phrase), not a generic "I'll look into this." If the repo's policy requires disclosing AI assistance used in preparing a contribution, the comment includes that disclosure plainly — not buried, not omitted because the rest of the comment "sounds human enough." Boilerplate that could be pasted onto any issue in any repo is a fail even if every fact in it happens to be true.
