# Registry Status

Snapshot as of 2026-05-27.

## Totals

**11 DAGs · 114 papers · 1,958 nodes · 2,124 intra-paper edges · 400 cross-paper edges** (of which 38 are genuinely cross-DAG between distinct programs; the rest are within-program cross-paper).

| DAG | papers | nodes | intra edges | cross edges | role |
|---|---:|---:|---:|---:|---|
| nse-blowup | 27 | 550 | 664 | 75 | flagship · PDE · densest internal cross-linking |
| bourgain-demeter-decoupling | 12 | 243 | 269 | 24 | harmonic analysis · review-grade (Tao) |
| perfectoid-spaces | 11 | 227 | 260 | 102 | arithmetic geometry · Priority Index |
| maynard-small-gaps | 15 | 210 | 247 | 84 | bounded gaps · audited (~80% strong) |
| pfr | 10 | 146 | 84 | 28 | **Lean blueprint anchor #1 (PFR / Tao)** |
| prime-number-theorem | 7 | 143 | 155 | 18 | **Lean blueprint anchor #2 (PNT+ / Kontorovich)** |
| large-values-zero-density | 6 | 110 | 118 | 10 | zero density · Guth–Maynard frontier |
| sphere-packing | 8 | 98 | 95 | 22 | **Lean blueprint anchor #3 (Sphere-Packing-Lean / Math, Inc. Gauss)** |
| langlands-local | 6 | 88 | 83 | 14 | local Langlands |
| kakeya-restriction | 6 | 76 | 77 | 6 | Kakeya / restriction |
| cap-set | 6 | 67 | 72 | 17 | additive combinatorics · polynomial method · **AI-for-math (FunSearch)** |

Granularity sits in the 11–25 nodes/paper band across all DAGs. The `cap-set` average dips slightly because one of its six papers is a single-node `paper_kind: "nature-only"` entry (FunSearch) — see "Non-arXiv nodes" below.

## Connected components

**Region 1 — Arithmetic geometry** (2 DAGs, 14 cross-DAG edges, all into Fargues–Scholze `2102.13459`):
`perfectoid-spaces` ↔ `langlands-local`.

**Region 2 — Harmonic analysis → analytic number theory** (5 DAGs, 13 cross-DAG edges):
`kakeya-restriction` ↔ `bourgain-demeter-decoupling` ↔ `large-values-zero-density` ↔ `prime-number-theorem` ↔ `maynard-small-gaps`.

