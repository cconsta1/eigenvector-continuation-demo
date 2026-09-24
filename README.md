# Eigenvector Continuation Demo

Demos of eigenvector continuation (EC), following Frame, He, Ipsen, Lee, Lee, and Rrapaj, *Eigenvector Continuation with Subspace Learning*, Physical Review Letters 121, 032501 (2018).

Paper: https://link.aps.org/accepted/10.1103/PhysRevLett.121.032501

Videos:
- Part I, the idea behind EC: https://youtu.be/kZiLMA-5UMs
- Part II, the Bose-Hubbard benchmark: *link coming soon*

## The idea

For a Hamiltonian that depends on one parameter, H(c) = H0 + c H1, the ground state moves through a huge Hilbert space but stays close to a very low-dimensional subspace as c varies. EC takes exact ground states at a few sample values of c, projects H0 and H1 onto their span once, and then solves a tiny K x K generalized eigenvalue problem for any c. Unlike perturbation theory it is variational, so it has no radius of convergence and can extrapolate into regimes where a perturbative series diverges.

## Contents

### 1. `eigenvector_continuation_demo.nb` (Mathematica)

A minimal demo with random real symmetric matrices. It builds H(c) = H0 + c H1, computes the exact ground state across a range of c, and shows that a handful of sampled eigenvectors reproduce the whole curve.

### 2. `bose_hubbard_20260923.ipynb` (Python, Colab) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cconsta1/eigenvector-continuation-demo/blob/main/bose_hubbard_20260923.ipynb)

Reproduces the Bose-Hubbard benchmark from the paper (Fig. 1a and 1b): 4 bosons on a 4 x 4 x 4 periodic cubic lattice.

- Builds the full Fock basis of 766,480 states, indexed with the combinatorial number system so no lookup table is needed
- Applies the Hamiltonian matrix-free: only about 18 million of its roughly 587 billion entries are nonzero
- Computes exact ground states with Lanczos (scipy `eigsh`) on the GPU
- Runs EC from 3 sample points across the full range, and from 5 closely spaced points in a narrow window
- Computes Rayleigh-Schrodinger perturbation theory up to 6th order for comparison

Key results:
- First-order perturbation theory gives E(1) = 3/32 U, matching the analytic result N(N-1)/(2M)
- Perturbation theory at every order misses the sharp drop in energy at strong attraction (U/t below about -3.5)
- EC with 3 vectors out of 766,480 reproduces the exact curve across the whole range
- EC trained only on -2.0 < U/t < -1.6 extrapolates into the strongly bound regime once enough sample vectors are included

<!-- Optional: upload the two plots to a figures/ folder and uncomment
![Exact vs EC vs PT](figures/fig1a.png)
![EC from a narrow window](figures/fig1b.png)
-->

## Running the notebook

Open it in Colab with the badge above and select a GPU runtime (Runtime, Change runtime type, T4 GPU). Each exact Lanczos solve takes roughly 5 to 10 seconds on a T4, and the full notebook runs in a few minutes. It also runs on CPU, just more slowly.

Requirements: `numpy`, `scipy`, `torch`, `matplotlib` (all preinstalled on Colab).

## Companion videos

These notebooks accompany videos on the Doctor No Does Science YouTube channel walking through the paper and the demos.

## License

MIT, see the LICENSE file.
