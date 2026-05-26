# Sphere Packing

The proof that the $E_8$ and Leech lattices realize the densest sphere packings in $\mathbb{R}^8$ and $\mathbb{R}^{24}$. The program has a clean two-stage structure: **the LP framework** sets up the problem and conjectures the form of the answer; **the modular-form construction** then realizes the conjectured magic functions.

## The arc

**Cohn–Elkies (`math/0110009`, 2003)** prove the linear-programming bound: any admissible radial Schwartz $f$ with $f(0)=\widehat{f}(0)$, $f(x)\le 0$ for $|x|\ge r$, and $\widehat{f}\ge 0$ everywhere bounds the sphere-packing center density by $f(0)/(2^n\widehat{f}(0))$. They conjecture (Conjecture 2 / Conjecture 4) that such a *magic function* exists and is sharp in dimensions 2, 8, 24, with roots exactly at the lattice vector lengths.

**Viazovska (`1603.04246`, 2016)** constructs the magic function for $E_8$ from weight-3/2 weakly-holomorphic modular forms on the theta group: $g = \frac{\pi i}{8640}a + \frac{i}{240\pi}b$, where $a$ and $b$ are the $+1$ and $-1$ Fourier eigenfunctions built as contour integrals of quasi-modular forms. The Fields-medal result, resolving Cohn–Elkies Conjecture 2 for $n=8$.

**CKMRV (`1603.06518`, 2016)** extends Viazovska's template to the Leech lattice in $\mathbb{R}^{24}$ with different modular forms — same eigenfunction architecture, different weights and group.

**Cohn–Miller (`1603.04759`, 2016)** studies the structure of the magic functions: a polynomial-times-Gaussian numerical method, the value-and-derivative constraints at $\sqrt{2n}$, Taylor coefficients, and a conjectural energy-minimization reformulation that becomes the next stage of the program.

**Radchenko–Viazovska (`1701.00265`, 2017)** abstracts the magic-function construction into a free-standing **Fourier interpolation theorem** on $\mathbb{R}$: even Schwartz functions are uniquely determined by their values at $\pm\sqrt n$ and the Fourier values at $\pm\sqrt n$, with an explicit interpolation basis from modular forms.

**Cohn–Kumar (`math/0607446`, 2006)** had earlier developed the universal-optimality framework on spheres and compact two-point homogeneous spaces, and conjectured (Conjecture 32) universal optimality of $E_8$ and Leech.

**CKMRV (`1902.05438`, 2019)** proves that conjecture — universal optimality of $E_8$ and Leech for every completely monotonic pairwise energy — via a higher-dimensional interpolation formula (now with derivative data $f'(\sqrt{2n})$), the modular-form annihilator-space machinery on $\mathbb{C}[\mathrm{PSL}_2(\mathbb{Z})]$, and a kernel-positivity reduction verified by computer.

**Hariharan–Birkbeck–Lee (`2604.23468`, 2026)** close the loop with the Lean 4 formalization of Viazovska's $E_8$ proof — this DAG's blueprint-validation anchor, included as an arXiv node so the informal-to-formal correspondence is captured directly as an intra-DAG `imports_result` edge.

## Blueprint validation

The Lean project `Sphere-Packing-Lean` (kickstarted at EPFL March 2024 by Viazovska and Hariharan; maintained by Birkbeck, Hariharan, Mehta, Lee; completed February 2026 with Math, Inc.'s Gauss autoformalization model assisting the final stages) is the **third blueprint-validation anchor** in the registry, after PFR and PNT+. Project URLs: dim-8 main project at [`thefundamentaltheor3m/Sphere-Packing-Lean`](https://github.com/thefundamentaltheor3m/Sphere-Packing-Lean) with live blueprint at [`thefundamentaltheor3m.github.io/Sphere-Packing-Lean/blueprint/`](https://thefundamentaltheor3m.github.io/Sphere-Packing-Lean/blueprint/); ongoing dim-24 extension at [`math-inc/Sphere-Packing-Lean`](https://github.com/math-inc/Sphere-Packing-Lean).

The blueprint formalizes Viazovska's $E_8$ proof at fine granularity — **139 nodes** (19 theorems, 17 propositions, 15 corollaries, 54 lemmas, 34 definitions), as verified by fetching the live dep-graph on 2026-05-26. Our extraction of `1603.04246` collapses these to 12 chapter-level theorem nodes (the same ~11× ratio as PFR: blueprint 218 nodes ↔ our 21). The blueprint's "Cohn–Elkies" theorems (Theorem 5.1 / Theorem 5.2) match `math/0110009:thm:2` and `1603.04246:thm:2` verbatim; a full label-by-label correspondence for the remaining Chapter-6 / Chapter-7 nodes (magic-function construction and eigenfunctions) is the analog of the open PFR 16-node audit, and is flagged as an open item.

Unique here vs the other two anchors: (i) **the formalization paper is itself an arXiv node in this DAG**, so the informal/formal correspondence shows up directly as cross-paper edges (`2604.23468v2:thm:1` `imports_result` `1603.04246v2:thm:1`); (ii) **the formalization was partly AI-assisted** (Math, Inc.'s Gauss model finished the final verification stages) — directly relevant to AI for Math, since the validation anchor was itself produced by the kind of human–AI workflow this graph infrastructure is meant to support.

## Stats

8 papers extracted (98 theorem- and lemma-level nodes, 95 intra-paper edges), plus 22 cross-paper edges that lay out the program's structural arc (LP conjectures → realized → abstracted → universally generalized → formally verified). No cross-DAG edges: sphere packing is a standalone island in the registry, but the densest island — every paper contributes load-bearing structure (`imports_result`, `proves`, `extends`, `abstracts`, `generalizes`, `uses_mechanism`) into the same connected component. All arXiv IDs verified against the arXiv API (2026-05-26); every per-paper DAG passes the integrity gate.
