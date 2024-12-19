## 3.1 Memory Management

### Introduction

Memory management involves the efficient sharing of scarce memory resources among multiple processes in a computer system. Key tasks include determining which processes remain in memory, logically and physically organizing them, and managing virtual memory.

### Loading and Linking

- **Absolute Addressing**: Object code uses fixed addresses; loaders have limited flexibility.
- **Relocatable Addressing**: Logical addresses are translated to physical ones at load time, allowing dynamic relocation.
- **Run-Time Address Translation**: Hardware translates logical to physical addresses during execution, enabling flexible memory placement.

### Partitioning

#### Fixed Partitioning

- **Static Partitions**: Memory divided into fixed-size partitions, leading to **internal fragmentation**.
- **Dynamic Partitions**: Variable-sized partitions minimize internal fragmentation but introduce **external fragmentation**.

#### Placement Algorithms

1. **Best-Fit**: Finds the smallest suitable partition, leading to small unusable fragments.
2. **First-Fit**: Selects the first sufficient partition, often faster but may create many small fragments.
3. **Next-Fit**: Resumes searching from the last allocated partition, typically faster for sequential loads.

#### Compaction

- Consolidates free memory blocks by relocating processes, reducing fragmentation but requiring significant processing time.

### Buddy System

- Memory divided into power-of-2-sized blocks.
- Blocks split or merged based on process requirements.
- Provides flexibility while ensuring efficient memory use.

## 3.2 Paging

### Concept

Paging divides memory into fixed-size blocks called **frames**, and process images are split into **pages** of the same size. Frames need not be contiguous in memory.

### Benefits

- Eliminates **external fragmentation**.
- Minimizes **internal fragmentation** (on average, half a page per process).

### Address Translation

- Logical address split into **page number** and **offset**.
- **Page Table**: Maps logical page numbers to physical frame numbers.
- Hardware performs translations efficiently.

### Key Considerations

- Modern processors (e.g., x86) use hierarchical or inverted page tables to reduce memory overhead.

## 3.3 Segmentation

### Concept

Segmentation organizes memory into logical units (**segments**) like code, data, and stack, varying in size and placed non-contiguously.

### Address Translation

- Logical address split into **segment number** and **offset**.
- **Segment Table**: Stores segment base addresses and sizes.
- Includes protections like access permissions and bounds checking.

### Comparison with Paging

- **Paging** is simpler and causes only internal fragmentation.
- **Segmentation** is more intuitive but may suffer from external fragmentation.

### Implementation in x86

- Early x86 systems combined segmentation and paging.
- Modern x86 systems often operate in **flat mode**, making segmentation largely transparent.

---

## Key Points to Remember

- **Memory Management**:

  - Efficient memory sharing and protection are critical.
  - Address translation (logical to physical) ensures flexible resource use.

- **Partitioning**:

  - Fixed partitioning is simple but wasteful.
  - Dynamic partitioning reduces waste but introduces complexity.

- **Paging**:

  - Eliminates external fragmentation.
  - Logical addresses are translated using page tables.

- **Segmentation**:

  - Organizes memory into logical units.
  - Can lead to external fragmentation but provides flexibility.

- **Buddy System**:

  - Balances fixed and dynamic approaches for efficient use of memory.

- Modern systems favor paging over segmentation for memory management due to simplicity and scalability.
