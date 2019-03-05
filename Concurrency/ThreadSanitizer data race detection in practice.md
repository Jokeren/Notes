# ThreadSanitizer data race detection in practice

## Source

WBIA '09 Proceedings of the Workshop on Binary Instrumentation and Applications 
https://dl.acm.org/citation.cfm?id=1791203

## Problem

Public avaiable data race detectors are either too slow or miss many races.

## Motivation

ThreadSanitizer uses a hybrid algorithm based on both happens-before and lockset to detect data races. It allows users use annotations to specify tricky syncrhonization patterns in user programs. For practical purposes, it has three modes correspond to three speed and accuracy levels.

## Solution

1. High running time overhead but acceptible memory overhead. For each memory location, it creates a unique id. Then for each it, it records memory access events and check if read and write events still isolate. In experiments, this method causes 3x-4x memory overhead and 20x runtime overhead.

2. Completeness. With fast-mode, segments are only captured within a small context, therefore missing many races. While in precise mode and default mode, the results are nearly precise.

3. Effectiveness. With ThreadSanitizer, 90% of the unit test cases in Google can pass, while with the previous open source software only 10% can pass. The tool has been utilized in famous softwares including chromium.

## My Questions&Notes