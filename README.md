# Eigenvector Continuation Demo

A simple Mathematica notebook demonstrating eigenvector continuation, following Frame, He, Ipsen, Lee, Lee, and Rrapaj, Eigenvector Continuation with Subspace Learning, Physical Review Letters 121, 032501, 2018.

Paper: https://link.aps.org/accepted/10.1103/PhysRevLett.121.032501

Video: coming soon

## What this notebook does

Builds a family of Hermitian matrices H(c) = H0 + c H1, computes the exact ground state across a range of c, then shows how a few sampled eigenvectors reproduce the entire curve using a small projected eigenvalue problem.

The notebook has four sections:

1. Setup, build H0 and H1
2. Exact diagonalization, direct calculation of the ground state across a range of c
3. Eigenvector continuation, build a small basis from sampled eigenvectors
4. Compare EC vs exact, overlay both curves

## Companion video

This notebook is a companion to a video on the Doctor No Does Science channel walking through the paper and the demo.

## License

MIT, see LICENSE file.