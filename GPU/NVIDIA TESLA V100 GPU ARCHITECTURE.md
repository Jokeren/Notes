##Source

NVIDIA

http://www.nvidia.com/object/volta-architecture-whitepaper.html

##Features

1. SM

- Tensor cores: eight per SM and two per partition. Each tensor core performs 64 floating-point operation in a cycle, yielding 120 TFLOPS at maximum.

- L0 instruction cache: provide high efficient instruction buffers.

- Unified shared memory and L1 resources: 96KB per SM. Texture units also use L1 cache. It narrows the gap between explict memory and implicit memory.

2. Independent thread scheduling

- Volta maintains per-thread scheduling resources.

- `__syncwarp()` primitive to force reconvergence.

3. MPS

- Provides a hardware-level module that enables MPC clients to submit work to the queue within a GPU.

4. Cooperative groups

- Provides an abstraction by which developers could write flexible codes.