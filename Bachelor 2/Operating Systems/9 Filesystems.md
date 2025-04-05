## 9.1 Introduction to Filesystems

### Filesystem Attributes

- **Filesystems** organize data on storage devices.
- Key attributes of files:
  - **File name**, **Type**, **Location**, **Size**, **Protection** (permissions), **Time/Date/User ID**.
- Directory structures consolidate file information.

### Importance of Filesystems

- Filesystem is foundational for data storage and retrieval.
- Each file is defined by attributes stored in directories.

## 9.2 File Operations and Open-File Tables

### File Operations

1. **Create**: Uses free-space management.
2. **Read/Write**: File location and pointer.
3. **Search/Delete**: Adjust pointers and free space.

### Open-File Tables

- Maintains file entries for quick access.
- Types:
  - **Per-process table**: Tracks open files per process.
  - **System-wide table**: Tracks global file information.
- Avoids redundant directory searches.

## 9.3 Directory Structures

### Types of Structures

1. **Tree-based**: Files identified by paths.
2. **Graph-based**: Symbolic links and hard links.
   - Challenges: Closed paths and unique paths.

### Directory Structure Implementation

- **Linear List**: Simple but slow.
- **Binary Tree**: Faster searches, more management.
- **Hash Function**: Efficient but relies on clustering.

## 9.4 Access and Allocation Methods

### Access Methods

1. **Sequential**: Process records linearly.
2. **Direct/Relative**: Access via logical record number.

### Allocation Methods

1. **Continuous**:
   - Fast but faces fragmentation.
2. **Linked/Chained**:
   - Flexible but slower.
3. **Indexed**:
   - Combines benefits with a tradeoff on overhead.

## 9.5 UNIX Inodes

### Structure of Inodes

- **Inodes**: Metadata structure for files/directories.
- Direct pointers handle small files efficiently.
- Multilevel indexing manages large files.
- Placement of inodes near data optimizes performance.

## 9.6 Free-Space Management

### Techniques for Free-Space Management

1. **Bitmap**: Tracks free blocks using bits.
2. **Linked List**: Efficient but less flexible.
3. **Indexing**: Organizes free blocks into multilevel structures.

## 9.7 Journaling

### Journaling Process

- **Goal**: Quick recovery after crashes.
- **Technique**:
  1. Log changes before execution.
  2. Apply changes atomically.
  3. Remove log entries post-execution.
- **Advantages**:
  - Prevents **data inconsistency**.
  - Recovery focuses on uncompleted logs.

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
