## 9.1: Introduction to Filesystems
### Summary
- **Filesystems** organize data on storage devices.
- Key attributes of files:
  - **File name**, **Type**, **Location**, **Size**, **Protection** (permissions), **Time/Date/User ID**.
- Directory structures consolidate file information.

### Key Concepts
- Filesystem is foundational for data storage and retrieval.
- Each file is defined by attributes stored in directories.

## 9.2: File Operations and Open-File Tables
### Summary
1. **File Operations**:
   - **Create**: Uses free-space management.
   - **Read/Write**: File location and pointer.
   - **Search/Delete**: Adjust pointers and free space.
2. **Open-File Tables**:
   - Maintains file entries for quick access.
   - Types:
     - **Per-process table**: Tracks open files per process.
     - **System-wide table**: Tracks global file information.
   - Avoids redundant directory searches.

### Key Concepts
- **Per-process pointers** ensure isolation.
- **Reference counters** in system-wide tables facilitate safe file deletion.

## 9.3: Directory Structures
### Summary
1. **Types of Structures**:
   - **Tree-based**: Files identified by paths.
   - **Graph-based**: Symbolic links and hard links.
   - Challenges: Closed paths and unique paths.
2. **Implementation**:
   - **Linear List**: Simple but slow.
   - **Binary Tree**: Faster searches, more management.
   - **Hash Function**: Efficient but relies on clustering.

### Key Concepts
- Symbolic links add flexibility; hard links ensure integrity.
- Hashing minimizes search time.

## 9.4: Access and Allocation Methods
### Summary
1. **Access Methods**:
   - **Sequential**: Process records linearly.
   - **Direct/Relative**: Access via logical record number.
2. **Allocation Methods**:
   - **Continuous**:
     - Fast but faces fragmentation.
   - **Linked/Chained**:
     - Flexible but slower.
   - **Indexed**:
     - Combines benefits with a tradeoff on overhead.

### Key Concepts
- **File Allocation Table (FAT)** improves linked allocation.
- **Indexed allocation** is analogous to memory paging.

## 9.5: UNIX Inodes
### Summary
- **Inodes**: Metadata structure for files/directories.
- Direct pointers handle small files efficiently.
- Multilevel indexing manages large files.
- Placement of inodes near data optimizes performance.

### Key Concepts
- **Direct pointers** offer simplicity.
- **Multilevel pointers** scale for large files.

## 9.6: Free-Space Management
### Summary
- **Techniques**:
  - **Bitmap**: Tracks free blocks using bits.
  - **Linked List**: Efficient but less flexible.
  - **Indexing**: Organizes free blocks into multilevel structures.

### Key Concepts
- Bitmaps are compact but can become unwieldy.
- Linked lists are ideal for chained allocation.

## 9.7: Journaling
### Summary
- **Goal**: Quick recovery after crashes.
- **Technique**:
  1. Log changes before execution.
  2. Apply changes atomically.
  3. Remove log entries post-execution.
- **Advantages**:
  - Prevents **data inconsistency**.
  - Recovery focuses on uncompleted logs.

### Key Concepts
- Write-ahead logging ensures durability.
- Cost of logging depends on transaction size.

---

## Key Points to Remember
- **File Attributes**: Name, location, size, and permissions.
- **Directory Structures**:
  - Trees and symbolic links.
  - Efficient implementation using hashes.
- **Access and Allocation Methods**:
  - Continuous for performance.
  - Linked for flexibility.
  - Indexed for scalability.
- **UNIX Inodes**: Core of file management.
- **Free-Space Management**: Optimized with bitmaps and indexes.
- **Journaling**: Critical for reliability and quick recovery.