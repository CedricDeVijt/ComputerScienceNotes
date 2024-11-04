## 2.1 Introduction to Cache Memory
Cache memory is a type of high-speed memory that sits between the CPU and main memory. Its purpose is to speed up access to frequently used data and instructions.

- **Purpose**: Bridge the gap between the **processor speed** and **main memory speed**.
- **Memory Discrepancy**: Processor operates much faster than memory, so cache reduces wait times.
- **Hierarchy**: Cache is smaller but much faster than main memory.

## 2.2 Memory Hierarchy
### 2.2.1 Storage Hierarchy
- **Levels of memory** include registers, cache, main memory (RAM), and secondary storage (hard drives, SSDs).
- **Key trade-offs**:
  - **Speed**: Faster at higher levels (cache, registers).
  - **Capacity**: Larger at lower levels (RAM, secondary storage).
  - **Cost**: More expensive at higher levels.  
### 2.2.2 Volatile vs Non-Volatile Memory
- **Volatile memory**: Loses its contents when power is turned off (e.g., **RAM**).
- **Non-volatile memory**: Retains data without power (e.g., **flash memory**, hard drives).

![[Pasted image 20241014174501.png]]
## 2.3 Cache Operation
### 2.3.1 Locality of Reference
- Locality of Reference helps the memory hierarchy function effectively. Two types are:
	- **Spatial Locality**: Access to data elements that are stored close to each other (e.g., arrays).
	- **Temporal Locality**: Access to the same data elements within a short period of time (e.g., variables within loops).

- As we go deeper into the memory hierarchy (from cache to main memory), data request frequency decreases.
### 2.3.2 Cache Organization
- **Memory is partitioned** into blocks, each containing words.
- Cache stores data in **cache lines** and uses **tags** to identify each line.

- A **block** (or cache line) is the basic unit of data transfer between the main memory and the cache. It is a contiguous chunk of memory that the cache loads from main memory at one time.
- A **word** is the standard unit of data that the CPU processes at one time. The size of a word depends on the system architecture (e.g., 32-bit or 64-bit).

![[Pasted image 20241104090740.png]]
### 2.3.3 Cache Connection to CPU
- Cache memory is placed between the **CPU** and **Main Memory** to reduce data access time.
- **Fast bus** (on-chip) connects the processor and the **L1 cache** for quick access.
- **Slower shared bus** connects the cache to the main memory, transferring larger blocks of data (cache lines).

- Memory is divided into **blocks** of data, and the cache is divided into **lines** that store these blocks.
- Each cache line has a **tag** to identify which memory block it contains, along with a status bit to indicate if the line is currently in use.

### 2.3.4 Hit Ratio
- **Hit**: The data is in the cache, and the processor accesses it immediately.
- **Miss**: The data is not in the cache, and it must be fetched from main memory.
- **Hit Ratio (H)**: The ratio of cache hits to the total number of memory accesses. It's defined as $H = \frac{C}{M}$, where $C$ is the number of cache lines, and $M$ is the total number of memory blocks.

### 2.3.5 Block Size Impact
- **Small Block Size**: Increases the number of cache lines, reducing spatial locality effectiveness.
- **Large Block Size**: Decreases the number of lines, eventually lowering the effectiveness of spatial locality. 
- Cache memory stores data in **blocks** to exploit the principle of locality.
- **Cache lines** are used to store blocks, and each line is tagged to track which memory block it stores.
- Data is transferred between memory and cache in **blocks**, with a larger block size improving spatial locality but reducing the number of available lines.

## 2.4 Mapping Techniques

**Cache mapping** is a placement policy, it specifies how a block of data from main memory is assigned a location in the cache.
### 2.4.1 Direct Mapping
- Each memory block is mapped to exactly one cache line.
- **Advantages**: Simple and fast to implement.
- **Disadvantages**: High chance of collision (two blocks mapped to the same line).

![[Screenshot 2024-10-17 at 10.00.20.png|500]]
### 2.4.2 Associative Mapping
- A memory block can be placed anywhere in the cache.
- **Advantages**: Reduces collisions.
- **Disadvantages**: More complex lookup process (compares tags with all lines in parallel).

