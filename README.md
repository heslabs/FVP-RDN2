# FVP-RDN2-SVE

---
## Matrix Multiplication Optimization
* Reference: https://github.com/arm-university/AI-on-Arm/blob/main/lab1.ipynb

This lab begins with an exploration of matrix multiplication operators, the core computational components of AI workloads. Understanding and optimizing these operations can significantly enhance the inference performance of generative AI models. In this section, we will implement and compare three matrix multiplication approaches. While they are mathematically identical, their differing implementations result in vastly different performance outcomes. We will implement:

* Naive Kernel (src/c/kernels/naive.c)
  * A simple, baseline implementation of matrix multiplication to provide a reference point for performance.
* FP32 Neon Kernel (src/c/kernels/fp32_neon.c)
  * A matrix multiplication optimized for single-precision floating-point operations using Arm Neon SIMD instructions to leverage vectorized computation.
* INT8 Neon Kernel (src/c/kernels/int8_neon.c)
  * An integer matrix multiplication tailored for 8-bit operations, utilizing Neon SIMD to maximize throughput for lower-precision workloads.

By analyzing these implementations, you will gain insight into the performance trade-offs and benefits of hardware-specific optimizations that Arm can offer.

---
## Benchmarking

Let's now compute the latency of results of these three operators across different matrix sizes to empirically measure their differences. We can set the matrix sizes used in the benchmark by writing them out to src/c/sizes.c as seen below. Feel free to adapt the sizes yourself to see how it can effect latency, Bear in mind, however, that large matrix multiplications are compute intensive operations!

* Note This code is tested on Raspberry Pi 5 (Cortex-A76) with matmul size of 1024 can take upto 45s.
* Note This code is tested on FVP-RD-N2 with matmul size of 1024 can take upto few minutes.

---
## Rsults 



---
### Resource
* Optimizing Generative AI on Arm Processors
  * https://github.com/arm-university/AI-on-Arm
