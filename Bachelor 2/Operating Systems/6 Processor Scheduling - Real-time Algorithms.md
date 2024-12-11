## 6.1: Introduction to Processor Scheduling

### Overview

Processor scheduling determines which processes get CPU time in a system. It includes:

- **Long-Term Scheduling**: Moves processes to the "ready" state.
- **Medium-Term Scheduling**: Manages processes in the "suspended" state.
- **Short-Term Scheduling**: Decides which process gets immediate CPU access.

### Scheduling Types

1. **Static Scheduling**: Predefined orders based on tasks.
2. **Dynamic Scheduling**: Decisions are made during runtime.

## 6.2: Short-Term Scheduling Algorithms

### Real-Time Algorithms

- Focus on tasks with deadlines (**hard** vs. **soft** deadlines).
- Include **static (offline)** and **dynamic (online)** approaches.

### **Earliest Deadline First (EDF)**

- **Definition**: Schedule tasks based on ascending deadlines.
- **Key Characteristics**:
  - Minimizes lateness $L_{\text{max}} = \max(C_j - d_j)$.
  - Ensures feasibility if $L_{\text{max}} \leq 0$.
  - Optimal when all deadlines are feasible.
- **Example**: If two tasks have deadlines $d_1$ and $d_2$, prioritize the task with $\min(d_1, d_2)$.

### **Moore-Hodgson Algorithm (MHA)**

- Objective: Minimize the sum of unmet deadlines $\sum U_j$.
- **Steps**:
  1. Sort tasks by EDF.
  2. Identify late tasks.
  3. Remove the task with the highest processing time and repeat.

## 6.3: Preconditions for Scheduling

### Release/Arrival Times

- EDF is optimal for the problem $1|r_j, \text{pmtn}| \sum U_j$, where $r_j$ is the release time.
- Load factor $u$ is critical:
  - If $u \leq 1$, all deadlines are feasible.
  - Otherwise, minimize unmet deadlines.

### **Precedence**: Lawler’s Algorithm

- Handles tasks with dependencies represented by a graph $G = (V, E)$.
- **Steps**:
  1. Identify tasks with no dependencies (nodes with no outgoing edges).
  2. Select the task with the latest deadline.
  3. Assign priorities, remove the task, and repeat.

	![[Pasted image 20241211160103.png|200]]

## 6.4: Periodic Task Scheduling

### **EDF for Periodic Tasks**

- Tasks repeat at fixed intervals $T_i$.
- EDF guarantees feasibility if:
  - **Utilization $U$**: $U = \sum \frac{p_i}{T_i} \leq 1$.
- **Proof**: Utilization $U$ matches the load factor $u$.

### **Rate Monotonic Scheduling (RMS)**

- Tasks are assigned fixed priorities inversely proportional to their periods ($T_1 \leq T_2 \leq \ldots \leq T_n$).
- **Feasibility**:
  - Guaranteed if $U \leq n(2^{1/n} - 1)$.
  - For large $n$, $n(2^{1/n} - 1) \approx \ln(2) = 0.693$.

---

## Key Points to Remember

- **Earliest Deadline First (EDF)**:
  - Optimal when deadlines are feasible ($L_{\text{max}} \leq 0$).
  - Effective for periodic tasks if $U \leq 1$.
- **Moore-Hodgson Algorithm (MHA)**:
  - Focuses on minimizing unmet deadlines.
  - Removes tasks with the longest execution times when infeasible.
- **Lawler’s Algorithm**:
  - Addresses task precedence constraints optimally.
  - Selects tasks based on dependencies and deadlines.
- **Rate Monotonic Scheduling (RMS)**:
  - Best for static priority-driven periodic tasks.
  - Works well when $U$ is within threshold limits.
