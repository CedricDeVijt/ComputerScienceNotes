### Computer Architecture Overview
- **Four Main Components**:
  - **Processor**: Executes instructions.
  - **Memory**: Stores instructions and data, organized into addressable words.
  - **I/O Devices**: Facilitate communication with the system (e.g., hard disk, keyboard).
  - **Communication Element**: Allows data exchange among components.
- **Instruction Cycle**:
  - Stages: Fetch, Execute, Interrupt.
  - **Program Counter (PC)**: Tracks the next instruction.
  - **Interrupt Mechanism**: Handles delays from I/O operations, system calls, or exceptions.

### Processes
- **Definition**: A program in execution.
- **Attributes**:
  - **Code**: Instructions to execute.
  - **Data**: Manipulated by code; can be static or dynamic.
  - **User Stack**: Handles procedure calls.
  - **Heap**: Stores dynamically allocated memory.
  - **Process Control Block (PCB)**: Stores process-specific information:
    - Process Identification (ID, parent process, user ID).
    - Processor State Information (register values).
    - Control Information (state, privileges, memory allocation).

#### Process States
- **New**: Process created.
- **Running**: Actively using the processor.
- **Ready**: Awaiting execution.
- **Blocked**: Waiting for an event.
- **Exit**: Process completed or terminated.
- **Suspend**: Process moved to secondary storage to free up memory.
- **UNIX Model**: Includes states like "Kernel Running" and "User Running."

### Threads
- **Definition**: Lightweight processes sharing the same resources.
- **Multithreading**:
  - Threads share code, data, and PCB but have separate stacks.
  - Improves efficiency by reducing context-switching overhead.

#### Thread Models
1. **Single-Threaded Process**: Single execution path.
2. **Multi-Threaded Process**: Multiple threads in a single process.
3. **Multi-Process Multi-Threaded**: Combines multiple processes with multithreading.

#### Thread Implementation
1. **User-Level Threads (ULTs)**:
   - Managed at the application level.
   - Pros: Efficient thread switching, customizable scheduling.
   - Cons: Blocking affects all threads, single thread execution on multi-core systems.
2. **Kernel-Level Threads (KLTs)**:
   - Managed by the operating system.
   - Pros: True parallel execution, avoids ULT limitations.
   - Cons: Higher overhead due to mode switching.

---

## Key Points to Remember

- A **process** represents a program in execution, consisting of code, data, stack, and PCB.
- **Interrupts** are critical for managing I/O operations and exceptions without halting processor efficiency.
- **Process States**: Key states include New, Running, Ready, Blocked, Exit, and Suspend.
- **Threads** allow a single process to execute multiple paths of execution, enhancing performance.
- **ULTs vs. KLTs**: ULTs are application-managed and efficient but limited in certain scenarios, while KLTs offer greater flexibility at the cost of higher overhead.