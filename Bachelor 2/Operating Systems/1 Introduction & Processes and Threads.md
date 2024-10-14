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
## 1.4 Modern Computer Systems  
In a modern computer system, the OS coordinates tasks such as video file reproduction, where it manages **concurrency**, **memory**, and **I/O operations**.

![[Pasted image 20241014164011.png]]
## 1.5 What is a Process?  
A **process** is a program in execution that consists of the program code, data, stack, and **Process Control Block (PCB)**, which holds critical information such as process ID, user ID, and state information.

- **Process States**: 
  - **Running**: Actively using the CPU.
  - **Ready**: Ready to run but waiting for CPU time.
  - **Blocked**: Waiting for I/O or other events.

## 1.6 Process Switching and Privilege Levels  
- **Process Switch**: Occurs when the OS interrupts a running process, saves its state, and switches to another process.
- **Mode Switch**: Involves switching between user mode and kernel mode, allowing the system to perform privileged operations.

## 1.7 What are Threads?  
Threads allow multiple sequences of execution within a process, sharing resources like code and data, but having their own stack. This improves efficiency, especially in lightweight, parallel tasks.

## 1.8 Processes vs. Threads  
- **Processes**: Slower in creation and switching, require kernel-level communication for shared resources.
- **Threads**: Faster in creation and switching, but synchronization is not guaranteed.

## 1.9 User-Level vs. Kernel-Level Threads  
- **User-Level Threads (ULTs)**: Managed by the application, faster thread switching, but blocked processes can prevent further execution.
- **Kernel-Level Threads (KLTs)**: Managed by the OS, allows multiple processors, but thread switching involves significant overhead.

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

This outline should make studying operating systems easier by focusing on essential concepts and clear definitions.