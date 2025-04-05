## 2.1 Overview of Computer Memory

### Internal and External Memory

- **Internal memory** includes:
  - Registers in the processor
  - **Cache memory**
  - Main memory (RAM)
  - Characteristics: Often volatile, loses data without power.
- **External memory** includes:
  - Disks
  - Flash memory
  - Tapes

### Memory Hierarchy

- Types of memory organized in a hierarchy:

  1. **Cost per bit** decreases as we move to lower levels.
  2. **Capacity** of memory increases.
  3. **Access time** increases.
  4. **Frequency of access** by the processor decreases.

- Key concept: **Locality of Reference**
  - Temporal repetition in data/instruction access (e.g., in loops).
  - Proximity of data/instructions increases the likelihood of access.

### Key Figures

- Cache: Several Kbytes to several Mbytes.
- Main Memory: Several Gbytes.
- Disks: Several Tbytes.
- Access times:
  - Cache: Nanoseconds (40x faster than main memory).
  - Main memory: 10,000x faster than disks (milliseconds).

## 2.2 Cache Memory Organization

### Basic Structure

- **Cache memory**:
  - Typically **on-chip** (close to the processor).
  - Connects via a **fast bus** to the processor.
  - Slow memory (main memory) connected via a shared bus.

### Cache Function

- Cache contains a **subset** of main memory.
- Organization:
  - Main memory divided into **blocks** (K words).
  - Cache has **lines** with:
    - Tag: Identifies blocks.
    - Data: Words from blocks.
    - Control bits (e.g., "In Use", "UPDATE").

### Cache Hits and Misses

- **Hit**: Requested word is directly available in the cache.
- **Miss**: Block is loaded from main memory into the cache.
  - **Hit ratio**: Probability that a word is in the cache.

### Direct Mapping

- Each block in main memory maps to a unique line in the cache.
  - Formula: $i = `j mod 2^r`
  - `i`: Cache line number
  - `j`: Block number

#### Advantages

- Simple implementation.

#### Disadvantages

- **Thrashing**: Repeated overwriting of blocks due to mapping conflicts.

### Associative Mapping

- Blocks can be placed anywhere in the cache.
  - **Advantages**: No fixed location; prevents thrashing.
  - **Disadvantages**: Complex and expensive; requires longer tags.

### Set-Associative Mapping

- Cache divided into "sets"; blocks restricted to a specific set.
  - **k-way set-associative cache**:
    - Combines advantages of direct and associative mapping.
    - Small values for `k` (e.g., 2, 4, 8) are common.

#### Advantages

- Avoids thrashing.
- Less complex than associative mapping.

#### Disadvantages

- Less flexible than associative mapping.

### Replacement Algorithms

- **Least Recently Used (LRU)**

  - Removes the least recently used block.
  - Requires additional storage for tracking.

- **First In First Out (FIFO)**

  - Removes the oldest block.
  - Simple implementation with a circular buffer.

- **Pseudo LRU (PLRU)**
  - Variants: Tree-based (TB) and Most Recently Used (MRU).
  - Faster implementation of LRU.

## 2.3 Memory Updates: Write Policy

### Write-Through

- Each update immediately written to main memory.
- **Disadvantage**: High bus traffic.

### Write-Back

- Update only written to main memory when the block is removed.
  - UPDATE bit: Indicates if data differs from main memory.

## 2.4 Caches in Modern Systems

### Cache Levels

- **L1 Cache**: Small, fast (e.g., 32 Kbyte, ~4 cycles).
- **L2 Cache**: Larger, slower (e.g., 256 Kbyte).
- **L3 Cache**: Shared, largest, and slowest (several Mbytes).

### Inclusive vs. Exclusive Caches

- **Inclusive**: L1 cache content is always in L2.
- **Exclusive**: Data resides in only one cache at a time.

### Split Cache

- Separate caches for data and instructions.
- Advantages:
  - Parallel access possible.
  - **Prefetching**: Loading future data/instructions.

## 2.5 Cache Benchmarking

### Test Methodology

- Traverse arrays of varying sizes with different strides.
- Plot average access time as a function of stride.

### Results

- **L1 Cache Size**: 128 Kbyte.
- **Additional Compute Time on L1 Miss**: ~425 nanoseconds.
- **Cache Associativity**: 4-way set-associative.
- **No L2 Cache** observed in results.
- **TLB Page Size**: 16 Kbytes.

---

## Key Concepts

- **Cache Memory**: Fast, small memory close to the processor.
- **Memory Hierarchy**: Organization into layers based on speed and cost.
- **Mapping Methods**:
  - Direct: Simple but conflict-prone.
  - Associative: Flexible but expensive.
  - Set-Associative: Balance of simplicity and flexibility.
- **Locality of Reference**: Foundation of cache efficiency.
- **Write Policy**:
  - Write-through: Immediate updates.
  - Write-back: Updates on cache removal.

### Cache Specifications

- **Hit Ratio**: Crucial for performance.
- **Replacement Algorithms**: Optimize use of limited cache space.
- **Benchmarks**: Evaluate cache properties like size and associativity.
