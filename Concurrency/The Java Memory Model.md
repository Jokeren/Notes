# The Java Memory Model

## Source

POPL '05 Proceedings of the 32nd ACM SIGPLAN-SIGACT symposium on Principles of programming languages 
https://dl.acm.org/citation.cfm?id=1040336

## Problem

Before Java 5.0, the Java Memory Model is fully flawed.

## Motivation

A high-level memory model should makes it easier for the programmer to write subtle and complicated concurrent algorithms that do not use explicit synchronization. At the same time, it should be strong enough to respect the safety and security properties of Java and weak enough to allow standard compiler and hardware optimizations.

## Solution

1. Happens-before memory model, which defines a set of orders to form a total order in a correctly synchronized program.
2. Causality, which provide a well-behaved defition to gaurantee that values are not out-of-thin-air, even for incorrectly synchronized programs.

## My Questions&Notes

Why not C++ and C define well-behaved executions?