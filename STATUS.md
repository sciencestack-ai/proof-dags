# Registry Status

Snapshot as of 2026-05-26.

## Totals

**10 DAGs · 108 papers · 1,853 nodes · 2,013 intra-paper edges · 382 cross-paper edges** (of which 27 are genuinely cross-DAG between distinct programs; the rest are within-program cross-paper).

| DAG | papers | nodes | intra edges | cross edges | role |
|---|---:|---:|---:|---:|---|
| nse-blowup | 27 | 512 | 625 | 75 | flagship · PDE · densest internal cross-linking |
| bourgain-demeter-decoupling | 12 | 243 | 269 | 24 | harmonic analysis · review-grade (Tao) |
| perfectoid-spaces | 11 | 227 | 260 | 102 | arithmetic geometry · Priority Index |
| maynard-small-gaps | 15 | 210 | 247 | 84 | bounded gaps · audited (~80% strong) |
| pfr | 10 | 146 | 84 | 28 | **Lean blueprint anchor #1 (PFR / Tao)** |
| prime-number-theorem | 7 | 143 | 155 | 17 | **Lean blueprint anchor #2 (PNT+ / Kontorovich)** |
| large-values-zero-density | 6 | 110 | 118 | 10 | zero density · Guth–Maynard frontier |
| sphere-packing | 8 | 98 | 95 | 22 | **Lean blueprint anchor #3 (Sphere-Packing-Lean / Math, Inc. Gauss)** |
| langlands-local | 6 | 88 | 83 | 14 | local Langlands |
| kakeya-restriction | 6 | 76 | 77 | 6 | Kakeya / restriction |

Granularity sits in the 12–25 nodes/paper band across all DAGs.

## Connected components

**Region 1 — Arithmetic geometry** (2 DAGs, 14 cross-DAG edges, all into Fargues–Scholze `2102.13459`):
`perfectoid-spaces` ↔ `langlands-local`.

**Region 2 — Harmonic analysis → analytic number theory** (5 DAGs, 13 cross-DAG edges):
`kakeya-restriction` ↔ `bourgain-demeter-decoupling` ↔ `large-values-zero-density` ↔ `prime-number-theorem` ↔ `maynard-small-gaps`.

