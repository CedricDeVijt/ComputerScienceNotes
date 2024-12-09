## 8.1: Introduction to Concurrency

**Concurrency** involves the coordinated functioning of multiple processes in an operating system. It's essential because processes that share resources can result in incorrect program flow if not properly managed.

**Key Concepts:**

- **Mutual Exclusion**: Ensuring that only one process accesses a critical section at a time.
- **Critical Section**: A part of the program where shared resources are accessed.
- **Starvation (Livelock)**: A process never gets the chance to proceed because others are continuously favored.
- **Deadlocks**: Two or more processes are waiting indefinitely for each other to release resources.

## 8.2: Software-Based Solutions

### Approaches to Achieving Mutual Exclusion

1. **Software-Based Solutions**: Processes handle mutual exclusion themselves.
2. **Hardware-Based Solutions**: Special hardware instructions support mutual exclusion.
3. **OS and Programming Language Support**: The operating system or language provides mechanisms.

### Bit per Critical Section Approach

- **Idea**: Use a variable (bit) for each critical section to indicate if a process is present.
- **Process**:
  - Check if `bit == 0` before entering.
  - Set `bit = 1` upon entry.
  - Set `bit = 0` upon exit.
- **Issues**:
  - **Non-Atomic Operations**: Testing and setting the bit aren't atomic; interruptions can occur between them.
  - **Busy Waiting**: Processes constantly check the bit, consuming CPU resources.

	![[Pasted image 20241209141255.png|300]]
### Dekker's Algorithm

A pioneering solution for achieving mutual exclusion between two processes.

#### First Attempt

- **Use**: A global variable `turn` indicating whose turn it is to enter the critical section.
- **Issue**: Can cause delays for faster processes and may favor one process over the other.
	
	![[Pasted image 20241209142936.png|500]]

#### Second Attempt

- **Use**: Individual flags `flag[0]` and `flag[1]` to show intent to enter the critical section.
- **Issue**: Mutual exclusion isn't guaranteed if a process is interrupted after the while loop.
	
	![[Pasted image 20241209142956.png|500]]

#### Third Attempt

- **Modification**: Switch the order of setting the flag and checking the other's flag.
- **Issue**: Can lead to a **deadlock** where both processes are stuck indefinitely.
	
	![[Pasted image 20241209143020.png|500]]

#### Fourth Attempt

- **Addition**: Introduce a pause mechanism to reset the flag and retry after some delay.
- **Issue**: **Unbounded Waiting Time**; no guarantee on when a process can proceed.
	
	![[Pasted image 20241209143044.png|500]]
	
#### Final Solution

- **Combination**: Use both `flag` variables and a `turn` variable.
- **Mechanism**:
  - If both processes want to enter, one yields based on the `turn` variable.
- **Properties**:
  - **Ensures Mutual Exclusion**.
  - **Prevents Deadlocks**.
  - **Not Easily Scalable** to multiple processes.
	
	![[Pasted image 20241209143104.png|500]]

### Peterson's Algorithm

An elegant solution that works for two or more processes.

#### Two-Process Version

- **Process**:
  - Set `flag[i] = true` to indicate intent.
  - Set `turn = j` to allow the other process to proceed if needed.
  - Wait while `flag[j]` is true and `turn == j`.
- **Advantages**:
  - **Simple** and easy to understand.
  - **Ensures Mutual Exclusion**.

	![[Pasted image 20241209143355.png|400]]

#### N-Process Version

- **Mechanism**:
  - Each process goes through `n-1` phases.
  - Uses `flag[i]` and `turn[j]` variables for synchronization.
- **Concept**:
  - Processes wait at each stage unless they're allowed to proceed.
- **Note**: Requires more complex management but achieves mutual exclusion for multiple processes.

	![[Pasted image 20241209143417.png|400]]
## 8.3: Hardware-Based Solutions

### Disabling Interrupts

- **Method**: Prevent context switches during the critical section by disabling interrupts.
- **Disadvantages**:
  - **Not Suitable** for large critical sections.
  - **Limited** to single-processor systems.

	![[Pasted image 20241209145430.png|300]]

### Machine Instruction Support (Spinlocks)

- **Atomic Instructions**:
  - **Test-and-Set**: Tests and sets a variable atomically.
  - **Exchange**: Atomically swaps values.
- **Characteristics**:
  - **Busy Waiting**: Processes loop until the lock is available.
  - **No Starvation Guarantees**: Processes may wait indefinitely.

### Semaphores

Introduced by **Dijkstra**, semaphores are synchronization tools used to control access to shared resources.

![[Pasted image 20241209145541.png|500]]

#### Counting Semaphores

- **Components**:
  - `count`: An integer representing resource availability.
- **Operations**:
  - **Wait (P operation)**:
    - Decrements `count`.
    - If `count < 0`, the process blocks.
  - **Signal (V operation)**:
    - Increments `count`.
    - If `count ≤ 0`, a blocked process is unblocked.
- **Use Case**: Managing access to multiple instances of a resource.

#### Binary Semaphores

- **Characteristics**:
  - `count` can be either `0` or `1`.
- **Equivalent** to mutex locks.
- **Use Case**: Ensuring mutual exclusion.

### Implementing Semaphores

