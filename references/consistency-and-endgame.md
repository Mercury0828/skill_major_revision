# Consistency Passes, Build Mechanics, and the Page-Budget Endgame

The closing phases of a revision (workflow steps 7 through 12). Section-local edits and double-rounding are the two classic ways revisions break; the first three passes exist to catch exactly those.

## 1. Coverage cross-check (step 7)

Build a coverage matrix: one row per comment and sub-point, with columns for response written, manuscript change made (or "no change" with the reason), revised-block text matches the manuscript verbatim, and figures/tables referenced actually exist. Every row must close. Specific checks:

- Every response that says "the correction has been made in Section N" points to a real change in Section N.
- Every `revisedblock` quote matches `revised_manuscript.tex` character for character. Diff the quoted text against the manuscript, do not eyeball it.
- No orphaned labels, citations, or figure files in either document; no letter figure referenced but missing from the letter's `fig/`.
- Cross-references between duplicate comments (Reviewer 2's Comment 5 pointing at Reviewer 1's Comment 4) point at the right IDs after any renumbering.

## 2. Number-consistency sweep (step 8)

Tables, figures, prose, abstract, and conclusion numbers reconciled in one dedicated sweep; every number in prose traced to its generating artifact.

- Re-derive every quoted number from the generating CSV or raw output directly. Double-rounding is a systematic error source: log prints 3 decimals, the response quotes them, the manuscript re-rounds.
- A corrected number propagates everywhere: letter response, revised block, manuscript body, table, caption, abstract, conclusion. Grep for the old value to find the echoes; a single stale instance is a round-2 comment.
- Letter and manuscript must agree wherever they report the same quantity. The letter may carry more digits or more cells, but never a different value.

## 3. Fresh-reader logic pass (step 9)

After the revision cycle, a clean-context read of the revised manuscript front to back as a first-time reader, hunting specifically for:

- logic holes and non-sequiturs;
- concepts used before they are introduced (revision insertions are the usual culprit: a paragraph added to Section VII that uses a term defined only in the response letter);
- numbers or claims updated in one location but not in their echoes (abstract, intro, body, caption, conclusion);
- narrative discontinuities left by section-local edits;
- references to figures or tables whose meaning changed in the revision.

Section-local resolution of comments systematically creates these seams; the global pass is what closes them. Run it after all per-comment edits are in, not before.

## 4. Build mechanics

- Pin the toolchain (TeX Live vs MiKTeX, version) at the start of the revision; identical source builds differently across toolchains. TeX Live does not auto-install packages (`tlmgr install`).
- Record the exact build command. Full multi-pass build (latex, bibtex, latex, latex) after every content change; a stale PDF that does not reflect source is a source-of-truth failure.
- After each build, check: page count, errors, undefined references and citations, overfull/underfull boxes, distinguishing pre-existing from newly introduced.
- Inspect new figures in the rendered PDF at high zoom before declaring done; quick previews miss overlaps and clipped labels.
- On Windows, set `.gitattributes` with `*.pdf binary` (plus png and similar) before committing binaries; autocrlf can corrupt them.

## 5. latexdiff: invocation and fallback ladder

Default invocation, run against the version the reviewers last saw:

```
latexdiff original_manuscript.tex revised_manuscript.tex > diff_manuscript.tex
```

For multi-file projects add `--flatten`. Then compile `diff_manuscript.tex` with the full multi-pass build and inspect the PDF page by page.

latexdiff often breaks on heavy math, tables, and TikZ. **Never let it fail silently and ship a broken diff**: a diff that compiles but renders mangled equations is still a broken deliverable. The fallback ladder, applied until the diff builds and renders cleanly:

1. **Math markup.** Step `--math-markup` down (FINE, then COARSE, then WHOLE, then OFF) until math sections compile and render correctly. WHOLE marks entire changed equations without intra-equation markup, which is usually an acceptable trade.
2. **Graphics and floats.** Use `--graphics-markup=none` if changed figures break the build. Exclude problem environments from markup via the PICTUREENV config, e.g. `--config "PICTUREENV=(?:picture|DIFnomarkup|tikzpicture)"` to skip TikZ bodies.
3. **Per-section bypass.** If a specific environment still mangles, wrap it in a `DIFnomarkup` exclusion or temporarily replace that block in both input files with identical placeholder text so latexdiff skips it, then mark the change in that section by hand.
4. **Hand-marking.** As the last resort for problem sections, mark added text manually with `\DIFadd{}` and removed text with `\DIFdel{}` (the same macros latexdiff emits), so the diff document stays visually consistent.

Document in the letter which sections, if any, were hand-marked.

**In-text marking exception.** Some editors require changes highlighted in the manuscript body instead of a separate diff file. In that case skip latexdiff: mark revised passages directly in a copy of the manuscript with `\hl{}` (package `soul`) or `\textcolor{blue}{}`, state the convention in the letter ("changes are marked in blue"), and keep `revised_manuscript.tex` clean as the submission file if the venue wants both. Default remains latexdiff.

## 6. Page-budget endgame (step 12, last)

Revisions add content, so the manuscript will exceed the venue limit; that is expected and ignored until now. Reconcile at the very end, because cuts may touch revision content, and every such cut forces a synchronized edit to the letter.

**The sync rule:** if new content added for Comment X is cut or compressed for page budget, update that comment's response and revised block to match what the manuscript now actually contains. The letter must never promise text the manuscript no longer has.

Locate the overflow precisely (which page, how many lines or columns), then pull levers in order of information loss:

1. Font step-downs (displays, captions, tables, algorithms);
2. Subsection merges and removal of redundant propositions or repeated explanations;
3. Targeted prose cuts, with measured per-paragraph savings;
4. Float spacing (`\textfloatsep`, negative `\vspace` at table tails, `\raggedbottom`); global float-spacing knobs can buy ~10 lines in one edit;
5. Demote a manuscript figure whose information fully lives in a table row (zero information loss; the full figure stays in the letter);
6. Weakest-reference deletion, respecting any venue citation floor.

Track the spill quantitatively (render the last page, measure how far over), not by feel. When the last lines stop responding to prose trims, float re-settling is absorbing them; switch levers instead of grinding sentences. Each step is logged with its page impact and is reversible.

Re-run the number sweep and a targeted fresh-reader pass over any section the endgame touched, then rebuild all three PDFs.
