# FVP-RDN2-SVE

---
## Matrix Multiplication Optimization
* Reference: https://github.com/arm-university/AI-on-Arm/blob/main/lab1.ipynb

This lab begins with an exploration of matrix multiplication operators, the core computational components of AI workloads. Understanding and optimizing these operations can significantly enhance the inference performance of generative AI models. In this section, we will implement and compare three matrix multiplication approaches. While they are mathematically identical, their differing implementations result in vastly different performance outcomes. We will implement:

* **Naive Kernel** (src/c/kernels/naive.c)
  * A simple, baseline implementation of matrix multiplication to provide a reference point for performance.
* **FP32 Neon Kernel** (src/c/kernels/fp32_neon.c)
  * A matrix multiplication optimized for single-precision floating-point operations using Arm Neon SIMD instructions to leverage vectorized computation.
* **INT8 Neon Kernel** (src/c/kernels/int8_neon.c)
  * An integer matrix multiplication tailored for 8-bit operations, utilizing Neon SIMD to maximize throughput for lower-precision workloads.

By analyzing these implementations, you will gain insight into the performance trade-offs and benefits of hardware-specific optimizations that Arm can offer.

---
## Benchmarking

Let's now compute the latency of results of these three operators across different matrix sizes to empirically measure their differences. We can set the matrix sizes used in the benchmark by writing them out to src/c/sizes.c as seen below. Feel free to adapt the sizes yourself to see how it can effect latency, Bear in mind, however, that large matrix multiplications are compute intensive operations!

* Note This code is tested on Raspberry Pi 5 (Cortex-A76) with matmul size of 1024 can take upto 45s.
* Note This code is tested on FVP-RD-N2 with matmul size of 1024 can take upto few minutes.

---
## Results 

---
#### RDN2 (Neoverse-N2)

```
(zenv) root@rdn2:~/labs/AI-on-Arm# python3 ./bench_table.py
   mSize  Latency(s)  Latency(s)  Latency(s)  Latency(s)  Latency(s)  Latency(s)
0     32    0.000040         1.0    0.000003        13.0    0.000002        20.0
1     64    0.000317         1.0    0.000019        17.0    0.000010        32.0
2    128    0.002520         1.0    0.000149        17.0    0.000077        33.0
3    256    0.020093         1.0    0.001161        17.0    0.000591        34.0
4    512    0.160490         1.0    0.009167        18.0    0.004624        35.0
```

#### RPI5 (Cortex-A76)

```
(aivenv) demo@rx66h:~/AI-on-Arm$ python3 ./bench_table.py
   mSize  Latency(s)  Latency(s)  Latency(s)  Latency(s)  Latency(s)  Latency(s)
0     32    0.000189         1.0    0.000008        24.0    0.000005        38.0
1     64    0.001487         1.0    0.000057        26.0    0.000034        44.0
2    128    0.008819         1.0    0.000464        19.0    0.000247        36.0
3    256    0.083851         1.0    0.007986        10.0    0.001872        45.0
4    512    0.869829         1.0    0.145931         6.0    0.030637        28.0
```


---
### Demo Videos

* RDN2 FVP: Booting Ubuntu OS and running NEON benchmarks
  * https://youtu.be/qYT7es_vD9Y
* RDN2 FVP: Booting Ubuntu OS, Console only 
  * https://youtu.be/0vj9nLcrCCo



---
### Resource
* Optimizing Generative AI on Arm Processors
  * https://github.com/arm-university/AI-on-Arm
