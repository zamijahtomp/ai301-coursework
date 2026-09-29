# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer alive | Repo-facts block: "last 5 default-branch commits" dates, and "maintainer first-response sample" days-to-first-comment values | Pass if EITHER (a) the most recent default-branch commit is within 14 days of the captured date and authored by a non-bot human, OR (b) at least one issue in the first-response sample got a maintainer/owner/collaborator comment within 14 days, dated within 6 months of the captured date. | required |
| Repo in use | Repo-facts block: last push date, latest release date, open issues+PRs count | Pass if the last push to the default branch is within 90 days of the captured date, OR the latest release shipped within 12 months of the captured date. Star count alone does not satisfy this check | required |
| Scope fits you | Issue body text, and the comment thread if present | Pass if the issue describes one coherent, already-specified plan of work, satisfied by either (a) naming a specific file, function, or component to change — including an enumerated set of files or items under one plan, such as a multi-file restructuring or the same fix applied to several similar items — or (b) giving clear reproduction steps and/or an unambiguous description of current vs. expected behavior, such that "fixed" is recognizable even without a code location already identified. An open-ended list introduced by "etc." or similar does not fail this check on its own, as long as the items named follow an established pattern already present elsewhere in the codebase (e.g., other similar items already have the feature being requested) — this counts as one bounded, pattern-completion ask even though the exact count isn't enumerated. Multiple candidate causes, implementation approaches, or files touched for the same underlying problem or plan count as one ask, not multiple, as long as no part of the plan is left for the maintainer to decide. Fail if the issue is a general feature request with no described current/expected behavior and no concrete plan, an open design question still needing maintainer buy-in on whether or how to proceed, describes genuinely separate problems that don't share one underlying cause or plan, or is explicitly flagged by its author as not a precise spec. | required |
| Unclaimed | Repo-facts block: assignees and linked-PR fields, plus the comment thread | Pass if assignees is empty, there are no open linked PRs, and either no one has expressed intent to work on it, or the most recent such expression is more than 6 months old and the person who made it has not posted again since (a stale-bot notice or another person's comment does not count as follow-up). Fail if there's a live claim: an assignee, an open linked PR, an expressed intent within the last 6 months, or a claimant who has kept engaging since (e.g. posting updates or opening a PR). | required |

## Verdict rule

Accept only if all four required checks pass. Any single required check failing rejects the issue. `unclear` on any check counts as a fail for that check.
