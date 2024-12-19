# Operating Systems Study Guide

## 3.1 Memory Management

### Introduction

Memory management is critical for optimizing the use of the processor by allowing **multiple processes** to share the system's memory. The operating system (OS) is responsible for determining:

1. **Which processes are present in memory**.
2. **How these processes are organized**.

Key tasks include determining which processes remain in memory, logically and physically organizing them, and managing virtual memory.

### Loading and Linking

- **Absolute Addressing**: Object code uses fixed addresses; loaders have limited flexibility.
- **Relocatable Addressing**: Logical addresses are translated to physical ones at load time, allowing dynamic relocation.
- **Run-Time Address Translation**: Hardware translates logical to physical addresses during execution, enabling flexible memory placement.

![[Pasted image 20241219174024.png|400]]

## 3.2 Address Translation

### Compile Time

- **Absolute/physical addresses**: Defined at compile time, location is rigid and cannot change after translation.

### Load Time

- **Relative/logical addresses**: These are mapped to absolute addresses during load time. Once mapped, their location is fixed.

### Run Time

- The location of **relative/logical addresses** is flexible and can change as processes run.

![[Pasted image 20241219174154.png|400]]

## 3.3 Memory Organization

### Main Approaches

1. **Partitioning**
2. **Paging**
3. **Segmentation**

In most systems, part of the memory is reserved for the OS, while the remaining memory is shared by different user processes.

## 3.4 Partitioning

### Fixed Partitioning

#### Fixed Size

- **Description**: Divides memory into fixed-size partitions.
- **Advantages**:
  - Simple to implement.
- **Disadvantages**:
  - Leads to **internal fragmentation** (unused space in partitions).
  - Limits the size and number of processes in memory.

#### Variable Size

- **Description**: Memory is divided into partitions of variable size.
- **Advantages**:
  - **Reduces internal fragmentation**.
  - Allows larger processes to fit into memory.
- **Challenges**:
  - **External fragmentation** (unused memory between partitions).

![[Pasted image 20241219174400.png|400]]

### Dynamic Partitioning

- **Description**: Partitions are created dynamically based on the size required by processes.
- **Advantages**:
  - Maximizes memory usage.
- **Challenges**:
  - Results in memory holes (gaps) between partitions, causing **external fragmentation**.

![[Pasted image 20241219174429.png|400]]

#### Placement Algorithms

1. **Best-Fit**: Fits a process into the smallest available partition.
   - Produces small holes, leading to fragmentation.
2. **First-Fit**: Allocates the first available partition large enough for the process.
3. **Next-Fit**: Similar to First-Fit, but starts searching from the last allocated partition.
4. **Worst-Fit**: Allocates the largest available partition.
   - May block future processes from fitting into memory.

![[Pasted image 20241219174520.png|400]]

#### Compaction

- Consolidates free memory blocks by relocating processes, reducing fragmentation but requiring significant processing time.

### Buddy System

- Memory divided into power-of-2-sized blocks.
- Blocks split or merged based on process requirements.
- Provides flexibility while ensuring efficient memory use.
- Effective in managing **dynamic memory allocation** with **75% memory usage** efficiency.

![[Pasted image 20241219174556.png|400]]

## 3.5 Paging

### Description

- Divides both **memory** and **processes** into fixed-size blocks called **page frames** and **pages**, respectively.
- **Fragmentation**:
  - **No external fragmentation**.
  - **Small internal fragmentation** when a process’s size isn’t divisible by the frame size.

### Address Translation

- Logical address: **page number + offset**.
- Translation through **process page table**.
- Hardware performs translations efficiently.

![[Pasted image 20241219182144.png|400]]

### Key Considerations

- Modern processors (e.g., x86) use hierarchical or inverted page tables to reduce memory overhead.

## 3.6 Segmentation

### Description

- Similar to paging but uses **variable-sized segments** instead of fixed pages.
- **Fragmentation**:
  - **No internal fragmentation**.
  - **External fragmentation** may still occur, though less frequently than with partitioning.

### Memory Translation

- Logical address: **segment number + offset**.
- Translation is checked through the **process segment table**.

### Comparison with Paging

- **Paging** is simpler and causes only internal fragmentation.
- **Segmentation** is more intuitive but may suffer from external fragmentation.

### Implementation in x86

- **32-bit architecture**:
  - Frames of **4096 bytes**.
  - **Page table entries** are 4 bytes, with bits dedicated to page properties such as:
    - **P bit**: Page presence in memory.
    - **R/W bit**: Write permissions.
    - **D bit**: Indicates if the page has been modified.
- Early x86 systems combined segmentation and paging.
- Modern x86 systems often operate in **flat mode**, making segmentation largely transparent.

---

## Key Points to Remember

- **Memory Management**:

  - Efficient memory sharing and protection are critical.
  - Address translation (logical to physical) ensures flexible resource use.

- **Partitioning**:

  - **Fixed**: Easy but leads to internal fragmentation.
  - **Dynamic**: More efficient but leads to external fragmentation.
  - **Buddy System**: Efficient for dynamic memory allocation with 75% memory utilization.

- **Paging**:

  - Breaks memory into fixed-size pages.
  - No external fragmentation, but there is **small internal fragmentation**.

- **Segmentation**:

  - Uses variable-sized segments, causing **external fragmentation**, but avoids internal fragmentation.

- **x86 Paging and Segmentation**:
  - Paging: 4096-byte frames, page tables manage memory access and permissions.
  - Segmentation: Uses **segment registers** and **protected mode** to manage memory regions.