- **Atomicity**: `wait(s)` and `signal(s)` must be atomic operations.
- **Implementation Methods**:
  - **Hardware Instructions**: Utilize atomic machine instructions like test-and-set.
  - **Short Operations**: Keep semaphore operations concise to minimize busy waiting.
- **Disadvantages**:
  - **Busy Waiting**: Processes may consume CPU cycles while waiting.
  - **Interrupt Handling**: Disabling interrupts isn't practical in multi-processor systems.

#### Mutual Exclusion with Semaphores

- **Initialization**: Semaphore `s` is set to `1`.
- **Protocol**:
  - **Entry**: `wait(s);`
  - **Critical Section**
  - **Exit**: `signal(s);`

	![[Pasted image 20241209150706.png|300]]

## 8.4: Producers/Consumers Problem

### Problem Description

- **Producers** generate data and place it in a buffer.
- **Consumers** take data from the buffer.
- **Challenges**:
  - **Synchronization**: Ensure producers and consumers access the buffer correctly.
  - **Mutual Exclusion**: Protect shared variables (`in`, `out`, `buffer`).

### Implementation with Semaphores

#### Using Counting Semaphores

- **Semaphores**:
  - `s`: Mutual exclusion semaphore.
  - `n`: Counts the number of items in the buffer.

#### Producer Process

```pseudo
repeat
   produce item v;
   wait(s);
   append v to buffer;
   signal(s);
   signal(n);
forever;
```

#### Consumer Process

```pseudo
repeat
   wait(n);
   wait(s);
   remove item w from buffer;
   signal(s);
   consume item w;
forever;
```

#### Considerations

- **Avoid Deadlocks**: Order of `wait` operations is crucial.
- **Multiple Consumers/Producers**: The solution works with multiple consumers and producers.

## 8.5: Readers/Writers Problem

### Problem Description

- **Readers**: Processes that only read the shared data.
- **Writers**: Processes that modify the shared data.
- **Constraints**:
  - Multiple readers can read simultaneously.
  - Writers require exclusive access.

### Standard Implementation with Semaphores

#### Variables and Semaphores

- `rcount`: Number of active readers.
- `x`: Semaphore for mutual exclusion of `rcount`.
- `wsem`: Semaphore to ensure writers have exclusive access.

#### Reader Process

```pseudo
wait(x);
   rcount := rcount + 1;
   if rcount = 1 then wait(wsem);
signal(x);
READ;
wait(x);
   rcount := rcount - 1;
   if rcount = 0 then signal(wsem);
signal(x);
```

#### Writer Process

```pseudo
wait(wsem);
WRITE;
signal(wsem);
```

#### Considerations

- **Reader Priority**: This solution may cause writers to starve if readers are continuously present.
- **Mutual Exclusion**: `rcount` is protected using semaphore `x`.

### Writer-Priority Implementation

- **Additional Semaphores**:
  - `rsem`: Controls entry of readers when writers are waiting.
  - `y`: Semaphore for mutual exclusion of `wcount`.
- **Variables**:
  - `wcount`: Number of waiting writers.

#### Adjusted Reader Process

```pseudo
wait(rsem);
wait(x);
// Same as standard reader process
signal(x);
signal(rsem);
```

#### Adjusted Writer Process

```pseudo
wait(y);
   wcount := wcount + 1;
   if wcount = 1 then wait(rsem);
signal(y);
wait(wsem);
WRITE;
signal(wsem);
wait(y);
   wcount := wcount - 1;
   if wcount = 0 then signal(rsem);
signal(y);
```

#### Considerations

- **Writer Priority**: Prevents writer starvation by giving writers precedence over readers.
- **Increased Complexity**: Additional semaphores and variables are required.

## Key Points to Remember

- **Concurrency** is essential for managing multiple processes that share resources.
- **Mutual Exclusion** ensures that only one process accesses a critical section at a time.
- **Dekker's Algorithm** was the first correct solution to the mutual exclusion problem for two processes.
- **Peterson's Algorithm** simplifies mutual exclusion and can be extended to multiple processes.
- **Semaphores** are fundamental synchronization tools with `wait` and `signal` operations.
- **Counting Semaphores** allow multiple processes to access a resource up to a maximum limit.
- **Binary Semaphores** (mutex locks) ensure exclusive access to a resource.
- In the **Producers/Consumers Problem**, synchronization prevents race conditions between producers and consumers.
- The **Readers/Writers Problem** requires careful management to prevent starvation of either readers or writers.
- **Busy Waiting** and **Deadlocks** are key issues to be aware of in concurrency control.

## Highlighted Sections for Study

- **Concurrency**: Coordinated functioning of multiple processes.
- **Mutual Exclusion**: Critical for preventing race conditions.
- **Critical Section**: Code segment accessing shared resources.
- **Dekker's Algorithm**: Early mutual exclusion solution.
- **Peterson's Algorithm**: Simplified and extensible algorithm.
- **Semaphores**: Tools for process synchronization.
- **Counting vs. Binary Semaphores**: Differences in resource management.
- **Producers/Consumers Problem**: Classic synchronization challenge.
- **Readers/Writers Problem**: Balancing access between readers and writers.
- **Busy Waiting**: Inefficient waiting by looping.
- **Deadlock**: Processes stuck waiting indefinitely.
