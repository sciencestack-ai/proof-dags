# Cap Sets — Program Summary

A subset $A \subseteq \mathbb{F}_3^n$ is a **cap set** if it contains no three distinct elements in arithmetic progression — equivalently no nontrivial solutions to $x + y + z = 0$.

The cap-set problem asks for the largest cap set as a function of $n$. From 1995 (Meshulam, $O(3^n / n)$ via Roth-style Fourier density increment) to 2016, the upper bound resisted any exponential improvement despite repeated attacks. Then, in **a single month in May 2016**, the polynomial method broke it open. This DAG captures the cascade.

## The five papers, in order of dependency

1. **Croot–Lev–Pach** [`1605.01506`] proves the analogous bound in $\mathbb{Z}_4^n$: any progression-free $A$ has $|A| \le 4^{\gamma n}$ with $\gamma \approx 0.926$. The novel ingredient is a **polynomial-method lemma**: a multilinear polynomial $P$ that vanishes on all pairwise differences of a sufficiently large set must vanish at $0$, by a rank-counting argument on the matrix $[P(a-b)]_{a,b \in A}$.

2. **Ellenberg–Gijswijt** [`1605.09223`], independently and simultaneously, transport CLP's technique from $\mathbb{Z}_4^n$ to $\mathbb{F}_q^n$. Their key generalization (`prop:2`) adds a free coefficient parameter $\gamma$ to CLP `lem:1`, which lets the dimension-counting argument close in $\mathbb{F}_3^n$. Specializing to $q = 3$, the cap-set bound $|A| = o(2.756^n)$ falls out — breaking the four-decade Meshulam ceiling exponentially.

3. **Naslund–Sawin** [`1606.09575`], following Tao's blog post that re-cast the EG argument symmetrically, formalize the *slice rank* of a tensor and prove the **diagonal slice-rank lemma**: a tensor $T: A^3 \to \mathbb{F}$ supported exactly on the diagonal has slice rank $|A|$ (a non-trivial *exact equality*, not just an upper bound). They apply it to prove the **Erdős–Szemerédi sunflower conjecture** for triples: families of subsets of $\{1, \dots, n\}$ avoiding 3-sunflowers have size at most $(3/2^{2/3})^n \approx 1.890^n$ — the first sub-$2^n$ bound. Slice rank is the reformulation that makes the cap-set technique transportable.

4. **Blasiak–Church–Cohn–Grochow–Naslund–Sawin–Umans** [`1605.06702`], the same month, use the EG-style cap-set bound to prove a **matrix-multiplication barrier**: no construction in any abelian group of bounded exponent within the Cohn–Umans/CKSU framework can yield $\omega \le 2 + \varepsilon$ for $\varepsilon$ depending only on the exponent. The same machinery that closed off the upper bound on cap sets simultaneously closes off a major program for fast matrix multiplication.

5. **Tyrrell** [`2209.10045`], six years later, improves the cap-set *lower* bound from Edel's 2004 $2.2^n$ to $2.218^n$. The framework: **admissible sets** $S \subseteq \{0,1,2\}^m$ paired with **extendable triples** $(A_0, A_1, A_2)$ of cap sets in $\mathbb{F}_3^n$, glued by the *extended product construction* into cap sets of $\mathbb{F}_3^{nm}$. The witness sets are found via SAT-solver search.

The current state: $2.218^n \le |A| \le o(2.756^n)$. The gap is real and the registry's "AI-for-math" hook lives in this gap.

## The AI-for-math thread: FunSearch

