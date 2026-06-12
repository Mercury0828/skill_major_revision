# skill_major_revision

A Claude skill for writing major revision responses to journal and conference reviewers. It produces the response-to-reviewers letter and the matching manuscript revision, and it runs any experiments the comments require. Built for use in Claude Code.

## What it does
- Parses the decision letter into a comment inventory, splits compound comments into independently answerable sub-points, and triages each point: agree, partly agree, or disagree-with-evidence; writing-only, needs-experiment, or infeasible-explain-why.
- Drafts each response with a fixed five-move structure: concede something specific, diagnose what the old version did, give the fix in full, interpret the result carefully (downgrading any overclaim), and point to the manuscript location.
- Writes the matching manuscript revision in condensed, self-contained form, kept consistent with the letter.
- Runs the experiments a comment needs, with expected results written as acceptance criteria first, so the result is checked against a stated target rather than accepted as-is.
- Produces the three-file output: `response_letter.tex`, a clean `revised_manuscript.tex`, and `diff_manuscript.tex` generated with latexdiff.

## Layout
- `SKILL.md`: the workflow, the per-comment response anatomy, the writing principles, and the conventions. Start here.
- `assets/response_letter_template.tex`: copy-paste-ready LaTeX template. Four colored block environments (comment, response, revised, reference), float-in-box handling so tables and figures sit inside boxes, and theorem environments for reproducing proofs. Compile-verified. Requires `IEEEtran.bst` on the build machine.
- `references/ai-style-checklist.md`: the anti-AI-writing-style sweep run on every new prose batch, adjusted for the response-letter genre.
- `references/comment-archetypes.md`: a catalog of reviewer-comment types with the response move for each, including reviewer-misread-paper, pure-praise, and duplicate-across-reviewers.
- `references/experiments-for-reviewers.md`: acceptance-criteria framing, experiment-design heuristics, and integrity checks applied to results.
- `references/consistency-and-endgame.md`: the fresh-reader logic pass, the number-consistency sweep across letter, manuscript, and figures, the page-budget endgame with letter and manuscript kept in sync, build mechanics, and the latexdiff fallback ladder.

## How to use
In Claude Code, give the skill the decision letter, the current paper, and, for round two and beyond, the previous response letter. Follow the workflow in `SKILL.md`. Review the staged output before committing.

## Maintenance
This skill is meant to improve after each real revision. When a round surfaces something worth keeping, a better move for a comment type, a new failure mode, or a template tweak, update the relevant file and add a line to `CHANGELOG.md`. Keep everything in English.
