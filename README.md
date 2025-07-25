# Probabilistic Graphical Models and HHMMs – Optimal Transport Perspective

This repository contains a LaTeX-based scientific paper exploring **probabilistic graphical models**, with a particular focus on **Hierarchical Hidden Markov Models (HHMMs)** and their connection to **optimal transport theory**.

## Overview

This paper presents significant advancements in **Martingale Optimal Transport (MOT)** by incorporating additional constraints. The core innovation is an extension of the Sinkhorn algorithm that handles these constraints via geometric projections, improving computational efficiency and broadening applications in finance, physics, and operations research. Key contributions include:

- **Extended Sinkhorn Algorithm**:
  - Modifies the classical algorithm to include constraints as additional projections using non-commutative analysis.
  - Introduces **e-projections** (divergence minimization w.r.t. the first dimension) and **m-projections** (loss minimization w.r.t. the second dimension).
  - Ensures monotonic convergence while satisfying marginal and martingality constraints.

- **Computational Enhancements**:
  - Merges **BFGS optimization** with Bregman projections to handle non-linear constraints (e.g., Asian option prices).
  - Uses Kullback-Leibler (KL) divergence for efficient iterative proportional fitting.

- **Theoretical Framework**:
  - Extends Kantorovich duality and KKT conditions for constrained MOT.
  - Leverages information geometry to unify e/m-projections and Bregman divergences.

---

## Applications

### Finance
- **Exotic Option Pricing**:  
  MOT with volatility smile constraints prices **Equinox options** (a "light exotic" autocall structure) more accurately than traditional models. The payoff:  
  \[
  P = G \left( \mathbb{E}[1_{S_1 \geq B}] + \mathbb{E}[1_{S_1 \leq B \& S_2 \geq K}(S_2 - K)] 
ight)
  \]
  - \(S_1, S_2\): Asset prices at observation dates  
  - \(B\): Barrier, \(K\): Strike  

- **Deep Hedging**:  
  Closed-form hedge ratios for Equinox enable realistic Monte Carlo simulations of hedging costs under transaction costs and regulatory constraints.

### Gravitation & Quantum Physics
- **Quantum Gravity**:  
  Appendix sections (10, C.16–C.18) propose using **Multi-Marginal Optimal Transport (MMOT)** to model quantum gravity effects:
  - **Modified Newtonian Potential**: Bayesian MMOT frameworks may describe mass distributions in spacetime.
  - **Renormalization**: OT divergences (e.g., KL) could address UV divergences in quantum field theories.

- **Schrödinger Bridge Matching**:  
  Connects OT to quantum dynamics via entropy-regularized paths.

---

## Key Algorithms

- **Extended Sinkhorn for MOT**:  
  Iteratively updates transport plan \(\pi(x,y)\) using:  
  \[
  \pi(x,y) = \exp\left(rac{-C(x,y) + \phi(x) + \psi(y) + 	heta(x)(y-x) + \delta g(x,y)}{\epsilon} - 1
ight)
  \]  
  Constraints (e.g., martingality \(\int y \pi(x,y) dy = x\mu(x)\)) are linearized for BFGS integration.

- **BFGS-enhanced Projections**:  
  Combines quasi-Newton BFGS with Sinkhorn to enforce constraints like Asian option prices:  
  \[
  \min_{\delta} \int\int g(y,x) \pi(x,y)  dx  dy = p_{	ext{market}}
  \]

- **Iterative Proportional Fitting (IPF)**:  
  Alternating e-projections to fit marginals via KL minimization:  
  \[
  Q^{(n+1)} = rg\min_{Q \in \Pi(\mu_0,\cdot)} D_{KL}[Q : Q^{(n)}]
  \]

---

## Future Research

- **Multi-Marginal MOT (MMOT)**:  
  Scaling to 100–1000 maturities for autocallable pricing using sparsity/Markovianity.
- **Quantum Gravity via MMOT**:  
  Bayesian approaches to model quantum effects in gravity (Section 10.4).
- **Generative Modeling**:  
  Links to diffusion models and optimal control (Section 11.8).

---

## Prerequisites

To understand the paper, you should be familiar with:

- Bayesian networks and conditional independence
- Hidden Markov Models and EM algorithms
- Optimal Transport and Entropy Regularization

## License

© 2025 Olivier Croissant. All rights reserved.

---

For questions, contact: croissant.olivier@wanadoo.fr
