# Bounded gaps between primes

The Goldston–Pintz–Yıldırım $\to$ Zhang $\to$ Maynard–Tao arc, built on the multidimensional Selberg sieve.

**Sieve precursors.** GPY (`math/0508185`, and GPY-I `0710.2728`) prove $\liminf_n (p_{n+1}-p_n)/\log p_n = 0$ via a one-dimensional Selberg-sieve weight on admissible tuples, conditional on a level of distribution $\theta > 1/2$ for bounded gaps.

**Maynard's sieve** — Maynard (`1311.4600`): a multidimensional sieve weight removes the level-of-distribution barrier and proves, *unconditionally*, $\liminf_n(p_{n+1}-p_n) \le 600$, and for every $m$, $\liminf_n(p_{n+m}-p_n) \ll m^3 e^{4m}$ — bounded gaps for arbitrarily long blocks, qualitatively new beyond GPY/Zhang. Critical path: the $k$-dimensional sieve optimization (`thm:1.3`) $\to$ the diagonalized quadratic forms $S_1, S_2$ (`prop:4.1/4.2`) $\to$ explicit eigenvalue bounds (`lem:5.1`, `lem:6.1/6.2`).

**Polymath.** Polymath8b (`1407.4897`) pushes the unconditional bound to $246$ and optimizes the variational problem; Polymath8a (`1402.0811`) is the Zhang-side level-of-distribution improvement (Type I/II/III estimates via algebraic exponential sums).

**Consequences.** Pintz (`1305.6289`): Polignac numbers have positive lower density, and the limit set of normalized gaps contains an interval. Related extensions to gaps in dense sequences and prime tuples.

This program is logically disjoint from the prime-distribution / zero-density program (see **large-values-zero-density**) despite the shared Maynard authorship — a thematic, not load-bearing, adjacency.
