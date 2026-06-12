# Changelog

All notable changes to this skill. Keep entries short, newest on top.

## [0.1.0] - 2026-06-12
Initial version, extracted from a completed major-revision project (full paper plus its response letter).

- Workflow: comment inventory, compound-comment splitting, per-point triage, five-move response anatomy, letter-first drafting then condensed manuscript revision, cross-check that every comment is covered, full-document consistency pass, latexdiff diff generation, page-budget endgame.
- `assets/response_letter_template.tex`: four colored tcolorbox block environments (comment, response, revised, reference), float-in-box handling, theorem environments. Compile-verified, including tables, figures, and proofs placed inside boxes and a full bibtex pipeline.
- `references/ai-style-checklist.md`: migrated from skill_js, with response-letter genre adjustments ("rather than" allowed; scope-limit hedging adjusted). Bans em-dash, "comprehensive", and defensive hedging.
- `references/comment-archetypes.md`: 14 archetypes, including reviewer-misread-paper, pure-praise, and duplicate-across-reviewers.
- `references/experiments-for-reviewers.md`: experiments run inside the skill; acceptance criteria used as self-checks; integrity checks applied to produced results.
- `references/consistency-and-endgame.md`: fresh-reader logic pass, number-consistency sweep across letter, manuscript, and figures, page-budget endgame with letter and manuscript kept in sync, build mechanics, latexdiff fallback ladder.
- Conventions locked: latexdiff is the change-marking convention (clean revised manuscript plus a separate diff), with a fallback ladder and an in-text `\hl` or colored-text exception when an editor requires in-body highlighting; admitted errors carry an impact-on-conclusions statement; multi-round responses back-reference the previous round; a self-red-team pass runs before submission.
