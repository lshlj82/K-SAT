# Random K-SAT, one flip at a time

An interactive, single-file browser demo of the random *K*-satisfiability problem solved by the ASAT stochastic local search, following

> S. H. Lee, M. Ha, C. Jeon, and H. Jeong, "Finite-size scaling in random *K*-satisfiability problems," *Phys. Rev. E* **82**, 061109 (2010). [doi:10.1103/PhysRevE.82.061109](https://doi.org/10.1103/PhysRevE.82.061109)

Created by **Claude Opus 5.5** (Anthropic).

## What it does

**Watch one search.** Generates a random *K*-SAT instance with *N* variables and *M* = α*N* clauses, then runs ASAT: pick a random unsatisfied clause, try flipping one of its *K* variables, accept unless the number of unsatisfied clauses *M*<sub>u</sub> would increase, in which case accept with probability *p*. Time advances by 1/*M*<sub>u</sub> per trial flip, as in the paper. Every clause is drawn as a cell, and the density of unsatisfied clauses ρ<sub>u</sub>(*t*) is plotted on log–log axes with the paper's decay ρ<sub>u</sub> ∼ *t*<sup>−δ</sup> as a guide.

**Solve it by hand.** A small instance (4–40 variables) written out in full: every clause is listed with its literals, and each variable is a toggle. Click a variable, or any literal in a clause, to flip it; true literals light up and each clause shows whether it is unsatisfied, held by one literal, or held by two or more. Every variable also shows Δ, the change in the number of unsatisfied clauses if it were flipped, which is exactly what ASAT checks. You can let ASAT take single steps or run slowly to see which clause it picks and whether it accepts the flip, and filter the list to unsatisfied clauses only.

**Sweep α.** Runs many fresh instances across a range of α and several sizes *N*, plotting the solved fraction *P*<sub>s</sub> and the median solving time τ<sub>H</sub>. A toggle rescales the axis to ε*N*<sup>1/ν̄</sup>, with ε = (α − α<sub>c</sub>)/α<sub>c</sub>, to test the finite-size-scaling collapse.

Presets reproduce the three regimes of Table I in the paper:

| Problem | *p* | α<sub>c</sub> | *θ* | *z̄* | *δ* | ν̄ |
|---|---|---|---|---|---|---|
| 2-SAT (ASAT) | any > 0 | 1.002 | 1.0 | 1.0 | 1.0 | 3.0 |
| 3-SAT (RandomWalkSAT) | 1.00 | 2.6705 | 1.0 | 0.5 | 0.5 | 2.0 |
| 3-SAT (optimized ASAT) | 0.21 | 4.1855 | 1.0 | 1.0 | 1.0 | 3.0 |

## Caveats

Browser-sized systems (*N* in the hundreds to tens of thousands) are far smaller than those in the paper (up to 10<sup>6</sup> variables, *T*<sub>max</sub> = 10<sup>8</sup>). The paper notes serious finite-size effects below *N* ≈ 10<sup>3</sup>, so curve crossings in the sweep will drift from the quoted α<sub>c</sub>, most visibly for optimized ASAT. The rescaled solving-time plot omits the logarithmic corrections to scaling reported in the paper.

## Files

- `index.html` — the complete demo (HTML, CSS and JavaScript in one file)
- `README.md` — this file
