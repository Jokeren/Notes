##Source

ICML'15

http://dl.acm.org/citation.cfm?id=3045303

##Problem

Leverage the redundant and noisy nature of deep neural networks to design low precision computation models and relax constraints on certain hardwares.

##Motivation

Unlike traditional machine learning algorithms that require high precisions, deep neural networks are error resilient. Whereas hardwares are designed for high precisions, leading to unnecessary computations. By adopting fixed-point arithmethtics, we built low precision networks that are typically consume far less hardware resources and power than floating points.

##Solution

1. Fixed point representations

General fixed point representation contains two parameters [QI, QF], where QI and QF correspond to the integer and fraction parts respectively. And the bit width of integer plus the bit width of fraction part yields the number of bits to represent a number.

2. Rounding

The rounding operation is used to converting a floating number to a fixed-point number. Two common rounding methods are round-to-nearst and stoachastic rounding, of which the first is adopted in the inference phase, while the second is used in training period.

3. Multiply and accumulate operation

We first accumlate two given vectors *a* and *b*, calculating the integer part and fraction part respectively. Then, a convert operation is called to saturate the result to the limit set.