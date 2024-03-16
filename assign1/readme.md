# Assignment 1
## Team Members
|std_id|Name|
|--------|-|
|k21-3001|Noufal Ehaab|
|k21-3057|Affan Iqbal|
|k21-3078|Midhat Masood|
## Output Screenshots


Batch File:
![image](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/162920031/3c283993-199c-411b-b148-93d889ed6cbc)
![image](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/162920031/ae73be10-1708-40b1-9751-1ee5913bd40c)

Output:
![1](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/162918850/68511366-e641-47c3-9a88-66203ce5302c)
![2](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/162918850/2eaa0c69-8786-434d-9695-16a773a11ff2)
![OMP tile](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/126159610/5f439d21-a32b-46fd-917a-7b88928066ea)
![MPI Naive](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/126159610/addca689-2ef1-46a1-a303-79f01e3edf0c)
![MPI tile](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/126159610/f1c69d7a-6975-4e11-b898-4c542065bfe1)


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

  ![PC_B](https://github.com/NUCES-Khi/matrixtimesvector-nam/assets/162918850/a6e900a1-6538-4c8f-a4ab-a04b6206c331)

  **Analysis:**
  
 ### **Sequential Execution:**

  - Sequential execution performs computations one after another without parallelization.
  - Both PC-A and PC-B show similar performance in sequential execution.
  - As matrix size increases, execution time also increases linearly.
### **OpenMP Execution:**

  - OpenMP parallelization divides the work among threads on a shared-memory system.
  - Both PCs show improved performance with OpenMP parallelization compared to sequential execution.
  - PC-B generally outperforms PC-A in OpenMP execution across all matrix sizes, likely due to its better hardware       specifications.
### **OpenMP Tiling:**

  - OpenMP Tiling optimizes cache usage by partitioning data into smaller blocks.
  - Both PCs exhibit improved performance with OpenMP Tiling compared to the naive OpenMP approach.
  - Tiling helps reduce cache misses and improves data locality, resulting in faster execution times.
  - PC-B continues to outperform PC-A, although the performance gap may vary depending on the matrix size and cache      efficiency.
### **MPI Execution:**

  - MPI parallelization distributes work among separate processes in a distributed-memory system.
  - Both PCs show improved performance with MPI parallelization compared to OpenMP.
  - MPI execution is particularly beneficial for large matrix sizes where communication overhead is outweighed by        parallel processing gains.
  - PC-B consistently outperforms PC-A in MPI execution, indicating better scalability and efficiency.
### **MPI Tiling:**

  - MPI Tiling combines MPI parallelization with data tiling for distributed-memory systems.
  - Both PCs demonstrate further performance improvement with MPI Tiling compared to MPI Naive approach.
  - Tiling reduces communication overhead by minimizing data transfer between processes.
  - PC-B maintains its performance advantage over PC-A, suggesting better hardware utilization and scalability.
### **Overall Analysis:**

  - Regardless of PC specifications, the implementation technique significantly impacts performance.
  - OpenMP and MPI parallelization offer substantial speedup over sequential execution, with MPI showing better          scalability for larger datasets.
  - Tiling techniques further enhance performance by optimizing cache usage and reducing communication overhead.
  - PC-B consistently outperforms PC-A across all implementation techniques, indicating the importance of hardware       capabilities in parallel computing tasks.
  - **MPI (MPI_Tiling for PC-A and MPI_Naive for PC-B) proved to be the most efficient for matrix vector multiplication whereas    sequential proved to be the worst.**
  
## Major Problems Encountered
1. Issue 1: Parallelizing in MPI tiling approach
   The result vector was constantly throwing random pointer address. 
    - Solution1: Tried different approaches to debug even used different mpi functions to distribute the data. 
    - Solution2: Finally used MPI reduce with tiling approach taught in class.
    - **Resolved**
3. Issue 2: Calculating exact executing time in batch scripting.
    - Solution1: Tried to show time in miliseconds and centiseconds but bash scripting failed to show the time.     
      Finally used seconds to calculate time. Averaging helped us to calculate correct estimated time.
    - **Partially Resolved**
