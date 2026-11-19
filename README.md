# Formalizing the Convergence of Newton's Method for Square Roots

**CMU 21-321: Interactive Theorem Proving — Fall 2026**

## Project Overview

This project formalizes the convergence of Newton's method for computing square roots using Lean 4 and Mathlib.

For a positive real number \(a\) and an initial guess \(x_0>0\), Newton's method generates the sequence

\[
x_{n+1}=\frac{1}{2}\left(x_n+\frac{a}{x_n}\right).
\]

The main objective is to formally prove that this sequence converges to the positive square root of \(a\), regardless of the choice of positive initial value.

## Main Theorem

For any \(a>0\) and \(x_0>0\), the Newton iteration satisfies

\[
\lim_{n\to\infty}x_n=\sqrt{a}.
\]

The main theorem is formalized in Lean as `newton_converges`.

## Proof Strategy

The formalization builds toward the main theorem through several supporting results:

- **Positivity:** Every iterate remains strictly positive.
- **Lower bound:** After the first iteration, all subsequent iterates are at least \(\sqrt a\).
- **Monotonicity:** The sequence is nonincreasing after the first iteration.
- **Error identity:** The iteration satisfies

  \[
  x_{n+1}-\sqrt a
  =\frac{(x_n-\sqrt a)^2}{2x_n}.
  \]

- **Geometric error bound:** For every \(n\geq0\),

  \[
  0\leq x_{n+1}-\sqrt a
  \leq 2^{-n}(x_1-\sqrt a).
  \]

The geometric error bound approaches zero, allowing us to establish convergence using the squeeze theorem.

## Lean Formalization

The main Lean development is located in:

`ProjectTemplate/Basic.lean`

The file contains the Newton iteration definitions, supporting lemmas, and the main convergence theorem.

The project uses Lean 4 and Mathlib.

## Building the Project

From the repository root, run:

```bash
lake exe cache get
lake build
```

A successful build verifies that the Lean source files compile.

