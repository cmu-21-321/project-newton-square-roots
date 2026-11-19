# Newton's Method for Square Roots


Formal verification of the global convergence of Newton's method using **Lean 4** and **Mathlib**.

---

## Overview

Newton's method is a classical iterative algorithm for finding roots of nonlinear equations. This project focuses on the square root problem and formally proves that the iteration converges to the positive square root from **any positive initial value**.

Given $a > 0$ and $x_0 > 0$, define

$$
\boxed{x_{n+1}=\frac{1}{2}\left(x_n+\frac{a}{x_n}\right)}
$$

Our goal is to establish its convergence through a sequence of formally verified mathematical lemmas.

## Main Theorem

For every $a > 0$ and $x_0 > 0$, the Newton iteration converges to $\sqrt{a}$:

$$
\boxed{\lim_{n\to\infty}x_n=\sqrt{a}}
$$

This result is formalized in Lean as **`newton_converges`**.

## Proof Strategy

The proof is organized around the following mathematical properties.

| Property | Mathematical Result |
|---|---|
| Positivity | $x_n > 0$ for all $n \geq 0$ |
| Lower Bound | $x_n \geq \sqrt{a}$ for $n \geq 1$ |
| Monotonicity | $x_{n+1} \leq x_n$ for $n \geq 1$ |
| Error Identity | Exact expression for the iteration error |
| Geometric Error Bound | Error decreases at least geometrically |

### Key Error Identity

A central observation is

$$
x_{n+1}-\sqrt{a}
=\frac{(x_n-\sqrt{a})^2}{2x_n}.
$$

Since $x_n\geq\sqrt{a}$ for $n\geq1$, we obtain

$$
0\leq x_{n+1}-\sqrt{a}
\leq\frac12(x_n-\sqrt{a}).
$$

By induction, this gives the explicit error bound

$$
\boxed{
0\leq x_{n+1}-\sqrt{a}
\leq\frac{x_1-\sqrt{a}}{2^n}
}
$$

As $n\to\infty$, the upper bound approaches zero. The Squeeze Theorem then establishes the main convergence result.

## Lean Formalization

The formal proof is implemented in:

`ProjectTemplate/Basic.lean`

The development includes definitions of the Newton iteration, supporting lemmas, error estimates, and the main convergence theorem.

### Build Instructions

Run the following commands from the repository root:

```bash
lake exe cache get
lake build
```

A successful build confirms that the Lean code compiles under the project's configured environment.


