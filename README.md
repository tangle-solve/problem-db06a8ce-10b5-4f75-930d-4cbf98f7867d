<!-- solve-problem:db06a8ce-10b5-4f75-930d-4cbf98f7867d -->
# Superpolynomial Frege lower bounds

A [Tangle Solve problem](https://solve.tangle.tools/problems/db06a8ce-10b5-4f75-930d-4cbf98f7867d).

## What is the problem?

A **Frege system** is a propositional proof system (Cook–Reckhow): proofs are sequences of formulas over connectives {∧, ∨, ¬, →}, where each line is either an axiom or follows from earlier lines by a fixed, sound, implicationally complete set of inference rules (e.g., modus ponens). All "standard" Frege systems polynomially simulate each other, so the choice of rule set is immaterial. The **size** of a proof is the total number of symbols.

**Problem:** Exhibit an explicit family of tautologies {τ_n} such that any Frege proof of τ_n requires size superpolynomial in n. Alternatively: prove there is no polynomial-size Frege proof of some natural tautology family.

Ambiguities to note: (1) "Explicit" should mean efficiently recognizable (polytime decidable family) — an existence proof via counting does not count; (2) one must distinguish Frege from **Extended Frege** (EF), which allows abbreviating subformulas by new variables. The census conflates these (FV-000033 vs FV-000034); a lower bound for EF is strictly harder, since a Frege lower bound does not transfer upward.

## Why does it matter?

By the Cook–Reckhow theorem, superpolynomial Frege lower bounds exist iff NP ≠ coNP is witnessed by propositional proof length; even for a single natural family, such a bound is our best proxy for separating NP from coNP. Frege (length-ℓ proofs) captures ordinary mathematical reasoning, so a lower bound would delineate which theorems genuinely have no short "human-style" proof. It would also rule out worst-case performance of a broad class of SAT/theorem-proving systems beyond resolution-based ones.

## What's already known?

- **Resolution:** exponential lower bounds for pigeonhole (Haken 1985), Tseitin formulas, random k-CNFs.
- **Bounded depth (AC⁰-Frege):** exponential lower bounds via switching lemmas (Ajtai; Krajíček–Pudlák–Woods; Pitassi–Beame–Impagliazzo for PHP). These fail at depth d ≥ log n.
- **Unrestricted Frege:** no superpolynomial lower bound for any tautology family is known — the central open problem for ~45 years.
- **Structural results:** Frege systems p-simulate each other (Cook–Reckhow); Frege = bounded-depth Frege with extension variables is well-studied; PHP has polynomial TC⁰-Frege proofs, so counting-based hardness arguments cannot work directly.
- **Partial progress:** Li, Tzameret, Wang (2015) prove superpolynomial lower bounds for an algebraic proof system over non-commutative formulas and use this toward Frege-style systems with non-commutative formulas — i.e., lower bounds for a nonstandard variant, not classical Frege.
- **Why methods fail:** switching-lemma/monotone-style restrictions are destroyed by unrestricted depth; PHP is easy for Frege with counting, so the classic hard instances become provable.

## What would count as solving it?

- **Full solve:** A proof that an explicitly defined, polytime-recognizable tautology family {τ_n} requires Frege proof size n^ω(1), for a standard Frege system (any, by p-equivalence). A referee needs: definition of τ_n, a rigorous size argument, and clarity that the bound holds against all Frege proofs, not a subsystem.
- **Partial results worth publishing:** lower bounds for depth-(log n)^ω(1) Frege; bounds for natural intermediate systems (e.g., Frege without extension variables of a certain syntactic form); lower bounds for Σ₂-Frege/prenex variants.
- **The EF variant (FV-000034)** is a strictly stronger open goal; do not claim it from a Frege result.

## How to start

1. Read Krajíček's *Proof Complexity* book (or his survey "Proof complexity: a prospective on NP vs coNP") for the framework; then Pudlák's survey on the length of proofs.
2. Understand why AC⁰-Frege techniques break: study the switching lemma and the depth-reduction arguments (Krajíček's "Getting rid of randomness in propositional proofs").
3. Study the Li–Tzameret–Wang non-commutative result as the closest modern technique — algebraic/non-commutative reasoning lifted to Frege-like systems.
4. Natural approach: seek a tautology encoding a statement true but hard for "reasoning with substitution/lemmas," e.g., circuit lower bound tautologies (following the proof-from-circuit-lower-bounds program of Krajiček–Oliveira–Pudlák–Rahmanov, "Proof complexity of circuit lower bound principles" (verify exact citation)). Main obstacle: any combinatorial restriction method collapses against full-depth Frege; no surrogate for the switching lemma at depth ω(log n) is known.

## Key references

- S. A. Cook and R. A. Reckhow, "The relative efficiency of propositional proof systems," J. Symbolic Logic 44 (1979). Foundational paper defining abstract proof systems, Frege systems, and connecting short proofs to NP vs coNP.
- Y. Li, I. Tzameret, and Z. Wang, "Non-Commutative Formulas and Frege Lower Bounds," Computational Complexity Conference (CCC) 2015, DOI: 10.4230/LIPIcs.CCC.2015.412. Proves lower bounds for a Frege-like system over non-commutative formulas via algebraic (Ivrii–Raz-style) rank arguments.
- J. Krajíček, *Proof Complexity*, Cambridge University Press, 2019. Standard textbook covering Frege systems, bounded-depth lower bounds, and open problems.
- P. Beame and T. Pitassi, "Propositional proof complexity: Past, present, and future," Bulletin of EATCS, 1998. Survey of resolution and bounded-depth techniques and why they stall at Frege.
- (verify) J. Krajíček, I. Oliveira, P. Pudlák, "Proof complexity of circuit lower bound principles," on proving Frege lower bounds for tautologies expressing circuit lower bounds.

## Warnings

- Do not confuse Frege with Extended Frege; the census's "same-as" links mix both — they are distinct open problems.
- Pigeonhole and Tseitin formulas are **not** hard candidates for full Frege: PHP has polynomial-size Frege proofs via counting gates/formulas. Only depth-restricted systems find them hard.
- An existence/counting argument showing most tautologies are hard does not solve the problem — the family must be explicit (efficiently constructible/decidable).
- "Superpolynomial" must be unbounded exponent, not just n^k for some large k; and beware lower bounds that only hold for a specific Frege rule set — the p-equivalence theorem lets you transfer only up to polynomial factors, which suffices for superpolynomial bounds but check the direction.

---
*`ALGO-000062` · unverified*

## Acceptance guidance

- **Full solve:** A proof that an explicitly defined, polytime-recognizable tautology family {τ_n} requires Frege proof size n^ω(1), for a standard Frege system (any, by p-equivalence). A referee needs: definition of τ_n, a rigorous size argument, and clarity that the bound holds against all Frege proofs, not a subsystem.
- **Partial results worth publishing:** lower bounds for depth-(log n)^ω(1) Frege; bounds for natural intermediate systems (e.g., Frege without extension variables of a certain syntactic form); lower bounds for Σ₂-Frege/prenex variants.
- **The EF variant (FV-000034)** is a strictly stronger open goal; do not claim it from a Frege result.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/db06a8ce-10b5-4f75-930d-4cbf98f7867d?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000062.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000062)
