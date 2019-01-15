## Source

Communications of the ACM CACM Volume 54 Issue 5, May 2011

https://dl.acm.org/citation.cfm?id=1941507

## Problem

In the next decades, diminishing transistor-speed scaling and practical energy limits create new challenges for continued performance scaling. As a result, the frequency of operations will increase slowly, with energy the key limiter of performance.

## Motivation

1. Transistors

Putting it all together, in every technology generation transistor integration doubles, circuits are 40% faster, and system power consumption (with twice as many transistors) stays the same.

2. Core microarchitecture techniques

Advanced microarchitecture techniques includes pipeline, cache, super-scalar, speculative execution.

3. Cache

DRAMs are not inherently slow; rather, the memory organization is optimized for density and lower cost, making it slower. As energy became a concern, increasing cache size for performance has proven more energy efficient than additional core-microarchitecture techniques requiring energy-intensive logic. 
 
## Solution

1. Transistor

Transistor current leaking increases exponentially with reduction in the threshold voltage which is reduced to keep electric field constant and saving engergy. To keep leakage under control, the threshold voltage cannot be further reduced.

2. Power

Chip architects must limit frequency and number of cores to keep power within reasonable bounds. The dual core processor is designed by matching the perfect number of transistor for both power and cache.

3. Multi-core

Employing more little cores increase the over all performance.

4. Hardware customization

Customization includes fixed-function accelerators, programmable accelerators, and even dynamically customizable logic. Units hardwired to a particular data representation or computational algorithm can achieve magnitudes of speedup.
 
5. Moving data

Cores in a many-core system are typically connected through a network-on-a-chip to move data around the cores.

6. Voltage

Small cores benefit from reducing supply voltage.

7. Software

Extreme studies suggest that aggressive high-performance and extreme-energy-efficient systems may go further, eschewing the overhead of programmability features that software engineers have come to take for granted.

## My Questions&Notes