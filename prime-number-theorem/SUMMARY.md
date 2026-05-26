# The Prime Number Theorem: zero-free regions, equidistribution, and the modern frontier

The dependency structure of prime distribution, anchored on the Prime Number Theorem. The classical spine — Riemann's explicit formula $\to$ a zero-free region for $\zeta$ $\to$ PNT with error term $\to$ primes in arithmetic progressions — is pre-arXiv and lives in `manifest.json` under `foundational`. It is the layer with a Lean blueprint (the **PNT+** project), so it doubles as the external ground truth for validating extracted nodes and edges. The arXiv-era spine carries the program in three directions.

**Effective / explicit PNT.** Ford (`1910.08205`) builds the Vinogradov–Korobov zero-free region from a "zero detector" (a cotangent-integral identity localizing $-\Re\,\zeta'/\zeta$ over nearby zeros), giving the explicit region $1-\beta \le \frac{1}{57.54(\log|t|)^{2/3}(\log\log|t|)^{1/3}}$. Mossinghoff–Trudgian–Yang (`2212.06867`) re-run Ford's apparatus with sharpened constants — its lemmas *are* Ford's lemmas (the proofs cite "Ford Lemma 2.2", "Ford Lemma 5.1" verbatim) — improving the constant to $55.241$ and the classical-type region to $5.558691$. Platt–Trudgian (`1809.03134`) feed a zero-free region ($R=5.573412$), a verified Riemann Hypothesis up to height $3\times 10^{12}$, and a Pintz-type zero-density estimate into the truncated explicit formula to get a fully explicit bound on $|\psi(x)-x|$.

**Equidistribution beyond Bombieri–Vinogradov.** Maynard's large-moduli programme pushes primes-in-APs past the $1/2$ barrier; part III (`2006.08250`, uniform residue classes) is extracted here, parts I & II are shared nodes from the `maynard-small-gaps` DAG. Shao–Teräväinen (`2006.05954`) prove a Bombieri–Vinogradov theorem for nilsequence twists (levels $1/4$, $1/3$, $1/2$) via the Green–Tao equidistribution machinery, with applications to bounded gaps and Chen primes in nil-Bohr sets and Green–Tao in progressions.

**Short intervals.** Matomäki–Radziwiłł (`1501.04585`) prove that multiplicative functions have nearly constant average in almost all short intervals — a landmark whose engine is a Parseval bound on a Dirichlet polynomial (built from Halász's theorem and mean/large-value estimates), with corollaries on smooth numbers, Liouville correlations, and sign changes. Part II (`2007.04290`) extends the method to complex-valued functions with the sharp range $\rho<1/3-2/(3\pi)$ and applications to norm-forms.

## The keystone role

This DAG joins the analytic-number-theory region. **Cross-DAG → `large-values-zero-density`:** zero-*free* regions (here) and zero-*density* estimates (there) are the two complementary controls on $\zeta$-zeros — Ford's VK region improves Ingham's qualitative region, and Platt–Trudgian's Pintz density estimate is the same Ingham–Pintz mechanism as Starichkova's zero-density route. **Cross-DAG → `maynard-small-gaps`:** Maynard III's equidistributed minorant `provides_input_to` the Maynard–Tao sieve (`1311.4600v3:prop:4.1`), the load-bearing level-of-distribution the sieve consumes; Maynard III is the `companion_result` of Maynard I; and Shao–Teräväinen's nil-Bohr bounded gaps `extends` the Maynard bounded-gaps theorem.

## Validation against the PNT+ blueprint

The classical-core layer (PNT via Newman's Tauberian proof, PNT in APs) is formalized in the PNT+ Lean blueprint. As with the PFR cross-check, the blueprint's statement-level dependency graph is the external precision/recall yardstick for our extracted nodes on the PNT spine — and the contrast is the point: the blueprint maps the inside of the classical proof, while this DAG extends outward to the effective-PNT, equidistribution, and short-interval literature the blueprint does not reach.

## Stats

7 papers extracted (143 theorem- and lemma-level nodes, ~20.4/paper — matching the densest peer DAGs; 155 intra-paper edges), plus 17 cross-paper edges (6 cross-DAG). 2 shared nodes reused from `maynard-small-gaps`. All arXiv IDs verified against the arXiv API (2026-05-25); all edges resolve to real nodes; every per-paper DAG passes the integrity gate (node/edge resolution, connected critical path, full layer coverage, KaTeX-clean summaries).
