# Foundations of the C++ Concurrency Memory Model

## Source

PLDI '08 Proceedings of the 29th ACM SIGPLAN Conference on Programming Language Design and Implementation 
https://dl.acm.org/citation.cfm?id=1375591

## Problem

Currently multi-threaded C or C++ programs combine a single-threaded programming language with a separate threads library, which is not entirely sound for the following reasons:

1. The informal specifications provided by current libraries are ambiguous.

2. Without precise semantics, it is hard to reason when a compiler transformation will violate these semantics.

3. There are many situations in which the overhead of preventing concurrent access to shared data is simply too high.

## Motivation

The data-race-free models can be adopted to achieve both the simple programmability of sequential consistency and the implementation flexibility of the relaxed models. The Java model does preclude some compiler optimizations and the full model is quite complex. Since C++ is not type safe, neither the restrictions nor the complexity of the full Java model appear justified for C++.

## Solution

1. Sequentially consistent atomics

If a program (on a given input) has a sequentially consistent execution with a (type 1) data race, then its behavior is undefined. Otherwise, the program (on the same input) behaves according to one if its sequentially consistent executions.

2. New try_lock definition

The C++0x specification is expected to allow trylock to “spuriously fail” in this manner. This effectively prevents a failed trylock from reliably revealing anything about the state of the lock (and hence the write of the lock operation has no means to convey any synchronization information).

3. Semantics for low-level atomics

There are some frequently used idioms for which sequential consistency is not required, such as an increment counter. Therefore, it is essential for C++ to support low-level atomics.

## My Questions&Notes

This paper perfectly answers my question why C/C++ does not incoporate Java's memory model.