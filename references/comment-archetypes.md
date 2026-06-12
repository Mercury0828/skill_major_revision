# Reviewer Comment Archetypes

Consult this catalog during triage (workflow step 3). Each archetype names the comment pattern, the strategy, and the moves that make the response land. Patterns extracted from a real JSAC major-revision cycle; add new archetypes as dated entries when later revisions surface them.

## 1. Real error caught (wrong proof step, wrong number, broken inequality)

The reviewer found a genuine mistake. Strategy: admit fully, fix completely, state the impact.

- Admit plainly, with no hedging: "We agree that the proof of Proposition 1 in the previous manuscript was incorrect. In particular, the inequality direction was reversed."
- Fix at the root. Do not patch the symptom: if a proof cited a classical result without justifying the quantum step, rewrite the proof with the correct machinery, not just the flipped inequality.
- Recheck everything the error touches. A wrong number gets corrected and then propagated through every table, figure, and sentence that quoted it.
- Close the admission with the impact statement: "This correction does not affect the main results or the conclusions of the paper", or state honestly what does change. Editors fear cascading errors; answer that fear explicitly.
- Reproduce the full corrected proof or derivation in the revised block, not a summary.

## 2. Technical question / clarification ask

The reviewer asks how or why something works. Strategy: answer in maximal detail.

- Detail is the currency: equations where equations answer it, experiments where data answers it, a figure where structure answers it.
- Answer the question actually asked first, then the question behind it (a "how was Fig. 3 obtained" usually also wants "is this single- or multi-qubit, and is it part of the main experiment").
- Put the full machinery in the letter; put a condensed clarification in the manuscript so the next reader does not need the letter.

## 3. Missing experiment / ablation ask

The reviewer wants results that do not exist yet. Strategy: if it is feasible, do it. That is the rule: feasible means it gets run.

- Write acceptance criteria first, then design and run per `references/experiments-for-reviewers.md`.
- Cover the reviewer's stated ranges. If they name parameter values (qubit counts 10, 15, 20, 25), run those values, not a convenient subset.
- Full grid, tables, and figures into the letter; one condensed paragraph plus at most one table or figure into the manuscript.
- If the result contradicts the expected trend, report it honestly and adjust the paper's claim; a corrected claim plus data beats a defended claim every time.

## 4. Weak or missing baselines

The reviewer doubts the comparison. Strategy: strengthen the comparison until it would convince you.

- A reviewer-proposed baseline that embodies your own theory is the best kind to implement: either it wins (their point improves the paper) or it loses to the full method (the delta is exactly the contribution).
- Sweep the competitor's knob before claiming victory. A baseline's own tuning curve can be its refutation: if its best tuning equals a degenerate policy, one structural sentence converts "your baseline was mistuned" into "this rule class cannot do X, which is the paper's thesis".
- Name baselines after the prior work they implement; every named baseline doubles as a citation and a rebuttal.

## 5. Unclear novelty / overlap with prior work

The reviewer names a paper that does something similar. Strategy: concede the connection, then make the distinction precise.

- Acknowledge the related work directly and substantively. Never minimize it.
- If the previous manuscript's wording could be read as claiming more than was done ("the first general framework"), say so and show the corrected, narrower wording.
- Give a connection-and-distinction discussion in the letter, ideally as a two-column aspect table (focus, object of study, role of the key tool, experimental scope), plus a comparison paragraph in the related work or discussion section of the manuscript.
- The distinction must be a real technical difference (what object is measured, what setting is targeted), not an adjective.

## 6. Overclaim flagged

The reviewer says a claim is too strong. Strategy: concede and downgrade visibly.

- Quote the removed wording and the replacement wording side by side in the response: "We have removed the stronger wording about X and replaced it with this more precise statement: ..."
- The new claim must be checkable against the evidence presented.
- Sweep the manuscript for echoes of the old claim (abstract, intro, conclusion); downgrading one instance while the abstract still overclaims is a round-2 comment waiting to happen.

## 7. Complexity / scalability claims questioned

The reviewer doubts a cost, scaling, or performance claim. Strategy: derivation plus measurement.

- Give the derivation in the letter (count the operations, state the assumptions) and a scaling experiment over the relevant range.
- If the claim was wrong, this is archetype 1; admit and correct.

## 8. Citation errors / missing references

Wrong, missing, or misattributed citations. Strategy: fix and engage.

- Fix the entry, and discuss the work substantively where it matters; never just append a reference to the list to placate.
- If the missed work overlaps the contribution, treat it under archetype 5.

## 9. Reviewer misread the paper

The reviewer's comment rests on a misunderstanding of what the paper actually says or does. Strategy: never say the reviewer is wrong. Convert their error into our unclear writing.

- The frame is always: "We agree that the original manuscript did not make this clear. The intended meaning is X. We have clarified this in Section N."
- Then actually clarify the manuscript. If a careful reviewer misread it, the text was misreadable; the clarification is a real improvement, not a concession of convenience.
- Do not restate the original text and assert it was already clear. That move loses even when technically correct.
- Distinct from counter-strengthen (archetype 10): there the reviewer's premise is engaged with evidence; here the premise dissolves once the text says what it meant.

## 10. Counter-strengthen: the comment rests on a refutable premise

The reviewer's objection can be structurally refuted with evidence. Strategy: concede the surface, refute the premise, end stronger.

- Open with a genuine concession: the premise was inviting because the paper was unclear or the evidence was missing.
- Carry the refutation with an experiment, a derivation, or a structural argument, never with assertion.
- Done well, a scope apology becomes a stronger claim. The response should read as "your question made the paper stronger", never as "you are wrong".

## 11. Infeasible ask (hardware access, research-scale extension, structural constraint)

The request cannot be met for real reasons. Strategy: the principled decline. This is rare; effort is never the reason.

- Explain the principled reason in detail. Example pattern: real-hardware noise is uncontrolled and drifting, so it cannot be converted into a certified guarantee without backend-specific characterization, which is a separate study.
- Offer the closest feasible alternative and actually do it (the simulator scaling study in place of hardware runs), so the decline arrives bundled with new work.
- Frame the original ask as future work, named specifically, not as a brush-off.
- Acceptable decline grounds also include page-budget violations and submission-mechanics asks; state them as such.

## 12. Notation / presentation inconsistency

Inconsistent symbols, duplicated notation, formatting drift. Strategy: unify globally and state the convention.

- Fix every instance, not just the flagged one.
- State the unified convention in the manuscript where the notation first appears ("Throughout this paper, epsilon and its variants denote privacy budgets; e denotes Euler's number").
- In the letter, show representative corrected formulas so the reviewer can verify without re-reading the whole paper.

## 13. Pure praise / no change requested

The reviewer compliments something or explicitly requires nothing. Strategy: brief acknowledgment, one or two sentences of thanks.

- Do not force the five-move arc onto praise; it reads as sycophantic.
- If the praise touches something the revision changed for other reasons, add one sentence noting the change so the reviewer is not surprised.

## 14. Duplicate comment across reviewers

Two reviewers raise the same issue. Strategy: full treatment once, self-contained summary at the second occurrence.

- First occurrence gets the complete response, including any rewritten proof or new experiment.
- Second occurrence gets a complete, self-contained summary of the fix, closing with an explicit cross-reference: "This correction is the same revision made in response to Reviewer 1, Comment 4, where the complete revised proof is provided."
- Never answer with only "see above"; each reviewer reads their own section.