In December 2023 DeepMind published *Mathematical discoveries from program search with large language models* (Romera-Paredes et al., **Nature 625, 468–475, 2024**, DOI [`10.1038/s41586-023-06924-6`](https://doi.org/10.1038/s41586-023-06924-6)). The system, **FunSearch**, uses an LLM (a code-focused Codey/PaLM 2 model) inside an evolutionary loop: the LLM proposes candidate Python functions that score combinatorial objects, the objects are evaluated, the highest scorers feed back into the LLM prompt.

Applied to Tyrrell's framework, FunSearch:
- Searched for new admissible sets $S \subseteq \{0,1,2\}^m$ that Tyrrell's SAT solvers could not find;
- Discovered a new cap set of size **512** in $\mathbb{F}_3^8$, beating the previous best of 496 (the largest known explicit cap set in dimension 8 for over 15 years);
- Pushed the asymptotic lower-bound rate above $2.218^n$ in specific dimensions.

This is **the** canonical "LLM discovers a new mathematical object" result. One of FunSearch's coauthors is **Jordan Ellenberg** — the same mathematician who, seven years earlier, proved the cap-set upper bound (`1605.09223`). The loop closes: the human-discovered upper bound and the AI-assisted lower bound were both shaped by the same person.

### Why FunSearch is not a graph node

FunSearch has **no arXiv preprint** — DeepMind's standard "Nature-first" pattern, the same as AlphaFold 2, AlphaGo, AlphaTensor, AlphaGeometry, AlphaProof. With no LaTeX source we cannot parse it through `latex_pipeline`, and with no `paper_nodes` in ScienceStack it cannot be a first-class graph node. It appears in `manifest.json` under `related_work` with the Nature DOI; this `SUMMARY.md` is where the narrative lives.

This is a real structural limitation worth flagging: a growing share of flagship AI-for-math results live outside the arXiv ecosystem this registry is built on. The cap-set program is the registry's clearest illustration — the *math lineage* (5 papers, all on arXiv, all in the DAG) is well-typed, but the AI episode that operates on top of it is a Nature paper. Sphere-packing (`sphere-packing` DAG) sits at the other end: the arXiv-published Lean formalization paper (`2604.23468`) is a first-class node, and the Math, Inc. autoformalization work is documented in the formalization repos themselves. Cap-set's FunSearch story has to be narrated rather than graphed.

## Cross-DAG: thematic adjacency to `pfr`, not a connected region

The cap-set DAG sits adjacent to the **`pfr`** DAG (Tao 2023 and the polynomial Freiman–Ruzsa lineage) — both study the extremal structure of subsets of $\mathbb{F}_p^n$ — but the *machinery is disjoint*. Slice rank and the polynomial method are not used in PFR; entropy, Plünnecke–Ruzsa, and Bogolyubov-style additive combinatorics are not used here. There is no load-bearing dependency in either direction.

Three cross-DAG edges (EG `cor:5` ↔ PFR `conjecture:1.1`; BCCGNSU `prop:4.8` ↔ PFR `thm:1.8`; Tyrrell `thm:1.2` ↔ PFR `thm:1.2`) are all typed `addresses_same_question` — thematic only. **This does not constitute a connected region** in the load-bearing sense the README uses for the harmonic-analysis chain (13 load-bearing cross-DAG edges) or for perfectoid-spaces ↔ langlands-local (14 load-bearing). Both `cap-set` and `pfr` remain standalone islands in that load-bearing sense, with documented thematic adjacency. The honest statement is: cap-set adds a thematic neighbor to PFR, not a third connected region.

## Open audit items

1. **Slice-rank reformulation attribution.** Naslund–Sawin and BCCGNSU both cite Tao's blog post (May 2016) as the slice-rank reformulation. We list Tao's blog in `manifest.json` `foundational` but it is not an arXiv paper and is not a node. Anyone reproducing this DAG should know the slice-rank reformulation predates the two May/June 2016 arXiv papers and originates with Tao.

2. **FunSearch reproducibility.** FunSearch's Nature paper is the only canonical record, and DeepMind has not released the discovered admissible sets in a form that's trivial to verify independently. The claim "$|A| = 512$ in $\mathbb{F}_3^8$" should be checkable from supplementary material; that verification is outside the scope of this DAG but worth noting as a separate audit item.

3. **No Lean blueprint.** Unlike `pfr` (Tao 2023), `prime-number-theorem` (Kontorovich PNT+), and `sphere-packing` (EPFL/Math, Inc.), the cap-set program has no live Lean blueprint as of this writing. Dahmen–Hölzl–Lewis (`1907.01449`) formalized the EG cap-set proof in Lean 3 in 2019 — that's a one-off formalization, not an ongoing blueprint anchor. Listed in Tyrrell's bibliography but not as a registry anchor.

4. **Granularity for BCCGNSU.** The paper has 43 detected math envs; this DAG extracts 20 of them. The skipped envs are mostly proof bodies and definitional setup that don't carry independent navigation value at the program level. A finer-grained extraction would inflate node count without adding load-bearing edges.

5. **Expert audit pass.** Like most DAGs in this registry, the cap-set DAG is at the "verified-faithful structurally" tier — every edge was read aloud as English ("A `improves` B" etc.) and checked for direction; every JSON file parses; KaTeX wrapping is consistent. A ~30-minute additive-combinatorics expert pass (`maynard-small-gaps`-style) would be the audited-flagship-tier next step.
