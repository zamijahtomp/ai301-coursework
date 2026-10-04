# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | The repro report's environment record, read against what the repo-facts block or package's install docs say is needed to run it | Pass if the report states the specific OS/platform, language or runtime version, and the package's own version (or commit/tag), plus any other dependency the issue's reported behavior actually depends on. Fail if any of those is missing, stated vaguely ("my machine," "latest version"), or omits a dependency the behavior clearly hinges on | required |
| steps-followable | The repro report's listed steps, read against what's needed to reach the reported behavior from a clean install | Pass if, starting from the stated environment, a stranger could reach the same point the report claims. The setup/install action must be unambiguous (literal command, or exact package+version+install method). The exact command, function, or script invoked must be given, with exact arguments/options/parameters. For the input: whatever specifically triggers the reported behavior must be given precisely (pasted, or by exact reference to input already given elsewhere in the package); incidental parts that don't affect the behavior may be described generically rather than pasted verbatim — for example, a config/data file need not be pasted in full if the report names the exact field(s) that trigger the bug (e.g., an unrecognized key) and states that other required fields are present with ordinary, unremarkable values. Fail if the install action could mean more than one thing, the behavior-determining command or parameters are missing or vague, or the steps skip from setup straight to the claimed outcome. | required |
| behavior-matches | The artifact shown (output excerpt, error trace, screenshot), read directly against the issue's own description of the bug or missing behavior | Pass if EITHER (a) the report claims reproduction and the shown artifact demonstrates the same behavior the issue describes — same error type/message/location, or same missing/incorrect output, not a superficially similar but distinct failure — OR (b) the report claims it could not reproduce, and the shown artifact demonstrates the actual output obtained after following the documented steps, showing concretely that the issue's described symptom did not occur, rather than merely asserting absence. Fail if no artifact is shown either way, a reproduction claim's artifact depicts a different failure than the issue describes, or a cannot-reproduce claim shows no actual output from the attempt. | required |
| claim-specific | The report's stated outcome (reproduced / could not reproduce), read against the exact evidence line it cites | Pass if BOTH: (a) the repro report's stated outcome (reproduced / could not reproduce) cites the specific evidence that decided it, rather than a generic assertion; AND (b) the claim comment names something specific to this issue (its number, title phrase, or exact symptom) and limits its promise to investigation only — never a guaranteed fix, a completion date, or a demand for exclusive assignment. Fail if either half fails: a vague/unsupported outcome claim, OR a claim comment that is generic boilerplate (could be pasted onto any issue in any repo unchanged) or promises more than investigation. | required |
| conventions-respected | The repo's stated contribution policy (CONTRIBUTING.md or equivalent, especially any AI-disclosure requirement), read against the actual comment text being posted | Pass if the comment includes an affirmative disclosure statement whenever the repo's policy explicitly requires one (e.g., "disclose AI assistance"). If the repo's policy instead expresses a tone/authorship preference (e.g., "write in your own words") without requiring a specific disclosure statement, this check passes regardless — authorship cannot be verified from the comment's text alone, so it isn't tested here. Fail only when the policy names a required disclosure statement and the comment omits it. | required |

## Verdict rule

Accept (ready to post) only if all five required checks pass. Any single required check failing holds the package. `unclear` on any check counts as a fail for that check.
