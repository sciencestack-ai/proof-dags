# Polynomial Freiman–Ruzsa

The proof of the Polynomial Freiman–Ruzsa conjecture (Marton's conjecture) over $\mathbb{F}_2^n$, its entropic method, and downstream work.

**Main theorem** — Gowers–Green–Manners–Tao (`2311.05762`): if $A \subseteq \mathbb{F}_2^n$ has $|A+A| \le K|A|$, then $A$ is covered by at most $K^{12}$ translates of a subgroup $H$ with $|H| \le |A|$ — polynomial dependence on $K$, the conjectured form. The proof is entropic: it works with the Ruzsa distance $d[X;Y]$ between random variables and runs a "$\tau$-functional" descent that produces a subgroup from a near-minimizer.

**Method and improvement.** The generalized Ruzsa equivalences between sumset and entropic inequalities (`2312.11017`) underpin the translation. A sharpening (`2404.09639`) gives entropic PFR with constant $8$ and Marton's conjecture with $C = 9$. This proof was the object of Tao's 2023 Lean formalization (the "blueprint").

**Extensions.** Function-field / general-torsion PFR (`2501.11580`); approximate-group structure ($\varepsilon$-approximate groups, `2406.10872`); the quasi-polynomial covering bound $\exp(C_\varepsilon \log(2K)^{1+\varepsilon})$ (`2512.11217`); and applications of the entropic method to randomness extractors for sumset sources (`2405.10297`) and to Reed–Muller capacity (`2411.13493`).

Self-contained in the registry (no current cross-graph edges); included as the additive-combinatorics anchor and the worked counterpart to the PFR Lean blueprint.
