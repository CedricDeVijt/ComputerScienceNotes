# 1 Processes

## 1.1 What is a Process?
- **Definition**: A **process** represents a program in execution.
- The operating system (OS) manages multiple processes to maximize **processor utilization**.
- Processes need to share resources, primarily **memory**, which can lead to conflicts that the OS resolves.

### Physical Attributes of a Process
- Consists of **instructions (code)** and **data**.
- Data can be **static** (fixed size) or **dynamic** (can change).
- A process includes:
  - **User Stack**: Manages procedure calls.
  - **Heap**: Memory for dynamic allocations.
## 1.2 Process Attributes
- **Process Control Block (PCB)**: A data structure containing the essential attributes of a process:
  1. **Process Identification**: Unique ID, parent process info, user ID.
  2. **Processor State Information**: Reflects the contents of CPU registers.
  3. **Process Control Information**: Manages the process's resources, state, and scheduling data.

![[Pasted image 20241004173346.png]]

### Process Image
- The combination of **code**, **data**, **stack**, and **PCB** forms the **process image**.
- The OS uses tables like **memory tables**, **I/O tables**, **file tables**, and a **process table** to manage these process images.

## 1.3 Process States
- **Running**: Currently being executed.
- **Ready**: Ready to run but not currently executing.
- **Blocked**: Waiting for an I/O event or resource.
- Additional states:
  - **New**: Just created and waiting for execution.
  - **Exit**: Process has finished execution but may still hold data for debugging.
  - **Suspend**: Temporarily removed from memory and swapped out.

![[Pasted image 20241004173919.png]]
### State Diagram
- A typical OS manages state transitions using states like **Ready**, **Blocked**, **Running**, **New**, and **Exit**.
- Example: **UNIX Process States** include finer distinctions, such as **Kernel Running** and **User Running** modes.

## 1.4 Kernel, State, and Mode Switching
- The **kernel** manages essential OS functions.
- Processes operate in **user mode** and **kernel mode** for security.
- A **mode switch** occurs without changing the current process state, whereas a **process switch** changes the active process.

# 2 Threads

## 2.1 What are Threads?
- A **thread** represents an independent sequence of execution within a process.
- Threads allow splitting the execution flow, utilizing the same resources like **code**, **data**, and **PCB**, but each thread has its own **user stack**.

### Types of Processes
1. **Single-threaded**: A process with one thread.
2. **Multithreaded**: A process with multiple threads.
   - Example: In **Java**, multiple threads can handle different tasks simultaneously.

### Benefits of Multithreading
- **Efficiency**: Threads share the process's resources, making communication easier.
- **Speed**: Less overhead in context switching compared to multiple processes.

## 2.2 Thread States
- Threads, like processes, have states such as **Running**, **Ready**, and **Blocked**.
- Unlike processes, threads do not individually enter **Suspend**.

### Process vs. Thread Switching
- **Thread Switch**: Occurs within the same process, and no **mode switch** is needed.
- **Process Switch**: Includes more overhead since it requires a switch in context and resources.

## 2.3 Types of Threads
### User-Level Threads (ULTs)
- **Managed by the Application**: OS is unaware of the individual threads.
- **Advantages**:
  - **Efficiency**: No OS involvement in thread switching.
  - **Custom Scheduling**: Each application can define its own thread management strategy.
- **Limitations**:
  - If one thread makes a blocking call, the entire process is blocked.
  - Only one thread can run per process, even on multi-core systems.

### Kernel-Level Threads (KLTs)
- **Managed by the Kernel**: Kernel schedules and manages threads.
- **Advantages**:
  - Threads are scheduled independently, enabling true **parallelism**.
- **Limitations**:
  - **Higher Overhead**: Thread switches involve OS operations, causing more delay.

---

# Key Points to Remember

- **Processor State**: The processor uses a **program counter** and **registers** to execute instructions.
- **Process Control Block (PCB)**: Tracks information like **process state**, **identification**, and **resources**.
- **Thread vs. Process**: **Threads** share resources of a process, allowing faster and more efficient context switching compared to separate processes.
- **User-Level vs. Kernel-Level Threads**: **ULTs** are faster but have limitations in parallel execution, while **KLTs** allow for better performance on multi-core systems.
- **Interrupts and Scheduling**: Interrupts help the OS manage I/O events and **context switching** to ensure optimal processor use.

---

# Study Tips

- **Highlight** the differences between **processes** and **threads**.
- Focus on understanding **thread management** methods: **ULTs** vs. **KLTs**.
- Review the **process state transitions** and understand what conditions cause a state change.
- Emphasize **kernel vs. user mode** differences for better security understanding.

