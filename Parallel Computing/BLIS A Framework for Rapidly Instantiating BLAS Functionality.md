# BLIS: A Framework for Rapidly Instantiating BLAS Functionality

## Source

ACM Transactions on Mathematical Software (TOMS)

http://dl.acm.org/citation.cfm?id=2764454

## Problem

Tranditional blas implementations have many shortcomings:

- General striding

- Incomplete support of complex domain operations

- Opaque API

- Few portable framework

## Innovation

All computations within level-2 and level-3 operations can be expressed and optimized in terms of simple kernels that written in assembly codes. High-level loop controls codes follow C99 so that it could be resued accross various platforms.

## Solutions

level1-m: it provides level1 operations like *AXPYM* on matrices.

level1-f: it provides fused kernels to be exported for high performance.

level-2 (matrix-vector) and level-3 (matrix-matrix) operations depends on optimized kernels.

For instance, gemm consists three levels of blocking. First, it creates *rank-k* subproblems by iteration through a <m_c, k> matrix along the <m, k> panel and a <k, n_c> matrix along the <k, n> panel. Second, in the *macro-level* that fits in cache, data are packed into contiguous memory. The final level extracts <m_c, k> matrix and <k, n_r> matrix and load into register level. Only the macro kernel is implemented by assembly codes.

## My Questions&Notes

1. The BLIS framework instanitiate operations that are comparable with vendor products, but it lacks GPU implementations.

2. Multithread is introduced by another paper: *The BLIS Framework: Experiments in Portability*.