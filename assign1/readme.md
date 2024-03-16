I# Assignment 1
## Team Members
|std_id|Name|
|--------|-|
|k21-3001|Noufal Ehaab|
|k21-3057|Affan Iqbal|
|k21-3078|Midhat Masood|
## Output Screenshots


## Results and Analysis
**The Benchmarking is Performed on 2 different PCs to futher analyse the efficiency:**

**1. PC-A**

  Specifications: 
  - RAM: 8GB
  - Processor: Intel Core i5-8th Gen
  - OS: Windows 10 Enterprise

  Result of Benchmarking:
  
  | Size \ Filename | Sequential (secs) | OpenMP Naive (secs) | OpenMP Tiling (secs) | MPI Naive (secs) | MPI Tiling (secs) |
  |--|-|-|-|-|-|
  | 64 | 0 | 0 | 0.1 | 0 | 0.1 |
  | 128 | 0 | 0 | 0 | 0 | 0.1 |
  | 256 | 0 | 0 | 0 | 0.1 | 0 |
  | 512 | 0.1 | 0.1 | 0 | 0 | 0.1 |
  | 1024 | 0.1 | 0 | 0.1 | 0.1 | 0.1 |
  | 2048 | 0.2 | 0.3 | 0.2 | 0.2 | 0.1 |
  | 4096 | 0.9 | 0.9 | 0.8 | 1 | 0.1 |
  | 8192 | 3.1 | 3.4 | 3.9 | 3.8 | 0 |
  | 16384 | 19.3 | 12.9 | 16.8 | 13.2 | 0.1 |
  | 32768 | 123.6 | 55.6 | 64.2 | 71.7 | 0 |

![PC_A](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/162918850/a4d1557b-de18-427f-8e09-7a92edd0f266)

  Analysis:
  

  **1. PC-B**

  Specifications: 
  - RAM: 16GB
  - Processor: Intel Core i5-11th Gen
  - OS: Windows 11 Pro

  Result of Benchmarking:

  | Size \ Filename | Sequential (secs) | OpenMP Naive (secs) | OpenMP Tiling (secs) | MPI Naive (secs) | MPI Tiling (secs) |
  |--|-|-|-|-|-|
  | 64 | 0 | 0 | 0 | 0.1 | 0 |
  | 128 | 0.1 | 0 | 0.1 | 0 | 0 |
  | 256 | 0 | 0 | 0 | 0 | 0 |
  | 512 | 0 | 0.1 | 0 | 0 | 0.1 |
  | 1024 | 0 | 0 | 0 | 0.1 | 0 |
  | 2048 | 0.1 | 0.1 | 0.1 | 0.1 | 0.1 |
  | 4096 | 0.4 | 0.3 | 0.4 | 0.3 | 0.4 |
  | 8192 | 1.4 | 1.4 | 1.4 | 1.3 | 1.6 |
  | 16384 | 6.3 | 5.6 | 6.7 | 5.8 | 6.5 |
  | 32768 | 28 | 24.4 | 26.7 | 24.3 | 28.5 |
  
//-- Show graphs results and charts where necessary and discuss the results and what they signify. --// 

## Major Problems Encountered
1. Issue 1: Parallelizing in MPI tiling approach
   The result vector was constantly throwing random pointer address. 
    - Solution1: Tried different approaches to debug even used different mpi functions to distribute the data. 
    - Solution2: Finally used MPI reduce with tiling approach taught in class.
    - **Resolved**
3. Issue 2: Calculating exact executing time in bash scripting.
    - Solution1: Tried to show time in miliseconds and centiseconds but bash scripting failed to show the time.     
      Finally used seconds to calculate time. Averaging helped us to calculate correct estimated time.
    - **Partially Resolved**
