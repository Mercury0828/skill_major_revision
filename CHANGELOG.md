# Changelog

All notable changes to this skill. Keep entries short, newest on top.

## [0.1.2] - 2026-06-14
- Added an **improve-before-conceding** rule to the experiments protocol: on a failed or unfavorable result, do not
  default to an honest caveat first — diagnose the consequence, try a legitimate improvement (fairer/reviewer-proposed
  baseline, more data, better metric, representative vs. adversarial regime, sharper framing), and rerun; concede only
  when improvement is exhausted or the trend is genuinely wrong. Red line unchanged (no massaging/fabrication);
  integrity-sensitive reframes that move a headline number are surfaced to the user before applying. Adds a closing-phase
  task: re-review every earlier honest caveat once the last comment is done. Driven by live-revision feedback.

## [0.1.1] - 2026-06-14
- Strengthened the response-anatomy rule into a **self-contained-responses** principle (reviewer comfort first):
  each response must stand alone; restate key numbers/evidence/conclusions inline and **duplicate supporting
  figures/tables** into every response that uses them; cross-references are courtesy-only, never the sole home of
  the substance; cross-reviewer pointers for substance are forbidden (copy the figure and numbers instead). Driven
  by reviewer-experience feedback from a live revision (a Reviewer-2 point had pointed to Reviewer-1 responses for
  its evidence; fixed by duplicating the figures and numbers into the Reviewer-2 point).

## [0.1.0] - 2026-06-12
Initial version, extracted from a completed major-revision project (full paper plus its response letter).

- Workflow: comment inventory, compound-comment splitting, per-point triage, five-move response anatomy, letter-first drafting then condensed manuscript revision, cross-check that every comment is covered, full-document consistency pass, latexdiff diff generation, page-budget endgame.
- `assets/response_letter_template.tex`: four colored tcolorbox block environments (comment, response, revised, reference), float-in-box handling, theorem environments. Compile-verified, including tables, figures, and proofs placed inside boxes and a full bibtex pipeline.
- `references/ai-style-checklist.md`: migrated from skill_js, with response-letter genre adjustments ("rather than" allowed; scope-limit hedging adjusted). Bans em-dash, "comprehensive", and defensive hedging.
- `references/comment-archetypes.md`: 14 archetypes, including reviewer-misread-paper, pure-praise, and duplicate-across-reviewers.
- `references/experiments-for-reviewers.md`: experiments run inside the skill; acceptance criteria used as self-checks; integrity checks applied to produced results.
- `references/consistency-and-endgame.md`: fresh-reader logic pass, number-consistency sweep across letter, manuscript, and figures, page-budget endgame with letter and manuscript kept in sync, build mechanics, latexdiff fallback ladder.
- Conventions locked: latexdiff is the change-marking convention (clean revised manuscript plus a separate diff), with a fallback ladder and an in-text `\hl` or colored-text exception when an editor requires in-body highlighting; admitted errors carry an impact-on-conclusions statement; multi-round responses back-reference the previous round; a self-red-team pass runs before submission.
