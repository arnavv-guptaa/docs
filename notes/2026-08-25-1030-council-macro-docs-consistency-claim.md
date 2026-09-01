# Council — How much to disclose about the "one source of truth" consistency mechanism

**Date:** 2026-08-25
**Domain:** General (product documentation / disclosure)
**Scope:** Standard — 5 advisors, 3 peer reviewers, 1 chairman (9 agent calls)
**Branch:** `dev-ben-macro` (not merged to `origin/main` — pre-publication)
**Source of the question:** Vincent's review, point 8, `~/Downloads/DOCS_BEN_REVIEW.md`

---

## Decision question

How should the Parallax Macro Reports public docs handle the "one source of truth for shared facts" consistency mechanism? How many mentions, on which pages, at what specificity, with what wording scope?

Owner's two goals: (a) prospects read the firm as rigorous and data-driven; (b) do not disclose enough that a competitor could recreate the pipeline. Owner's instinct: "more is less, less is more."

---

## Verified inventory (three independent greps agreed)

Vincent's count was wrong. The real inventory:

**Five full-strength claims on three pages:**
| File | Line | Text |
|---|---|---|
| `macro/overview.mdx` | 33 | "a single authoritative source for key shared facts" |
| `macro/overview.mdx` | 77 | bullet: "One source of truth per shared fact" |
| `macro/methodology.mdx` | 67-71 | H3 section, "removes this by construction for key shared facts" |
| `macro/methodology.mdx` | 93 | bullet: "Every shared fact has one source, enforced by architecture rather than by diligence" |
| `macro/data-coverage.mdx` | 85 | "Consistency on those shared facts is enforced by architecture, not by proofreading" |

**Two adjectival echoes:** `macro/anatomy.mdx:28`, `macro/data-coverage.mdx:33` — both say "authoritative".

**Zero glossary hits.** Vincent's "plus a glossary page" does not reproduce. `glossary/curve-shape.mdx:16` mentions the policy rate as a generic definition with no consistency claim.

**One intentional disclaimer to preserve:** `macro/methodology.mdx:75` already says "not an independent source of truth". Any future grep gate must carve it out.

---

## Verdict

Adopt the Executor's edit set. One full-strength mention at `macro/methodology.mdx:67-71`, retitled and scoped to the named policy rate. Delete the other four claims. Downgrade both "authoritative" echoes to "verified".

Two chairman amendments:
1. Ship it in the same commit as the 600M and continuous-refresh cuts. `macro/` is not on `origin/main`, so this is a pre-publication gate, not a live correction.
2. Soften `methodology.mdx:69`. Drop the causal "removes this by construction".

### On the moat premise

All five advisors rejected it, and the chairman confirmed. Fetch-once-and-inject is a commodity engineering pattern. Secrecy buys nothing.

"Less is more" is correct, but for a different reason than the owner stated. One singular verifiable claim survives a MAS-scope audit. Five plural ones do not. The binding constraint is **evidencing burden per sentence**, not IP leakage.

This matters for the next decision. Held for the wrong reason, the same instinct will suppress the verified differentiators, which are demo currency and cost nothing to disclose.

---

## Edit set

| File | Line | Action |
|---|---|---|
| `overview.mdx` | 33 | Cut sentences 2-3. Keep framework + single-synthesis-layer. |
| `overview.mdx` | 77 | Delete bullet. List goes 4 → 3, all survivors true. |
| `methodology.mdx` | 67 | Retitle H3 → "The Policy Rate Is Fetched Once". |
| `methodology.mdx` | 69 | Cut "for key shared facts such as". Drop the causal "removes this by construction". Keep: fetched once, verified, date-stamped, "passed to every section that cites it". |
| `methodology.mdx` | 71 | Rewrite singular, or cut. Graceful degradation already lives at `:28` and `data-coverage.mdx:83`. |
| `methodology.mdx` | 93 | Delete bullet. Universal quantifier + "enforced by architecture" is the most exposed line. |
| `data-coverage.mdx` | 85 | Delete paragraph. |
| `data-coverage.mdx` | 33 | "authoritative" → "verified". |
| `anatomy.mdx` | 28 | "authoritative" → "verified". |

