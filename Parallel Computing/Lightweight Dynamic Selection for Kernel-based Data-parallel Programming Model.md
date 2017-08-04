# DySel: Lightweight Dynamic Selection for Kernel-based Data-parallel Programming Model

## Source

ASPLOS '16 Proceedings of the Twenty-First International Conference on Architectural Support for Programming Languages and Operating Systems

http://dl.acm.org/citation.cfm?id=2872373

## Problem

Emerging devices are aimed to increasing performance and reducing power simultaneously, while two daunting factor challenge programmers: the interaction of input data and diverse devices and preparing high-performance codes across devices. Therefore, it is desirable to support portability over different architectures.

## Background

Popular approaches for optimizing including compiler and runtime solutions. 

We could apply a *model-based* approach at compile time and run time.

*Compile time optimzation* cannot consider all factors that influence the performance of algorithms, without knowing runtime variables such as data shape.

*Run time optimization* mitigate the problem met in compile optimization.

## Motivation

The model-based approach still have some blind spot. **DySel** remove the burden of generating the most optimal codes at compile time and choosing the best kernel at run time, by devising a *micro-profiling* method. Because kernel-based data-parallel programming model handle parts of data independently, we could take part of the input for profiling.

## Solution

**Productive Profiling**

In *Fully Productive Profiling*, each kernel contributes to part of the output. In *Hybrid-based Partial Productive Profiling*, only i_th kernel contributes to the i_th output; the best kernel is reponsible for remain outputs. Whereas according to the *Swaped-based Partial Productive Profiling*, the best kernel contributes to all the outputs.

**Workflow**

We have to modes: sync and async. In the sync mode, we choose the best kernel before handling the remain inputs. In the async mode, we choose the best kernel iteratively, in which the kernel chosen might be suboptimal before ending profliing all kernels.

## Experiments

The experiments illustrate that DySel is yield comparable performance as compile time optimized code, it is capable of choosing the best kernel when heuristic approaches not work, and it could select the best approach due to various data shape.

## My Questions&Notes

1. Batch based micro-profiling.

