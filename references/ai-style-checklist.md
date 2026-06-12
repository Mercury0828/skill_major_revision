# AI Style Checklist: run on every batch of new prose

<!-- Migrated from skill_js templates/AI_STYLE_CHECKLIST.md (origin: CDRO project),
     adapted for the revision genre: response letters plus manuscript insertions.
     Genre adjustments are marked [revision-genre]. -->

Applies to both documents: every batch of new response-letter prose and every manuscript insertion gets its own pass before it is final. The sweep is per-batch, not per-project: a one-time sweep early in a revision misses everything later rounds add.

## PROCESS RULE (overrides everything)

**Propose-then-approve, one by one.** Run the sweeps, produce a NUMBERED list of candidate edits with before/after snippets, present to the owner, apply ONLY approved items. Never auto-apply. If an item holds up, say "fine"; no forced findings. Never add defensive or justification prose as a "fix".

## A. Grep token sweep (flag every hit; each hit = one numbered proposal)

| # | Pattern | Action |
|---|---------|--------|
| 1 | `—` em-dash as rhetorical glue (`---` in tex) | Restructure the sentence. (Proper-noun en-dashes are fine: Bernstein--Vazirani, Cauchy--Schwarz.) |
| 2 | `such as` | Ask: shorter / more concrete? Often deletable. |
| 3 | `not only ... but also` | Cap ~2 per document; prefer "both X and Y" or "X while Y". |
| 4 | `it is worth noting` `it should be noted` `in this regard` `from this perspective` `this observation is important` | Delete; state the content directly. |
| 5 | `enable` `facilitate` `leverage` `enhance` | Replace with the concrete verb (computes, outputs, reduces, selects...). |
| 6 | `comprehensive` `holistic` `seamless` `significant` `novel` `powerful` `flexible` `general` (as advertising) | Delete or replace with the specific property. |
| 7 | `framework` `paradigm` `mechanism` `module` `strategy` `scheme` (over-broad) | Replace with the concrete noun (controller, formulation, policy, method...). |
| 8 | `we aim to` `we seek to` `we attempt to` | Say what was done. |
| 9 | `in this paper, we propose` `the proposed` `robust and efficient` | Trim; state the result, don't advertise. |
| 10 | `not X, it is Y` / `The real problem is not A, it is B` | Rewrite. EXCEPTION: genuine mathematical disambiguation ("the set is not a product..., it is a single coupling") is exposition; keep. |
| 11 | Defensive hedging: `not a claim` `this is not intended` `should not be (interpreted\|read\|taken)` `we make no claim` `we (emphasize\|stress\|caution)` `does not (imply\|claim)` | Rewrite to plain statements of fact. See the genre adjustment below for the scope-limit exception. |
| 12 | `rather than` in manuscript prose | Restructure or split into two sentences; state the contrast positively. Allowed in response letters; see the genre adjustment below. |

## Genre adjustments for response letters [revision-genre]

The original checklist was written for fresh manuscript prose. Response letters legitimately need contrast and scope language that the manuscript bans:

1. **"rather than" is allowed in response letters** for old-versus-new contrast: "we now state X rather than the previous Y" is the genre's native construction. In manuscript prose the restriction stands (row 12).
2. **Reviewer-demanded scope limits are content, not hedging.** When a reviewer flags an overclaim, the corrected wording often must say what is not claimed: "This proposition does not claim additive composition for arbitrary joint measurements." That is a plain statement of scope; keep it. Row 11 still bans the chatty wrapper forms ("it should not be interpreted as...", "we emphasize that we make no claim..."): state the scope limit directly, without the wrapper.
3. **Old-versus-new comparison phrases are the letter's job.** "The previous manuscript did X; the revised manuscript does Y" repeats by design across responses; do not flag it as template repetition.
4. **Genre courtesy formulas are fixed, not flagged.** "We thank the reviewer for..." once per response is the convention. Flag only repetition inside a single response.

Everything else in the token table applies to letters at full strength, especially rows 1 (em-dash) and 6 (advertising adjectives).

## B. Read-level checks (whole-document pass)

1. Plain and understandable for a non-expert reviewer = top priority; no homemade jargon; define once in full, then use the short form.
2. No stacked abstract-noun strings ("uncertainty-aware safety-constrained grid-responsive flexibility management": say what it does).
3. Sentence-template repetition (e.g., three colon-led "The result is X:" in a row): vary or merge. (See genre adjustment 3 for the letter's structural repetition, which is exempt.)
4. Template openers ("X is no longer just...", "This is both a challenge and an opportunity") and rhetorical flourishes ("cannot be an afterthought"): state the mechanism directly.
5. Front-to-back repetition; metaphor/adjective density; excessive passive voice.
6. Cut obvious transition sentences; don't wrap simple things in big words.
7. Contributions and claims: specific, limited, credible; each maps to an existing theorem, figure, or table.
8. Find paragraphs that preemptively defend against criticism; rewrite plainly; keep necessary limitations as plain statements.
9. Respect the reword bound: if it's already clear, leave it. The "AI reword spiral", each pass making prose worse, is real and observed.

## C. Worked transformations (calibration examples)

- "AI data centers are no longer passive consumers. As workloads... they are becoming..." → "As large-scale workloads expand, AI data centers are becoming large, fast-varying electricity loads." (template opener + merge)
- "This is both a challenge and an opportunity: uncontrolled growth can..., but properly controlled..." → "Uncontrolled growth can aggravate peak demand, while properly controlled loads can provide..." (template frame → direct contrast)
- "safety cannot be an afterthought: the limits define when..." → "the thermal limits define when demand can be shifted, so they must be enforced inside the controller." (flourish → mechanism)
- "we use these measurements only to verify feasibility rather than to claim a solver-speed advantage" → "Absolute runtimes depend on solver implementation; these measurements confirm real-time feasibility." (defensive → plain facts)
- "Two points are worth making explicit, because the construction is easy to misread." → "Two properties of (eq) deserve emphasis." (chatty/defensive → direct)
- [revision-genre] "It should be noted that our framework does not intend to claim composition for arbitrary measurements." → "This proposition does not claim additive composition for arbitrary joint measurements." (wrapper stripped, scope limit kept as plain fact)

## Captions [rule]

Manuscript figure and table captions are SHORT: typically one sentence stating what is shown plus the conditions (seeds, axes, special markers); at most two sentences when a table needs a legend. Takeaways, mechanisms, and numbers belong in the body text, never in the manuscript caption. When trimming an over-long caption, first move any caption-only fact into the body (don't delete evidence), then cut.

[revision-genre] Response-letter captions are the exception: they can be richer and conclusion-first ("ASR drops from 0.96 to 0.54 as p reaches 0.5, confirming the noise parameter controls inference success"), because each letter figure is standalone evidence for a skeptical reader.
