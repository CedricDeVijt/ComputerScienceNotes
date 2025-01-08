# Operating Systems Course: Memory Management

## 3.1 Introduction to Memory Management

Modern operating systems handle multiple processes simultaneously to maximize processor utilization. This necessitates efficient memory sharing among processes. The key responsibilities include:

- Determining which processes reside in main memory.
- Organizing and protecting memory logically and physically.
- Facilitating memory sharing between processes.

**Key Concept**: Memory is managed using **secondary/virtual memory** (e.g., disk space), with processes often swapped in and out of main memory.

## 3.2 Loading and Linking

### Absolute and Relocatable Addresses

1. **Absolute Addresses**: Compiled with fixed physical addresses, limiting flexibility.
2. **Relocatable Addresses**: Compiled with logical addresses, translated into physical addresses during loading.

### Runtime Address Translation

- **Advantages**: Flexibility in process placement, enabling dynamic relocation.
- **Hardware Support**: Uses base and bounds registers to support runtime relocation.

## 3.3 Memory Organization Techniques

### 3.1 Partitioning

Partitioning divides memory into blocks (partitions). Three types are commonly used:

#### Fixed Partitioning

- **Characteristics**: Fixed-size partitions.
- **Problems**: Internal fragmentation, as processes rarely use the entire partition.

#### Dynamic Partitioning

- **Characteristics**: Partitions created to fit processes exactly.
- **Problems**: External fragmentation caused by scattered unused spaces.
- **Solutions**:
  - Placement algorithms: **First-fit**, **Next-fit**, **Best-fit**, **Worst-fit**.
  - Compaction to merge fragmented spaces (expensive in terms of processing).

#### Buddy System

- Memory divided into partitions of sizes that are powers of 2.
- Blocks split or merged recursively based on requirements.
- **Advantages**: Fast allocation, simple merging.
- **Drawbacks**: Inefficient memory usage (33% overhead on average).

### 3.2 Paging

- Divides memory into fixed-size frames and process images into pages.
- **Advantages**:
  - Eliminates external fragmentation.
  - Minimal internal fragmentation.
- **Address Translation**:
  - Uses a page table to map logical to physical addresses.
  - Hardware support ensures fast translations.

### 3.3 Segmentation

- Divides memory into variable-sized segments based on logical divisions (e.g., code, data).
- **Advantages**:
  - Reduces internal fragmentation.
  - Segments can be independently sized and located.
- **Drawbacks**: External fragmentation may occur.
- **Use in x86 Architecture**:
  - Segmentation used for logical to linear address translation.
  - Typically combined with paging for physical address translation.

---

## Key Points to Remember

- **Memory Sharing**: Processes share memory through virtual memory management.
- **Relocation**: Processes can be dynamically relocated within memory.
- **Partitioning Techniques**:
  - **Fixed Partitioning**: Simple but suffers from internal fragmentation.
  - **Dynamic Partitioning**: Flexible but prone to external fragmentation.
  - **Buddy System**: Balances flexibility and speed but with overhead.
- **Paging**: Efficient memory use by eliminating external fragmentation.
- **Segmentation**: Logical division of memory for improved flexibility.
- **Address Translation**: Essential hardware mechanisms support logical-to-physical address mappings for efficiency and protection.

**Highlighted Terms**:

- **Internal Fragmentation**: Unused space within allocated memory.
- **External Fragmentation**: Scattered unused memory spaces.
- **Page Table**: Maps logical pages to physical frames.
- **Base Register**: Holds the starting address for a process’s memory.
- **Bounds Register**: Defines the limit of a process’s memory.