![[Screenshot 2024-10-17 at 10.01.21.png|500]]
### 2.4.3 Set-Associative Mapping
- A hybrid of direct and associative mapping. Cache is divided into sets, and each memory block can map to one set.
- **Advantages**: Balances the trade-offs of direct and associative mapping.
- **k-way Set Associative Mapping**: Typically k is small (e.g., 2-way or 4-way), reducing thrashing while keeping lookups manageable.

![[Screenshot 2024-10-17 at 10.02.20.png|500]]
## 2.5 Cache Replacement Algorithms
### 2.5.1 Why Replacement Matters
- On a cache miss, data must be brought into the cache, displacing older data. The choice of which data to replace affects performance.
### 2.5.2 Replacement Strategies
- **Random**: Replace a random cache line (simple but inefficient).
- **FIFO (First-In, First-Out)**: Replace the oldest line (easy but may replace frequently used data).
- **LRU (Least Recently Used)**: Replace the least recently accessed line (very effective but complex).
- **Pseudo-LRU**: Approximation of LRU, balancing performance and simplicity.
  - **Tree-based Pseudo-LRU**: Organizes cache lines into a binary tree for tracking usage.
  ![[Screenshot 2024-10-17 at 10.13.56.png|400]]
  - **Most Recently Used (MRU)**: Replaces the least recently accessed lines.
![[Pasted image 20241017101510.png|400]]

## 2.6 Cache Write Policies
### 2.6.1 Write Through
- Every write to the cache is immediately written to the main memory.
- **Advantages**: Simplifies cache consistency.
- **Disadvantages**: Causes more traffic and slower performance.
### 2.6.2 Write Back
- Data is only written to main memory when it is evicted from the cache.
- **Advantages**: Faster, as it reduces memory writes.
- **Disadvantages**: Requires a "dirty bit" to track modified lines, risking data loss if the system crashes.

## 2.7 Current Cache Designs
- **Modern CPUs** have multiple levels of cache:
  - **L1 Cache**: Smallest and fastest, built directly into the CPU.
  - **L2 Cache**: Larger but slower, still close to the CPU.
  - **L3 Cache**: Shared between cores, larger but slower than L1 and L2.

- **Split Cache**: Separates instruction cache from data cache to allow simultaneous access, improving efficiency.

## 2.8 Benchmarking Cache Performance
### 2.8.1 Cache Benchmarking Process
- Cache performance is tested by repeatedly requesting data from an array with different strides (gaps between accesses).
- As the stride increases or the array size exceeds the cache size, **cache misses** increase, slowing performance.
### 2.8.2 Key Observations from Benchmarking
- **Cache size** affects performance: Arrays smaller than the cache exhibit faster access times.
- **Associative mapping**: More ways (higher k in k-way set associative caches) lead to fewer misses.

---

# Key Points to Remember

- **Cache Memory**: A small, fast memory that bridges the speed gap between CPU and main memory.
- **Memory Hierarchy**: Higher levels (cache, registers) are faster but smaller and more expensive.
- **Locality of Reference**: Data and instructions used recently are likely to be used again (temporal), and data close to recently accessed data is also likely to be used soon (spatial).
- **Mapping Techniques**: 
  - **Direct Mapping**: Simple but prone to collisions.
  - **Associative Mapping**: Flexible but slower due to parallel comparison.
  - **Set-Associative Mapping**: Combines both techniques to optimize performance.
- **Replacement Algorithms**:
  - **FIFO**: Replace the oldest data.
  - **LRU**: Replace the least recently used data.
  - **Pseudo-LRU**: Approximate LRU for better performance.
- **Write Policies**:
  - **Write Through**: Writes data immediately to memory.
  - **Write Back**: Writes data only when it’s evicted from the cache, reducing memory traffic.
- **Modern Cache Designs**: Multi-level caches (L1, L2, L3) improve performance by balancing speed and size.
- **Benchmarking**: Testing cache performance by accessing memory in a structured manner reveals how cache size and mapping affect speed.