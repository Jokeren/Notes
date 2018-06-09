# Graspan: A Single-machine Disk-based Graph System for Interprocedural Static Analyses of Large-scale Systems Code

## Source

## Problem

Most of the existing static analyses developed for complicated systems are simple checkers that has false positive and negatives. Traditional approcaches do not scale well and are hard to parallelize.

## Motivation

Interprocedural analysis could be formulated as graph reachability problem and thus be solved by extending existed Big Data systems. For example, pointer/alias analysis can be described as a data flow among different variables in a program, linking via assignment, allocation, and dereference.

## Solution

This paper turns sophisticated code analysis into Big Data analytics and leverage novel data processing techniques to solve this traditional programming language problem.

Graspan represents transitive edges explicitly. Large burned of computation and memory cost won't be a challenge because big data systems have already developed approaches.

## Experiments

1. Graspan is effective of finding new bugs in large-scale systems.
2. Graspan finished processing Linux in a few hours with less than 6GB memory on the desktop with a much less powerful CPU.