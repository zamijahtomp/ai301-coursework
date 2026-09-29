# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/71

**Verdict output**

❯ issue-select: grade these candidate first issues: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/75 https://github.com/codepath/pathreview-ai301-fa26-howard/issues/72 https://github.com/codepath/pathreview-ai301-fa26-howard/issues/71

I already graded these three live issues earlier in this conversation — repeating the same result:

- #75 (README/.env.example mismatch): accept — maintainer alive, repo in use, bounded doc scope, unclaimed.
- #71 (heading hierarchy test fixture): accept — same repo-health checks pass, bounded single-cause test fix, unclaimed.
- #72 (verify_password UnknownHashError): reject — repo-health and scope checks pass, but Unclaimed fails: PR #76 is open, unmerged, and was updated 2026-09-26 (2 days before capture), addressing this exact issue — a live claim.

Nothing about the repo or these issues has changed since the last grading, so the verdicts stand. Fit-ranking between #75 and #71 still can't be done — scope.md's fit profile is still unfilled.

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/75",
    "checks": [
      {"name": "Maintainer alive", "grade": "pass", "evidence": "Latest default-branch commit 2026-09-16 by Andrew Burke (human), 12 days before capture"},
      {"name": "Repo in use", "grade": "pass", "evidence": "pushed_at 2026-09-16, 12 days before capture"},
      {"name": "Scope fits you", "grade": "pass", "evidence": "Body names exact files README.md, .env.example, core/config.py and one bounded fix"},
      {"name": "Unclaimed", "grade": "pass", "evidence": "assignees: [], no comments, no linked PRs"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/71",
    "checks": [
      {"name": "Maintainer alive", "grade": "pass", "evidence": "Latest default-branch commit 2026-09-16 by Andrew Burke (human), 12 days before capture"},
      {"name": "Repo in use", "grade": "pass", "evidence": "pushed_at 2026-09-16, 12 days before capture"},
      {"name": "Scope fits you", "grade": "pass", "evidence": "Body names exact files test_readme_parser.py and readme_parser.py, single-cause indentation bug"},
      {"name": "Unclaimed", "grade": "pass", "evidence": "assignees: [], no comments, no linked PRs"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/72",
    "checks": [
      {"name": "Maintainer alive", "grade": "pass", "evidence": "Latest default-branch commit 2026-09-16 by Andrew Burke (human), 12 days before capture"},
      {"name": "Repo in use", "grade": "pass", "evidence": "pushed_at 2026-09-16, 12 days before capture"},
      {"name": "Scope fits you", "grade": "pass", "evidence": "Body names exact files core/security.py, tests/unit/test_security.py and one bounded fix"},
      {"name": "Unclaimed", "grade": "fail", "evidence": "Open unmerged PR #76 addressing this issue, updated 2026-09-26 (2 days before capture)"}
    ],
    "verdict": "reject"
  }
]
---

## Eval iterations

**Run history**

Run 1: 17/20 (below bar) — Run 2: 15/20 (below bar, regression from tightening one check without re-testing others) — Run 3: 18/20 (bar met, PASS — this is the run committed to `eval-run.txt`)

**Issue analysis**

issue-19: my rubric's verdict was reject (failed "Scope fits you"); gold label is accept. My rubric read the issue as leaving an open implementation decision — it names two candidate causes ("which should be fixed," implying both need addressing) and three separate suggested approaches (multiprocessing, selective category matching, threaded application) with none chosen. I judged that as a real unresolved design decision rather than a fully specified plan, so it failed my check's requirement that "no part of the plan is left for the maintainer to decide." Gold treats it as accept, likely reading a bug report with named causes and candidate fixes as sufficiently scoped for a first issue even without a locked-in approach. I re-ran this exact item twice with no wording change and got the same reject both times, so this isn't grader noise — it's a genuine, defensible disagreement about where the "already-specified plan" line sits.

**Check rationale**

"Scope fits you" pass condition, as currently written in `rubric.md`:

> Pass if the issue describes one coherent, already-specified plan of work, satisfied by either (a) naming a specific file, function, or component to change — including an enumerated set of files or items under one plan, such as a multi-file restructuring or the same fix applied to several similar items — or (b) giving clear reproduction steps and/or an unambiguous description of current vs. expected behavior, such that "fixed" is recognizable even without a code location already identified. An open-ended list introduced by "etc." or similar does not fail this check on its own, as long as the items named follow an established pattern already present elsewhere in the codebase (e.g., other similar items already have the feature being requested) — this counts as one bounded, pattern-completion ask even though the exact count isn't enumerated. Multiple candidate causes, implementation approaches, or files touched for the same underlying problem or plan count as one ask, not multiple, as long as no part of the plan is left for the maintainer to decide. Fail if the issue is a general feature request with no described current/expected behavior and no concrete plan, an open design question still needing maintainer buy-in on whether or how to proceed, describes genuinely separate problems that don't share one underlying cause or plan, or is explicitly flagged by its author as not a precise spec.

I rewrote this check three separate times over the course of the eval run, each time because a real accept-gold issue was failing for a reason my earlier wording didn't distinguish: first because it required an exact file/line (excluding well-described bugs without a diagnosed location yet), then because it treated any multi-file or multi-cause issue as "unrelated asks," then because an "etc." in a list read as an unclear spec even when the pattern itself was obvious.

**Trade-offs**

This check still misses issue-19, and I've decided to accept that rather than loosen the wording further. issue-19 shows exactly what this check gives up: any issue that frames multiple stated causes as things that "should be fixed" (not just candidate diagnoses) plus multiple unpicked implementation approaches will fail Scope, even if gold considers it a reasonable first issue. Loosening the check further to catch this would risk letting through issues that are genuinely open design questions (like calib-04), which is a worse failure mode for a first-timer than being slightly conservative. I re-ran issue-19 twice with identical wording and got reject both times, confirming this is the check's actual behavior, not noise.

---

## Selection rationale

1. I picked issue #71 mainly for time — it's a narrowly scoped bug (one indentation issue across two files) rather than something touching config/env files across three, so it's realistic to actually finish given how much of tonight went into the rubric itself.
2. The verdict correctly identified that it's a single-cause, two-file fix with an active maintainer and no existing claim. What I weighed beyond that: the *kind* of fix (a straightforward logic bug I can reason about directly) over #75's config/env surface, which felt more likely to need environment-specific setup before I could even reproduce it.
3. I expect claiming and reproducing this to be low-difficulty — it's a small, well-described bug in two named files with no dependencies on external services, so the main risk is just making sure I understand *why* the indentation causes the bug before proposing a fix, not that the fix itself is hard to find.
