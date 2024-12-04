## 5.1 Introduction to Processor Scheduling
Processor scheduling determines how processes access the processor and ensures fair and efficient CPU utilization.
### Process States
- **States**: Each process may be in a different state, such as **running**, **ready**, or **blocked**.
- **Scheduling Mechanisms**: Scheduling mechanisms control state transitions.
- **Types of Scheduling**:
  - **Long-term scheduling**: Controls when a new process is added to the system.
  - **Medium-term scheduling**: Handles suspended processes, often related to memory management.
  - **Short-term scheduling**: Selects the next process to run from the ready queue.

## 5.2 Types of Scheduling
### 5.2.1 Long-Term Scheduling
- Manages **New → Ready** transitions.
- **Decisions**:
  - When to activate a process.
  - Which process to activate based on **processor** vs. **I/O-bound** types.
- **Goals**:
  - Balance active processes.
  - Avoid excessive CPU or I/O-bound process activity.

### 5.2.2 Medium-Term Scheduling
- **Suspension** of processes, usually to manage memory.
- Ensures balanced memory and CPU utilization.

### 5.2.3 Short-Term Scheduling
- Decides the next process to **execute** on the CPU.
- **Algorithms**: FIFO, Round Robin, Shortest Process Next (SPN), and others, designed for different system goals and process types.

![[Screenshot 2024-11-04 at 13.56.56.png]]

## 5.3 Scheduling Performance Metrics
### 5.3.1 Key Metrics
- **Turnaround Time (Tq)**: Time taken for a process to complete, including waiting and execution.
- **Response Time**: Time before a process starts executing.
- **Fairness**: Ensures all processes get CPU time fairly, measured by **normalized turnaround time**.
- **Predictability**: Consistent process execution time despite other processes.

### 5.3.2 Notation and Models
- **Universal Notation (α | β | γ)**:
  - **α**: Machine environment, e.g., single or multiple processors.
  - **β**: Constraints, e.g., arrival times, preemption, and precedence conditions.
  - **γ**: Goal function to minimize, e.g., total completion time.

## 5.4 Short-Term Scheduling Algorithms
### 5.4.1 Non-Real-Time Scheduling Algorithms
- **First-In, First-Out (FIFO)**:
  - **Oldest process** runs first.
  - Long processes may delay smaller tasks.

	![[Pasted image 20241104142017.png | 400]]
- **Round Robin (RR)**:
  - Each process gets a **time quantum (q)**; goes to the end of the queue when the quantum expires.
  - Works better for **small processes** but can disadvantage I/O-bound tasks.

	![[Screenshot 2024-11-04 at 14.20.51.png|500]]
### 5.4.2 Optimal Algorithms
- **Shortest Process Next (SPN)**:
  - Runs the **shortest task** first.
  - Optimal for **single-batch processes** arriving simultaneously.
  - Requires knowledge of each process’s execution time.
- **Shortest Remaining Time Next (SRTN)**:
  - **Preemptive**: Always selects the process with the least remaining time.
  - Optimal for systems where processes arrive at different times.
- **Weighted Shortest Process Next (WSPN)**:
  - **Weighted priority** applied to processes.
  - Optimal for minimizing weighted turnaround times in batch processing.

### 5.4.3 Advanced Algorithms
- **Multilevel Feedback Queues**:
  - Simulates multiple scheduling strategies.
  - **Priority-based queues**: Longer time spent by a process reduces its priority.

	![[Pasted image 20241106175920.png|400]]

- **Highest Response Ratio Next (HRRN)**:
  - **Response ratio** (waiting time + execution time) / execution time.
  - Favors processes with higher response ratios, balancing short and long tasks.

## 5.5 UNIX Scheduler
- **Multilevel Feedback with Priorities**:
  - Divides time into intervals; each process has a **priority**.
  - **Priority formula**: Adjusted periodically based on CPU usage and user-defined “nice” values.
  - Ensures **fairness** and prevents **starvation**.

---

# Key Points to Remember

- **Scheduling Types**:
  - Long-term, medium-term, and short-term scheduling play distinct roles.
- **Short-Term Algorithms**:
  - **FIFO** and **Round Robin** provide simple scheduling but may be unfair to I/O-bound processes.
  - **SPN** and **SRTN** offer optimal scheduling for specific contexts but may require preemptive switching or known execution times.
- **Performance Metrics**:
  - **Turnaround Time (Tq)**, **Response Time**, and **Fairness** are core metrics.
- **UNIX Scheduling**:
  - Employs a multilevel feedback approach for balancing CPU usage and priorities across user processes.