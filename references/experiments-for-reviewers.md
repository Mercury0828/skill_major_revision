# Experiments for Reviewer Comments

Protocol for every point triaged needs-experiment. The skill runs these experiments itself, as part of the revision: design, execution, validation, and write-up all happen here.

## 1. Acceptance criteria before code

Before running anything, write down for the point:

- **Expected trends.** What the result should show, directionally, if the paper's claims hold ("TVD decreases as shots increase; the certified budget is flat in shots"; "the QDP-QRDP gap grows with K").
- **Parameter ranges.** The ranges to cover, including every value the reviewer named explicitly. If the reviewer says "10, 15, 20, 25 qubits", those exact values appear in the result.
- **Required outputs.** The exact tables and figures the comment requires, named before the run (a sensitivity table over the grid; a trend figure with error bars; a heatmap for two-dimensional sweeps).
- **Held-fixed set.** Which parameters stay at the paper's original values, stated explicitly, so the new result is comparable to the published one.

The criteria are a self-check on your own results. If the first run misses them, debug or redesign and rerun until results and criteria agree. If it becomes clear the expected trend was wrong, that is a finding: report it honestly and adjust the paper's claim (archetype 6 or 1), never massage the result toward the criteria.

## 2. Design heuristics

- **Answer weaknesses with experiments, not only prose.** "The mechanism is never exercised" and "your comparison confounds A with B" are both answerable with cheap targeted runs: exercise the mechanism live and show the predicted behavior; implement the hypothesized confounder as a baseline.
- **A reviewer-proposed baseline that embodies your own theory is the best kind.** Either it wins (the reviewer's point improves the paper) or it loses to the full method (the delta is exactly the contribution). Implement it as proposed, not a weakened version.
- **Sweep the competitor's knob before claiming victory.** A baseline beaten at one setting is a strawman; a baseline whose entire tuning curve is dominated is a refutation.
- **Separate what the experiment controls from what it measures.** When two noise sources or factors are entangled in the comment, design the grid so each axis isolates one factor (shots vs channel noise; circuit size vs noise level), and state which output each factor controls.
- **Check units and magnitudes before the full run.** A knob swept over the wrong decade range produces three identical curves and wastes the run.
- **Seeds and uncertainty.** Multiple independent seeds (default 20 or more, 50 for cheap simulations), mean plus a stated uncertainty (standard deviation or 95% CI), warm-up discard where relevant. State the seed count in both documents and flag exceptions.
- **Config-driven runs.** Every figure reproducible from a tracked config plus script. No notebook-only results; the letter's figures will be regenerated when something upstream changes, and they must regenerate identically.

## 3. Integrity checks (validate your own output before writing it up)

Run these on every new table and figure. They are checks on results you produced, applied before any number enters either document.

- **Sanity-print.** The figure-generating code prints the table values it must match; verify the correspondence programmatically, not by eye.
- **Per-cell invariant checks.** Consistency identities, monotonicity where the model implies it, arithmetic recomputed row by row, cross-table totals reconciled.
- **Re-derive from source.** Every number quoted in prose comes from the generating CSV or raw output, not from a rounded log line. Double-rounding (log prints 3 decimals, report quotes them, paper re-rounds) is a systematic error source.
- **Statistical plausibility.** Error bars must survive a reviewer's sigma-arithmetic; a zero-violation mean sitting within 2.5 sigma of its limit is implausible.
- **No suspicious roundness.** Values all on a 0.05 grid read as fabricated; real pipelines produce irregular digits.
- **Figures from tracked code only.** Never hand-edit an image. Render at high resolution and visually inspect for overlaps, clipping, and label collisions before declaring done.

## 4. Write-up split

- **Letter:** the full result. Complete grids, every figure, the setup paragraph with all parameters, seeds, and ranges. Letter captions are conclusion-first and self-contained, because each letter figure is standalone evidence for a skeptical reader.
- **Manuscript:** the distilled result. One condensed paragraph stating the setup in one sentence and the headline numbers, plus at most one table or figure, chosen for the strongest single view of the result. Manuscript captions stay minimal (one sentence: what is shown plus conditions).
- The condensed manuscript text appears verbatim in the letter's revised block.
- Keep the letter's figure files in the letter's own `fig/` folder; copy into the manuscript's folder only the figures that actually enter the manuscript.
