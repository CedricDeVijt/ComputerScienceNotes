## 7.1: Introduction to Disk Management
### Overview
Disk management constitutes an integral domain within modern operating systems, underpinning efficient data organization, access, and storage across disk drives. Its role is pivotal in ensuring system reliability and optimal performance.

## 7.2: Disk Organization
### Disk Components and Operation
- **Disks**: Rotating metal platters engineered for high-density data storage.
- **Disk Head**: Mechanism that enables precision reading and writing of data.
- **Fixed Rotation Speeds**: Standardized speeds, typically 7200 or 10000 RPM, crucial for consistent access times.

### Disk Partitioning
- **Tracks**: Circular paths on a disk surface.
- **Sectors**: The smallest addressable units of data storage, each accommodating fixed byte lengths.

![[Pasted image 20241202135817.png|500]]

### Zone Bit Recording (ZBR)
- **Zones**: Modern disk architecture segments platters into approximately 15 zones, with sector density tailored to the radial position.
- **Outer Zones**: Feature a higher sector count, enhancing data transfer rates due to reduced rotational delays.

## 7.3: Access and Seek Times
### Access Time Formula
- **Formula**: $T_a = T_s + \frac{1}{2r} + \frac{b}{rN}$
  - $T_s$: The seek time required to position the disk head.
  - $r$: Rotational velocity, measured in revolutions per minute (RPM).
  - $N$: Number of bytes per track.
- **Applicability**: While primarily relevant for random read operations, the formula accounts for variations introduced by buffered I/O processes.

### Seek Times
- **Phases**:
  1. Speed-up.
  2. Coasting.
  3. Deceleration.
  4. Settling.
- **Characteristics**:
  - **Short Seeks (2-4 tracks)**: Dominated by the settle phase.
  - **Long Seeks**: Exhibit a linear correlation with the number of tracks traversed.

## 7.4: Disk Controller and Caching
### Disk Controller
- **Functions**:
  - Manages incoming I/O requests via device driver interfaces.
  - Temporarily buffers data to bridge the speed disparity between the disk and system bus.
  - Implements command queueing to optimize request sequencing and minimize latency.

### Disk Caching
- **Read-Ahead Strategy**:
  - Anticipates the sequential nature of typical read operations, pre-loading subsequent data blocks into cache.
  - Aggressive prefetching extends across multiple tracks to maintain throughput.
- **Utility**:
  - Accelerates read operations by leveraging cached data.
  - Provides limited utility for volatile write operations, given the ephemeral nature of cache memory.

## 7.5: Disk Scheduling Algorithms
### First-In First-Out (FIFO)
- **Mechanism**: Sequentially processes I/O requests in the order of arrival.
- **Characteristics**:
  - Ensures fairness.
  - Exhibits efficiency for spatially clustered operations.
  - Suboptimal for non-sequential, random reads due to higher seek overheads.

![[Pasted image 20241202142515.png|500]]

### Shortest Seek Time First (SSTF)
- **Mechanism**: Prioritizes the request necessitating the shortest seek distance.
- **Advantages**: Enhances throughput by exploiting locality of reference.
- **Drawbacks**: Can result in request starvation, particularly for data located on distant tracks.

![[Pasted image 20241202142544.png|500]]

### SCAN and Cyclic-SCAN (C-SCAN)
- **SCAN**:
  - Moves the disk arm to one extremity, servicing requests along the way, and reverses direction to process remaining requests.
  - Balances service latency but introduces moderate delay variability.
- **C-SCAN**:
  - On reaching an extremity, resets the arm to the opposite end without servicing intermediate tracks.
  - Mitigates unfairness for centrally located requests.

![[Pasted image 20241202144746.png|500]]

### LOOK and C-LOOK
- **LOOK**:
  - A refinement of SCAN, wherein the arm reverses direction upon servicing the last pending request in its current trajectory.
  - Improves efficiency by eliminating unnecessary traversal.
- **C-LOOK**:
  - Operates akin to C-SCAN, with optimizations to minimize arm movement.

### VSCAN and FSCAN
- **VSCAN**:
  - Introduces parameter $R$ (0 $\leq$ $R$ $\leq$ 1) to balance between SSTF and LOOK strategies.
- **FSCAN**:
  - Employs a two-stage buffer system to manage I/O requests effectively.
  - Sequentially processes requests in the first buffer while deferring secondary buffer operations.

## 7.6: RAID (Redundant Arrays of Independent Disks)
### RAID Overview
- **Concept**: RAID amalgamates multiple physical disks into a composite logical volume, enhancing performance, reliability, and capacity.
- **Historical Context**: Introduced by Patterson, Gibson, and Katz in 1988 as a seminal advancement in data storage.

### RAID Levels
1. **RAID 0**: Implements data striping to maximize throughput but lacks redundancy.
	![[Pasted image 20241202150312.png|300]]
2. **RAID 1**: Employs mirroring to replicate data, ensuring high fault tolerance but with reduced write efficiency.
	![[Pasted image 20241202150342.png|300]]
3. **RAID 3 & 4**:
   - **RAID 3**: Optimized for sequential reads using synchronized disk heads.
   - **RAID 4**: Adapts to random access patterns by maintaining independent disk heads.
	![[Pasted image 20241202150432.png|300]]
1. **RAID 5 & 6**:
   - **RAID 5**: Balances performance and reliability via distributed parity.
   - **RAID 6**: Augments fault tolerance with additional parity redundancy.
   ![[Pasted image 20241202150451.png|300]]
1. **Hybrid Configurations**:
   - **RAID 0+1**: Combines striping and mirroring, prioritizing performance.
   - **RAID 1+0**: Inverts the layering of striping and mirroring for enhanced robustness.
	![[Pasted image 20241202150553.png|300]]

---

## Key Points to Remember

- **Disk Organization**:
  - The architecture of tracks, sectors, and ZBR significantly influences access efficiency.
- **Access and Seek Times**:
  - Seek time and rotational delay are pivotal in determining data retrieval latency.
- **Disk Caching**:
  - Read-ahead strategies optimize sequential operations by leveraging anticipatory caching.
- **Scheduling Algorithms**:
  - Each algorithm (FIFO, SSTF, SCAN, LOOK) presents unique trade-offs between efficiency and fairness.
- **RAID Levels**:
  - RAID configurations cater to diverse priorities, from raw speed (RAID 0) to comprehensive redundancy (RAID 6).
