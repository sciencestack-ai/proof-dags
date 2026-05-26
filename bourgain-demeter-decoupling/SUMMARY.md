# Fourier decoupling

The Bourgain–Demeter $\ell^2$ decoupling theorem, its roots in multilinear Kakeya, and its number-theoretic consequences.

**Main theorem** — Bourgain–Demeter (`1403.5335`): for a compact hypersurface with nonzero Gaussian curvature, the $\ell^2$ decoupling inequality holds in the full conjectured range $2 \le p \le \tfrac{2(n+1)}{n-1}$. Proof structure: a wave-packet decomposition and parabolic rescaling reduce the linear inequality to a multilinear one (the linear-vs-multilinear reduction, thm:5.3), and the multilinear estimate is supplied by the Bennett–Carbery–Tao multilinear restriction/Kakeya inequality.

**Kakeya foundation.** Bennett–Carbery–Tao (`math/0509262`) prove near-optimal multilinear Kakeya and restriction by heat-flow monotonicity (the Loomis–Whitney / induction-on-scales mechanism). Guth gives an endpoint version (`0811.2251`) and a short proof (`1409.4683`). This is the geometric input the decoupling theorem imports.

**Vinogradov consequence.** Decoupling for the moment curve yields the main conjecture in Vinogradov's mean value theorem (`1512.01565` and downstream). The graph records the *parallel* proof: Wooley's efficient congruencing (`1401.3150`) proves the same theorem by a $p$-adic iteration, with no logical dependency on decoupling — a `parallel_result` edge between two structurally unrelated proofs of one theorem.

**Cross-graph.** Shares `math/0509262` with the **kakeya-restriction** graph (multilinear Kakeya is foundational to both programs — and is also the input to Guth's restriction estimate there). Shares `1408.5794` (Bourgain's decoupling $\zeta$-bound) and `2405.20552` (Guth–Maynard) with the **large-values-zero-density** graph: decoupling feeds the exponential-sum bounds that drive zero-density estimates for $\zeta$.
