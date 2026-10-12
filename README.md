
Parallel Quicksort using OpenMP 🚀

A high-performance computing repository evaluating the metrics, architectural differences, and execution bottlenecks between Serial vs. Parallel Quicksort structures.

📌 Project Overview

This repository features an implementation of a task-based Parallel Quicksort algorithm using the OpenMP framework in C++. The testing framework evaluates how multi-threaded recursive tasks balance across processor cores when handling massive, randomized datasets.

💻 Student Profile

• Name: Rao-Muhammad_Amaan
• Roll No: FA23-BSCS-0151
• Course: Parallel and Distributed Computing (PDC)
• University: Muhammad Ali Jinnah University

🛠️ Performance Architecture

The application runs dynamic sub-array handling via a hybrid processing setup:

Structural Parameter	Active Value	Functional Purpose
Dataset Size (N)	10,000,000	Simulates a heavy workload using 10M random integers.
Thread Group	4 Cores	Target parallel compute allocation environment.
CUTOFF Boundary	5000	Sub-array limit where execution drops down to serial sorting to avoid task thread overhead.
MAX_DEPTH Guard	8	Caps parallel recursive depth to eliminate stack overflows.


📊 Benchmark Results

Benchmarks derived from running the codebase under a 4-thread runtime window:

Evaluation Metric	Benchmark Measurement
Serial Execution Time	⏱️ 3.83337 seconds
Parallel Execution Time	⏱️ 17.0151 seconds
Calculated Speedup	📉 0.225293 (Parallel runs ~4.4x slower)
Calculated Core Efficiency	⚙️ 0.056323 (~5.6% active multi-core scaling)


🔍 Bottleneck Analysis (The Parallel Slowdown)

The results reflect a common parallel computing phenomenon where parallel code executes slower than serial equivalents. This stems from:
• Over-Tasking Overhead: Creating hundreds of thousands of lightweight micro-tasks causes the CPU to spend more runtime scheduling, queue-allocating, and context-switching than doing real arithmetic work.
• Memory Invalidation: In-place vector modifications spark hardware cache-line thrashes across cores, blocking execution pipelines.

🚀 Execution & Setup Guide


1. Compile the Code

Compile with the OpenMP runtime multi-threading flag enabled:
bash
g++ -fopenmp quicksort.cpp -o quicksort
Use code with caution.

2. Configure Threads & Run

Export your desired core group and run the executable:
bash
export OMP_NUM_THREADS=4
./quicksort