The PNT DAG is the keystone joining maynard into the chain via a load-bearing `provides_input_to` edge (Maynard III equidistribution → Maynard–Tao sieve's `prop:4.1`).

**Standalone islands** (3 DAGs):
- `nse-blowup` — PDE; very dense internally (75 within-DAG cross-paper edges), no cross-DAG out.
- `pfr` — additive combinatorics; only foundational refs out (Ruzsa 1996, Tao 2010 entropy notes).
- `sphere-packing` — discrete geometry; standalone but the densest island (22 within-program cross-paper edges, every paper load-bearing).

## Lean blueprint anchors

Three programs are paired with live Lean blueprints — independent subfields, independent projects, all checkable against the extraction:

| DAG | Blueprint project | Lead | Subfield | Blueprint size | Verified label matches |
|---|---|---|---|---:|---|
| `pfr` | PFR (Tao 2023) | T. Tao | additive combinatorics | 218 nodes | 16-node correspondence proposed; full label-by-label table is an open audit item; one questionable edge in `papers/2311.05762.json` (endgame attachment) flagged |
| `prime-number-theorem` | PNT+ | A. Kontorovich et al. | analytic number theory | (not crawled label-by-label) | classical-core layer matches the project's stated scope; label-by-label table not yet built |
| `sphere-packing` | Sphere-Packing-Lean (EPFL/Math, Inc.) | Viazovska, Hariharan, Birkbeck, Mehta, Lee — final stages by Math, Inc. Gauss autoformalization | discrete geometry / modular forms | 139 nodes (verified on 2026-05-26) | one verified label match (Cohn–Elkies = blueprint Thm 5.1/5.2); Chapter 6/7 mapping not label-by-label verified |

The sphere-packing anchor is unique in two ways: (i) the formalization paper itself (`2604.23468`) is an arXiv node in the DAG, so the informal/formal link is captured as an intra-DAG `imports_result` edge rather than only via external reference; (ii) the final formalization stages were AI-assisted — directly relevant to AI for Math.

## What the registry shows

- **Structure beyond citations.** 2,013 intra-paper edges + 382 cross-paper edges use the typed vocabulary in `README.md` (`improves`, `extends`, `imports_result`, `provides_input_to`, `addresses_same_question`, `shared_mechanism`, …). The distinction the proposal makes — load-bearing vs thematic — is realized.
- **Cross-program connections.** 27 cross-DAG edges across two genuine connected regions. The proposal's distinctive claim ("where one program hands off to another, which citation graphs cannot express") is instantiated, notably by the load-bearing `2006.08250v1:thm:1.3 provides_input_to 1311.4600v3:prop:4.1` edge.
- **Three blueprint-validation cases across three subfields.** Not "we validated once"; methodology shown across additive combinatorics, analytic number theory, and discrete geometry.
- **Feasibility evidence.** PNT (7 papers / 143 nodes) and sphere packing (8 papers / 98 nodes) were each built end-to-end in roughly a session using only the live ScienceStack AST API — empirical evidence the per-program cost is bounded by extraction-and-review, not by infrastructure rebuilding.

## Honest open audit items

1. **Full label-by-label correspondence tables** for the PFR, PNT, and sphere-packing blueprint anchors — three "verify each node" tables, none built yet. The proposal-grade move is to do them.
2. **PFR edge re-pointing** — `1402.0290v3`'s endgame edges are placed at the wrong parent level vs the Lean blueprint (transitively correct, structurally off).
3. **Expert audit pass** — only `maynard-small-gaps` has the ~30-min expert pass (~80% strong per `README.md`). The other nine DAGs are at the "verified-faithful structurally, not edge-audited" tier.
4. **Granularity consistency within DAGs** — sphere-packing's Leech paper (7 nodes) and the Lean formalization paper (2 nodes) pull the average down; defensible since both papers are inherently short, but a strict reviewer comparing papers side-by-side will notice.

These don't break what's built — they're the work between "structurally verified" and the audited-flagship tier.

## File state

Each DAG lives at `registry/dags/<topic>/` with `manifest.json` (program description, papers and roles, related DAGs, blueprint anchor), `index.json` (extraction status per paper), `queue.json` (work queue, mostly empty after this session), `graph.json` (cross-paper and cross-DAG edges), `papers/*.json` (per-paper DAGs with nodes, edges, critical_path, proof_architecture, bibliography), and `SUMMARY.md` (readable program overview). All JSON files validate. Every arXiv ID has been verified against the arXiv API.

## What was built in the 2026-05-25 → 2026-05-26 sessions

- `prime-number-theorem` — built from scratch (parse 6 papers, extract 7 DAGs, cross-paper graph, manifest, SUMMARY), then enriched (4 papers brought to full lemma depth: Maynard III 10→21 nodes, Shao–Teräväinen 20→27, Matomäki–Radziwiłł I 11→25, Matomäki–Radziwiłł II 13→27). Final: 7 papers, 143 nodes, 20.4/paper.
- `sphere-packing` — built from scratch (parse 8 papers, extract 8 DAGs, cross-paper graph). 8 papers, 98 nodes. Includes the Lean formalization paper `2604.23468` as a first-class arXiv node.
- Blueprint cross-checks: re-fetched the live PFR and Sphere-Packing-Lean blueprint dep-graphs; recorded sizes (218 and 139 nodes); fixed a fabricated URL in the sphere-packing manifest.

**Net change:** 8 → 10 DAGs · 92 → 108 papers · 1,612 → 1,853 nodes · 2 → 3 Lean-blueprint-anchored programs.
