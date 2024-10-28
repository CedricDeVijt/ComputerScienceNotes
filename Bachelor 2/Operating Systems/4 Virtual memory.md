## 4.1: Introduction to Virtual Memory
- **Memory Management**: Process images aren’t stored as a single block. Some pages are loaded into memory, while others stay in swap space (disk).
- **Logical to Virtual Address**: Logical addresses are converted to virtual addresses to manage larger process images.
  
### Key Concepts
- **Page Hit**: Similar to a cache hit, where the page is in main memory.
- **Page Fault**: Like a cache miss, this requires OS intervention.
- **Page Table**: Manages the virtual-to-physical address translation.

## 4.2: Virtual Memory Layout
- **Page Table Organization**: Includes frame numbers for entries in memory.
- **Segmentation Fault**: Error occurs when accessing unauthorized memory segments.

## 4.3: Page Table Organization and Optimization
- **Challenges**: Large page tables for high memory processes.
- **Solutions**:
  - **Multilevel Page Tables**: Divide page tables to reduce memory load.
  - **Inverted Page Tables**: Uses fewer entries and requires hashing for efficiency.

### Types of Page Tables
1. **Multilevel Page Tables**:
   - Split into multiple levels (e.g., Level 1, Level 2).
   - Reduces memory requirements by storing only active page tables.
2. **Inverted Page Tables**:
   - Utilizes fewer entries.
   - Employs hashing to optimize page lookup.

## 4.4: Translation Lookaside Buffer (TLB)
- **Purpose**: A cache reducing the need for frequent virtual-to-physical address translations.
- **Operation**: Stores (VPN, frame number) pairs for quicker access during processes.
- **Context Switching**: TLB must be flushed when switching processes.

## 4.5: Software Support in Virtual Memory
- **Address Translation**: Managed by hardware; page faults handled by OS.
- **Frame Allocation**: OS determines which frame to load new pages.
  - **Resident Set Management**: Controls # of pages per process.
  - **Replacement Algorithms**: Identifies which page to replace.

## 4.6: Page Replacement Algorithms
- **Optimal Algorithm (MIN)**:
  - Replaces pages unlikely to be needed soon.
  - Used as a benchmark but isn’t feasible in real systems.
- **Least Recently Used (LRU)**:
  - Replaces the page that hasn’t been used recently.
  - Limited by needing frequent updates and lacking frequency info.
- **First-In-First-Out (FIFO)**:
  - Replaces the oldest page.
  - May result in **Belady’s Anomaly** (more memory leading to more faults).
- **Clock Algorithm**:
  - Circular buffer approach with “use bits” to determine page replacement.

## 4.7: Resident Set Policy
- **Fixed vs. Variable Allocation**:
  - Fixed: Pages are restricted to a set number per process.
  - Variable: Pages can be dynamically allocated.
- **Active Working Set (W(t, ∆))**:
  - Defines pages needed in a recent period.
  - Monitored by page fault rates.

---

# Key Points to Remember
- **Page Tables**: Efficient organization crucial for system performance.
- **Address Translation**: Primarily hardware-managed; OS steps in on page faults.
- **Replacement Algorithms**:
  - **MIN**: Ideal but theoretical.
  - **LRU**: Practical but requires high maintenance.
  - **FIFO**: Simple, but susceptible to Belady’s Anomaly.
  - **Clock**: Balances between FIFO and LRU with fewer updates.
- **TLB**: Essential for reducing address translation times.
- **Resident Set Policy**: Dictates which frames can be used for replacements, varying based on allocation type.