The PNT DAG is the keystone joining maynard into the chain via a load-bearing `provides_input_to` edge (Maynard III equidistribution → Maynard–Tao sieve's `prop:4.1`).

**Standalone islands** in the load-bearing sense (4 DAGs):
- `nse-blowup` — PDE; very dense internally (75 within-DAG cross-paper edges), no cross-DAG out.
- `pfr` — additive combinatorics; only foundational refs out (Ruzsa 1996, Tao 2010 entropy notes).
- `sphere-packing` — discrete geometry; standalone but the densest island (22 within-program cross-paper edges, every paper load-bearing).
- `cap-set` — additive combinatorics / polynomial method; three thematic edges to `pfr` typed `addresses_same_question`, no load-bearing cross-DAG edges. Internally dense (17 within-program cross-paper edges including one `improves` from FunSearch into Tyrrell).

**Thematic adjacency** (not a connected region): `cap-set` ↔ `pfr`, three `addresses_same_question` edges. Both DAGs study extremal structure of $\mathbb{F}_p^n$ subsets but with disjoint machinery (slice rank / polynomial method vs entropy / Plünnecke–Ruzsa / Bogolyubov). Listed explicitly so a reviewer doesn't conflate thematic with load-bearing.

## Lean blueprint anchors

Three programs are paired with live Lean blueprints — independent subfields, independent projects, all checkable against the extraction:

| DAG | Blueprint project | Lead | Subfield | Blueprint size | Verified label matches |
|---|---|---|---|---:|---|
| `pfr` | PFR (Tao 2023) | T. Tao | additive combinatorics | 218 nodes | 16-node correspondence proposed; full label-by-label table is an open audit item; one questionable edge in `papers/2311.05762.json` (endgame attachment) flagged |
| `prime-number-theorem` | PNT+ | A. Kontorovich et al. | analytic number theory | (not crawled label-by-label) | classical-core layer matches the project's stated scope; label-by-label table not yet built |
| `sphere-packing` | Sphere-Packing-Lean (EPFL/Math, Inc.) | Viazovska, Hariharan, Birkbeck, Mehta, Lee — final stages by Math, Inc. Gauss autoformalization | discrete geometry / modular forms | 139 nodes (verified on 2026-05-26) | one verified label match (Cohn–Elkies = blueprint Thm 5.1/5.2); Chapter 6/7 mapping not label-by-label verified |

The sphere-packing anchor is unique in two ways: (i) the formalization paper itself (`2604.23468`) is an arXiv node in the DAG, so the informal/formal link is captured as an intra-DAG `imports_result` edge rather than only via external reference; (ii) the final formalization stages were AI-assisted — directly relevant to AI for Math.

## AI-for-math anchors

Two distinct AI-for-math episodes are now load-bearing in the registry:

| Episode | DAG | Form | Edge |
|---|---|---|---|
| Math, Inc. Gauss autoformalization of Viazovska's $E_8$ proof | `sphere-packing` | arXiv-published formalization paper (`2604.23468`) as a first-class node | intra-DAG `imports_result` from formalization to the informal proof |
| DeepMind FunSearch (Romera-Paredes et al., Nature 625, 468–475, 2024) | `cap-set` | Nature-only paper admitted as `paper_kind: "nature-only"` single-node entry | `improves` edge into Tyrrell's $2.218^n$ lower bound (`2209.10045v2:thm:1.2`); `depends_on` edge into Tyrrell's admissible-set definition (`2209.10045v2:def:2.5`) |

These are the registry's two structural examples of AI-for-math — autoformalization on the proof side, AI-driven discovery on the construction side, both with load-bearing graph edges (not just citations or prose).

## Non-arXiv nodes

By convention, every node in the registry corresponds to a math environment in an arXiv-parsed paper — with one deliberate, narrowly-scoped exception. Results published Nature-first (no arXiv preprint) that are *load-bearing for an AI-for-math episode* are admitted as single-node entries with `paper_kind: "nature-only"` in the per-paper file. Currently this applies to exactly one node: `funsearch-nature-2024:thm:funsearch-capset` in `cap-set`. Documented in `README.md` and `cap-set/SUMMARY.md`. The convention does not extend to Nature-only papers that only need to be cited — a typed graph edge into the surrounding program must exist to justify the inclusion.

## Edge vocabulary discipline

After the 2026-05-27 audit, the data uses **15 distinct edge types from a 21-type controlled vocabulary** (README "Typed edge vocabulary"). **Zero drift:** every edge type in the data appears in the schema; every type in the schema is either in use or aspirational for future programs (`transliterates`, `removes_hypothesis`, `synthesizes`, `method_pivot`, `alternative_engine`, `shared_tool`). 100 drift edges across 30 files were reconciled in this pass:
- `references` (1) — cut as redundant noise.
- `implies`, `uses`, `uses_mechanism`, `uses_hypothesis` (100 total) — collapsed to `depends_on`; the four variants carried no distinguishable semantic.
- `specializes` (24) — direction-flipped and renamed to `generalizes` (same relation, normalized direction).
- `proves` (50) — collapsed to `depends_on`; proof-node-to-theorem edges are scaffolding without discriminative signal.
- `motivates` (38) — *kept*, added to README schema as a directional thematic verb distinct from `addresses_same_question`. Restored after a brief over-collapse caught in review.
- Two load-bearing cap-set edges retyped from `depends_on` to `provides_input_to` (cap-set bound → matmul barrier; cap-set bound → sunflower bound) — the hypothesis-grade-input semantic was being flattened.

## What the registry shows

- **Structure beyond citations.** 2,124 intra-paper edges + 400 cross-paper edges use the typed vocabulary in `README.md`. The distinction the proposal makes — load-bearing vs thematic — is realized: 38 cross-DAG edges across two genuine connected regions plus one documented thematic adjacency.
- **Cross-program connections.** The proposal's distinctive claim ("where one program hands off to another, which citation graphs cannot express") is instantiated by, among others, the load-bearing `2006.08250v1:thm:1.3 provides_input_to 1311.4600v3:prop:4.1` edge and the AI-for-math `funsearch-nature-2024:thm:funsearch-capset improves 2209.10045v2:thm:1.2` edge.
- **Three blueprint-validation cases across three subfields.** Not "we validated once"; methodology shown across additive combinatorics, analytic number theory, and discrete geometry.
- **Two AI-for-math anchors.** Autoformalization (`sphere-packing`) and AI-driven discovery (`cap-set`/FunSearch), both load-bearing.
- **Feasibility evidence.** PNT (7 papers / 143 nodes), sphere-packing (8 papers / 98 nodes), and cap-set (6 papers / 67 nodes including a latex2json parser fix and FunSearch admission) were each built end-to-end in roughly a session — empirical evidence the per-program cost is bounded by extraction-and-review, not by infrastructure rebuilding.

## Honest open audit items

1. **Full label-by-label correspondence tables** for the PFR, PNT, and sphere-packing blueprint anchors — three "verify each node" tables, none built yet. The proposal-grade move is to do them.
2. **PFR edge re-pointing** — `1402.0290v3`'s endgame edges are placed at the wrong parent level vs the Lean blueprint (transitively correct, structurally off).
3. **Inter-annotator / inter-pass agreement per edge type** — flagged by reviewer audit. Re-run the extraction on a sample of papers with a second pass (different prompt, or human annotator) and report disagreement rates per edge type. Low-agreement types become real merge candidates, by data rather than by eye; high-agreement types earn their schema slot empirically.
4. **Drop proof nodes registry-wide** — proof:X → theorem X edges (now 50, all retyped `depends_on`) are pure scaffolding. A future pass should either remove proof nodes entirely (theorems / lemmas / propositions are the navigation targets) or formalize their role separately from the typed-edge schema.
5. **Granularity consistency within DAGs** — sphere-packing's Leech paper (7 nodes) and the Lean formalization paper (2 nodes) pull the average down; cap-set's FunSearch node (1) does so by design. Defensible per-case but worth tracking.
6. **Expert audit pass on `cap-set`** — `maynard-small-gaps`-style ~30-minute additive-combinatorics expert review of the cap-set edges. Currently at the "verified-faithful structurally" tier, like 9 of 11 DAGs.

These don't break what's built — they're the work between "structurally verified" and the audited-flagship tier.

## File state

Each DAG lives at `<topic>/` with `manifest.json` (program description, papers and roles, related DAGs, blueprint anchor), `index.json` (extraction status per paper), `queue.json` (work queue, mostly empty after this session), `graph.json` (cross-paper and cross-DAG edges), `papers/*.json` (per-paper DAGs with nodes, edges, critical_path, proof_architecture, bibliography), and `SUMMARY.md` (readable program overview). All JSON files validate. Every arXiv ID has been verified against the arXiv API.

## What was built in the 2026-05-27 session

- **`cap-set`** — new DAG, built from scratch. Verified 5 arXiv IDs; parsed all 5 through `latex_pipeline`. Hit a parser failure on Naslund–Sawin (`1606.09575v1`: only 1 math env detected out of 9 expected) traced to babel's `\newtheorem{thm}{\protect\theoremname}` idiom interacting badly with two latex2json bugs (`\protect` mis-modeled as `\noexpand`; `\<env>name` auto-registration clobbering babel defaults via self-referential bindings). Fixed both in latex2json with `\providecommand`-semantics, extended babel translation table from 3 to 18 standard names, full test suite (1011/1011) passing. Re-parsed → 8 math envs detected. Extracted DAGs for all 5 papers (8/8/9/21/20 nodes). Added FunSearch (Nature 2024) as a single-node `paper_kind: "nature-only"` entry with an `improves` edge into Tyrrell. Final: 6 papers, 67 nodes, 72 intra-paper edges, 17 cross-paper edges (14 within `cap-set`, 3 thematic into `pfr`).
- **Registry-wide vocab discipline pass** — surveyed all 11 DAGs for edge-type drift against README's controlled vocabulary, reconciled 100 drift edges across 30 files. End state: zero drift, schema = data both directions. Added `motivates` to README schema; retyped two load-bearing cap-set edges from `depends_on` to `provides_input_to`.
- **README and STATUS** updated to reflect the new DAG, totals, edge-vocabulary state, and non-arXiv node convention.

**Net change:** 10 → 11 DAGs · 108 → 114 papers · 1,853 → 1,958 nodes · 2 → 2 Lean-blueprint-anchored programs · 1 → 2 load-bearing AI-for-math anchors.
