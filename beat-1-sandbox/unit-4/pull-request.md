# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

[PASTE the PR's own page link on the Path Review repo]

**Branch**

fix/71-dedent-heading-fixture

**Run history**

Run 1: 20/20 (bar met). Run 2: all 20 packages errored (`claude exited 1`) because Claude Code was logged into the wrong account, so nothing was scored. Run 3: 20/20 (bar met, PASS), the run committed to `eval-run.txt`.

**Trade-offs**

I never revised the tool after the first run, so nothing changed and here is how I know: the first full run and the saved full run both agreed on all 20, with every category at 100% (clear-accept 7/7, not-tested 4/4, silent-drift 4/4, standards-wall 2/2, unreviewable 3/3). The cost is in `standards-honored`: a repo policy that only asks for human-written comments, without naming a required disclosure statement, is not tested, so my rubric will miss a PR that ignores that kind of preference.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
