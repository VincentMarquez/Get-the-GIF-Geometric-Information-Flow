In the WORKS



---

# Geometric Information Flow (GIF) — System Hierarchy

## Overview

GIF explores **adaptive computation in sequential models** by maintaining multiple internal states and selectively applying more expensive operations when needed.

Instead of one hidden state and one update rule, the system tracks several interacting components.

---

## Primary Components (Level 1)

These are **explicitly implemented, stateful, and required**.
Removing any one of them changes system behavior.

| Component               | State               | What it does                                               | Why it exists                             |
| ----------------------- | ------------------- | ---------------------------------------------------------- | ----------------------------------------- |
| **Temporal Processing** | ( h_{\ell,t} )      | Runs multiple sequence processors at different time scales | One timescale is often insufficient       |
| **Spectral Memory**     | ( \Psi_t )          | Tracks a low-rank summary of recent history                | Store structure without storing sequences |
| **Conditional Solver**  | ( \Delta z_t )      | Corrects latent state when predictions degrade             | Fix state instead of adding depth         |
| **Control Logic**       | ( m_t )             | Decides *when* to trigger expensive steps                  | Prevent constant or noisy corrections     |
| **Energy Tracking**     | ( E_t )             | Combines diagnostic signals into one trigger value         | Stable, normalized decision signal        |
| **Fusion Weights**      | ( \alpha_{\ell,t} ) | Combines parallel lanes safely                             | Avoid dominance by unstable lanes         |

---

## Secondary Components (Derived)

These are **not separate modules**, but arise naturally from Level-1 behavior.

| Component                 | What it represents                   | Where it shows up                  |
| ------------------------- | ------------------------------------ | ---------------------------------- |
| **Information Structure** | Gradient / state uncertainty         | Conditioning checks, entropy, rank |
| **Compute Allocation**    | Where time and cost are spent        | Sparse solver activation           |
| **Stability Regions**     | When the system recovers vs diverges | Dwell time, hysteresis behavior    |

---

## How This Differs From Typical Models

| Typical Model              | GIF                         |
| -------------------------- | --------------------------- |
| 1 hidden state             | Multiple interacting states |
| Fixed update rule          | Conditional updates         |
| Fixed compute per step     | Adaptive compute            |
| Optimization outside model | Optimization inside model   |
| No internal diagnostics    | Explicit diagnostics        |

---

## What This Repo Is For

* Experimenting with **conditional correction**
* Studying **when extra computation actually helps**
* Exploring **control-style logic inside neural models**

This is **research code**, not a finished system.

---

## Status

* Components work independently
* Combined behavior is still being explored
* Benchmarks are ongoing



Attribution
If you use this vision, methodology, or code in your work, please:

Provide clear attribution to Vincent Marquez in your paper's acknowledgments or methods section
Reference this repository when describing derived work
Maintain this notice in any derivative works or forks
Thank you for respecting the effort that went into developing this work.