Roughly 12 lines, 4 files, one sitting.

**Pass condition:**
```
grep -rniE "source of truth|shared fact|authoritative|enforced by architecture" macro/ glossary/
```
Hits only inside `methodology.mdx:67-71` and `:75`.

**Do not publish the roadmap.** Singular phrasing claims nothing about other fields. Silence is truthful. Roadmap language becomes a commitment compliance must later evidence.

---

## Rejected: the substitution move

Three advisors (Contrarian, First Principles, Outsider) wanted to refill the vacated `overview.mdx:33` slot with the no-fabrication / graceful-degradation claim.

The chairman rejected this against three advisors. Peer Reviewer A's reason: that claim carries a **higher** evidencing burden than the one being cut, and nobody proposed testing it first. Promoting an untested claim to load-bearing in the same commit repeats the failure being corrected.

Test it adversarially first. Force a data gap. Confirm the editor pass emits an explicit silence rather than plausible prose. Then promote it.

---

## Dissent worth hearing

**Expansionist:** put the date-stamped policy rate, with its source, in the weekly report itself. Two of three reviewers endorsed it. The artifact proves every week what no marketing sentence can, and it costs zero disclosure.

It lost only because it is a product change, not an answer to the docs question. It becomes the better move the moment the docs edit ships and the claim still needs external proof.

---

## Blind spots the peer review surfaced

**1. The remediation perimeter is wider than the repo.** Reviewers A and B converged independently. This copy is served to clients through the Parallax MCP `get_docs` / `explain_methodology` surface, and plausibly sits in decks, the website, and delivered reports. A docs-only fix leaves the overclaim live in the channel that repeats it under the firm's name. Nobody has scoped this sweep yet.

**2. Injection guarantees the input, not the output.** Reviewer C drew the consequence. The pipeline injects the same value into every section. Nothing verifies the model reproduces it faithfully in prose.

This kills the Outsider's proposed replacement wording ("so two sections cannot quote different rates"). It also indicts the surviving line: `methodology.mdx:69` currently says "removes this by construction". That is an unevidenced causal claim. Keep the mechanical description. Drop the causal one until a post-generation checker exists.

**3. Publication state.** Reviewer C checked. `macro/` is not in `main`. There is no live-compliance urgency and no reason for a separate commit.

---

## Convergence warning

All five advisors converged on "cut to one mention, methodology only, singular, name the policy rate."

Two peer reviewers flagged this as **partly manufactured**. The context brief handed the advisors Vincent's own recommendation ("use it once, framed as one example"). Responses 1, 2 and 4 restate it. Only 3 and 5 added information the brief did not contain.

The chairman's High confidence therefore rests on three independent greps, not on the five-way consensus.

---

## Engineering alternative (not gating)

Make the stronger claim true rather than making the weak claim smaller:
- **Post-generation checker:** extract the rate value from each drafted section, assert it matches the injected value, fail loudly. This makes "enforced" true instead of aspirational. Estimated ~half a day plus one weekly run to measure false positives.
- **Extend the shared-fact dict** to 10y yield / CPI / FX spot. Cheaper, but earns plural phrasing only after the checker exists.

Neither should gate the docs edit. Both are unverified from here — that pipeline is not in this worktree.

---

## Confidence

**High** on the edit set. Three independent greps, not consensus.
**Medium** on the wider perimeter sweep, which nobody has yet scoped.

---

## Follow-ons

1. Apply the nine edits with the 600M and refresh cuts, one commit, then run the grep gate.
2. Build the claims register (First Principles): one row per rigor claim, naming the evidencing artifact and the person who can produce it on demand. Chuan Yang signs the register, not the prose.
3. Scope the MCP / decks / website sweep for the same language.
4. Adversarially test graceful degradation before promoting it anywhere.
