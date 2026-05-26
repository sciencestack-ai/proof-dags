# Local Langlands after Fargues–Scholze

Fargues–Scholze (`2102.13459`) attach to every reductive $G/\mathbb{Q}_p$ a semisimple $L$-parameter $\varphi_\pi^{\mathrm{FS}}$, via the spectral action of $\mathrm{Perf}(Z^1(W_E,\widehat{G}))$ on the category $D_{\mathrm{lis}}(\mathrm{Bun}_G)$ of $\ell$-adic sheaves on the stack of $G$-bundles, with the dual group produced by geometric Satake on the $B_{\mathrm{dR}}^+$-affine Grassmannian. The map is unconditional but a priori abstract: not known to equal the classical correspondence, and its categorical refinement (Fargues' conjecture) is open. This graph is the work that pins it down.

**Compatibility** — Hamann (`2109.01210`): $\varphi^{\mathrm{FS}}$ agrees with Gan–Takeda for $\mathrm{GSp}_4$ and Gan–Tantono for the inner form $\mathrm{GU}_2(D)$; for supercuspidal parameters ($L/\mathbb{Q}_p$ unramified, $p>2$) the cohomology $R\Gamma_c(G,b,\mu)[\pi]$ is middle-degree concentrated. Route: basic uniformization of abelian-type Shimura varieties (Shen, Hansen) + a simple-trace-formula globalization, localized at a Hecke maximal ideal.

**Endoscopy** — Kazhdan–Varshavsky (`2503.00621`): elliptic FS $L$-packets satisfy $\mathcal{E}$-stability, giving an endoscopic decomposition $\Theta(G(F)) = \bigoplus_{\mathcal{E}} \Theta_{\mathcal{E}}(G(F))$; the key input ($K_0$ of compact FS sheaves $\cong$ the packet character space) is the FS spectral action. Extended to arbitrary coefficient fields by Galois descent.

**Categorical conjecture** — Fu (`2504.13869`) verifies the categorical equivalence for depth-zero regular supercuspidals via the spectral action on the Whittaker generator; Nguyen (`2505.10724`) decomposes $D_{\mathrm{lis}}^{[C_\varphi]}(\mathrm{Bun}_G)$ along $\mathrm{Irr}(S_\varphi)$, produces the predicted Hecke eigensheaves, and reads off torsion in $\mathrm{GL}_n$ Rapoport–Zink cohomology.

**Independence of $\ell$** — Scholze (`2501.07944`): a motivic refinement ($\mathcal{D}_{\mathrm{mot}}(\mathrm{Bun}_G)$, motivic geometric Satake $\mathrm{Sat}_G^I \simeq \mathrm{Rep}(\widehat{G}^I)$) proves $\varphi_\pi^{\mathrm{FS}}$ is independent of $\ell$ and $\iota$ — FS Conjecture I.9.5.

The root `2102.13459` is shared with the **perfectoid-spaces** graph, where it is the terminus of the diamonds / $p$-adic-Hodge machinery; here it is the root. Edges into it are recorded with the exact FS theorem each downstream result cites (e.g. Hamann's Thm 3.6 = FS I.9.6; Kazhdan–Varshavsky repeat FS IX.6.1 verbatim).
