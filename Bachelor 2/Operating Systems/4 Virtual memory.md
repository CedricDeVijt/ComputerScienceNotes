 ## 4.1: Introduction to Virtual Memory
- **Memory Management**: Process images aren’t stored as a single block. Some pages are loaded into memory, while others stay in swap space (disk).
- **Logical to Virtual Address**: Logical addresses are converted to virtual addresses to manage larger process images.

![[Pasted image 20241028135433.png]]

![[Pasted image 20241028135446.png]]

### Key Concepts
- **Page Hit**: Similar to a cache hit, where the page is in main memory.
- **Page Fault**: Occurs when a page isn’t in memory and must be loaded.
- **Page Table**: Maps virtual addresses to physical addresses.

## 4.2: Virtual Memory Layout
- **Page Table Organization**: Includes frame numbers for entries in memory.
- **Segmentation Fault**: Error occurs when accessing unauthorized memory segments.

![[Pasted image 20241028140214.png]]

## 4.3: Organization and Optimization of Page Tables

### Desirable Features:
- The entire page table should reside in memory.
- The starting address of the page table should be stored in a register.
- The page number should be used as an index to the page table.

### Problems:
- Page tables can become very large.
- Page numbers can no longer be directly used as an index.

### Solutions:
- **Multilevel Page Tables**: Divide the page table into multiple levels to reduce memory usage.
- **Inverted Page Tables**: Use fewer entries and employ hashing for efficient page lookup.

### Types of Page Tables
1. **Multilevel Page Tables**:
   - The page table is divided into multiple levels (e.g., Level 1, Level 2).
   - This approach reduces memory requirements by storing only the active parts of the page table.

   ![[Screenshot 2024-10-28 at 14.07.33.png]]

2. **Inverted Page Tables**:
   - This type of page table uses fewer entries.
   - It employs hashing to optimize the page lookup process.

   ![[Pasted image 20241028140949.png]]

## 4.4: Translation Lookaside Buffer (TLB)
- **Purpose**: A cache reducing the need for frequent virtual-to-physical address translations.
- **Operation**: Stores (VPN, frame number) pairs for quicker access during processes.
- **Context Switching**: TLB must be flushed when switching processes.

![[Pasted image 20241028142753.png]]

## 4.5: Software Support in Virtual Memory
- **Address Translation**: Managed by hardware; page faults handled by OS.
- **Frame Allocation**: OS determines which frame to load new pages.
  - **Resident Set Management**: Controls # of pages per process.
  - **Replacement Algorithms**: Identifies which page to replace.

## 4.6: Page Replacement Algorithms
- **Optimal Algorithm (OPT)**:
  - Replaces pages unlikely to be needed soon.
  - Used as a benchmark but isn’t feasible in real systems.
- **Least Recently Used (LRU)**:
  - Replaces the page that hasn’t been used recently.
  - Limited by needing frequent updates and lacking frequency info.
- **First-In-First-Out (FIFO)**:
  - Replaces the oldest page.
  - May result in **Belady’s Anomaly** (more memory leading to more faults).
- **Clock Algorithm (CLOCK)**:
  - Circular buffer approach with “use bits” to determine page replacement.

![[Pasted image 20241028145346.png]]

![[Pasted image 20241028142846.png]]

## 4.7: Resident Set Policy
- Frames of the OS are never eligible for replacement
- **Fixed vs. Variable Allocation**:
  - Fixed: Pages are restricted to a set number per process.
  - Variable: Pages can be dynamically allocated.
- **Active Working Set W(t, ∆)**:
  - Defines pages needed in a recent period.
  - Monitored by page fault rates.

---

# Key Points to Remember
- **Page Tables**: Efficient organization crucial for system performance.
- **Address Translation**: Primarily hardware-managed; OS steps in on page faults.
- **Replacement Algorithms**:
  - **OPT**: Ideal but theoretical.
  - **LRU**: Practical but requires high maintenance.
  - **FIFO**: Simple, but susceptible to Belady’s Anomaly.
  - **Clock**: Balances between FIFO and LRU with fewer updates.
- **TLB**: Essential for reducing address translation times.
- **Resident Set Policy**: Dictates which frames can be used for replacements, varying based on allocation type.
