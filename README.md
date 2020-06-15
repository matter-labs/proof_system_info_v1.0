# Description

This repository contrains a short information about the extension of the PLONK proof system used in zkSync v1.0. A PDF file contrains an unrolled protocol and below we also give a short intuitive description for interested readers.

## Warning for Github viewers

Github's Markdown renderer does not support inline formulas used in this document, so you can open this file in your favorite Markdown viewer for better experience or open a PDF for the same short descriptions as the one made below.

## Extensions

Compared to the original PLONK [paper](https://eprint.iacr.org/2019/953.pdf) we use two extensions:
- State width is four instead of three in the original paper. This requires one extra permutation polynomial at the setup $\sigma_{3}(x)$ and does not change the copy-permutation argument that is generic over number of state (witness) polynomials.
- Main gate equation is now $q_a(x) a(x) + q_b(x) b(x) + q_c(x) d(x) + q_d(x) d(x) + q_m(x) a(x) b(x) + q_{const}(x) + q_{d_{next}} d(x\omega) = 0$ where $a(x),..,d(x)$ are state polynomials (witnesses) and $\omega$ is a generator of the multiplicative domain $D$, such that for a circuit size $n$ one has $|D| = n+1$. Such gate equation allows one to work more efficiently with long linear combination by including up to three terms per gate compared to the original paper where it would be one term per gate ($q_{d_{next}} d(x\omega)$ term allows one to "peek" into the next row for efficient placement of terms).

A strict original source of this extension is unknown to us, but most likely it was first mentioned by Zachary Williamson in one of the Telegram chats along with his work on custom gates in PLONK 

We also invite all interested readers to get the latest information about extensions of a PLONK proof system such as custom gates and lookup table in [PLONK Cafe](https://www.plonk.cafe/)