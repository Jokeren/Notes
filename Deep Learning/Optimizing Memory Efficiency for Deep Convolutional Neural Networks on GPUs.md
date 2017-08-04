# Optimizing Memory Efficiency for Deep Convolutional Neural Networks on GPUs

## Source

International Conference on High Performance Computing, Networking, Storage, and Analysis (SC’16), 2016

http://hgpu.org/?p=16486

## Problem

Due to the intricuate data layout of CNNs, memory efficiency has a large impact on the performance of pooling layer and convolution layer.

## Motivation
GPU performance depends on particular data layout, as it uses thread grid and block to instantiate a kernel call. For convolution networks, there are 24 ways of day layout. A single data layout achieves suboptimal performance in a CNN, for different layers prefer different layouts. 

Further, previous works also overlook off-chip memory accesses. For instance, In the softmax layer, calling multiple kernels might incur redundant memory accesses.

## Solution

1. Data layout

For matrix multiplication and direct convolution, we compare cuda-convnet with cudnn. When N is large and C is small, cuda-convnet with *CHWN* is better than *NCHW*. *CHWN* is better because it uses *N* for better **memory coalescing** and **register reuse**. Additionally, *CHWN* is similar to *HWCN*. 

FFT algorithms have the similar performance feature as matrix multiplication, and Pooling layer prefers CHWN.

2. Off-chip memory accesses

2.1 Pooling Layer

Poor memory bandwidth usage is caused by *NCHW* layout's strided memory accesses and redundant memory accesses. The solution is using *CHWN* layout and increase the output elements per thread.

2.2 Softmax Layer

First, in Caffe, the softmax layer is computed by different kernels. Second, the parallelism is not enough to hide the loading latency. Therefore, we could fuse all kernels together and increase the parallelism by injecting threads to calculate each element.

## My Questions&Notes

1. Typos

Figure 7, the first Transformation routine. The comment "from CHWN to NHWC" should be "from CHWN to NCHW".

Section IV, Part A. "For the rest layers performing better with cuDNN, the values of **N** are either 64 or 32. " should be "For the rest layers performing better with cuDNN, the values of **C** are either 64 or 32. "

2. Why do not test NHWC layout?

3. Why not use matrix transportation to transform CHWN to NCHW.

4. Implicit or explicit GEMM of Cudnn?

5. Could the data layout adaptive strategy apply to other types of neural networks?

6. The comparision between cudnn and cuda-convnet might be unfair because cuda-convnet2 is written in C, but cudnn might be highly optimized by assembly codes.

