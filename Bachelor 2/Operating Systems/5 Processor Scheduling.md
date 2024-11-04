## Overview
Processor scheduling in operating systems (OS) is the mechanism by which the OS decides which process or task should use the processor at any given time. It consists of three main scheduling types:

1. **Long-Term Scheduling**: Decides which processes are admitted to the system.
2. **Medium-Term Scheduling**: Controls which processes are swapped out or in, often in response to memory management needs.
3. **Short-Term Scheduling**: Determines which process in the ready queue gets the processor next, and is critical for performance.

![[Screenshot 2024-11-04 at 13.56.56.png]]
## 5.1: Types of Processor Scheduling
### 5.1.1 Long-Term Scheduling
- **Function**: Manages new processes entering the system (New → Ready state).
- **Key Considerations**:
  - Balancing processor-bound and I/O-bound processes.
  - Preventing too many active processes to avoid resource overload.
### 5.1.2 Medium-Term Scheduling
- **Function**: Suspends or resumes processes, interacting with virtual memory management.
- **Frequency**: Occurs more often than long-term scheduling.
### 5.1.3 Short-Term Scheduling
- **Function**: Selects the next process for processor execution from the ready queue.
- **Techniques**: Uses various algorithms to optimize CPU utilization and response times.

## 5.2: Performance Metrics for Scheduling
### 5.2.1 Average Turnaround Time ($T_q$)
- **Definition**: Time from process submission to completion, including wait times.
- **Importance**: Measures system responsiveness.
### 5.2.2 Response Time
- **Definition**: Time taken for a process to begin execution after it is ready.
- **Relevance**: Crucial in interactive systems where user feedback is essential.
### 5.2.3 Fairness
- **Goal**: Equitably distribute CPU resources among processes.
- **Measurement**: Often subjective; sometimes assessed by normalized turnaround time.
### 5.2.4 Predictability
- **Goal**: Ensure processes have consistent execution times.
- **Challenge**: Minimizing interference from other processes.

## 5.3: Scheduling Models & Notation
### 5.3.1 Universal Notation
- **Format**: `α | β | γ`
  - **α (Machine Environment)**: Defines processor configuration (e.g., single (1) or multiple processors (Pm which are m identical machines/processors)).
  - **β (Pre-conditions)**: Defines task conditions like release times (r$_j$), preemptions (pmtn), and precedence constraints (prec).
  - **γ (Objective)**: Specifies the function to be minimized (e.g., $\Sigma c_j$ total completion time).
### 5.3.2 Examples
- **Single Processor with Precedence**: $1 | prec, r_j | ∑C_j$

## 5.4: Short-Term Scheduling Algorithms
### 5.4.1 Non Real-Time Algorithms
- **First-In First-Out (FIFO)**: Processes are served in arrival order.
  - **Drawbacks**: High turnaround for small tasks; I/O-bound tasks suffer.
![[Pasted image 20241104142017.png | 400]]

- **Round Robin (RR)**: Processes take turns with a fixed quantum time.
  - **Advantages**: Reduces wait for small processes.
  - **Challenges**: Quantum choice is crucial; may disadvantage I/O-bound processes. If q is too small, the processor switches more than it executes (processor sharing).

![[Screenshot 2024-11-04 at 14.20.51.png|500]]

### 5.4.2 Optimal Algorithms
- **Shortest Process Next (SPN)**: Selects the process with the shortest execution time.
  - **Optimal for**: Batch tasks arriving together.
  - **Limitation**: Requires knowledge of task duration.
  - **Formula**: $T_q = q_1 + (q_1+q_2) + \dots + (p_1+q_2+ \dots +q_N) = \sum\limits_{i=1}^{N} (N - i + 1) p_i$ (optimal if $p_0≤p_2 \dots ≤p_N$)
- **Weighted Short Process Next (WSPN)**: a variant of SPN where each process is assigned a weight $w_j$ to prioritize processes based on importance or urgency.
	- **Objective**: Minimize the weighted average turnaround time $T_q$ defined as: $T_q = \frac{1}{N} \sum_{j=1}^{N} w_j C_j$
	  where $C_j$ is the completion time of process $j$.
	- **Optimality**: WSPN is optimal for $1 || \sum w_j C_j$, meaning it effectively schedules a batch of processes arriving at the same time.
	- **Smith’s Rule**: WSPN orders processes by the ratio $\frac{p_j}{w_j}$, selecting the process with the smallest value first.
- **Shortest Remaining Time Next (SRTN)**: Chooses process with the least remaining execution time.
  - **Properties**: Preemptive, optimal for minimizing average completion time.
  - **Drawback**: Long tasks may starve.
- **Non-Preemptive SRTN**: selects the process with the shortest remaining execution time and runs it to completion without interruption.
	- **Objective**: Minimize the average completion time $T_q$ in scenarios where preemption is not possible.
	- **Properties**:
	  - **Optimality Context**: The algorithm minimizes total completion time in specific conditions where tasks do not need preemption.
	  - **Complexity**: Finding the optimal order can be challenging, as the problem is NP-hard for larger sets of processes.
	  - **Approximation**: Non-preemptive SRTN can achieve an order with a total completion time at most twice as large as the optimal (a 2-approximation).
	- **Order Construction**: Given an optimal sequence, completion times are built based on the order in which processes are executed. If arrival times $r_j$ are involved, the processor might remain idle until the task with the shortest execution time arrives.
- **Highest Response Ratio Next (HRRN)**: Chooses based on response ratio, balancing between short and long processes.
  - **Application**: Effective for smaller tasks, avoids starvation.

## 5.5: Multilevel Feedback Queues
- **Concept**: Processes move across priority queues based on their CPU usage.
- **Structure**:
  - Multiple queues, each with decreasing priority.
  - Processes that consume more CPU time are moved to lower-priority queues.
  - Last queue operates in a round-robin manner to prevent starvation.
### Unix Scheduler Relation
- **Implementation**: Similar to multilevel feedback with priority adjustments.
- **Key Mechanism**: Uses factors like CPU usage and user-defined "nice" values to prevent large processes from starving.

---

## Key Points to Remember
- **Types of Scheduling**: Long-term (New → Ready), Medium-term (Swapping), and Short-term (Ready → Running).
- **Performance Metrics**:
  - **Turnaround Time (Tq)**: Total process completion time.
  - **Response Time**: Time for process to start execution.
  - **Fairness & Predictability**: Equitable resource distribution, consistent performance.
- **Scheduling Notation**: `α | β | γ` (machine environment, conditions, minimization objective).
- **Short-Term Scheduling Algorithms**:
  - **FIFO**: Simple, fair but slow for smaller tasks.
  - **Round Robin**: Fair with quantum adjustment, best for multitasking.
  - **Optimal Strategies**: SPN, SRTN, HRRN, each with unique application scenarios.
- **Multilevel Feedback Queues**: Adaptive priority for long-running processes, preventing starvation.
- **Unix Scheduler**: Combines priority adjustments and fair CPU time distribution.