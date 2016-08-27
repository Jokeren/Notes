#Implementing Strassen's Algorithm with BLIS

##Source

https://arxiv.org/abs/1605.01078

##Problem

Theoretically, Strassen's algorithm provides lower complexity compared with naive implementations. However, on current structures, two problems hinder its efficiency on small matrices. The first problem is that it induces additional data movement. A secondary concern has been that extra workspace are required.

##Motivation

We could adopt the BLIS framwork to develop faster Strassen's algorithm by changing data movement between different cache layers.

##Solution

**One-level Strassen**

M = α(X + Y)(V + W); C+= γ0M; D+= γ1M;

Figure 1 illustrates that *V + W* and *X + Y* are fused during the packing stage. Hence, finally submatrices could resue the kernel of tranditional gemm by incoporating formulas in Figure 2. In this way, it reduces additional data movement and avoids extra data movement.

Since two level Strassen is similar to the one-level solution, we do not review its implementation here.

##My Questions&Notes

This paper is published in SC'16.