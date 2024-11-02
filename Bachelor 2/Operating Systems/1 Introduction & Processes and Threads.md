## 1.1 What is an Operating System?  
An **Operating System (OS)** acts as an intermediary between users and computer hardware, providing an environment for the efficient execution of programs. It manages hardware resources and offers services to applications and users. 

- **Single-user OS**: Designed for one user, it focuses on **high performance** with low resource utilization.
- **Multi-user OS**: Multiple users share resources, leading to **high resource utilization** but potentially lower performance.

![[Pasted image 20241014163909.png]]
## 1.2 System Perspective  
From the system's perspective, the OS is a **resource manager**, ensuring efficient and fair operation of hardware, controlling program execution, and managing I/O devices.

## 1.3 The Kernel  
The **kernel** is the core part of the OS, responsible for resource management, security, and process scheduling. It always runs on the system and interacts closely with hardware.

![[Pasted image 20241014163947.png]]

### Differences kernel and OS

| **Aspect**           | **Kernel**                                                      | **Operating System (OS)**                                                   |
| -------------------- | --------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **Scope**            | Core component managing hardware and low-level system resources | Complete software package managing hardware, software, and user interface   |
| **Role**             | Manages CPU, memory, devices, and process control               | Provides a platform for user interaction and software execution             |
| **User Interaction** | Typically not directly interacted with by users                 | Directly interacted with through GUIs or CLIs                               |
| **Components**       | Handles process scheduling, memory, and hardware control        | Includes the kernel, system libraries, user interface, and system utilities |
| **Example**          | Linux Kernel, Windows NT Kernel                                 | Linux OS (Ubuntu, Fedora), Windows 11, macOS                                |

The **kernel** is the foundational core that controls all the interactions between hardware and software, while the **operating system** is the broader system that includes the kernel, utilities, and interfaces necessary for user and software interaction.

## 1.4 Modern Computer Systems  
In a modern computer system, the OS coordinates tasks such as video file reproduction, where it manages **concurrency**, **memory**, and **I/O operations**.

![[Pasted image 20241014164011.png]]
## 1.5 What is a Process?  
A **process** is a program in execution that consists of the program code, data, stack, and Process Control Block (PCB), which holds critical information such as process ID, user ID, and state information.

Each process is composed of several parts:
- **Text (Code)**: The program code that the process is executing.
- **Data**: Static and dynamic data that the process manipulates.
- **User Stack**: Used to store temporary data such as function parameters, return addresses, and local variables.
- **Kernel Stack**: Supports kernel mode operations such as system calls.
- **Process Control Block (PCB)**: A data structure used by the operating system to store all the information about the process.
## 1.6 Process Control Block (PCB)
The **Process Control Block (PCB)** contains crucial data that the operating system uses to manage processes. It acts as a repository for information about the current state of the process and its characteristics. Key components of a PCB include:

1. **Process Identification**:
   - **Process ID (PID)**: A unique identifier for the process.
   - **User ID**: The user that owns the process.
   - **Parent Process ID**: ID of the process that spawned the current one.

2. **Processor State Information**:
   - Data related to the CPU state, including contents of all **registers** (e.g., program counter, stack pointer).

3. **Process Control Information**:
   - **Process State**: Current state (e.g., Running, Ready, Blocked).
   - **Scheduling Information**: Priority, process queue pointers.
   - **Memory Management Info**: Base and limit registers, page tables, segment tables
## 1.7 Process states
A process can exist in one of several states during its lifetime. These states are managed by the operating system to ensure efficient CPU utilization and task execution. Below are the main process states:

- **New**:  
  The process is being created. The operating system has recognized the process and is setting it up in memory, but it has not started executing yet.
- **Ready**:  
  The process is ready to run but is waiting for CPU time. It has all the necessary resources and can execute when the CPU becomes available.
  - The process is moved to the **ready queue** by the OS scheduler.
- **Running**:  
  The process is currently being executed by the CPU. Only one process can be in the running state per CPU core at any given time.  
  - The **process control block** is updated continuously to reflect the process's current execution state.
- **Blocked (or Waiting)**:  
  The process cannot proceed until some external event occurs, such as input/output operations or receiving a resource. It remains in this state until the event is resolved.
  - Example: Waiting for a file to be read from disk or user input.
