# Abelian Sieve v 2.0

## Speculative Index-Calculus Research for Elliptic Curve Discrete Logarithms

> A theoretical and experimental framework exploring whether ECDLP instances can be lifted into Jacobians of specially constructed high-genus curves in order to recover index-calculus-like structure.

---

# ⚠️ IMPORTANT DISCLAIMER

This repository does **NOT** break secp256k1.

This project:
- is speculative research,
- contains unproven assumptions,
- explores toy-model constructions,
- and should not be interpreted as a practical cryptanalytic attack.

There is currently **no known practical subexponential algorithm** for general ECDLP on standard curves such as:
- secp256k1,
- NIST P-256,
- Curve25519.

Modern elliptic curve cryptography remains secure.

---

# Motivation

Classical index calculus methods achieve subexponential complexity for:
- integer factorization,
- finite-field discrete logarithms,
- number field sieve variants.

However, elliptic curve groups lack the natural factor-base structure that makes these methods possible.

The central research question of this project is:

> Can one artificially construct a usable factor-base structure for elliptic curves by lifting ECDLP into Jacobians of carefully engineered high-genus covering curves?

---

# Core Idea

Instead of attacking an elliptic curve directly:

```math
E / \mathbb{F}_q
```

the framework investigates lifting ECDLP into Jacobians:

```math
\mathrm{Jac}(C_g)
```

of specially constructed curves:

```math
C_g
```

whose Jacobians contain the original elliptic curve as an isogeny factor.

The proposed mechanism relies on:
- controlled isogeny constructions,
- high-genus covers,
- divisor smoothness,
- p-adic lifting,
- sparse relation collection,
- and Jacobian arithmetic.

---

# Abelian Sieve v2.0

Version 2.0 significantly revises the original proposal and addresses several major theoretical objections.

The framework no longer assumes:
- arbitrary universal coverings,
- unrestricted smoothness heuristics,
- or efficient generic Jacobian decompositions.

Instead, the construction is restricted to specialized curve families with explicit algebraic structure.

---

# Mathematical Architecture

## 1. Isogeny-Guided Lifting

Rather than constructing coverings for arbitrary elliptic curves, the framework investigates curves related through small-degree isogenies:

```math
\phi : E \rightarrow E'
```

using modular curves:

```math
X_0(\ell)
```

for small primes:

```math
\ell
```

The high-genus covering curves are chosen such that:

```math
\mathrm{Jac}(C_g)
\sim
E \times A
```

where:
- `A` is an auxiliary abelian variety,
- and the projection onto `E` is explicitly computable.

---

## 2. Controlled High-Genus Covers

The framework studies special curve families such as:

```math
y^\ell = f(x)
```

including:
- cyclic covers,
- Artin–Schreier constructions,
- superelliptic curves,
- and curves with large automorphism groups.

These families admit:
- structured Jacobian arithmetic,
- explicit divisor representations,
- and potentially smoother decomposition behavior.

---

## 3. Ascending Smoothness

The key heuristic is the concept of **ascending smoothness**.

Instead of decomposing directly in the elliptic curve group, divisors are:
1. lifted into the Jacobian,
2. deformed through kernel walks,
3. transformed into equivalent divisors,
4. and tested for smooth decomposition over a factor base.

The factor base consists of small-degree divisors:

```math
(P) - (\infty)
```

with bounded norm and bounded field degree.

---

## 4. p-adic Divisor Deformation

The framework investigates whether divisors can be:
- lifted into characteristic zero,
- decomposed via polynomial factorization,
- and reduced back into finite characteristic.

This idea is inspired by:
- number field sieve techniques,
- p-adic lifting methods,
- and divisor arithmetic on algebraic curves.

---

## 5. Jacobian Arithmetic

The project explores arithmetic using:
- Mumford representations,
- Cantor reduction,
- Kummer surfaces,
- theta-function methods,
- and structured superelliptic Jacobians.

Target complexity for divisor arithmetic:

```math
O(g^2)
```

field operations for carefully chosen curve families.

---

# Complexity Goal

The speculative target complexity is:

```math
L_q(1/3,c)
=
\exp\left(
(c+o(1))
(\log q)^{1/3}
(\log\log q)^{2/3}
\right)
```

analogous to Number Field Sieve behavior.

This complexity claim remains entirely hypothetical.

---

# Why secp256k1 Is NOT Broken

Even under the assumptions of Abelian Sieve v2.0:

- constructing the required isogenies remains difficult,
- extension-field lifting introduces major overhead,
- divisor smoothness is unproven at scale,
- Jacobian arithmetic constants are enormous,
- and no practical attack is known.

For secp256k1 specifically:
- no efficient covering construction is known,
- no usable factor base is known,
- and the proposed framework does not yield a practical solver.

---

# Repository Goals

This repository exists to:
- formalize speculative ideas,
- build toy-model implementations,
- test divisor smoothness experimentally,
- explore Jacobian arithmetic,
- and invite mathematical criticism.

---

# Repository Structure

```text
/papers
    speculative papers and mathematical notes

/toy-models
    small-field demonstrations

/jacobians
    Jacobian arithmetic experiments

/divisors
    divisor representations and reductions

/smoothness
    smoothness heuristics and experiments

/linalg
    sparse linear algebra prototypes

/cpp
    experimental C++ implementations

/sage
    SageMath verification scripts

/notes
    discussions and open problems
```

---

# Demonstration Implementation

The repository includes toy-scale examples over very small finite fields.

Example:
- elliptic curves over `F_101`,
- genus-2 lifting constructions,
- divisor arithmetic via Mumford representation,
- Cantor reduction,
- smooth divisor decomposition,
- sparse relation collection.

These examples are intended purely for:
- educational purposes,
- experimental validation,
- and mathematical exploration.

They do NOT scale to cryptographically relevant curves.

---

# Related Research Areas

- Index Calculus
- Number Field Sieve
- Function Field Sieve
- Weil Descent
- Isogeny Theory
- Jacobian Arithmetic
- Semaev Summation Polynomials
- Algebraic Geometry in Cryptography
- p-adic Methods
- Kummer Surfaces

---

# Research Philosophy

This project intentionally embraces speculative exploration.

The goal is not sensationalism.

Negative results, impossibility arguments, failed heuristics, and counterexamples are considered valuable outcomes.

---

# Contributing

Mathematical criticism and experimental validation are highly encouraged.

Especially valuable:
- proofs of impossibility,
- counterexamples,
- smoothness estimates,
- Jacobian decomposition analysis,
- complexity critiques,
- toy-model implementations,
- and algebraic geometry insights.

---

# License

MIT License

---

# Final Note

At present there is no evidence that Abelian Sieve v2.0 leads to a practical attack on modern elliptic curve cryptography.

This repository should be viewed as:
- a speculative research sandbox,
- a mathematical exploration,
- and a study of whether index-calculus-style structures can exist for elliptic curves under highly constrained conditions.
