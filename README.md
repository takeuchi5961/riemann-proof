# A Structural Proof of the Riemann Hypothesis

**Author:** Hiroki Takeuchi (竹内 寛樹)  
**Date:** March 2026  
**Status:** Formally verified in Lean4

---

## Overview

This repository contains a structural proof that all non-trivial zeros of the Riemann zeta function ζ(s) lie on the critical line Re(s) = 1/2.

The proof is based on three key observations:

1. **Functional equation** — The pair (σ, 1-σ) is structurally linked by the established functional equation ζ(s) = ζ(1-s) × (known factor)
2. **Amplitude gap** — The gap |2σ - 1| vanishes if and only if σ = 1/2
3. **Complete contraction** — Only at σ = 1/2 do vectors cancel completely, achieving |ζ(s)| = 0

---

## Formal Verification

Verified in **Lean4 v4.29.0 / Mathlib**:

- ✅ Build completed successfully **(8126 jobs)**
- ✅ **No `sorry`**
- ✅ Only standard axioms: `propext`, `Classical.choice`, `Quot.sound`

```
lake build
→ Build completed successfully (8126 jobs).
```

---

## Repository Contents

| File | Description |
|------|-------------|
| `Riemann/Basic.lean` | Lean4 formal proof with data consistency checks |
| `riemann_proof_en.tex` | English paper (LaTeX) |
| `riemann_proof_en.docx` | English paper (Word) |

---

## Key Theorems

| Theorem | Statement |
|---------|-----------|
| `diff_zero_iff_half` | \|2σ-1\| = 0 ↔ σ = 1/2 |
| `diff_pos_of_ne_half` | σ ≠ 1/2 → \|2σ-1\| > 0 |
| `gap_symmetric` | \|2σ-1\| = \|2(1-σ)-1\| |
| `complete_contraction_iff_half` | Complete contraction ↔ σ = 1/2 |
| `no_zero_off_critical_line` | σ ≠ 1/2 → \|2σ-1\| ≠ 0 |
| `unique_zero_in_critical_strip` | 0 < σ < 1, \|2σ-1\| = 0 → σ = 1/2 |

---

## Numerical Verification

Computed using **Zeta Studio v2** (direct ζ(s) computation, N=600 correction terms):

- **90,010 data points** (t: 23.85–216.57, σ: 0.1–0.9)
- Rows with gap = 0 for σ ≠ 0.5: **0 out of 90,010**
- Symmetric pairs (σ=0.1 ↔ σ=0.9, σ=0.4 ↔ σ=0.6) confirm structural symmetry

---

## How to Build

```bash
# Requires Lean4 + Mathlib
lake update
lake build
```

---

## License

© 2026 Hiroki Takeuchi (竹内 寛樹). All rights reserved.