- **Suspended (or Swapped)**:  
  The process is temporarily moved from main memory (RAM) to secondary storage (disk) to free up memory. This happens when system memory is low, and the process is not immediately needed.
  - **Blocked-Suspend**: A blocked process that is swapped out.
  - **Ready-Suspend**: A ready process that is swapped out to allow more critical tasks to proceed.
- **Terminated**:  
  The process has finished execution and is removed from the process table. Its resources are freed, and the process ID (PID) is released.  
  - The process can reach this state either after successful execution or due to errors/interruptions.

![[Pasted image 20241004173919.png]]
## 1.8 Process Switching and Privilege Levels  
- **Process Switch**: Occurs when the OS interrupts a running process, saves its state, and switches to another process.
- **Mode Switch**: Involves switching between user mode and kernel mode, allowing the system to perform privileged operations.

![[Pasted image 20241014172742.png]]
## 1.9 What are Threads?  
Threads allow multiple sequences of execution within a process, sharing resources like code and data, but having their own stack. This improves efficiency, especially in lightweight, parallel tasks.

![[Pasted image 20241014173209.png]]

## 1.10 Processes vs. Threads  
- **Processes**: Slower in creation and switching, require kernel-level communication for shared resources.
- **Threads**: Faster in creation and switching, but synchronization is not guaranteed.

| **Criteria**                                     | **Multiple Processes**                                                                 | **Multiple Threads**                                                                   |
|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| **Creation & Switching Speed**                   | Slower in creation, switching (10x) (-)                                                | Fast in creation, switching (+)                                                       |
| **Communication & Sharing**                      | Requires process communication or sharing, which involves the kernel (-)               | Immediate information exchange (+)                                                    |
| **Concurrency**                                  | Concurrency guaranteed by OS (+)                                                       | Synchronization and mutual exclusion not guaranteed (-)                               |
| **Process States**                               | Different process states (+)                                                           | One process state (for user-level threads) (-)                                        |
| **Swapping**                                     | Independently swapped (+)                                                             | Jointly swapped (-)                                                                   |

## 1.11 User-Level vs. Kernel-Level Threads  
- **User-Level Threads (ULTs)**: Managed by the application, faster thread switching, but blocked processes can prevent further execution.
- **Kernel-Level Threads (KLTs)**: Managed by the OS, allows multiple processors, but thread switching involves significant overhead.


| **Criteria**                                         | **User-Level Threads (ULTs)**                                                          | **Kernel-Level Threads (KLTs)**                                                     |
|------------------------------------------------------|----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| **Thread Switching Speed**                           | Thread changes are fast (+)                                                            | Thread change/execution is slower (10-30x) due to OS scheduling (-)                |
| **Scheduling**                                       | Application-specific scheduling (+)                                                    | OS-controlled scheduling (-)                                                      |
| **Processor Utilization**                            | Processor independent (+)                                                              | Processor-dependent (-)                                                           |
| **Blocking**                                         | Process is blocked by calling one thread unless jacketing (-)                          | A single thread blocked will not block others (+)                                 |
| **Processor Use**                                    | Can only use 1 processor (-)                                                           | Can use multiple processors simultaneously (+)                                    |

---

# Key Points to Remember

- **Operating System** is an intermediary that provides an environment for applications and manages hardware resources.
- **Kernel** is the core program of the OS, responsible for system-level tasks and resource management.
- **Processes** are programs in execution, each with its own memory space and control information.
- **Threads** are the subdivision of processes that share resources but execute independently.
- **Process states**: Running, Ready, Blocked (and sometimes Suspended/Swapped).
- **Process Control Block (PCB)** contains vital information about processes such as IDs and states.
- **Process vs. Mode switch**: A process switch changes which program is running, while a mode switch alters the privilege level.
- **User vs. Kernel Threads**: ULTs are efficient but may block the entire process, while KLTs allow better CPU usage but have higher overhead.

---

# Highlighted Sections for Study

- **Operating System (OS)**: Intermediary between users and hardware.
- **Kernel**: The part of the OS that manages resources and hardware directly.
- **Process**: A program in execution, defined by its code, data, stack, and Process Control Block (PCB).
- **Process Control Block (PCB)**: Contains important information for process management.
- **Threads**: Independent paths of execution within a process.
- **Process States**: Running, Ready, Blocked.
- **User-Level Threads (ULTs)**: Fast but limited in CPU usage.
- **Kernel-Level Threads (KLTs)**: Slow but allows for multiple processor usage.
