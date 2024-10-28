## 3.1: Introduction to Memory Management
Memory management is critical for optimizing the use of the processor by allowing **multiple processes** to share the system's memory. The operating system (OS) is responsible for determining:
1. **Which processes are present in memory**.
2. **How these processes are organized**.

## 3.2: Address Translation
### Compile Time
- **Absolute/physical addresses**: Defined at compile time, location is rigid and cannot change after translation.
### Load Time
- **Relative/logical addresses**: These are mapped to absolute addresses during load time. Once mapped, their location is fixed.
### Run Time
- The location of **relative/logical addresses** is flexible and can change as processes run.

## 3.3: Memory Organization
### Main Approaches
1. **Partitioning**
2. **Paging**
3. **Segmentation**

In most systems, part of the memory is reserved for the OS, while the remaining memory is shared by different user processes.

## 3.4: Partitioning
### 1. Fixed Partitioning (Fixed Size)
- **Description**: Divides memory into fixed-size partitions.
- **Advantages**:
  - Simple to implement.
- **Disadvantages**:
  - Leads to **internal fragmentation** (unused space in partitions).
  - Limits the size and number of processes in memory.
### 2. Variable Partitioning
- **Description**: Memory is divided into partitions of variable size.
- **Advantages**:
  - **Reduces internal fragmentation**.
  - Allows larger processes to fit into memory.
- **Challenges**:
  - **External fragmentation** (unused memory between partitions).
### 3. Dynamic Partitioning
- **Description**: Partitions are created dynamically based on the size required by processes.
- **Advantages**:
  - Maximizes memory usage.
- **Challenges**:
  - Results in memory holes (gaps) between partitions, causing **external fragmentation**.

## 3.5: Paging
### Description
- Divides both **memory** and **processes** into fixed-size blocks called **page frames** and **pages**, respectively.
- **Fragmentation**:
  - **No external fragmentation**.
  - **Small internal fragmentation** when a process’s size isn’t divisible by the frame size.
### Memory Translation
- Logical address: **page number + offset**.
- Translation through **process page table**.

## 3.6: Segmentation
### Description
- Similar to paging but uses **variable-sized segments** instead of fixed pages.
- **Fragmentation**:
  - **No internal fragmentation**.
  - **External fragmentation** may still occur, though less frequently than with partitioning.
### Memory Translation
- Logical address: **segment number + offset**.
- Translation is checked through the **process segment table**.

## 3.7: Placement Algorithms
### Fixed Partitioning
1. **Best-Fit**: Fits a process into the smallest available partition.
   - Produces small holes, leading to fragmentation.
2. **First-Fit**: Allocates the first available partition large enough for the process.
3. **Next-Fit**: Similar to First-Fit, but starts searching from the last allocated partition.
4. **Worst-Fit**: Allocates the largest available partition.
   - May block future processes from fitting into memory.
### Dynamic Partitioning
- **Buddy System**:
  - Divides memory recursively into smaller blocks.
  - If a block is released, it merges with its buddy to form a larger block.
  - Effective in managing **dynamic memory allocation** with **75% memory usage** efficiency.

## 3.8: x86 Architecture
### Paging in x86
- **32-bit architecture**:
  - Frames of **4096 bytes**.
  - **Page table entries** are 4 bytes, with bits dedicated to page properties such as:
    - **P bit**: Page presence in memory.
    - **R/W bit**: Write permissions.
    - **D bit**: Indicates if the page has been modified.
### Segmentation in x86
- **Real and protected modes** are used to manage segmentation.
- Segmentation is controlled through **4 segment registers**:
  - Program code (2), stack (1), and data (1).

---

## Key Points to Remember

- **Address Translation**:
  - Done during **compile time**, **load time**, and **run time**.
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

---

## **Highlighted Terms and Concepts for Quick Review**

- **Memory Management**: Organizes processes in memory to optimize processor usage.
- **Address Translation**: Converts logical addresses to physical addresses at different times (compile, load, run).
- **Partitioning**: Divides memory into partitions, either fixed or variable-sized.
- **Paging**: Divides memory into fixed-size pages to avoid external fragmentation.
- **Segmentation**: Divides memory into variable-sized segments, reducing internal fragmentation.
- **Buddy System**: Dynamic memory allocation technique that merges and divides blocks based on process requirements.
